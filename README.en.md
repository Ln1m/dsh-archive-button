> A vk-free build lives on the [https://github.com/Ln1m/dsh-archive-button/tree/official](https://github.com/Ln1m/dsh-archive-button/tree/official); main is the dual-path version (official slots without vk-suite, vk layout seats with it).

# dsh-archive-button

[中文](README.md) · English

![Archive button in the sidebar workspace row](assets/dsh-archive-button.png)

*Screenshot of a running DSH instance; demo content is sanitized.*

An archive button on the sidebar's workspace-title row (it falls back to an inline footer capsule when that row is not mounted). The first click dry-runs a scan and lists the sessions idle for more than 3 days; the second click packs each one into a byte-verified zip and deletes the original folder. The host half registers the `/dsh-archive/*` routes and runs the archive script; the client half only draws the button. The model never triggers it.

## Install

```sh
dsh plugin --profile web add file:<this repo>
```

Restart the web instance afterwards.

## Environment

| Variable | Default | Purpose |
|---|---|---|
| `DSH_ROOT` | `~/DeepSeek_harness` | DSH install root; the archive directory and button log are derived from it |

## Requirements

- Windows PowerShell 5.1
- No vk-suite dependency: with vk-suite the button lands in `vk.sidebar.footer`; without it, in the official `sidebar.footer.action` slot
- The archive script ships with this repo (`scripts/archive-dsh-sessions.ps1`) and works as installed
- The bundled script wins; `<DSH_ROOT>\scripts\archive-dsh-sessions.ps1` is the fallback
- A session folder is deleted only after its zip is reopened and byte-verified
