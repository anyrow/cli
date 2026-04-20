# Anyrow CLI

[![MIT License](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)

Command-line interface for the [Anyrow](https://anyrow.ai) API.

## Install

Download a prebuilt binary from [Releases](https://github.com/anyrow/cli/releases), or build from source:

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
