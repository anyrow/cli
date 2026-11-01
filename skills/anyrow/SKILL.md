---
name: anyrow
description: "Call the Anyrow API API from the shell with anyrow: find a command, read its request and answer, call it, and branch on its JSON output and exit code."
---

# anyrow

## Find a command
- `anyrow commands` lists every command, one usage line each: `<path> <arg> --flag kind [--optional a|b] [--data json] (stream) # summary`.
- `anyrow commands search <words>` prints the 5 best matches.
- `anyrow schema <command>` prints its method and path, its `--data` body, its answer (`returns`) or `events`, and its error statuses with their keys.

## Before a call
Run `anyrow config` before a call that changes data: it prints each setting with its source and `target local|remote <host>`.
Settings come from a flag, else `$ANYROW_<NAME>`, else `~/.config/anyrow/config.toml`: `--base-url`, `--api-key`, `--timeout`, `--header "Name: value"`.

## Call
- `<arg>` is positional; `--data` takes JSON, `@file`, or `-` for stdin.
- Piped output is one line of compact JSON; `--format yaml|table|ndjson`, `-o <file>`, `-i` adds the status and headers.
- An error is one JSON line on stderr: `{"error":{"kind","status","errorKey","message"}}`.

## Streams
A stream command (sse) prints one JSON line per event; `--take N` ends it after N.

## Exit codes
0 ok, 1 a 4xx or other failure, 2 a 5xx, 3 no answer (transport, timeout, a dropped stream), 4 a usage error, 5 a redirect not followed, 130 interrupted.
