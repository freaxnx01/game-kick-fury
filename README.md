# KICK FURY 🥊

A retro Amiga 500–style kickboxing game in a single HTML file. Canvas 320×200, pixel art, copper-bar gradients, chiptune-style sound via WebAudio. No build step, no dependencies, no server.

**Play:** open `index.html` — or the GitHub Pages URL once published.

## Game modes

- **[1] 1P vs CPU** — singleplayer against an AI opponent
- **[2] 2P local** — two players, one keyboard
- **[3] Online P2P** — WebRTC datachannel, serverless: players exchange connection codes manually (chat, email). Host runs the simulation; guest sends inputs and renders snapshots.

## Controls

| Action | Player 1 | Player 2 |
|--------|----------|----------|
| Move   | A / D    | ← / →    |
| Block  | S        | ↓        |
| Punch  | F        | K        |
| Kick   | G        | L        |

Enter = rematch, Esc = back to menu. Best of 3 rounds, 60 s each, KO or points.

## Online P2P notes

- Signaling is manual (copy/paste base64 SDP codes) — no backend needed, works on any static host like GitHub Pages.
- Uses a public STUN server only. Very strict NATs may fail to connect; adding a TURN server would fix that but requires infrastructure.
- Requires HTTPS (GitHub Pages provides this) or localhost for clipboard + WebRTC.

## Tech

- Single file: `index.html` (~22 KB). Only external asset: Google Fonts "Press Start 2P".
- Fixed 60 Hz logic loop, host-authoritative netcode with full-state snapshots.
- Pre-rendered arena background with dithered Amiga-style shading.
