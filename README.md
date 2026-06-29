# Chatlytics Agent — Releases

Signed release feed for the Chatlytics Agent auto-updater. Binaries only (source is private).

## Download

**Windows** — download **ChatlyticsAgentSetup.exe** from the [latest release](../../releases/latest) and run it.

**Linux** (server, mini-PC, Raspberry Pi) — run the installer one-liner. It auto-detects Intel/AMD vs ARM, verifies the download, and installs a background service:

    curl -fsSL https://github.com/omernesh/chatlytics-agent-releases/releases/latest/download/install.sh | sudo bash

Or download **agent-linux-amd64** / **agent-linux-arm64** plus **install.sh** manually and run `sudo bash install.sh --local ./agent-linux-amd64`.

After install, the device appears on the **Proxy Devices** page in the Chatlytics web app.

## What's in each release

- **Windows:** `agent.exe`, `agent-tray.exe`, `ChatlyticsAgentSetup.exe`
- **Linux:** `agent-linux-amd64`, `agent-linux-arm64`, `install.sh`, `uninstall.sh`
- Detached **`.ed25519`** signatures for every binary, plus a **`SHA256SUMS`** file.

The agent's built-in updater verifies SHA-256 **and** the Ed25519 signature against its baked-in public key before installing — unsigned or tampered binaries are rejected.
