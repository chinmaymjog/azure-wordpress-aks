# azure-wordpress-aks

Application layer for the azure-wordpress-aks-infra platform: layered container images (`containers/docker-base`, `containers/static-assets`), a site image (`charts/Dockerfile`), a Helm chart (`charts/deploy`), and operator scripts (`scripts/`) for MySQL and Azure Files/Blob.

## Hard rules
- You have no cloud credentials. Never run `helm install/upgrade`, `kubectl`, `az`, `docker push`, or the `scripts/` against real systems; the owner deploys after review.
- Never commit secrets, passwords, connection strings, tokens, or real hostnames/IDs. Use placeholders; chart secrets must not be rendered in plaintext or unquoted.
- Don't change `.github/workflows/` unless the issue asks for it.
- Don't bump image/base-image or chart dependency majors unless the issue asks for it; pin versions rather than using `latest`.

## Working on issues
- Verify with `helm lint charts/deploy` and `helm template test charts/deploy` (same as CI in `.github/workflows/helm-lint.yml`); for shell changes run `bash -n <script>` and `shellcheck <script>`.
- Add or update docs (`README.md`, `docs/`) when behavior or usage changes.
- Keep changes minimal and scoped to the issue; one issue per PR.
- Open a PR against `main` that references the issue (`Fixes #N`). Never push to `main` directly.
