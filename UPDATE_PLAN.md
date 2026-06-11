# Sandro vs Samurai — v2.0 Update Design Doc

## 1. Overview

Expand from a 3-level shooter into a 5-level warehouse gauntlet with a real ammo/reload economy, richer environments, a progressively stranger enemy roster, and a final boss fight. Difficulty still scales per level, but now also through environment complexity and enemy variety, not just stat multipliers.

---

## 2. Weapons & Ammo System

All three weapons are unlocked from the start (no more 5s/10-15s cooldown gating on F/G) — instead, each weapon has its own **magazine + reload**.

| Weapon | Key | Color | Mag size | Reload time | Damage | Notes |
|---|---|---|---|---|---|---|
| **Light** (was "normal") | `D` | Yellow | 50 | 1.0s | 25 | Fast, spammable, primary workhorse |
| **Heavy** (was "heavy shot") | `F` | Green | 20 | 3.0s | 55 | Slower fire rate built-in, hits hard |
| **Bomb** | `G` | — | 3 (see below) | 10-15s per bomb | 80 AOE | Kept resource-limited, see below |

**Reload rules:**
- Fully automatic — when a magazine hits 0, that weapon starts reloading immediately, no key press needed.
- Reloading one weapon doesn't block firing another (independent timers) — but you can't fire the weapon currently reloading.
- HUD shows current/max ammo per weapon + a reload progress bar (replacing the old cooldown bars).

**Bomb adjustment:** Since bombs are the only counter to flying enemies (Level 4) and the boss's laser (Level 5), giving bombs a *hard limited count* (e.g. 3 per level, refilled at level-complete) instead of pure cooldown ensures players can't infinitely spam but always have a way to deal with aerial threats. Cooldown between bombs (10-15s) still applies on top of the count.

**Carry-over between levels:** Ammo and bomb count refill to max at the start of each level (consistent with existing "+35 HP heal on level complete" pattern).

---

## 3. Levels & Difficulty (3 → 5)

| Level | Enemies | Difficulty multiplier | Arena | Color scheme |
|---|---|---|---|---|
| 1 | 1 Samurai (classic) | base (1.0x) | Small warehouse bay | Dark red / rust |
| 2 | 2 Samurai (classic + new style) | 1.25x | Medium warehouse, more crates | Cold blue / steel |
| 3 | 3 Samurai (mixed styles + 1 new) | 1.5625x | Large warehouse, multi-room | Toxic green / yellow hazard stripes |
| 4 | 2 ground Samurai + 1-2 Flying Samurai | 1.953x | Large open warehouse w/ catwalks/gantries | Purple / violet neon |
| 5 | **Boss only** — Giant Samurai | 2.44x baseline, boss stats below | Boss arena (largest, most open + cover rings) | Black / molten orange |

Difficulty curve stays compounding (×1.25 per level), giving Level 4 a noticeable jump and Level 5 a true boss-tier spike.

---

## 4. Environment — Warehouse Theme

- **Core kit:** large stackable crates (multiple sizes), shipping containers, support pillars, low walls/barricades, chain-link or metal fencing — all serving as cover from bullets and line-of-sight breaks for dodging.
- **Per-level escalation:**
  - L1: Single open bay, a handful of crates — introductory, easy to read.
  - L2: Two connected bays, more crate clusters, a few choke points.
  - L3: Multi-room layout with corridors connecting rooms — forces repositioning.
  - L4: Vertical element — catwalks/platforms above the floor (relevant since flying enemies can use the airspace; player can also gain height for line-of-sight).
  - L5 (Boss): Large circular/octagonal arena with a ring of cover pieces around the perimeter — boss occupies center, player kites around cover.
- **Color schemes per level:** achieved via lighting tint + crate/wall material recoloring (rust red → steel blue → toxic green/yellow → violet neon → black/molten orange), reinforcing level identity at a glance.
- **Destructible crates (new addition, see §6):** bombs and heavy shots can destroy certain crates, dynamically opening/closing sightlines mid-fight.

---

## 5. Enemy Roster

| Level | Enemy type(s) | Visual concept |
|---|---|---|
| 1 | **Classic Samurai** (existing) | Current red-armored cubic samurai |
| 2 | **Classic Samurai** + **Ronin-style Samurai** (new) | Leaner, darker, jagged "broken armor" silhouette — blue/steel palette |
| 3 | **Classic** + **Ronin** + **Oni Samurai** (new, 3rd style) | Oni = wider frame, horned helmet blocks, glowing toxic-green eyes/markings |
| 4 | **Ground mix** (2 of the above) + **Flying Samurai** (new) | Flying = stripped-down torso+head with floating armor plates / thruster-like glow underneath; hovers and strafes through airspace |
| 5 | **Giant Samurai (Boss)** — single enemy | Combines Classic + Ronin + Oni visual motifs at ~2x scale, molten-orange cracks/glow across armor |

**Flying Samurai (L4) special rule:** immune to Light/Heavy bullet damage (or takes drastically reduced damage — e.g. 5%) — **only Bomb splash damage hurts them significantly**. This makes the limited bomb count in §2 a meaningful tactical resource at exactly the level it's introduced.

**Flying Samurai behavior:** doesn't stay in the arena permanently. It periodically **flies in** from off-arena/high above, swoops toward the player and performs a **dive-bomb attack** (telegraphed descent + AOE impact on landing/near-miss), then **flies back out** of the arena before re-entering again after a cooldown. While present, it's a bomb-only target; while absent, the player deals with the remaining ground enemies. This creates a rhythm: handle ground enemies, then react to the dive-bomb window with a bomb if timed well.

---

## 6. Boss Design (Level 5) — Giant Samurai

Kept as a **simple pure-HP fight** — no stagger/poise meter, no phase-based mechanic changes. Straightforward but tough damage race.

- **Stats:** HP **+50% over the highest-tier regular enemy** (i.e., L4-scaled Oni stats × 1.5). Movement/attack speed scaled similarly (+50% over L4 baseline).
- **Attacks:**
  1. **Regular bullets** — same baseline damage as enemy rifle shots.
  2. **Fire attack** — +15% damage vs. regular bullets, short-range cone or ground-fire patch that lingers (area denial — forces player to keep moving, pairs with the warehouse cover layout).
  3. **Laser attack** — +35% damage vs. regular bullets, telegraphed beam (brief charge-up glow) that sweeps across the arena — player must use cover or strafe-dodge timed to the telegraph.
- All three attacks are picked semi-randomly on the boss's attack timer (same cadence throughout the fight — no enrage/phase change).

---

## 7. Additional Ideas (proposed additions on top of yours)

1. **Pickups in the environment:** occasional ammo crates (refill one weapon's magazine) and health packs placed in warehouse cover spots — rewards aggressive repositioning instead of camping.
2. **Hit feedback & juice:** hit-markers, brief screen shake on taking damage, kill confirmation flash — makes the added weapon variety feel more responsive.
3. **Enemy cover-awareness (AI upgrade):** ground enemies path toward/duck behind crates instead of always walking straight at the player, matching the new "hide and dodge" environment goal.
4. **Destructible crates:** certain crates (visually marked, e.g. with hazard stripes) can be destroyed by Heavy shots/Bombs — opens new sightlines or removes an enemy's cover mid-fight.
5. **Post-level performance rating:** simple S/A/B/C rank per level based on time taken, accuracy %, and HP remaining — adds replay incentive without big scope.
6. **Level-specific ambient audio/music shift:** subtle audio palette change per level (alongside the color scheme) to reinforce escalating tension toward the boss.
7. **Mini-map/radar (Level 4+):** with flying enemies and larger/multi-room layouts, a small radar showing enemy positions (including airborne) helps readability without clutter.

---

## 8. Open Questions / Decisions Needed Before Implementation

1. **Bomb count per level (3 suggested)** — does that feel right given it's now also the *only* way to hurt Flying Samurai in L4? Could scale up slightly for L4/L5 specifically (e.g. 4-5 bombs).
2. **Scope check:** items in §7 are additive polish — happy to phase these into a v2.1 pass after the core 5-level/weapon/enemy rework ships, so the first update stays focused.

---

## 9. Suggested Implementation Order

1. Weapon rework: ammo + reload system, HUD update (all weapons usable from start).
2. Environment: warehouse asset kit (crates, containers, walls) + per-level color schemes + larger/more complex layouts for L1-3 (reuse existing 3-level structure).
3. New enemy visual styles (Ronin, Oni) + mixed spawns for L2/L3.
4. Level 4: catwalk arena + Flying Samurai (bomb-only damage rule).
5. Level 5: Boss arena + Giant Samurai (HP/attacks/phases) + win condition update (5-level completion screen).
6. Polish pass: items from §7 as time allows.
