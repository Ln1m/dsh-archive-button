# dsh-archive-button

[中文](README.md) · English

![Archive and restart buttons, including the two-click confirm state](assets/dsh-archive-button-restart-button.png)

*Mockup: layout rendered from the official theme tokens, not a screenshot of a running instance.*

An archive button on the sidebar's workspace-title row (it falls back to an inline footer capsule when that row is not mounted). The first click dry-runs a scan and lists the sessions idle for more than 3 days; the second click packs each one into a byte-verified zip and deletes the original folder. The host half registers the `/dsh-archive/*` routes and runs the archive script; the client half only draws the button. The model never triggers it.

## Install

```sh
dsh plugin --profile web add file:<this repo>
```

Restart the web instance afterwards.

## Environment

| Variable | Default | Purpose |
|---|---|---|
| `DSH_ROOT` | `~/DeepSeek_harness` | DSH install root; the archive script, archive directory and button log are all derived from it |

## Requirements

- Windows PowerShell 5.1
- `<DSH_ROOT>\scripts\archive-dsh-sessions.ps1` must be provided by you; this repo does not ship it
