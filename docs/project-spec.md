# Problem

## What are you building, and why?

A containerized WordPress deployment for AKS - the application layer for
the `azure-wordpress-aks-infra` platform. WordPress is the reference
workload; the point is the platform pattern: a layered container build
and a Helm chart driving Kubernetes deployment.

## Goals

- Build and deploy WordPress onto AKS with a small number of copy-pasteable
  commands - no CI/CD setup required to get a working deployment.
- Keep the base runtime image, the shared plugin/theme pool, and any one
  site's own content as separately buildable, separately versioned layers.
- Pull images via AKS's managed identity, not a stored registry password.

## Non-Goals

- Automated CI/CD on this branch - see the `advanced` branch for the
  OIDC-based GitHub Actions pipeline.
- Multi-environment (dev/preprod/prod) support on this branch.

## Success Criteria

- `docker compose up --build` in `charts/` gives a working local WordPress
  site with no cloud dependency at all.
- The three `az acr build` + one `helm upgrade --install` commands in the
  README produce a working deployment on a cluster provisioned by
  `azure-wordpress-aks-infra`.

## Risks

- Real Azure cost once images are pushed to ACR and the chart is deployed
  - no free tier.
- The Helm `--set` flags for `deploy to your AKS cluster` need values
  pulled from three different places (Terraform outputs, Key Vault) -
  documented in the README, but a genuine multi-step manual process.

## Notes

- Local dev (`docker compose up`) needs no cloud account at all.
- See the main [README.md](../README.md) for the full walkthrough.
