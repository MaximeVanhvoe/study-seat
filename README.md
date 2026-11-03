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
- `study-seat-macos.zip` — macOS (contains `study-seat.app`)
- `study-seat-windows.zip` — Windows (contains the `study-seat` folder with `study-seat.exe`)

## Setup

1. Download the release for your platform.
2. Copy `config.example.json` to `config.json` and fill in your access token.
3. Launch the app, set your preferred seats and booking time.

### macOS — "Not Opened" warning

Because study-seat is not distributed through the App Store, macOS will block it on first launch. To open it anyway:

**Option A — Right-click method (easiest)**
Right-click (or Control-click) the app → **Open** → click **Open** in the dialog that appears.

**Option B — System Settings**
Go to **System Settings → Privacy & Security**, scroll down, and click **Open Anyway** next to the study-seat entry.

**Option C — Terminal**
```bash
xattr -cr /path/to/study-seat.app
```
Then double-click as normal.

You only need to do this once.

### Windows — installing and first launch

1. Download `study-seat-windows.zip`.
2. **Unblock the zip before extracting:** right-click the zip → **Properties** → tick **Unblock** at the bottom → **OK**. Without this, Windows can refuse to load the app's components and it crashes on start.
3. **Extract the whole zip** (right-click → **Extract All…**) to a normal folder, e.g. `Documents\study-seat`. Do not run `study-seat.exe` from inside the zip: it needs the `_internal` folder next to it.
4. Open the extracted `study-seat` folder and double-click `study-seat.exe`.
5. If you see **"Windows protected your PC"** (SmartScreen): click **More info** → **Run anyway**. The app is not code-signed, so Windows shows this once.
6. If `study-seat.exe` disappears after extracting, Microsoft Defender flagged it as a false positive. Restore it via **Windows Security → Virus & threat protection → Protection history**.
7. If the window stays blank or white, install the free [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/) (Evergreen, x64) and start the app again.

Google Chrome must be installed for login and check-in. Windows 10 or 11 (64-bit) is required.

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
