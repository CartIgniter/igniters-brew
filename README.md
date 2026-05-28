# CartIgniter Managed Homebrew Bundles

This repo contains the approved Brewfiles consumed by Epic Igniter C9:
`Epic Igniter - Managed Homebrew Bundles`.

## Layout

```text
bundles/
  allowlist.txt
  catalog.json
  base-cli.Brewfile
  cloud-cli.Brewfile
  data-cli.Brewfile
  dev-web.Brewfile
  dev-gui.Brewfile
  mobile-ios.Brewfile
  security-cli.Brewfile
```

## Mosyle Variables

```text
EPICIGNITER_BREW_BUNDLE=base-cli
EPICIGNITER_BREW_BUNDLE_REPO=https://github.com/CartIgniter/igniters-brew.git
EPICIGNITER_BREW_BUNDLE_REF=v2026.05.28.2
EPICIGNITER_BREW_NO_UPGRADE=1
EPICIGNITER_HOMEBREW_BOOTSTRAP=0
```

Use protected tags or pinned commits for production. Avoid using `main` for fleet-wide production assignment.

## Rules

- Every Brewfile item must also appear in `bundles/allowlist.txt`.
- Keep Brewfiles declarative: simple `tap`, `brew`, `cask`, `mas`, and `vscode` lines only.
- Casks are blocked by C9 unless Mosyle explicitly sets `EPICIGNITER_BREW_ALLOW_CASKS=1`.
- Required baseline apps, VPN/browser controls, privileged helpers, and managed settings stay in Mosyle/PKG/profile deployment.
