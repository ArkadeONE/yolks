# Image builds

Every top-level directory has a workflow that builds each `<dir>/<tag>/Dockerfile` and pushes it to
GitHub Container Registry under this organisation:

| Workflow | Images |
|---|---|
| java | `ghcr.io/arkadeone/yolks:java_8` … `java_18j9` |
| nodejs | `ghcr.io/arkadeone/yolks:nodejs_12` … `nodejs_18` |
| python | `ghcr.io/arkadeone/yolks:python_3.7` … `python_3.11` |
| go | `ghcr.io/arkadeone/yolks:go_1.14` … `go_1.17` |
| oses | `ghcr.io/arkadeone/yolks:alpine`, `yolks:debian` |
| games | `ghcr.io/arkadeone/games:rust`, `games:source` |
| installers | `ghcr.io/arkadeone/installers:alpine`, `installers:debian` |

Tag names match upstream `ghcr.io/pterodactyl/*`, so an egg moves to these images by replacing the
namespace. Builds run on pushes that touch the directory, on manual dispatch, and weekly. amd64 only;
add `linux/arm64` to `platforms` (plus `docker/setup-qemu-action`) if you ever run an arm64 node.
Pushing with `GITHUB_TOKEN` needs the org's Actions "Workflow permissions" to allow write access to packages.
