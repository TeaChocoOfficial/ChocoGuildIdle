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

## Gameplay & How to Play

### Your Role
You are the **guildkeeper**—not the fighter. Characters act on their own; your job is to manage the guild: recruit members, equip weapons, upgrade stats, and decide when to push forward or retreat.

### Starting Out
1. You begin with **one character** and a small amount of gold.
2. The character automatically fights monsters in the current stage.
3. Gold earned goes into upgrading **stats** (HP, attack, defense, speed, etc.) or buying **weapons**.
4. Stronger characters unlock harder stages with better rewards.

### Characters
- **Recruitment**: Post a recruitment notice, wait, then choose to accept or decline up to 3 candidates.
- **Roster**: Each role slot (front / mid / back) holds one character. You can replace a character, but there is a fee/cooldown.
- **Stats**: Every character has unique randomized stats (seeded on the server—results are final).
- **Injury, not death**: When HP reaches zero, the character is **injured and rests**—they are not permanently lost.
- **Sleep & recovery**: Characters can be sent to sleep to restore HP and reduce drowsiness. Recovery is calculated when they wake.

### Combat
- Combat is **fully automatic**—you never control attacks.
- **Day/night cycle** changes which monsters appear.
- **Stage difficulty** is soft-gated: you *can* enter harder stages, but your character will barely scratch the monsters (and may be injured).
- **Permadeath is off**: losing means injury and time lost, not a lost character.

### Weight & Equipment
- Weapons have **weight** and **damage**.
- Carrying more weight than your character can handle slows attack speed, reduces accuracy, and lowers evasion.
- Heavier weapons hit harder but are slower—find the balance for each character.

### Status Effects
- Poison, burning, and bleeding deal damage over time (3 severity levels).
- **Status resistance** reduces the chance of being affected.
- Remedies can be bought from shops or found from monsters—they are limited, so use them wisely.

### Progression
- **Character level**: Grows from combat, unlocks skills and stat boosts.
- **Guild level**: Grows from the combined activity of all members, improves rare recruitment odds.
- **Stages**: Unlocked by both character level and in-game time.

### Social Features (Level 20+)
- Trade items with other players.
- Visit other players' homes and view profiles.
- Online chat and friend system.
- One account per device.

### Idle & Offline
- If you close the game, characters stop fighting but **continue recovering** HP over real time.
- When you return, recovery is calculated from the time you were away.

### Time in the Game
- **1 real day = 6 in-game minutes** (24 real minutes = 4 in-game days).
- The world clock is shared by all players—everyone experiences the same day, season, and time of day.
- **Day, evening, night, seasons, and dates** all affect monsters and rewards.

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

[x] Architecture planning
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
