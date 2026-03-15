# CerberAuth CI/CD

Shared GitHub Actions workflows and composite actions for CerberAuth projects.

## Actions

### `actions/codeql`

Runs CodeQL static analysis for a given language.

### `actions/go-build-test`

Lints, builds, tests, and uploads coverage for a Go project.

### `actions/releaser`

Publishes a Go project via GoReleaser with Docker Hub, GHCR, Snapcraft, and Chocolatey.

## Reusable Workflows

### `golang-codeql.yml`

Runs CodeQL analysis for Go projects (analyzes both `go` and `actions` languages).

## License

[MIT](./LICENSE)
