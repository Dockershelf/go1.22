# go1.22

> **⚠️ ARCHIVED: This repository has been retired**
>
> **Go 1.22** reached End of Life on **11 Feb 2025** and is no longer receiving updates from upstream.
>
> ### What This Means
> - ❌ **No new builds** will be published to the Dockershelf APT repository
> - ❌ **No security updates** will be provided
> - ❌ **This repository is now read-only** (archived)
> - ✅ **Existing packages remain available** for download via `apt install`
> - ✅ **Docker images remain available** on GHCR
>
> ### Last Build Information
> - **Last successful build:** 2026-09-09
>
> ### Migration Path
> Please upgrade to a supported version:
> - **Go 1.23** (next remaining line)
> - **Go 1.27** (latest stable, recommended)
>
> See the [Dockershelf Go Pipeline](https://github.com/Dockershelf/go-pipeline) for currently supported versions.
>
> ### Support Policy
> Dockershelf follows upstream EOL schedules:
> - **Go:** [Release Policy](https://go.dev/doc/devel/release)
>
> ---
>
> _Archived on 2026-09-19 by the Dockershelf maintainers._

Debian packaging for Go 1.22: compiles the Go toolchain from the official [golang/go](https://github.com/golang/go) source tree into `golang-1.22-go` packages for enterprise `.deb`-only installs.

## Supported Debian suites

- `trixie`
- `unstable`

Packaging trees live under `debiandirs/<suite>/`. Changelog tracks:

- **mainline** — `changelogs/mainline/<suite>`

## Build (from workspace)

Clone or seed this repo as a sibling of `go-pipeline/`, then from `go-pipeline/`:

```bash
make materialize GO=1.22 DIST=trixie
make build GO=1.22
```

## Layout

| Path | Purpose |
|------|---------|
| `go/` | Go source tree (git submodule from golang/go, `release-branch.go1.22` branch) |
| `patches/` | Quilt series (applied via `gbp pq`) |
| `debiandirs/` | Per-suite Debian packaging (`trixie`, `unstable`) |
| `changelogs/` | `mainline` dch history per suite |
| `.github/workflows/main.yml` | Caller workflow for scheduled CI (seeded per minor line) |
