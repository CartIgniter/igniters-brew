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
EPICIGNITER_BREW_BUNDLE_REF=v2026.05.29.3
EPICIGNITER_BREW_NO_UPGRADE=1
EPICIGNITER_HOMEBREW_BOOTSTRAP=0
```

Use protected tags or pinned commits for production. Avoid using `main` for fleet-wide production assignment.

## Rules

- Every Brewfile item must also appear in `bundles/allowlist.txt`.
- Keep Brewfiles declarative: simple `tap`, `brew`, `cask`, `mas`, and `vscode` lines only.
- Casks are blocked by C9 unless Mosyle explicitly sets `EPICIGNITER_BREW_ALLOW_CASKS=1`.
- Required baseline apps, VPN/browser controls, privileged helpers, and managed settings stay in Mosyle/PKG/profile deployment.

## Strict Mode Direction

Current C9 controls what Mosyle installs; it does not by itself prevent direct user-run Homebrew installs after Homebrew exists in a user-writable prefix.

For hard allowlist enforcement, move to this user workflow:

```bash
igniter-brew list
igniter-brew bundles
igniter-brew install ripgrep
igniter-brew install-bundle mobile-ios
```

Strict mode requirements:

- Homebrew is installed under a managed/root-controlled prefix or service account.
- Users do not get direct write access to the Homebrew prefix.
- Direct `brew install <package>` is blocked or unavailable to standard users.
- `igniter-brew` validates requested packages against `bundles/allowlist.txt`.
- Approved installs are logged and receipted.
