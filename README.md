# Chatlytics Agent — Releases

Signed release feed for the Chatlytics Agent auto-updater. Binaries only (source is private).

Each release ships gent.exe and gent-tray.exe plus their .ed25519 detached signatures and a SHA256SUMS file. The agent's built-in updater verifies SHA-256 **and** the Ed25519 signature against its baked-in public key before installing — unsigned or tampered binaries are rejected.