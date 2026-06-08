# ⚔️ Cubic Samurai — Game 1.0

A browser-based 3D first-person arena shooter built with [Three.js](https://threejs.org/).  
Face blocky samurai warriors across 3 escalating levels — each 25% harder than the last.

**[▶ Play Now](https://sandro-k.github.io/Cubic-Samurai-Game-1.0/)**

---

## 🎮 Controls

| Key | Action |
|-----|--------|
| `↑` / `↓` | Move forward / backward |
| `←` / `→` | Strafe left / right |
| `Space` | Jump |
| `D` | Shoot (normal) |
| `F` | Heavy shot — 3× damage, 5s cooldown |
| `G` | Bomb — massive AOE, 10–15s cooldown |

> **Bomb tip:** after firing, run to the opposite side of the arena and jump — or you'll take self-damage.

---

## ⚔️ Levels

| Level | Enemies | Speed | Fire Rate | Damage |
|-------|---------|-------|-----------|--------|
| 1 | 1 Samurai | base | base | base |
| 2 | 2 Samurais | +25% | +25% | +25% |
| 3 | 3 Samurais | +56% | +56% | +56% |

Each level the samurai armor and eye glow change:
- **Level 1** — Dark red armor, red eyes
- **Level 2** — Crimson armor, orange eyes
- **Level 3** — Black-purple armor, purple eyes + dark aura

---

## 🔫 Weapons

| Weapon | Key | Damage | Cooldown | Notes |
|--------|-----|--------|----------|-------|
| Normal shot | `D` | 25 | 0.28s | Fast yellow bullet |
| Heavy shot  | `F` | 55 | 5s | Large orange bolt |
| Bomb        | `G` | 80 AOE | 10–15s | Lobs in an arc, 8.5-unit blast radius |

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
