# Zellij by Shebka

The current development preview is **v0.2.0-rc.7**. This is the documentation
and product website engine, unrelated to the terminal multiplexer.

## macOS and Linux

```sh
brew install mylife-inc/tap/zel
```

Or install the native binary with an explicit preview version:

```sh
curl -fsSL https://github.com/mylife-inc/releases/releases/download/zellij-v0.2.0-rc.7/install.sh -o /tmp/zel-install.sh
ZEL_VERSION=v0.2.0-rc.7 sh /tmp/zel-install.sh
```

The shell installer selects Intel/x64 or ARM64 and installs into `~/.local/bin`
by default. Add that directory to your PATH if needed. Linux requires glibc.

## Windows PowerShell

```powershell
Invoke-WebRequest https://github.com/mylife-inc/releases/releases/download/zellij-v0.2.0-rc.7/install.ps1 -OutFile "$env:TEMP/zel-install.ps1"
& "$env:TEMP/zel-install.ps1" -Version v0.2.0-rc.7
```

The native installer supports x64 and ARM64 Windows and defaults to
`%LOCALAPPDATA%\Programs\Zellij\bin`. Add the directory to your user PATH.

Or install through the owned Scoop bucket:

```powershell
scoop bucket add mylife-inc https://github.com/mylife-inc/scoop-bucket
scoop install mylife-inc/zel
```

## Updates and channels

Homebrew installations update with `brew upgrade mylife-inc/tap/zel`.
Scoop installations update with `scoop update; scoop update zel`.
Standalone native installations can use `zel upgrade --preview` to select the
highest published version, including development previews. Without `--preview`,
self-upgrade selects stable releases only. Standalone shell/PowerShell
installers likewise require an explicit version to select a preview.

Do not treat an rc as a stable 1.0 release. If no stable Zellij release is
published, default stable lookup reports that fact instead of silently
installing a preview. Use the commands above during preview development.

Superseded pre-1.0 Zellij distributions are retired after their replacement and
active consumers pass verification. Old download links may therefore stop
working; source history and dated verification evidence are preserved. Other
products in this shared repository have their own release policies.

## Try the CLI

```sh
zel create my-docs
zel build my-docs
```

Edit `my-docs/content/` and open `my-docs/site/index.html` directly. Portable
web-only builds need no Node.js or container runtime. Hosted commands use a supported
container runtime and the CLI-matching engine image. Run `zel --help` for the
command reference or `zel explain` for the embedded authoring model.

## Templates

`zel templates` lists the bundled product documentation, hosted product page,
and classic reading-book starters. Creation works offline, records the exact
source revision and protects existing authored files:

```sh
zel create my-book -t book-classic --set 'author=Your name'
zel create my-product -t product-studio
```

Book-classic 0.2.0 includes a cover, preface, part, chapters and appendix.
`zel build my-book --pdf` publishes a matching PDF and download link with the
optional LuaLaTeX toolchain in Docker, Podman or nerdctl. PDF is off by default, and
`zel pdf my-book --check` checks compatibility without a runtime. The classic
print design supports English/LTR. rc.7 adds shared numbered equations, statement
and proof blocks, numeric citations, glossary and index across web and PDF.
Multilingual print and richer technical/study templates remain planned.
The hosted product template requires the normal engine runtime when building and an HTTP server when viewing.

Each release also contains a catalog and checksummed archives. They remain
available here independently of the development repository:

```sh
zel create my-docs -t product-docs@0.1.0 --catalog https://github.com/mylife-inc/releases/releases/download/zellij-v0.2.0-rc.7/templates-catalog.json
```

Add `--offline` to reuse an already cached catalog and archive. Local directories
are supported with `-t ./my-template`.

The [release](https://github.com/mylife-inc/releases/releases/tag/zellij-v0.2.0-rc.7)
contains six native archives, checksums, both installers and the generated
Homebrew formula and Scoop manifest, plus the template catalog and three archives. The [source repository](https://github.com/mylife-inc/Zellij)
records implementation and verification evidence. The binary remains governed
by the Zellij product's licensing; public downloads do not imply an open-source
license.
