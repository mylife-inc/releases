# releases

Public artefacts for projects whose source is private.

Each product owns a directory and a tag prefix. Nothing here is source; the
binaries are built from private repositories and published so that a
`curl … | sh` installer can reach them without a token.

| product | install | tags |
| --- | --- | --- |
| [CodeSeal](codeseal/) | `curl -fsSL https://raw.githubusercontent.com/mylife-inc/releases/main/codeseal/install.sh \| sh` | `codeseal-v*` |
| [Zellij](zellij/) | `brew install mylife-inc/tap/zel`, or the [pinned preview installers](zellij/README.md) | `zellij-v*` |

Zellij's development source is temporarily public. Its artifacts stay here so
installation remains independent of future source visibility. Its current
development preview requires the explicit version in its installation guide.

## Why the tags are prefixed

Several products share this repository, so `releases/latest` is whichever
product released most recently — not necessarily the one being installed. Each
installer asks for the release list and takes the newest tag carrying its own
prefix, skipping pre-releases unless you pin a version.

## Verifying a download

Every release carries `SHA256SUMS`. The installers verify it and refuse to
install when it is missing or does not match — they do not fall back to
installing an unverified binary. To check by hand:

```sh
shasum -a 256 -c SHA256SUMS
```
