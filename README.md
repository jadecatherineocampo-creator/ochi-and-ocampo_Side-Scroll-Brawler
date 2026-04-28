# IRON FIST CHRONICLES — Scroll Brawler

> A side-scrolling beat-em-up built in vanilla JavaScript (Canvas API).  
> Hand-crafted pixel sprites, Web Audio chiptune engine, and wave-based brawling combat.

**Developed by:** Ocampo, Jade Catherine and Ochi, Nobutoshi
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
- [Boss Wave](#boss-wave)
- [Upgrades](#upgrades)
- [Code Structure](#code-structure)
- [Authors](#authors)

---

## Game Description

**IRON FIST CHRONICLES** is a wave-based side-scrolling brawler where you fight through 5 stages of escalating street combat. Punch, kick, and unleash special attacks to clear each stage and face the Iron Lord in a climactic final boss fight.

The game features:

- Procedurally animated pixel-art characters drawn entirely via Canvas 2D primitives
- Three-attack combat system: Punch, Kick, and Special
- Four enemy types with distinct AI behaviors and attack patterns
- A level-up system with stat upgrade choices between stages
- Combo multiplier scoring
- Dynamic chiptune soundtrack with three handwritten tracks (Web Audio API)
- Full sound effects for all actions
- Responsive scaling to any screen size

---

## Features

| Feature | Details |
|---|---|
| Combat System | Punch, Kick, and Special attacks with individual cooldowns |
| Enemy AI | 4 types: Grunt, Knife, Gun, Brute — each with unique behavior |
| Boss Fight | Iron Lord on Stage 5 with multi-phase attacks and spread fire |
| Level-Up System | Earn XP per kill; choose from 3 random stat upgrades on level-up |
| Combo System | Consecutive hits multiply score; resets on taking damage |
| Chiptune Engine | 3 original tracks with lead melody, bass, and percussion (Web Audio) |
| Pixel Sprites | All characters drawn dynamically via Canvas 2D — no image assets |
| HUD | Live HP bar, XP bar, player level, stage counter, special cooldown, score |
| Pickup System | HP pills drop from defeated enemies (30% chance) |
| Persistent Camera | Smooth camera tracking with world scroll across 3000px stages |

---

## Setup Instructions

### Playing on Desktop / Laptop

No installation required. The game runs entirely in your browser.

**Step 1 — Download the file**

Click the green `Code` button on this repository, then select **Download ZIP**. Extract the ZIP file to any folder on your computer.

**Step 2 — Open the game**

Find `ScrollBrawl.html` (or `index.html`) inside the extracted folder. Double-click it. It will open directly in your default web browser (Chrome, Edge, or Firefox recommended).

**Step 3 — Play**

Click anywhere on the title screen or press **Enter** to start fighting.

> **Note:** No internet connection is required after downloading. No server, Node.js, or installs of any kind are needed.

---

### Playing via GitHub Pages

To host the game online so anyone can play it with just a link:

1. Push all project files to your GitHub repository
2. Make sure the game file is named `index.html` (or update the Pages source)
3. Go to your repo on GitHub → **Settings** → **Pages**
4. Under **Source**, select `Deploy from a branch`
5. Choose branch: `main`, folder: `/ (root)` → click **Save**
6. Wait about 1 minute, then your game will be live at:

```
https://<your-username>.github.io/<your-repo-name>/
```

Share this link for live demos or submissions.

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
| `P` | Pause / Resume |
| `Enter` | Start Game (title screen) |

> Special Attack has a longer cooldown. Watch the **SPECIAL RDY** indicator in the HUD before committing.

---

## Gameplay Guide

**Objective:** Fight through 5 stages of enemies. Clear all enemies in a stage to advance. The game ends when your HP reaches zero.

### Wave Progression

- Each stage spawns more enemies than the last, with more dangerous types introduced
- Enemy speed and attack frequency scale with stage number
- Completing a stage advances you to the next automatically after a brief announcement

### Scoring

- **Grunt:** 100 pts
- **Knife:** 100 pts
- **Gun:** 100 pts
- **Brute:** 300 pts
- **Boss (Iron Lord):** 5,000 pts
- Combo multiplier: every 5 consecutive hits adds a score bonus tier

### HP System

- You start with **100 HP**
- After taking a hit you receive brief invincibility frames
- HP pills drop from enemies with a 30% chance — prioritize picking them up when low
- Some upgrades increase your max HP

### Special Attack

- Deals your highest damage in a wide arc
- Fires 22 orange sparks on impact for visual feedback
- Cooldown displayed live in the HUD (`SP Xs` when recharging, `SPECIAL RDY` when available)

---

## Enemy Types

| Type | Behavior | HP | Threat Level |
|---|---|---|---|
| Grunt | Direct pursuit, melee attacks | 65 | Low |
| Knife | Faster, melee — closes distance quickly | 52 | Medium |
| Gun | Keeps range, fires projectiles | 46 | Medium |
| Brute | Slow but tanky, heavy melee | 170 | High |

- All enemies display an HP bar above them during combat
- Enemies flash white briefly when hit
- Brutes take reduced knockback due to their size
- Gun enemies fire homing-trajectory projectiles that must be dodged or blocked by positioning

---

## Boss Wave

Stage 5 replaces regular enemies with a single boss: **⚡ THE IRON LORD ⚡**

Each boss has a dedicated health bar at the bottom of the screen.

| Boss | Stage | HP | Special Attacks |
|---|---|---|---|
| Iron Lord | 5 | 720 | Spread fire (3-way), rapid shots below 35% HP |

**Boss Mechanics:**

- **Phase 2 (below 35% HP):** The Iron Lord enters a rage state and fires 3-way spread projectiles instead of single shots
- **Crown indicator:** The boss displays a pixel crown and red jewel to distinguish it visually
- **Defeating the boss** triggers a Victory screen with final score and kill count

---

## Upgrades

On leveling up (earned through XP from kills), you choose one of 3 randomly drawn upgrades:

| Icon | Name | Effect |
|---|---|---|
| 💪 | IRON FIST | Punch damage +15 |
| 🦵 | IRON BOOT | Kick damage +20 |
| ⚡ | NOVA BLAST | Special damage +30 |
| ❤️ | IRON SKIN | Max HP +50 (also restores 50 HP) |
| 🌪 | WIND STEP | Move speed +1.0 |
| 🌿 | CHI FLOW | HP regeneration per second |
| 🦅 | EAGLE JUMP | Jump power +3 |

You can level up a maximum of **5 times** per run. XP requirements scale with each level.

---

Code Structure

```
iron-fist-chronicles/
├── index.html        ← Entire game (HTML structure + CSS styling + JavaScript logic)
└── README.md         ← This file
```

All game logic is inside the `<script>` tag of `index.html`, organized into clearly separated sections:

| Section | Description |
|---|---|
| Web Audio Engine | Chiptune note player, drum synth, music track scheduler, SFX |
| Title Logo Renderer | Pixel-art fist logo drawn to offscreen canvas at startup |
| Game State (`initG`) | All runtime state: player, enemies, projectiles, sparks, camera |
| `mkPlayer()` | Player entity factory with stats, cooldowns, and physics properties |
| `updPlayer()` | Input handling, physics, jump, animation walk cycle, camera follow |
| `doAtk()` | Attack dispatch — hitbox generation, damage application, combo counter |
| `mkEnemy()` | Enemy factory for all 4 types + boss variant |
| `updEnemies()` | AI movement, range checks, attack firing, death handling |
| `fireProj()` | Projectile spawner for ranged enemies and boss |
| `spawnLogic()` | Wave-based enemy spawning with difficulty scaling |
| `checkLevel()` | Stage clear detection and boss spawn trigger |
| `render()` | Full frame draw: background, parallax, entities, sparks, floating texts |
| `drawChar()` | Universal pixel character renderer — draws player and all enemies procedurally |
| `drawProjectile()` | Shaped bullet renderer with motion trail |
| `drawPickup()` | Bobbing HP pill with glow ring |
| `hudSync()` | Live DOM updates for HP bar, XP bar, score, level, special cooldown |
| `showLvlUp()` | Level-up card with 3 random upgrade buttons |
| `announce()` | Stage name overlay with timed auto-dismiss |
| `gameOver()` / `victory()` | End screens with score, kill count, and time |

---
