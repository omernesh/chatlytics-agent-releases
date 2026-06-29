# Chatlytics Agent — Releases

Signed release feed for the Chatlytics Agent auto-updater. Binaries only (source is private).

## Download & install

### Windows
Download **ChatlyticsAgentSetup.exe** from the [latest release](../../releases/latest) and run it. Sign in with your Chatlytics username and password when prompted (or approve from a browser).

### Linux — one file (recommended)
The single binary is self-installing. Download it and run its built-in `setup`:

```bash
curl -fLO https://github.com/omernesh/chatlytics-agent-releases/releases/latest/download/agent-linux-amd64
chmod +x agent-linux-amd64
sudo ./agent-linux-amd64 setup
```

*(Raspberry Pi / ARM: download `agent-linux-arm64` instead.)*

`setup` signs you in, installs a background service, and starts it — one command.

**Installing over SSH on a headless server?** `setup` prints a link you open on your **phone or laptop** to approve — there's no local browser to open, and **no auth code to copy back**. It just works.

### Linux — Debian / Ubuntu / Raspberry Pi OS (`.deb`)
```bash
curl -fLO https://github.com/omernesh/chatlytics-agent-releases/releases/latest/download/chatlytics-agent-amd64.deb
sudo apt install ./chatlytics-agent-amd64.deb
sudo chatlytics-agent login --browser      # approve from any device — also enables & starts the service
```
*(ARM: `chatlytics-agent-arm64.deb`.)*

### Linux — Fedora / RHEL / openSUSE (`.rpm`)
```bash
curl -fLO https://github.com/omernesh/chatlytics-agent-releases/releases/latest/download/chatlytics-agent-x86_64.rpm
sudo dnf install ./chatlytics-agent-x86_64.rpm
sudo chatlytics-agent login --browser      # approve from any device — also enables & starts the service
```
*(ARM: `chatlytics-agent-aarch64.rpm`.)*

### Linux — script install (alternative)
Auto-detects Intel/AMD vs ARM, verifies the download, installs the service:
```bash
curl -fsSL https://github.com/omernesh/chatlytics-agent-releases/releases/latest/download/install.sh | sudo bash
```

After any method, your device appears on the **Proxy Devices** page in the Chatlytics web app.

## What's in each release

- **Windows:** `agent.exe`, `agent-tray.exe`, `ChatlyticsAgentSetup.exe`
- **Linux (single binary):** `agent-linux-amd64`, `agent-linux-arm64` — self-installing via `setup`
- **Linux (packages):** `chatlytics-agent-amd64.deb` / `chatlytics-agent-arm64.deb`, `chatlytics-agent-x86_64.rpm` / `chatlytics-agent-aarch64.rpm` (version-less stable names; version-pinned copies are also attached)
- **Linux (script):** `install.sh`, `uninstall.sh`
- Detached **`.ed25519`** signatures for every binary, plus a **`SHA256SUMS`** file.

The agent's built-in updater verifies SHA-256 **and** the Ed25519 signature against its baked-in public key before installing — unsigned or tampered binaries are rejected. The `.deb`/`.rpm` packages carry their own package-manager integrity.
