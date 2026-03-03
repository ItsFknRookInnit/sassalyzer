# Sass House Sassalyzer

> Dino Breeding · Stat Optimizer · Built by Sass House

Single-file, browser-based ARK breeding tool. Open the file, enter numbers, get your answer. No server, no backend, no dependencies.

---

## Purpose

Calculates the ideal stat baseline for any dino, detects priority spikes, and flags dump stat spikes so you never keep a creature that wasted its RNG on Oxygen or Food.

**Core rule:** Oxygen and Food are dump stats on all standard dinos.

**Exception:** Light and Charge Pets use Oxygen for recharge rate. In Light Pet mode, Oxygen is priority #2 — Health → Oxygen → Damage.

---

## Three Dino Modes

| Mode | Stats | Oxygen | Priority Stats |
|------|-------|--------|----------------|
| 🦖 Land / Air | 6 | Dump stat (orange) | Health · Stamina · Damage |
| 🐊 Aquatic | 5 — Oxygen disabled | N/A | Health · Stamina · Damage |
| 🐾 Light Pet | 6 | **Priority #2 — recharge** | **Health · Oxygen · Damage** |

**Land / Air:** Rex, Giga, Wyvern, Spino, Raptor, Theri, Argy
**Aquatic:** Sarco, Megalodon, Deinosuchus, Plesiosaur, Mosasaurus
**Light Pet:** Bulbdog, Cosmo, Featherlight, Glowbug, Shinehorn, Glowtail

Food is a dump stat in every mode — no exceptions.

---

## Verdict Reference

| Verdict | Meaning |
|---------|---------|
| ⭐ Star Dino! (gold) | Priority spike — always breed regardless of spread |
| ⭐ Weight Star (silver) | Major Weight spike — valuable for flyers |
| ⚠ Dump Spike! (orange) | Oxygen or Food spiked with no priority spike — cull unless Light Pet |
| ✓ Strong Breed (green) | Good spread, no dump spikes |
| ~ Marginal (grey) | Nothing notable |
| ✕ Cull It (red) | Below average, nothing worth keeping |

Dump spikes are excluded from verdict scoring. Star verdicts show a sub-note when dump spikes are also present.

---

## The Maths

```
Baseline = floor(Level / N)
  N = 6  Land/Air and Light Pet
  N = 5  Aquatic

Spike threshold = max(6, floor(Baseline x 0.3))

Level 150 Land:    25 avg  → spike at +8
Level 150 Aquatic: 30 avg  → spike at +9
```

---

## Technical Details

- **Single HTML file** — CSS, JS, base64 backgrounds. Fully offline.
- `setDinoMode('land'|'aquatic'|'lightpet')` — controls stat count, Oxygen priority, badge text, info banner
- **Dump spike logic** — `priority: -1` stats excluded from `goodAbove`/`goodBelow` verdict counters
- **Floating tooltip** — `position: fixed` `#tt` div, JS-positioned on mouseover, auto-flips above/below, dynamic `max-content` width, never clipped by parent overflow

---

## Changelog

### v1.4 — Three-Mode Toggle · Light Pet · Tooltip Fix

**3-way Dino Mode pill** (replaces old 2-button Stat Count Mode):
- **Land / Air** — 6 stats, Oxygen flagged orange as dump stat
- **Aquatic** — 5 stats, Oxygen disabled; same priority as Land
- **🐾 Light Pet** — 6 stats; Oxygen promoted to priority #2; priority order: Health → Oxygen → Damage
- Light Pet info banner appears when mode is active listing eligible creatures
- Mode badge shows active mode name and stat divisor

**Dump spike system:**
- Oxygen and Food set to `priority: -1` (dump stats)
- Orange `spike-dump` row styling distinct from gold/silver/green
- Excluded from `goodAbove` — cannot inflate Strong Breed verdict
- ⚠ Dump Spike! verdict when dump stat spiked with no priority spike
- Sub-note on Star/Weight Star when dump spikes also present
- In Light Pet mode, Oxygen flips to `priority: 1` — spike renders gold

**Tooltip overhaul:**
- Replaced CSS `position: absolute` (clipped by parent containers) with JS-driven `position: fixed` global `#tt` element
- `width: max-content` — dynamically sizes to content, never clips text
- Auto-flips below trigger when near top of viewport; arrow repositions to match
- All tooltip text updated for three-mode system

---

### v1.3 — Dual Themes
- Light Pet Mode Added
- Pistola (red neon) and Keebs (teal neon)
- Base64 background images, frosted glass panels

### v1.2 — Priority Spike Detection
- Health, Stamina, Damage spikes (gold)
- Weight spikes (silver)
- Dynamic spike threshold

### v1.1 — Aquatic Mode
- 5-stat mode, Oxygen row disabled

### v1.0 — Initial Release
- Baseline calculator, 6-stat comparator

---

## Credits

Built for the Sass House ARK tribe. Featuring Pistola and Keebs. Keebs likes giraffes.

No dinos were harmed. Several were culled. One was a Star Dino.
