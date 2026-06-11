# ⚔️ Sandro vs Samurai

A browser-based 3D first-person arena shooter built with [Three.js](https://threejs.org/).
Fight your way through a 5-level warehouse gauntlet — from a lone classic samurai to the towering Giant Samurai boss.

**[▶ Play Now](https://sigije.ge)**

---

## 🎮 Controls

| Key | Action |
|-----|--------|
| `↑` / `↓` | Move forward / backward |
| `←` / `→` | Strafe left / right |
| `Space` | Jump |
| `D` | Light shot — 50-round mag, 1.0s auto-reload |
| `F` | Heavy shot — 20-round mag, 3.0s auto-reload, hits hard |
| `G` | Bomb — massive AOE, limited count per level, only way to hurt Flying Samurai |

> All three weapons are available from the start. Each has its own magazine — when it empties it reloads automatically, no key press needed.
> **Bomb tip:** after firing, run to the opposite side of the arena and jump — or you'll take self-damage.

---

## ⚔️ Levels

| Level | Enemies | Difficulty | Arena | Color scheme |
|-------|---------|-----------|-------|--------------|
| 1 | 1 Samurai (Classic) | base | Small warehouse bay | Dark red / rust |
| 2 | Classic + Ronin Samurai | +25% | Medium warehouse, more crates | Cold blue / steel |
| 3 | Classic + Ronin + Oni Samurai | +56% | Large multi-room warehouse | Toxic green / hazard yellow |
| 4 | Ground Samurai + Flying Samurai | +95% | Large warehouse w/ catwalks | Purple / violet neon |
| 5 | **Giant Samurai (Boss)** | +144% baseline, boss stats further boosted | Boss arena w/ cover ring | Black / molten orange |

Every level features a unique warehouse layout — crates, walls, and obstacles for cover and dodging — with its own color palette and lighting.

---

## 🥷 Enemy Roster

| Enemy | Levels | Description |
|-------|--------|-------------|
| **Classic Samurai** | 1–3 | Red-armored cubic samurai, the baseline foe |
| **Ronin Samurai** | 2–4 | Leaner, darker, jagged broken-armor silhouette |
| **Oni Samurai** | 3–4 | Wider frame, horned helmet, glowing toxic-green markings |
| **Flying Samurai** | 4 | Hovers and dive-bombs the player; immune to bullets — **only bombs can hurt it** |
| **Giant Samurai (Boss)** | 5 | Combines Classic/Ronin/Oni motifs at ~2x scale with molten cracks; +50% HP/stats over the toughest regular enemy |

---

## 🔫 Weapons

| Weapon | Key | Damage | Magazine | Reload | Notes |
|--------|-----|--------|----------|--------|-------|
| Light shot | `D` | 25 | 50 | 1.0s | Fast yellow bullet, primary workhorse |
| Heavy shot | `F` | 55 | 20 | 3.0s | Large green bolt, hits hard |
| Bomb | `G` | 80 AOE | limited per level | cooldown between bombs | 8.5-unit blast radius, only counter to Flying Samurai and the boss's laser |

The Giant Samurai boss also fires **Fire** attacks (+15% damage) and **Laser** attacks (+35% damage) in addition to regular shots.

---

## 🚀 Run Locally

No build step required. Just open `index.html` in any modern browser.

```bash
# Or serve with any static server, e.g.:
npx serve .
```

---

## 🛠️ Tech

- **Three.js r134** — 3D rendering (loaded via CDN)
- **Web Audio API** — procedural sound effects
- Pure vanilla HTML/CSS/JS — zero dependencies, single file

---

## 📄 License

MIT
