<div align="center">

# ⚽ Sol Football

### Real-Time Physics-Based Football on Solana

[![Live Demo](https://img.shields.io/badge/Live%20Demo-solball.vercel.app-brightgreen?style=for-the-badge)](https://solball.vercel.app/)
[![GitHub](https://img.shields.io/badge/GitHub-Source%20Code-181717?style=for-the-badge&logo=github)](https://github.com/Amogh-007-Rin/SOL.FOOTBALL)
[![Solana](https://img.shields.io/badge/Blockchain-Solana-9945FF?style=for-the-badge&logo=solana)](https://solana.com/)
[![Next.js](https://img.shields.io/badge/Framework-Next.js%2014-000000?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

**Sol Ball** is a fast-paced, physics-driven **3v3 multiplayer football game** built on the **Solana blockchain** — inspired by the classic Haxball experience.  
Compete in real-time matches, stake SOL, and earn on-chain rewards for winning.

[Play Now](https://solball.vercel.app/) · [View Source](https://github.com/Amogh-007-Rin/SOL.FOOTBALL) · [Report Bug](https://github.com/Amogh-007-Rin/SOL.FOOTBALL/issues) · [Request Feature](https://github.com/Amogh-007-Rin/SOL.FOOTBALL/issues)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Core Features](#-core-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Running Locally](#running-locally)
- [How to Play](#-how-to-play)
- [Smart Contract](#-smart-contract)
- [Reward System](#-reward-system)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌐 Overview

Sol Ball bridges **real-time competitive gaming** and **on-chain finance** into a single seamless experience. Players connect their Solana wallets, deposit SOL into a smart contract escrow, and compete in 3v3 football matches — with winners receiving instant on-chain payouts.

The game is inspired by **Haxball**, a beloved browser-based football game, but supercharged with:

- ⚡ Real-time WebSocket-powered gameplay
- 🔗 Solana smart contracts for trustless escrow and settlements
- 🔒 Privy-powered authentication and wallet management
- 🏟️ A full lobby system for creating and joining matches

---

## ✨ Core Features

### ⚽ Real-Time 3v3 Multiplayer
- Physics-driven ball movement with realistic collisions
- Smooth latency handling for responsive online play
- Up to 6 simultaneous players per match (3 per team)
- Player movement via keyboard controls (WASD / Arrow Keys)

### 💰 On-Chain Deposits & Rewards
- Deposit SOL directly from your connected wallet before a match
- Funds are locked in an on-chain escrow contract for the match duration
- Instant payouts distributed to winners upon match settlement
- Transparent 80/20 reward split (see [Reward System](#-reward-system))

### 🔒 Privy Wallet Integration
- Seamless authentication via [Privy.io](https://privy.io)
- Supports popular Solana wallets:
  - 👻 Phantom
  - 🌞 Solflare
  - 🎒 Backpack
- Non-custodial: players retain full control of their funds

### 🧩 Lobby System
| Feature | Details |
|---------|---------|
| Lobby Name | Custom display name set by the creator |
| Entry Fee | Configurable SOL amount per player |
| Visibility | Public (open to all) or Private (invite only) |
| Capacity | 3v3 — 6 players per lobby |
| Host Controls | Start match or cancel the lobby |

### 🧠 Fair On-Chain Logic
- Escrow and settlement handled by a verified **Anchor** smart contract
- Transparent match validation ensures no party can manipulate results
- All on-chain logic is open-source and auditable

### 🎨 Clean UI/UX
- Built with **Tailwind CSS** and **shadcn/ui**
- Responsive design optimised for both desktop and mobile
- Minimal, distraction-free interface focused on gameplay

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| Next.js 14 | Frontend framework (App Router) |
| React 19 | UI component layer |
| TypeScript | Type safety across the codebase |
| Tailwind CSS | Utility-first styling |
| shadcn/ui | Accessible, composable UI components |

### Blockchain & Web3
| Technology | Purpose |
|-----------|---------|
| Solana Web3.js | Blockchain interaction and transaction building |
| Anchor Framework | Smart contract development and IDL generation |
| Privy SDK | Wallet authentication and embedded wallet support |

### Backend & Infrastructure
| Technology | Purpose |
|-----------|---------|
| Node.js | Game server and lobby management |
| WebSockets | Real-time bidirectional gameplay communication |
| Supabase | Player sessions, matchmaking data, and persistence |

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        CLIENT (Browser)                     │
│  Next.js 14 · React 19 · Tailwind CSS · Privy SDK          │
└──────────────────────────┬──────────────────────────────────┘
                           │
          ┌────────────────┴────────────────┐
          │                                 │
          ▼                                 ▼
┌─────────────────┐               ┌──────────────────┐
│  Node.js Game   │◄─ WebSocket ─►│  Supabase        │
│  Server         │               │  (Sessions &     │
│  (Lobby + Game  │               │   Matchmaking)   │
│   State)        │               └──────────────────┘
└────────┬────────┘
         │
         ▼
┌─────────────────────────────────────────────────────────────┐
│                     SOLANA BLOCKCHAIN                       │
│  Anchor Smart Contract · Escrow Program · Payout Logic      │
└─────────────────────────────────────────────────────────────┘
```

**Data Flow:**
1. Player connects wallet via Privy → authenticates session
2. Lobby created → entry fee deposited into on-chain escrow
3. Match starts → real-time game state synced via WebSockets
4. Match ends → server signals result to smart contract
5. Smart contract settles → rewards distributed to winners instantly

---

## 🚀 Getting Started

### Prerequisites

Ensure the following are installed on your machine:

- [Node.js](https://nodejs.org/) `v18+`
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- [Rust](https://www.rust-lang.org/tools/install) (for Anchor / smart contract development)
- [Anchor CLI](https://www.anchor-lang.com/docs/installation) `v0.29+`
- [Solana CLI](https://docs.solana.com/cli/install-solana-cli-tools) `v1.18+`
- A Solana wallet (Phantom, Solflare, or Backpack) funded with Devnet SOL for testing

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/Amogh-007-Rin/SOL.FOOTBALL.git
cd SOL.FOOTBALL
```

**2. Install frontend dependencies**
```bash
npm install
# or
yarn install
```

**3. Install game server dependencies**
```bash
cd server
npm install
```

**4. Build the Anchor smart contract**
```bash
cd programs/sol-ball
anchor build
```

### Environment Variables

Create a `.env.local` file in the project root and populate the following:

```env
# Privy Authentication
NEXT_PUBLIC_PRIVY_APP_ID=your_privy_app_id

# Solana Network
NEXT_PUBLIC_SOLANA_RPC_URL=https://api.devnet.solana.com
NEXT_PUBLIC_SOLANA_NETWORK=devnet

# Smart Contract
NEXT_PUBLIC_PROGRAM_ID=your_anchor_program_id

# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Game Server
NEXT_PUBLIC_GAME_SERVER_URL=ws://localhost:8080
```

### Running Locally

**Start the frontend:**
```bash
npm run dev
```

**Start the game server:**
```bash
cd server
node index.js
```

**Deploy the smart contract to Devnet:**
```bash
anchor deploy --provider.cluster devnet
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🎮 How to Play

### Step 1 — Connect Your Wallet
Visit [solball.vercel.app](https://solball.vercel.app/) and log in using Privy or a supported Solana wallet (Phantom, Solflare, or Backpack).

### Step 2 — Create or Join a Lobby
- **Create:** Set a lobby name, choose an entry fee in SOL, and set visibility (Public/Private).
- **Join:** Browse public lobbies or enter a private lobby code.

### Step 3 — Deposit Funds
Once in a lobby, deposit the required SOL entry fee. Funds are locked into the on-chain escrow — safe until the match concludes.

### Step 4 — Play
When all 6 players are ready, the host starts the match.

| Control | Action |
|---------|--------|
| `W` / `↑` | Move Up |
| `S` / `↓` | Move Down |
| `A` / `←` | Move Left |
| `D` / `→` | Move Right |

Score goals and outplay your opponents in real-time physics-driven gameplay.

### Step 5 — Match Settlement
When the match ends, the result is submitted to the smart contract for on-chain verification and settlement.

### Step 6 — Withdraw Rewards
Winners can instantly withdraw their balance from their Solana sub-account at any time.

---

## 📄 Smart Contract

The Sol Ball smart contract is built using the **Anchor Framework** on Solana.

### Key Instructions

| Instruction | Description |
|-------------|-------------|
| `initialize_match` | Creates an escrow account and records player deposits |
| `deposit` | Locks player funds into the escrow for the match duration |
| `settle_match` | Validates the match result and distributes rewards |
| `cancel_match` | Returns all deposits to players if the match is cancelled |

### Security Properties
- All funds held in a Program Derived Address (PDA) escrow — no central custody
- Match settlement requires a trusted authority signature (the game server)
- Cancel functionality ensures players are never locked out of funds

---

## 💸 Reward System

The total prize pool is the sum of all player entry fees.

```
Total Pool = Entry Fee × 6 Players

Winners' Share  = 80% of Total Pool  → split equally among the 3 winning players
Platform Fee    = 20% of Total Pool  → sent to the game owner's wallet
```

**Example — 0.1 SOL entry fee:**

| | Amount |
|-|--------|
| Total Pool | 0.6 SOL |
| Each Winner Receives | 0.16 SOL |
| Platform Fee | 0.12 SOL |

---

## 🗺 Roadmap

### ✅ Completed
- [x] Real-time 3v3 multiplayer with physics engine
- [x] Privy wallet integration (Phantom, Solflare, Backpack)
- [x] On-chain escrow and match settlement via Anchor
- [x] Public/Private lobby system
- [x] SOL deposit and withdrawal flow
- [x] Responsive UI with Tailwind CSS + shadcn/ui

### 🔄 In Progress
- [ ] Global and lobby-specific chat via WebSockets
- [ ] Leaderboards (wins, goals, total earnings)

### 📅 Planned
- [ ] **Referral Program** — Unique referral codes with commission rewards for onboarding new players
- [ ] **Skill-Based Matchmaking** — ELO-based ranked system with seasonal rewards
- [ ] **Custom Avatars & Skins** — Cosmetic items purchasable with SOL or SPL tokens
- [ ] **Multi-Token Support** — Allow entry fees and rewards in SPL tokens beyond native SOL
- [ ] **Spectator Mode** — Watch live matches without participating
- [ ] **Tournament Mode** — Bracket-style competitions with pooled prize pots

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature-name`
3. **Commit** your changes: `git commit -m 'feat: add your feature'`
4. **Push** to your branch: `git push origin feature/your-feature-name`
5. **Open** a Pull Request

Please ensure your code follows the existing TypeScript conventions and that any smart contract changes are accompanied by updated tests.

### Development Guidelines
- Use `npm run lint` to check for linting issues before committing
- Smart contract changes must include Anchor tests under `tests/`
- UI changes should be tested on both desktop and mobile viewports

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Built with ❤️ on Solana · [solball.vercel.app](https://solball.vercel.app/)

</div>
