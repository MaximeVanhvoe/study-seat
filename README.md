# study-seat

**Automated library seat booking assistant for university students.**

Popular study spots fill within seconds of becoming available — especially in peak exam periods. study-seat monitors availability and books your preferred spot automatically at the configured time, so you don't lose out by not being at your keyboard at exactly the right moment.

## Features

- Monitors seat availability in real time
- Books your preferred seat automatically at a scheduled time
- Handles automatic check-in so your reservation isn't cancelled
- Supports multiple user accounts
- Runs on macOS and Windows (distributed as compiled binaries)

## Download

Get the latest version from the **[Releases page](../../releases/latest)**.

Each release includes:
- `study-seat.app` — macOS
- `study-seat.exe` — Windows
- `config.example.json` — configuration template

## Setup

1. Download the release for your platform.
2. Copy `config.example.json` to `config.json` and fill in your access token.
3. Launch the app, set your preferred seats and booking time.

## Why binary-only distribution?

The booking engine is not open-sourced. Publishing the automation logic would make it trivial to flood the reservation system with bulk requests, degrading availability for all students who use the library. By distributing compiled binaries and managing access via tokens, the tool stays fair and the shared infrastructure stays protected.

The configuration schema, issue templates, and any future CLI tooling in this repository are MIT-licensed.

## Reporting Issues

Found a bug? Open an [Issue](../../issues/new/choose). Please include:

- Your platform (macOS / Windows and version)
- What you expected to happen
- What actually happened
- The relevant lines from your log file (found in the app's settings menu)

## Roadmap

- [x] Automatic seat booking at scheduled time
- [x] Automatic check-in handling
- [x] Multi-account support
- [ ] **AI log analysis** — pipe failed booking logs to Claude for instant diagnosis
- [ ] **Issue triage assistant** — auto-categorize incoming GitHub issues by failure type (login / network / booking conflict) to speed up fixes

## License

MIT for everything in this repository.  
The booking engine binary is proprietary — see above for why.
