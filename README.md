# IRON FIST CHRONICLES — Scroll Brawler

> A side-scrolling beat-em-up built in vanilla JavaScript (Canvas API).  
> Hand-crafted pixel sprites, Web Audio chiptune engine, and wave-based brawling combat.

**Developed by:** Ocampo, Jade Catherine, and Ochi, Nobutoshi
**Language:** JavaScript (HTML5 Canvas)  
**Course / Project:** Programming 2 — Game Sprint Project

---

 ## Table of Contents
 
- [Game Description](#game-description)
- [Features](#features)
- [Setup Instructions](#setup-instructions)
  - [Playing on Desktop / Laptop](#playing-on-desktop--laptop)
  - [Playing via GitHub Pages](#playing-via-github-pages)
- [Controls](#controls)
- [Gameplay Guide](#gameplay-guide)
- [Enemy Types](#enemy-types)
- [Boss Fight](#boss-fight)
- [Upgrades](#upgrades)
- [Code Structure](#code-structure)
- [Authors](#authors)
---
 
## Game Description
 
**IRON FIST CHRONICLES** is a wave-based side-scrolling beat-em-up where you fight through 5 stages of increasingly brutal street thugs, armed goons, and brutes — all leading up to a final showdown against the **Iron Lord**. Survive every stage, rack up kills, and post a high score.
 
The game features:
 
- Fully hand-drawn pixel art characters rendered in real time via Canvas 2D
- 5 distinct stages with unique enemy lineups and music tracks
- 4 enemy types with individual AI behaviors
- A level-up upgrade system with 7 stat boosts to choose from
- Chiptune Web Audio engine — all music and SFX generated programmatically
- CRT scanline + vignette post-processing overlay
- Parallax pixel-art city backgrounds with per-stage color themes
- Combo multiplier system for score bonuses
---
 
## Features
 
| Feature | Details |
|---|---|
| Main Menu | New Game and How to Play options |
| Core Gameplay Loop | Side-scroll brawler with delta-time physics |
| Game Over Screen | Final score, kills, stage reached |
| Wave / Stage System | 5 stages, each cleared by defeating all spawned enemies |
| Enemy AI | 4 types: Grunt, Knife, Gun, Brute |
| Boss System | Iron Lord final boss with ranged triple-shot at low HP |
| Upgrade System | 7 upgrades: Iron Fist, Iron Boot, Nova Blast, Iron Skin, Wind Step, Chi Flow, Eagle Jump |
| HUD | Live HP bar, XP bar, player level, stage counter, score, special cooldown |
| Combo System | Hit streak counter with score multiplier |
| Chiptune Audio | 3 music tracks + 8 SFX, all synthesized via Web Audio API |
 
---
 
## Setup Instructions
 
### Playing on Desktop / Laptop
 
No installation required. IRON FIST CHRONICLES runs entirely in your browser.
 
**Step 1 — Download the file**
 
Click the green `Code` button on this repository, then select **Download ZIP**. Extract the ZIP file to any folder on your computer.
 
**Step 2 — Open the game**
 
Find `Scroll-Brawler.html` inside the extracted folder. Double-click it. It will open directly in your default web browser (Chrome, Edge, or Firefox recommended).
 
**Step 3 — Play**
 
Click anywhere on the title screen or press **Enter** to reach the main menu, then click **NEW GAME** and start brawling.
 
> **Note:** No internet connection is required after downloading. No server, Node.js, or installs of any kind are needed.
 
---
 
### Playing via GitHub Pages
 
To host the game online so anyone can play it with just a link:
 
1. Push all project files to your GitHub repository
2. Make sure the game file is named `Scroll-Brawler.html`
3. Go to your repo on GitHub → **Settings** → **Pages**
4. Under **Source**, select `Deploy from a branch`
5. Choose branch: `main`, folder: `/ (root)` → click **Save**
6. Wait about 1 minute, then your game will be live at:
```
https://<your-username>.github.io/<your-repo-name>/Scroll-Brawler.html
```
 
---
 
## Controls
 
### Desktop Controls
 
| Input | Action |
|---|---|
| `A` or `←` | Move Left |
| `D` or `→` | Move Right |
| `W` / `↑` / `Space` | Jump |
| `J` | Punch |
| `K` | Kick |
| `L` | Special Attack |
| `P` | Pause / Unpause |
 
> Attacks auto-combo into enemies in range. Use **Special (L)** when surrounded — it hits a wide area but has a cooldown.
 
---
 
## Gameplay Guide
 
**Objective:** Fight through all 5 stages by defeating every enemy in each wave. The game ends when your HP reaches zero.
 
### Stage Progression
 
- Each stage spawns a set number of enemies before clearing (`goal` count per stage)
- Enemy speed, attack damage, and type variety increase each stage
- Completing a stage transitions automatically after a short delay
### Scoring
 
- **Grunt:** 100 pts × combo multiplier
- **Knife:** 100 pts × combo multiplier
- **Gun:** 100 pts × combo multiplier
- **Brute:** 300 pts × combo multiplier
- **Boss (Iron Lord):** 5,000 pts flat
### Combo System
 
- Chaining hits without taking damage builds a **COMBO** counter
- A multiplier based on your combo is applied to each kill's score
- Taking a hit or letting the combo timer expire resets it to zero
### HP System
 
- Your fighter starts with **100 HP** (upgradeable via Iron Skin)
- The HP bar turns yellow below 50% and red below 25%
- HP slowly regenerates per second if you've unlocked the **Chi Flow** upgrade
- Collect green **pill pickups** dropped by enemies to restore **+35 HP**
### Special Attack (L)
 
- Deals high AoE damage in a large forward arc
- Has a **~17-second cooldown** — the HUD shows the remaining time
- The cooldown can be reduced by upgrading the Nova Blast stat
---
 
## Enemy Types
 
| Type | Color | Behavior | HP | Threat Level |
|---|---|---|---|---|
| Grunt | Red | Direct pursuit, melee punch | 65 | Low |
| Knife | Purple | Fast mover, close-range lunge | 52 | Medium |
| Gun | Blue | Keeps distance, fires projectiles | 46 | Medium |
| Brute | Brown/Orange | Tanks hits, heavy melee | 170 | High |
 
- All enemies display an HP bar above them during combat
- Enemies flash when they take a hit
- Enemies that physically touch your fighter deal damage and knock you back
- Gun enemies fire blue projectiles — **jump over them** to dodge
- Brutes are slow but hit hard; use kick and special to stagger them
---
 
## Boss Fight
 
**Stage 5** replaces the normal enemy wave with a single powerful boss: the **Iron Lord**.
 
| Boss | HP | Shield | Special Attacks |
|---|---|---|---|
| ⚡ IRON LORD | 720 | None | 3-way spread shot when below 35% HP |
 
**Boss Mechanics:**
 
- **Phase Transition** — below 35% HP, the Iron Lord switches to a triple-shot spread that fires in 3 directions simultaneously
- **Crown & Armor** — visually distinct with a gold crown and shoulder armor plates
- A dedicated **boss HP bar** appears at the bottom of the screen during the fight
- Defeating the Iron Lord triggers the **Victory** screen
---
 
## Upgrades
 
When your player levels up (by earning XP from kills), you choose **1 of 3 randomly offered upgrades**:
 
| Icon | Name | Effect |
|---|---|---|
| 💪 | **Iron Fist** | Punch damage +15 |
| 🦵 | **Iron Boot** | Kick damage +20 |
| ⚡ | **Nova Blast** | Special damage +30 |
| ❤️ | **Iron Skin** | Max HP +50 (also heals +50 immediately) |
| 🌪 | **Wind Step** | Move speed +1.0 |
| 🌿 | **Chi Flow** | Adds HP regeneration per second |
| 🦅 | **Eagle Jump** | Jump power +3 |
 
- XP required per level scales up by ×1.65 each level
- Maximum player level is **5**
---
 
## Code Structure
 
```
iron-fist-chronicles/
├── Scroll-Brawler.html    ← Entire game (HTML + CSS + JavaScript)
└── README.md              ← This file
```
 
All game logic lives inside the `<script>` tag of `Scroll-Brawler.html`, organized into clearly separated sections:
 
| Section | Description |
|---|---|
| `scaleFrame()` | Responsive scaling — fits the 800×500 game frame to any screen size |
| Web Audio Engine | `playNote()`, `playDrum()`, `sfx()`, `playTrack()` — all sound synthesized via Web Audio API |
| `TRACKS[]` | 3 chiptune music tracks defined as note/duration arrays (Street Hustle, Warehouse Tension, Final Boss) |
| Title & Menu | `showMenu()`, `showGuide()`, splash canvas logo drawing |
| Game State `G` | Central state object — player, enemies, projectiles, sparks, score, level config |
| `mkPlayer()` | Player entity factory with stats object |
| Input Handling | `keydown` / `keyup` listeners — movement, attacks, pause |
| `update(dt)` | Per-frame logic — player, enemies, projectiles, pickups, combos, spawn logic, level checks |
| `updPlayer(dt)` | Player movement, jump, attack cooldowns, camera follow |
| `doAtk(type)` | Attack dispatch — creates hitbox, checks enemy overlaps, applies damage |
| `updEnemies(dt)` | Enemy AI — pursuit, range detection, melee/ranged attack logic |
| `spawnLogic(dt)` | Timed enemy spawning based on stage goal and current alive count |
| `checkLevel()` | Stage clear detection, boss spawn trigger, victory condition |
| `render()` | Master draw call — background, ground, pickups, projectiles, characters, sparks, HUD texts |
| `drawBG()` | Parallax pixel city — stars, moon, buildings, street lamps, fog, per-stage color theme |
| `drawCharacter()` | Procedural pixel-art character renderer — animated limbs, palette swap per enemy type |
| `showLvlUp()` | Level-up card UI — picks 3 random upgrades and renders selection buttons |
| `hudSync()` | Syncs HP bar, XP bar, score, stage, and special cooldown to DOM elements |
| `gameOver()` / `victory()` | End-state screens with stats |
 
---
