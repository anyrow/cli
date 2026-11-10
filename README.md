# Anyrow CLI

[![MIT License](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)

Command-line interface for the [Anyrow](https://anyrow.ai) API.

## Install

macOS and Linux:

```bash
curl -fsSL https://anyrow.ai/cli/install.sh | sh
```

Windows (PowerShell):

```powershell
irm https://anyrow.ai/cli/install.ps1 | iex
```

Both install the latest release to `~/.local/bin` and check the archive's sha256. When [cosign](https://docs.sigstore.dev/cosign/system_config/installation/) is on your `PATH`, they also verify the release's signature; set `ANYROW_INSTALL_VERIFY=require` to refuse an install without it. `ANYROW_VERSION` pins a version and `ANYROW_INSTALL_DIR` picks the directory.

Package managers:

```bash
brew install --cask anyrow/tap/anyrow                                                  # Homebrew
scoop bucket add anyrow https://github.com/anyrow/scoop-bucket && scoop install anyrow  # Scoop
winget install Anyrow.anyrow                                                           # winget
yay -S anyrow-bin                                                                      # AUR
```

`.deb`, `.rpm` and `.apk` packages and every archive are on [Releases](https://github.com/anyrow/cli/releases). From source:

```bash
go install github.com/anyrow/cli@latest
```

## Auth

Resolution order (high to low):

1. `--api-key <value>`
2. `ANYROW_API_KEY` env var
3. `~/.config/anyrow/config.toml` → `api_key = "..."`
4. `$XDG_CONFIG_HOME/anyrow/config.toml`

## Global flags

`--api-key`, `--base-url`, `--output` (json | ndjson | yaml | table), `--verbose`, `--config`, `--timeout`

## Exit codes

  0   success
  1   4xx client error
  2   5xx server error
  3   network failure / timeout
  4   bad flags / missing api-key
  5   unexpected 3xx

## Resources

- [OpenAPI spec](https://anyrow.ai/openapi.json)
- [TypeScript SDK](https://github.com/anyrow/sdk-typescript)
- [Go SDK](https://github.com/anyrow/sdk-go)
- [Python SDK](https://github.com/anyrow/sdk-python)
- [Rust SDK](https://github.com/anyrow/sdk-rust)

## License

MIT — see [LICENSE](./LICENSE).
