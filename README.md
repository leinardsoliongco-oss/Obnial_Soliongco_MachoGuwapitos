# SKYDRIFT — Aerial Assault

> A top-down aerial shooter built in vanilla JavaScript (Canvas API) for the UPHSD Molino College of Computer Studies — Programming 2: 2-Week Game Sprint.

**Developed by:** SOLIONGO & OBNIAL  
**Language:** JavaScript (HTML5 Canvas)  
**Course:** Programming 2 — Game Sprint Project

---

## Table of Contents

- [Game Description](#game-description)
- [Features](#features)
- [Setup Instructions](#setup-instructions)
  - [Playing on Desktop / Laptop](#playing-on-desktop--laptop)
  - [Playing on Mobile / Phone](#playing-on-mobile--phone)
  - [Playing via GitHub Pages](#playing-via-github-pages)
- [Controls](#controls)
- [Gameplay Guide](#gameplay-guide)
- [Enemy Types](#enemy-types)
- [Powerups](#powerups)
- [Screenshots](#screenshots)
- [Code Structure](#code-structure)
- [Authors](#authors)

---

## Game Description

**SKYDRIFT** is a wave-based top-down aerial shooter where you pilot a fighter jet against increasingly difficult waves of enemy aircraft. Survive as long as possible, rack up kills, and post a high score.

The game features:
- Mouse-aimed shooting with a directional bullet system
- 4 distinct enemy types with unique AI behavior
- Wave progression with scaling difficulty
- A powerup drop system (HP restore, ammo refill, rapid fire)
- Screen shake, particle explosions, and animated thrust effects
- Persistent high score saved in your browser

---

## Features

| Feature | Details |
|---|---|
| Main Menu | Controls reference and mission launch |
| Core Gameplay Loop | Wave-based combat with delta-time physics |
| Game Over Screen | Final score, wave reached, kills, and hi-score |
| Wave Clear Screen | Between-wave summary with bonus points |
| Enemy AI | 4 types: Basic, Heavy, Scout, Bomber |
| Powerup System | HP, Ammo, and Rapid Fire drops |
| HUD | Live score, wave counter, hull bar, ammo pips |
| High Score | Saved locally via `localStorage` |

---

## Setup Instructions

### Playing on Desktop / Laptop

No installation required. SKYDRIFT runs entirely in your browser.

**Step 1 — Download the file**

Click the green `Code` button on this repository, then select **Download ZIP**. Extract the ZIP file to any folder on your computer.

**Step 2 — Open the game**

Find `SKYDRIFT.html` inside the extracted folder. Double-click it. It will open directly in your default web browser (Chrome, Edge, or Firefox recommended).

**Step 3 — Play**

Click **LAUNCH MISSION** on the main menu and start flying.

> **Note:** No internet connection is required after downloading. No server, Node.js, or installs of any kind are needed.

---

### Playing on Mobile / Phone

SKYDRIFT was built for desktop mouse controls, but you can still play it on a phone using a browser with touch support.

**Option A — Via GitHub Pages (easiest)**

1. Open your phone's browser (Chrome recommended)
2. Go to the GitHub Pages link: `https://github.com/leinardsoliongco-oss/Obnial_Soliongco_MachoGuwapitos.git`
3. Tap **LAUNCH MISSION**
4. **Touch controls:** Tap on the canvas to fire toward that point. The ship aims at your tap location automatically.

**Option B — From a file on your phone**

1. Transfer `SKYDRIFT.html` to your phone (via USB, Google Drive, or email)
2. Open your phone's Chrome browser
3. Type `file:///sdcard/Download/SKYDRIFT.html` in the address bar (adjust the path to wherever you saved the file)

**Tips for mobile play:**
- Rotate your phone to **landscape orientation** for the best view
- Pinch-zoom out slightly if the canvas is too large for your screen
- The game is fully playable with one finger — tap to fire, the ship moves toward your touch point

---

### Playing via GitHub Pages

To host the game online so anyone can play it with just a link:

1. Push all project files to your GitHub repository
2. Make sure the game file is named `SKYDRIFT.html`
3. Go to your repo on GitHub → **Settings** → **Pages**
4. Under **Source**, select `Deploy from a branch`
5. Choose branch: `main`, folder: `/ (root)` → click **Save**
6. Wait about 1 minute, then your game will be live at:

```
https://github.com/leinardsoliongco-oss/Obnial_Soliongco_MachoGuwapitos.git
```

Share this link for your Day 14 live demo.

---

## Controls

### Desktop Controls

| Input | Action |
|---|---|
| `W` or `↑` | Move Up |
| `S` or `↓` | Move Down |
| `A` or `←` | Move Left |
| `D` or `→` | Move Right |
| `Mouse` | Aim (ship rotates to face your cursor) |
| `Left Click` | Fire |
| `Spacebar` | Fire (alternative) |
| `Shift` (hold) | Boost speed (1.6× movement) |
| `R` | Manual Reload |

> Ammo auto-reloads when empty. Use `R` to reload early during a break in combat.

### Mobile / Touch Controls

| Input | Action |
|---|---|
| Tap canvas | Fire toward tap point |
| Touch and drag | Move ship toward drag direction |

---

## Gameplay Guide

**Objective:** Survive wave after wave of enemy aircraft. Destroy all enemies in a wave to advance to the next. The game ends when your hull (HP) reaches zero.

**Wave Progression:**
- Each wave spawns more enemies than the last (`4 + wave × 2` enemies per wave)
- Enemy speed, fire rate, and type variety increase with each wave number
- Completing a wave awards a **Wave Bonus** (`wave × 500` points) and restores **+20 HP**

**Scoring:**
- Basic enemy: `100 × current wave`
- Scout enemy: `150 × current wave`
- Bomber enemy: `200 × current wave`
- Heavy enemy: `300 × current wave`

**Hull (HP) System:**
- Your ship starts with 100 HP
- After taking a hit you receive 0.7 seconds of invincibility frames so you can't be instantly combo'd
- Your HP bar turns yellow below 50% and red below 25% — prioritize picking up HP powerups at that stage

**Ammo System:**
- You carry 12 rounds before needing to reload
- Reloading takes 1.5 seconds — try not to run dry mid-fight
- Press `R` to reload early during a quiet moment

---

## Enemy Types

| Type | Color | Behavior | HP | Threat Level |
|---|---|---|---|---|
| **Basic** | Red-orange | Direct pursuit, single shot | 40 | Low |
| **Heavy** | Orange | Slow but tanky, fires a 3-bullet spread | 120 | Medium |
| **Scout** | Pink | Fast strafe-dodge movement, fires quick shots | 20 | Medium |
| **Bomber** | Purple | Hovers at mid-range, fires 4-directional burst | 80 | High |

- All enemies display an **HP bar** above them during combat
- Enemies flash white when they take a hit
- Destroying a Heavy or Bomber causes a large explosion with screen shake
- Enemies that physically collide with your ship deal 20 damage and self-destruct on impact

---

## Powerups

Powerups drop randomly (25% chance) from destroyed enemies. They float in place for 8 seconds before disappearing. Fly over one to collect it.

| Powerup | Label | Effect | Color |
|---|---|---|---|
| **Health** | `HP` | Restores 30 HP | Green |
| **Ammo** | `AM` | Instantly refills all ammo and cancels any active reload | Cyan |
| **Rapid Fire** | `RD` | Doubles your fire rate for 5 seconds | Yellow |

---

## Code Structure

```
skydrift/
├── index.html          ← Entire game (HTML structure + CSS styling + JavaScript logic)
└── README.md           ← This file
```

All game logic is inside the `<script>` tag of `SKYDRIFT.html`, organized into clearly separated sections:

| Section | Description |
|---|---|
| `class Entity` | Base class all game objects inherit from |
| `class Particle` | Visual particles for explosions and hit effects |
| `class Bullet` | Projectile movement and trail rendering |
| `class Player` | Ship movement, mouse aiming, fire system, reload, damage handling |
| `class Enemy` | Four enemy AI types with unique movement and shooting patterns |
| `class PowerUp` | Collectible drops with bobbing animation and on-collect effects |
| `drawBackground()` | Scrolling parallax star field |
| `spawnWave()` | Enemy generation with type scaling per wave number |
| `gameLoop()` | Main delta-time loop — update all entities, run collision checks, draw everything |
| `updateHUD()` | Live DOM updates for score, health bar, ammo pips, wave counter |
| Screen functions | `startGame()`, `endGame()`, `waveComplete()`, `showMenu()` |

---

## Authors

**SOLIONGO** — [GitHub: @soliongo](https://github.com/leinardsoliongco-oss/Prog2-9302-AY225-SOLIONGCO.git)
- `class Player` — movement, aiming, fire system, reload logic, damage and invincibility frames
- `class Bullet` — projectile physics, bullet trail rendering
- Collision detection system (player bullets vs enemies, enemy bullets vs player, ram detection)
- HUD implementation (health bar color transitions, ammo pip display, reload progress bar)

**OBNIAL** — [GitHub: @obnial](https://github.com/MrRezmor/Prog2-9302-AY225-OBNIAL.git)
- `class Enemy` — all 4 AI types with unique movement behavior and attack patterns
- `class PowerUp` — drop system, bobbing animation, effect application per type
- Wave spawning logic and difficulty scaling system
- Screen state management (Main Menu, Wave Clear, Game Over transitions)

---

*UPHSD Molino — College of Computer Studies | Programming 2 | 2-Week Game Sprint*