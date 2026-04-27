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
| Boss System | Unique boss fight every 5th wave with phases, shields, and special attacks |
| Powerup System | HP, Ammo, Rapid Fire, Shield, Triple Shot, Nuke, Speed Boost, and Score Multiplier drops |
| HUD | Live score, wave counter, hull bar, ammo pips, boss health bar |
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

## Boss Waves

Every **5th wave** is a Boss Wave. Normal enemies are replaced by a single powerful boss that must be destroyed to advance. A **⚠ BOSS INCOMING ⚠** warning flashes on screen before the boss enters.

Each boss has a dedicated **health bar** at the top of the screen showing its name, current HP, shield status, and active phase.

| Wave | Boss | Tier | HP | Phases | Shield | Score | Special Attacks |
|---|---|---|---|---|---|---|---|
| **5** | WARDEN MK-I | Easy Boss | 600 | 1 | None | 5,000 | 5-way spread shot, 12-bullet ring burst |
| **10** | SENTINEL PRIME | Medium Boss | 1,200 | 2 | 80 HP | 12,000 | Rotating turrets + aimed shot, double bullet ring |
| **15** | DREADNOUGHT X | Hard Boss | 2,200 | 3 | 150 HP | 25,000 | Homing missiles, 3-bullet spread, charged laser beam |
| **20** | APOCALYPSE CORE | ⚠ Ultra Boss | 4,000 | 4 | 200 HP | 60,000 | All of the above — rotating spread, triple missiles, sweeping laser, bullet storm |

**Boss Mechanics:**

- **Phases** — Bosses with multiple phases increase their attack speed and fire rate each time they drop to a new HP threshold. A particle burst and screen shake signal each phase transition.
- **Shields** — Higher-tier bosses start with a shield (shown as a purple overlay on the health bar). All damage is absorbed by the shield first; destroying it triggers a large explosion. Shields can partially regenerate on phase transitions.
- **Homing Missiles** — Dreadnought X (Wave 15) and Apocalypse Core (Wave 20) fire homing missiles that track your position. They can be outmaneuvered but not outrun.
- **Laser Beam** — Dreadnought X and Apocalypse Core charge up a sustained laser beam that sweeps across the screen and deals continuous damage if you stay in its path.
- **Nuke vs. Bosses** — Using a Nuke powerup during a boss wave deals 25% of the boss's current HP as damage instead of an instant kill.
- **Defeating a boss** awards a massive score bonus and clears the wave.

---

## Powerups

Powerups drop randomly (25% chance) from destroyed enemies. They float in place for 8 seconds before disappearing. Fly over one to collect it.

| Powerup | Label | Effect | Color |
|---|---|---|---|
| **Health** | `HP` | Restores 30 HP | Green |
| **Ammo** | `AM` | Instantly refills all ammo and cancels any active reload | Cyan |
| **Rapid Fire** | `RF` | Doubles your fire rate for 5 seconds | Yellow |
| **Shield** | `SH` | Absorbs all incoming damage for 6 seconds | Purple |
| **Triple Shot** | `3X` | Fires a 3-bullet spread for 7 seconds | Orange |
| **Nuke** | `NK` | Instantly destroys all regular enemies; deals 25% HP damage to bosses | Red |
| **Speed Boost** | `SP` | Increases movement speed by 1.8× for 6 seconds | Cyan |
| **Score Multiplier** | `2X` | Doubles all score gains for 8 seconds | Yellow |

Active timed powerups display as icons at the bottom of the screen with a countdown bar so you always know what's running.

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
| `class Missile` | Homing missile tracking logic used by boss enemies |
| `class Player` | Ship movement, mouse aiming, fire system, reload, damage handling |
| `class Enemy` | Four enemy AI types with unique movement and shooting patterns |
| `class Boss` | Boss entity with multi-phase AI, shields, laser, and per-boss attack patterns |
| `class PowerUp` | Collectible drops with bobbing animation and on-collect effects |
| `BOSS_DEFS` | Data definitions for all 4 bosses (stats, phases, shield HP, score value) |
| `drawBackground()` | Scrolling parallax star field |
| `spawnWave()` | Enemy generation with type scaling per wave number; triggers boss on wave % 5 === 0 |
| `gameLoop()` | Main delta-time loop — update all entities, run collision checks, draw everything |
| `updateHUD()` | Live DOM updates for score, health bar, ammo pips, wave counter, boss health bar |
| Screen functions | `startGame()`, `endGame()`, `waveComplete()`, `showMenu()` |

---

## Authors

**SOLIONGO** — [GitHub: @soliongo](https://github.com/leinardsoliongco-oss/Prog2-9302-AY225-SOLIONGCO.git)
- `class Player` — movement, aiming, fire system, reload logic, damage and invincibility frames
- `class Bullet` — projectile physics, bullet trail rendering
- Collision detection system (player bullets vs enemies, enemy bullets vs player, ram detection)
- HUD implementation (health bar color transitions, ammo pip display, reload progress bar)
- `class Boss` — all 4 bosses with multi-phase AI, shields, homing missiles, laser beam, and per-boss attack patterns

**OBNIAL** — [GitHub: @obnial](https://github.com/MrRezmor/Prog2-9302-AY225-OBNIAL.git)
- `class Enemy` — all 4 AI types with unique movement behavior and attack patterns
- `class Missile` — homing missile tracking and rendering
- `class PowerUp` — expanded drop system (8 types), bobbing animation, effect application per type
- `BOSS_DEFS` — boss stat definitions and wave trigger logic
- Wave spawning logic, difficulty scaling, and boss wave detection
- Screen state management (Main Menu, Wave Clear, Game Over, Boss Warning overlay transitions)

---

*UPHSD Molino — College of Computer Studies | Programming 2 | 2-Week Game Sprint*
