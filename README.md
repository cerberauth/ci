# CerberAuth CI/CD

Shared GitHub Actions workflows and composite actions for CerberAuth projects.

## Actions

### `actions/codeql`

Runs CodeQL static analysis for a given language.

### `actions/go-build-test`

Lints, builds, tests, and uploads coverage for a Go project.

### `actions/node-build-test`

Sets up Node.js, installs dependencies, then runs `format:check`, `lint` and
`ci-test`. Optional `coverage-command` and `codecov` / `codecov-token` inputs
add a coverage step and Codecov upload.

### `actions/releaser`

Publishes a Go project via GoReleaser with Docker Hub, GHCR, Snapcraft, and Chocolatey.

## Reusable Workflows

### `golang-codeql.yml`

Runs CodeQL analysis for Go projects (analyzes both `go` and `actions` languages).

### `argvio-metrics.yml`

Validates a CLI's `argvio.metrics.yaml` (the
[Argvio metric catalog](https://github.com/getargvio/argvio/blob/main/docs/metric-catalog.md))
with the `argvio` CLI. With `sync: true`, it also replaces the CLI's catalog
in Argvio through `PUT /v1/metric-definitions/{service}`, using the
`ARGVIO_METRICS_ADMIN_KEY` secret (the CLI tenant's `metrics_admin` key,
printed by `argvio-bootstrap` in `cerberauth/infrastructure`). Without the
secret the sync is skipped with a warning. Run it with `sync: false` on pull
requests and with `sync: true` on release.

### JavaScript / TypeScript actions

`vulnapi-action`, `jwtop-action` and `stubidp-action` share these:

- `action-ci.yml` — format check, lint, tests, coverage (`test-typescript` job).
  The caller keeps only its action-specific integration job.
- `action-check-dist.yml` — rebuilds `dist/` and fails if it is stale.
- `action-linter.yml` — super-linter run.
- `typescript-codeql.yml` — CodeQL for `typescript` and `actions`. `config-file`
  defaults to `.github/codeql/typescript-config.yml` in this repo, so consumers
  no longer need their own copy.
- `licensed.yml` — Licensed cache check / update.
- `action-release.yml` — on `release: published`, syncs the major-version tag
  (`v1`) and `releases/v1` branch.

## License

[MIT](./LICENSE)
