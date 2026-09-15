# Tasks

Keep this short and current. Delete finished work you don't need a
record of - this is a working list, not an audit log.

## Now

- [ ] ...

## Next

- [ ] Exercise a real `docker build` for all three Dockerfiles once a
      Docker daemon is available - only a structural review has been
      done so far.
- [ ] Add a basic smoke test (e.g. `helm template` diffed against a
      known-good snapshot) to catch accidental template regressions.

## Done

- [x] Consolidated from `charts`/`containers/docker-base`/
      `containers/static-assets`/`automation-toolkit`'s `scripts/` into
      one repo, fixing real bugs found in review (unresolved Dockerfile
      placeholders, non-deterministic PVC binding, a PV secretNamespace
      mismatch, `$VAR`-style files never applied by `helm install`,
      missing probes/resource requests) (2026-09-15)
- [x] Found real secrets in the old `charts` repo's history (Azure
      Storage key, Docker Hub password, DB password, basic-auth hash) -
      squashed that component's history instead of migrating it, rather
      than attempting per-secret redaction. Rotated separately outside
      this repo. (2026-09-15)
- [x] Dropped the CI/CD requirement from `main` - `advanced` branch keeps
      the full OIDC-based `build.yml`/`deploy.yml` pipeline (2026-09-15)
