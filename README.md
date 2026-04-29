# SKYDRIFT — Aerial Assault

> A top-down aerial shooter built in vanilla JavaScript (HTML5 Canvas API) for the UPHSD Molino College of Computer Studies — Programming 2: 2-Week Game Sprint.

**Developed by:** SOLIONGO & OBNIAL
**Language:** JavaScript (HTML5 Canvas, single-file)
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
- [Boss Waves](#boss-waves)
- [Powerups](#powerups)
- [Code Structure](#code-structure)
- [Authors](#authors)

---

## Game Description

**SKYDRIFT** is a wave-based top-down aerial shooter where you pilot a fighter jet against increasingly difficult waves of enemy aircraft. Survive as long as possible, rack up kills, and post a high score.

The game features:
- Mouse-aimed shooting with a directional bullet system and bullet trail rendering
- 4 distinct enemy types with unique AI behavior patterns
- Infinite wave progression with scaling difficulty
- Boss encounters every 5th wave — each with unique attack patterns, phases, and shields
- A full powerup drop system with 8 powerup types and active powerup HUD
- Homing missiles, charged laser beams, screen shake, particle explosions, and animated thrust effects
- Persistent high score saved in your browser via `localStorage`

---

## Features

| Feature | Details |
|---|---|
| Main Menu | Controls reference and mission launch button |
| Core Gameplay Loop | Wave-based combat with delta-time physics |
| Game Over Screen | Final score, wave reached, kills, and hi-score |
| Wave Clear Screen | Between-wave summary with bonus points and +20 HP repair |
| Enemy AI | 4 types: Basic, Heavy, Scout, Bomber — each with distinct movement and attack patterns |
| Boss System | Unique boss fight every 5th wave (Waves 5, 10, 15, 20) with multi-phase AI, shields, homing missiles, and laser beams |
| Powerup System | 8 types: HP, Ammo, Rapid Fire, Shield, Triple Shot, Nuke, Speed Boost, Score Multiplier |
| Active Powerup HUD | Timed powerup icons with countdown bars displayed at the bottom of the screen |
| Boss Health Bar | Dedicated top bar showing boss name, tier, HP, shield HP, and current phase |
| Boss Warning Overlay | Flashing ⚠ BOSS INCOMING ⚠ alert with boss name before each boss wave |
| HUD | Live score, wave counter, hull bar, ammo pips, kill count, and hi-score |
| High Score | Saved locally via `localStorage` across sessions |

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
2. Make sure the game file is named `SKYDRIFT.html` (or `index.html` for root access)
3. Go to your repo on GitHub → **Settings** → **Pages**
4. Under **Source**, select `Deploy from a branch`
5. Choose branch: `main`, folder: `/ (root)` → click **Save**
6. Wait about 1 minute, then your game will be live at:

```
https://leinardsoliongco-oss.github.io/Obnial_Soliongco_MachoGuwapitos/
```

Share this link for your Day 14 live demo.

---

## Controls

| Input | Action |
|---|---|
| `W` or `↑` | Move Up |
| `S` or `↓` | Move Down |
| `A` or `←` | Move Left |
| `D` or `→` | Move Right |
| `Mouse` | Aim (ship rotates to face cursor at all times) |
| `Left Click` | Fire |
| `Spacebar` | Fire (alternative) |
| `Shift` (hold) | Boost speed (1.5× movement multiplier) |
| `R` | Manual Reload |

> Ammo auto-reloads when your clip runs empty. Use `R` to reload early during a break in combat.

---

## Gameplay Guide

**Objective:** Survive wave after wave of enemy aircraft. Destroy all enemies in a wave to advance. Every 5th wave is a Boss Wave — defeat the boss to proceed. The game ends when your hull HP reaches zero.

**Wave Progression:**
- Each wave spawns more enemies than the last (`4 + wave × 2` enemies per normal wave)
- Enemy speed, fire rate, and type variety all increase with each wave number
- Completing a wave awards a **Wave Bonus** (`wave × 500` points) and restores **+20 HP**
- Boss waves award a larger **Boss Bonus** (`wave × 2000` points) on top of the boss's own score value

**Scoring:**
- Basic enemy: `100 × current wave`
- Scout enemy: `150 × current wave`
- Bomber enemy: `200 × current wave`
- Heavy enemy: `300 × current wave`
- All score gains are doubled while the **2× Score Multiplier** powerup is active

**Hull (HP) System:**
- Your ship starts with 100 HP
- After taking a hit you receive 0.7 seconds of invincibility frames (i-frames)
- Enemy bullet collision: damage varies by enemy type
- Enemy ram collision: 20 damage (enemy self-destructs on impact)
- Your HP bar turns yellow below 50% and red below 25% — prioritize HP powerups at that point

**Ammo System:**
- You carry 12 rounds before needing to reload
- Reloading takes 1.5 seconds — a reload progress bar appears below your ship
- Press `R` to reload early; ammo auto-reloads when the clip hits zero

---

## Enemy Types

| Type | Color | HP | Behavior | Fire Pattern | Threat |
|---|---|---|---|---|---|
| **Basic** | Red-orange | 40 | Direct pursuit toward player | Single aimed shot | Low |
| **Heavy** | Orange | 120 | Slow direct pursuit | 3-bullet spread aimed at player | Medium |
| **Scout** | Pink | 20 | Strafing lateral movement while closing | Fast single aimed shot | Medium |
| **Bomber** | Purple | 80 | Hovers at mid-range; retreats if too close | 4-directional burst (cardinal directions) | High |

- All enemies display an **HP bar** above them during combat
- Enemies flash white when they take a hit
- Destroying a Heavy or Bomber triggers a large explosion with screen shake
- Enemies that physically collide with your ship deal **20 damage** and self-destruct on impact
- Enemy fire rate and movement speed scale upward each wave (capped at reasonable minimums)

---

## Boss Waves

Every **5th wave** replaces all normal enemies with a single powerful boss. A **⚠ BOSS INCOMING ⚠** warning flashes on screen for 2.5 seconds before the boss enters from the top. A dedicated health bar at the top of the screen shows the boss's name, tier, HP, shield status, and current phase throughout the fight.

| Wave | Boss Name | Tier | HP | Phases | Shield HP | Score Value |
|---|---|---|---|---|---|---|
| **5** | WARDEN MK-I | Easy Boss | 600 | 1 | None | 5,000 |
| **10** | SENTINEL PRIME | Medium Boss | 1,200 | 2 | 80 | 12,000 |
| **15** | DREADNOUGHT X | Hard Boss | 2,200 | 3 | 150 | 25,000 |
| **20** | APOCALYPSE CORE | ⚠ Ultra Boss | 4,000 | 4 | 200 | 60,000 |

### Boss Attack Patterns

**WARDEN MK-I (Wave 5)**
- Side-to-side horizontal movement
- Regular attack: 5-way spread shot aimed at player
- Special: 12-bullet ring burst in all directions

**SENTINEL PRIME (Wave 10)**
- Figure-8 movement pattern
- Regular attack: 4 rotating turret bullets + 1 aimed shot
- Special: Double bullet ring (16 bullets × 2 rings) + screen shake
- Starts with an 80 HP shield; re-activates on phase transition

**DREADNOUGHT X (Wave 15)**
- Periodically charges directly at the player
- Regular attack: 3-bullet spread + homing missiles (Phase 2+)
- Special: 1-second laser charge warning, then a 2-second continuous laser beam that deals damage while you remain in its path
- Phase 3 restores a partial shield on transition

**APOCALYPSE CORE (Wave 20)**
- Tracks player horizontally while bobbing vertically
- Regular attack: 6-bullet rotating spread + 1 homing missile (Phase 2: +2 missiles, Phase 3: +3rd missile)
- Special: Bullet storm (20-bullet ring) + sweeping laser (2.5 seconds) + delayed missile salvo (Phase 3+)
- Attack rate and missile count escalate each phase

### Boss Mechanics

**Phases** — Bosses with multiple phases increase attack speed and fire rate each time they cross an HP threshold. A particle burst, screen shake, and `PHASE X!` notification signal each transition.

**Shields** — Higher-tier bosses start with a shield (shown as a purple overlay bar). All incoming damage hits the shield first. Destroying it triggers a large explosion and screen shake. Shields can partially regenerate on phase transitions (Dreadnought X and Apocalypse Core).

**Homing Missiles** — Fired by Dreadnought X and Apocalypse Core. Missiles steer toward your current position and must be outmaneuvered — they cannot simply be outrun.

**Laser Beam** — Fired by Dreadnought X and Apocalypse Core. A glow warning appears on the boss body during the charge period. The beam deals continuous damage if your ship stays inside it.

**Nuke vs. Bosses** — The Nuke powerup does not one-shot bosses; instead it deals **25% of the boss's current HP** as damage.

**Boss Defeat** — Awards the boss's full score value, drops 5 random powerups plus 1 guaranteed Health powerup, triggers a death explosion sequence, and advances to the Wave Clear screen.

---

## Powerups

Powerups drop randomly from destroyed enemies (approximately 25% chance per kill, with a small additional chance to force a Nuke or Shield drop). They float in place for 9 seconds with a bobbing animation before disappearing. Fly over one to collect it automatically.

Active timed powerups appear as labeled icons at the bottom center of the screen, each with a draining color bar showing remaining duration.

| Powerup | Label | Color | Effect |
|---|---|---|---|
| **Health** | `HP` | Green | Restores +30 HP (up to max 100) |
| **Ammo** | `AM` | Cyan | Instantly refills clip to 12 and cancels any active reload |
| **Rapid Fire** | `RF` | Yellow | Halves fire cooldown (0.18s → 0.08s) for **5 seconds** |
| **Shield** | `SH` | Purple | Absorbs all incoming damage for **6 seconds** (60 shield HP); displayed as a bubble around your ship |
| **Triple Shot** | `3X` | Orange | Fires a 3-bullet spread on each shot for **7 seconds** |
| **Nuke** | `NK` | Red | Instantly destroys all regular enemies on screen; deals 25% current HP damage to active bosses |
| **Speed Boost** | `SP` | Cyan | Increases movement speed to 1.8× base for **6 seconds** |
| **Score Multiplier** | `2X` | Yellow | Doubles all score gains for **8 seconds**; a `×2` indicator appears above your ship |

---

## Code Structure

```
skydrift/
├── SKYDRIFT.html     ← Entire game (HTML structure + CSS + JavaScript)
└── README.md         ← This file
```

All game logic lives inside the `<script>` tag of `SKYDRIFT.html`, organized into clearly labeled sections:

| Section | Description |
|---|---|
| `BOSS_DEFS` | Data definitions for all 4 bosses — HP, phases, shield HP, score value, size |
| `PTYPE / PTYPES_LIST` | Registry of all 8 powerup types with labels, colors, durations, and descriptions |
| `class Entity` | Base class all game objects inherit (`x`, `y`, `dead`, `alive`) |
| `class Particle` | Visual particles for explosions and hit effects with velocity decay |
| `class Bullet` | Projectile movement, trail rendering, and out-of-bounds culling |
| `class Missile` | Homing missile with angle-steering tracking logic and trail rendering |
| `class Boss` | Full boss entity — entry sequence, per-boss movement AI, multi-phase attack patterns, shield system, laser beam, phase transitions, and death animation |
| `class Player` | Ship movement, mouse aiming, fire system, reload, all powerup application, damage and i-frame handling |
| `class Enemy` | Four enemy AI types with unique movement and shooting patterns; HP bar rendering |
| `class PowerUp` | 8-type collectible drops with bobbing animation and per-type effect application |
| `drawBackground()` | Scrolling parallax star field with boss-wave color tint |
| `screenShake()` | Global canvas translate shake system with magnitude and duration |
| `spawnParticles()` / `spawnExplosion()` | Particle burst helpers used throughout for hit and kill effects |
| `showPickupNotif()` | DOM notification for powerup pickups, phase changes, shield breaks |
| `updateActivePowerupsUI()` | Rebuilds the active powerup icon strip with live countdown bars |
| `updateBossHUD()` | Syncs the boss health bar, shield bar, and phase label each frame |
| `spawnWave()` | Enemy generation with type scaling per wave; triggers boss warning and Boss instance on wave % 5 === 0 |
| `gameLoop()` | Main delta-time loop — updates all entities, runs all collision checks, draws all layers, updates HUD |
| `waveComplete()` | Handles wave-clear state, bonus scoring, countdown, and next wave transition |
| `endGame()` / `startGame()` / `showMenu()` | Screen state management for all overlays |

---

## Authors

**SOLIONGO** — [GitHub: @leinardsoliongco-oss](https://github.com/leinardsoliongco-oss/Prog2-9302-AY225-SOLIONGCO.git)
- `class Player` — movement, mouse aiming, fire system, reload logic, damage and invincibility frames
- `class Bullet` — projectile physics and bullet trail rendering
- Collision detection system (player bullets vs enemies, player bullets vs boss, enemy bullets vs player, missile vs player, enemy ram detection)
- HUD implementation (health bar color transitions, ammo pip display, reload progress bar, score multiplier indicator)
- `class Boss` — all 4 bosses with multi-phase AI, shields, homing missile attacks, laser beam charge and sweep, and per-boss attack patterns

**OBNIAL** — [GitHub: @MrRezmor](https://github.com/MrRezmor/Prog2-9302-AY225-OBNIAL.git)
- `class Enemy` — all 4 AI types with unique movement behavior and attack patterns
- `class Missile` — homing missile steering, tracking, and rendering
- `class PowerUp` — 8-type drop system, bobbing animation, and effect application per type
- `BOSS_DEFS` — boss stat definitions, phase thresholds, and wave trigger logic
- Wave spawning logic, difficulty scaling, and boss wave detection
- Active powerup icon strip UI and boss health bar HUD
- Screen state management (Main Menu, Wave Clear, Game Over, Boss Warning overlay transitions)

---

*UPHSD Molino — College of Computer Studies | Programming 2 | 2-Week Game Sprint*