# 🦖 Sass House Sassalyzer

> *Dino Breeding · Stat Optimizer · Built by Sass House*

A lightweight, browser-based tool for **ARK: Survival Evolved** players who take their breeding lines seriously. The Sassalyzer calculates the mathematically ideal stat baseline for any tamed or hatched dinosaur, identifies high-value stat spikes in priority stats, and instantly tells you whether a creature is worth breeding on — so you can make smarter decisions without doing the maths in your head.

No downloads. No backend. Open the page, enter your numbers, get your answer.

---

## 🎯 Purpose

In ARK, when a creature spawns or hatches, its total level is distributed across **5 or 6 core stats** by the game's RNG engine. Most of the time that distribution is mediocre — but occasionally a creature will land a massive spike in a high-value stat like Health, Stamina, or Damage. These creatures are goldmines for breeding lines even if every other stat is terrible, because you can breed that one exceptional stat into your existing lines.

The Sassalyzer handles two things:

1. **Baseline comparison** — calculates the average points per stat and colour-codes each one so you instantly see what's above or below average
2. **Spike detection** — identifies when a priority stat (Health, Stamina, Damage) has a significant spike above the baseline and flags the creature as a **Star Dino**, regardless of how the rest of its stats look

The goal is to stop you from culling creatures that have genuine breeding value hiding behind an otherwise poor stat spread.

---

## ✨ Features

- 🔢 **Instant baseline calculator** — enter any dino level and get the average target stat immediately (rounded down)
- ⭐ **Priority spike detection** — automatically flags massive Health, Stamina or Damage spikes as Star Dinos
- 🥈 **Weight spike detection** — separately flags significant Weight spikes, useful for flyers and hauling dinos
- 🏷️ **Priority stat labels** — Health, Stamina and Damage are marked as Priority stats; Weight as Notable, so you always know which stats matter
- 🔀 **5-stat / 6-stat mode** — switch for fully aquatic dinos that don't have an Oxygen stat
- 🖼️ **Immersive Background** — custom gaming room background featuring the Sass House crew
- 🧊 **Glassmorphism UI** — semi-transparent "glass" panels allow the background to bleed through for a modern aesthetic
- 📊 **Visual stat bars** — each stat renders as a bar with a marker showing exactly where the average falls
- 🟡🟢🔴 **Colour-coded rows** — gold for spike, green for above average, red for below, grey for exact
- ➕➖ **Variance display** — shows exactly how many points above or below average each stat is
- 💬 **Tooltips on everything** — hover over any element for a plain-English explanation
- 🦕 **Floating dino background** — because why not
- 📱 **Responsive** — works on desktop and mobile browsers

---

## 🦎 The Characters

| Character | Colours | Vibe |
|-----------|---------|------|
| **Pistola** | Black & Red | Dark hoodie, red racing stripes, bear ears, red-sole kicks. The aggressive breeder. |
| **Keebs** | Light Navy | Light navy hoodie, blonde hair. The methodical analyst. Loves giraffes. |

---

## 🚀 How To Use

### Step 1 — Enter the Dino's Level
Type the creature's **total level** into the level field at the top. This is the number shown on the creature's name tag in-game (e.g. `Rex - Lvl 150`).

Use the **▲ / ▼ buttons** to nudge the level up or down by 1.

The **Average Target Per Stat** updates instantly. This is calculated as `Level ÷ stat count`, rounded down — the number of points each stat would have if RNG were perfectly even.

### Step 2 — Select Stat Count Mode
At the bottom of the configuration panel is a **Stat Count Mode** pill selector:

| Mode | When To Use |
|------|-------------|
| **6 Stats** (default) | Most land, air, and amphibious dinos that **have** an Oxygen stat — e.g. Rex, Giga, Therizinosaur, Carno, Wyvern, Raptor, Spino, Baryonyx |
| **5 Stats (No Oxygen)** | Fully aquatic dinos that **do not have** an Oxygen stat — e.g. Sarco, Deinosuchus, Megalodon, Plesiosaur, Manta, Ichthy |

When you switch to **5 Stats**:
- The baseline recalculates using `Level ÷ 5` (average goes up since fewer stats share the pool)
- The **Oxygen row** is greyed out with an N/A overlay and excluded from all calculations

> 💡 **Not sure which mode?** Check the dino's stat panel in-game. If Oxygen is listed, use 6 Stats. If it isn't there at all, use 5 Stats.

### Step 3 — Enter the Stat Points
In the **Stat Comparator** grid, type the **wild/bred stat point values** into the input fields for each active stat.

> ⚠️ These are the **base stat point counts**, not the final multiplied values shown in-game. You can find them by checking the creature's detailed stat breakdown. Mods like Dino Storage or S+ make this easier to view.

The stats tracked, and their priority levels:

| Stat | Priority | Why It Matters |
|------|----------|----------------|
| ❤️ **Health** | ⭐ Top Priority | Total hit points. A spike here is always worth breeding on |
| ⚡ **Stamina** | ⭐ Top Priority | Energy for combat and travel. A spike is highly valuable |
| ◎ **Oxygen** | — Dump Stat | Breath capacity. Spikes here are worthless for breeding |
| ⬟ **Food** | — Dump Stat | Hunger rate. Not a breeding priority at all |
| ⊞ **Weight** | 🥈 Notable | Carry capacity. Especially valuable for flyers and hauling dinos |
| ⚔️ **Damage** | ⭐ Top Priority | Melee multiplier. A spike here is always worth breeding on |

---

## 🧮 The Maths

**Baseline average (6-stat dinos):**

```

Average Stat = floor(Level ÷ 6)

```

**Baseline average (5-stat dinos, no Oxygen):**

```

Average Stat = floor(Level ÷ 5)

```

**Spike threshold:**

```

Spike = stat is at least 30% above average, and at least 6 points above average
= variance >= max(6, floor(average × 0.3))

```

---

## 📋 Changelog

### v1.3
- **Integrated Custom Streaming Room Background** — Added a high-detail gaming setup background featuring Pistola and Keebs in their natural habitat.
- **Glassmorphism UI System** — Updated all panels and cards to use semi-transparent backgrounds (`rgba`), allowing the environment to show through while maintaining clarity.
- **Contrast & Readability Enhancements** — Added a global dark overlay to ensure the UI remains the primary focus and stats are easy to read against the detailed background.
- **Visual Refresh** — Updated Keebs' character palette to a light navy blue to match the new streaming aesthetic.

### v1.2
- Added **priority spike detection system** — Health, Stamina and Damage are tracked as top priority stats; a significant spike in any of them overrides the overall verdict.
- Added **Weight spike detection** — flagged separately as a secondary priority, particularly useful for flyers and hauling dinos.
- New **⭐ Star Dino!** verdict (gold, pulsing glow) — fires when any top priority stat has a major spike, regardless of overall stat spread.
- New **⭐ Weight Star** verdict (silver) — fires when Weight has a major spike and no primary spike is present.
- Spike threshold scales dynamically with level: `max(6, floor(average × 0.3))` — so the bar rises appropriately as dino level increases.
- Priority and Notable **stat badges** added to Health, Stamina, Damage and Weight rows so users always know which stats matter.
- Gold and silver row highlight styles added for spike rows.
- Removed the **"Use (Level − 1) ÷ 6"** offset toggle — simplified to a clean floor division that covers the vast majority of use cases without confusion.
- Average stat display now shows a rounded-down integer instead of a decimal.

### v1.1
- Added **5-stat mode** for fully aquatic dinos that do not have an Oxygen stat (e.g. Sarco, Deinosuchus, Megalodon).
- Stat count mode pill selector added to the configuration panel.
- Oxygen row disables with an N/A overlay when 5-stat mode is active.
- Baseline calculation dynamically switches between `÷ 6` (default) and `÷ 5`.
- Clear All Stats respects the active mode and skips disabled rows.
- Tooltips updated throughout to reflect stat count context.

### v1.0
- Initial release.
- 6-stat comparator with real-time variance and colour coding.
- Breeding verdict system (Strong Breed / Marginal / Cull).
- Floating dino background.
- Full tooltip system.
- Pistola & Keebs character branding.

---

## 👾 Credits

Built for the **Sass House** ARK tribe.
Featuring **Pistola** and **Keebs**.
Keebs likes giraffes.

---

*No dinos were harmed in the making of this tool. Several were culled. One was a Star Dino.*
