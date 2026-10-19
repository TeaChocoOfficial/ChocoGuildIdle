# Choco Guild Idle

An idle fantasy RPG where you manage a guild from behind the scenes—send guild members to fight monsters automatically, upgrade their stats, manage weapons and inventory, and grow your guild. You never control characters directly; you only manage gear, trading, and team composition.

![Status](https://img.shields.io/badge/status-in%20development-yellow)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## About the Game

- **Genre**: Idle / Incremental / Fantasy RPG
- **Platform**: Web (Desktop + Mobile + Gamepad)
- **Language**: TypeScript across the stack
- **Theme**: Deep Green + Warm Gold (Choco = brown)

### Core Loop

```
Character auto-fights monsters → earns gold + materials → upgrade stats/buy weapons → grow stronger → unlock harder stages
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React + React Router v7 (Framework Mode, SSR for SEO) + Tailwind + Zustand + Zod + Axios |
| Graphics | PixiJS 8 + `@pixi/sound` + `pixijs-input-devices` |
| Fonts | DotGothic16 (Latin/Japanese/Cyrillic) + Ark Pixel Font (Chinese) + Noto Sans KR (Korean) + Thai pixel font (external) |
| i18n | `i18next-react-router` + `react-i18next` |
| Transport | Socket.IO + REST |
| Backend | NestJS (ESM) + `@idlekitjs/core` |
| Database | PostgreSQL + Drizzle |
| Rate Limit | `@nestjs/throttler` |
| Observability | `nestjs-observability` |

---

## Supported Languages

| Priority | Language | Pixel Font |
|----------|----------|------------|
| Primary | Thai | External Thai pixel font |
| Primary | English | DotGothic16 |
| High | Simplified Chinese | Ark Pixel Font |
| High | Japanese | DotGothic16 |
| Later | Korean | Noto Sans KR (non-pixel) |
| Later | Russian | DotGothic16 (Cyrillic supported) |

> Google Fonts has no Thai pixel font. Thai UI needs an external pixel font (e.g. ARMBOX MOON Night) or falls back to a standard Thai font.

---

## Project Structure

```
choco-guild-idle/
├── apps/
│ ├── client/ # React Router v7 + PixiJS 8
│ └── server/ # NestJS + IdleKit + Drizzle
├── packages/
│ └── shared/ # Types, Zod schemas, balance constants
├── README.md
└── package.json # pnpm workspace
```

## Environment

```
cp apps/server/.env.example apps/server/.env
cp apps/client/.env.example apps/client/.env
# Edit DATABASE_URL, JWT_SECRET, etc.
```

## Development

```
pnpm dev          # Run both client and server
pnpm dev:client   # http://localhost:5173
pnpm dev:server   # http://localhost:3000
```

## Database

```
pnpm db:generate   # Generate migration from schema
pnpm db:migrate    # Run migration
pnpm db:studio     # Open Drizzle Studio
```

## Build & Test

```
pnpm build
pnpm test
```

---

## Documentation

- **apps/client/README.md** — Client details
- **apps/server/README.md** — Server details
- **/document** — In-game calculation reference

---

## Development Status

[/] Architecture planning
[] Monorepo setup
[] Auth (login/register)
[] Server game loop + Socket.IO
[] Drizzle schema
[] Game page (PixiJS)
[] Character summoning system
[] Combat + weight system
[] /document page
[] Admin panel
[] i18n setup (TH / EN / ZH / JA)
[] Social features (level 20+)
[] Fishing / Farming / Animal raising

---

## License
MIT
