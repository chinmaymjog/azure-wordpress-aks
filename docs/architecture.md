# Architecture

## What This Is

Three layered container images (`docker-base`, `static-assets`, and a
site-specific image that builds on both) plus a Helm chart that deploys
the site image onto AKS. See the diagram in `README.md`.

## How It Works

1. `docker-base` is the hardened WordPress + PHP-FPM/Apache runtime,
   built and pushed independently since it changes on its own cadence.
2. `static-assets` packages a common pool of plugins/themes, also built
   independently - content updates don't require rebuilding the base.
3. `charts/Dockerfile` builds the actual site image: `docker-base` +
   whichever of `static-assets`' plugins/themes this site's
   `charts/pkg-mgr/plugins.list`/`themes.list` selects + this site's own
   `charts/src/wp-content`.
4. `helm upgrade --install charts/deploy` renders a Namespace, Secrets
   (basic-auth gate + Azure Files storage key), a PV/PVC backed by an
   Azure Files share, a Deployment, a Service, and an Ingress - one
   command applies everything, no separate `kubectl apply` step needed.

## Key Decisions

- **Decision:** No CI/CD pipeline on this branch - `az acr build` and
  `helm upgrade --install` run by hand, documented as copy-pasteable
  commands in the README.
  **Why:** Getting a working deployment shouldn't require an Azure AD
  app registration and 8 GitHub secrets/variables first.
  **Revisit if:** You're deploying often enough that the manual commands
  get tedious - the `advanced` branch has the full pipeline.
- **Decision:** `imagePullSecrets` is conditional on a values flag,
  unset by default.
  **Why:** AKS's kubelet identity already has `AcrPull` on the registry
  (see the infra repo) - no pull secret needed for the default path.
  **Revisit if:** You're pulling from a registry other than the one the
  infra repo provisions.
- **Decision:** `namespace.yaml`/`secret.yaml` are real Helm templates
  (`{{ .Values.x }}`), not `envsubst`-style `$VAR` files applied
  separately.
  **Why:** One `helm upgrade --install` should apply everything - no
  hidden pre-processing step for anyone new to the repo to discover.
  **Revisit if:** Never - this is strictly simpler than the alternative.

## Known Risks / Rough Edges

- The Helm deploy command's `--set` flags need values pulled from three
  different places (Terraform outputs, Azure CLI, Key Vault) - documented
  in the README, but a genuine multi-step manual process the first time.
- No automated tests for the Dockerfiles or the chart beyond `helm lint`/
  `helm template` - `docs/tasks.md` tracks this as a known gap.
- Docker builds haven't been exercised against a live Docker daemon in
  this environment (structural review only) - worth a real
  `docker build` before your first deploy if you haven't already.
