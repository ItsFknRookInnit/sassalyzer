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
| **Keebs** | Blue | Blue dress with giraffe print, blonde hair. The methodical analyst. Loves giraffes. |

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

### Step 4 — Read the Results

Each row colour-codes in real time:

| Row Colour | Meaning |
|------------|---------|
| 🟡 **Gold glow** | This stat has a major spike in a priority stat — this creature is a **Star Dino** |
| 🥈 **Silver** | Major spike in Weight — valuable for flyers and haulers |
| 🟢 **Green** | Above average — good but not exceptional |
| ⚪ **Grey** | Exactly average |
| 🔴 **Red** | Below average — points wasted here |
| 🌫️ **Faded/disabled** | Stat not applicable (Oxygen in 5-stat mode) |

The **distribution bar** shows the stat's points relative to all others. The red line marks the average target.

The **variance column** shows `+X.X` if above average, `−X.X` if below, `±0.0` if exact.

### Step 5 — Check the Verdict

The verdict badge at the bottom right gives you the overall breeding assessment:

| Verdict | Meaning |
|---------|---------|
| ⭐ **Star Dino!** | Major spike detected in Health, Stamina or Damage — **keep and breed this regardless of overall spread** |
| ⭐ **Weight Star** | Major Weight spike — valuable for flyers and haulers even if other stats are poor |
| ✓ **Strong Breed** | Good overall spread above average, no individual spike |
| **~ Marginal** | Roughly average across the board — situational value |
| ✕ **Cull It** | Mostly below average with no redeeming spike — not worth keeping |

> A Star Dino with terrible overall stats is still more valuable than a Strong Breed with no spike. The spike is what you breed into your lines.

### Step 6 — Check the Summary

The summary bar below the comparator shows:

| Field | What It Means |
|-------|---------------|
| **Above Avg** | Count of stats beating the baseline (includes spikes) |
| **At Average** | Stats that hit exactly the average |
| **Below Avg** | Stats below average — wasted RNG points |
| **Net Points** | Total surplus/deficit across all active entered stats |

### Step 7 — Reset
Click **↺ Clear All Stats** to wipe all active inputs and start fresh. Disabled stats (Oxygen in 5-stat mode) are not affected.

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

**Example A — Level 150 Rex (6-stat), Star Dino result:**
```
floor(150 ÷ 6) = 25 points per stat (average)
Spike threshold = max(6, floor(25 × 0.3)) = max(6, 7) = 7 points above average

Health:  38  → +13  ⭐ SPIKE — 13 >= 7, priority stat  → ⭐ Star Dino!
Stamina: 16  → -9   ❌ below average
Oxygen:  12  → -13  ❌ below average (dump stat)
Food:    18  → -7   ❌ below average (dump stat)
Weight:  24  → -1   ≈ average
Damage:  42  → +17  ⭐ SPIKE — 17 >= 7, priority stat  → confirms Star Dino!

Verdict: ⭐ Star Dino! (two priority spikes — exceptional breeding candidate)
```

**Example B — Level 150 Sarco (5-stat, no Oxygen):**
```
floor(150 ÷ 5) = 30 points per stat (average)
Spike threshold = max(6, floor(30 × 0.3)) = 9 points above average

Health:  32  → +2   ✅ above average, not a spike
Stamina: 20  → -10  ❌ below average
Oxygen:  N/A → disabled
Food:    22  → -8   ❌ below average (dump stat)
Weight:  50  → +20  ⭐ SPIKE — 20 >= 9, but Weight is secondary priority
Damage:  26  → -4   ❌ below average

Verdict: ⭐ Weight Star (big Weight spike, valuable for hauling — but no primary spike)
```

> **Why floor?** Rounding down gives a slightly conservative baseline — it's better to slightly underestimate the average than to mark a genuinely good stat as average.

---

## 🐊 Common 5-Stat Dinos (No Oxygen)

These fully aquatic dinos **do not have** an Oxygen stat — use **5 Stats mode**:

`Sarco` · `Deinosuchus` · `Megalodon` · `Plesiosaur` · `Mosasaurus` · `Manta` · `Ichthyosaurus` · `Electrophorus` · `Tusoteuthis` · `Cnidaria`

## 🦖 Common 6-Stat Dinos (Have Oxygen)

These dinos **do have** an Oxygen stat — use the default **6 Stats mode**:

`Rex` · `Giganotosaurus` · `Therizinosaur` · `Carnotaurus` · `Allosaurus` · `Yutyrannus` · `Spinosaur` · `Baryonyx` · `Raptor` · `Wyvern` · `Rock Drake` · `Managarmr` · `Snow Owl` · `Shadowmane` · `Deinonychus` · `Megalosaurus` · `Argentavis` · `Ankylosaurus`

> 💡 When in doubt, check the dino's stat screen in-game — if Oxygen appears, use 6-stat mode.

---

## 🛠️ Technical Details

- **Pure HTML / CSS / JavaScript** — zero dependencies, no frameworks, no build step
- **Single file** (`index.html`) — runs locally or from any static host
- Spike threshold scales dynamically with level — no hardcoded values
- Priority system encoded per-stat: `1` = top priority, `2` = secondary (Weight), `0` = dump stat
- SVG character art drawn inline
- Animated SVG dino silhouettes generated procedurally via JavaScript
- Custom CSS tooltip system (no libraries)
- 5/6 stat mode handled entirely client-side with no page reload
- Fonts loaded from Google Fonts (Fredoka One, Nunito, Share Tech Mono)

---

## 🌐 Deployment

This is a static single-file app. It can be hosted anywhere that serves HTML:

- **Vercel** — connect your GitHub repo, auto-deploys on every push
- **GitHub Pages** — enable under repo Settings → Pages
- **Netlify Drop** — drag and drop the file at netlify.com/drop
- **Locally** — just open `index.html` in any browser

---

## 📁 Project Structure

```
sassalyzer/
└── index.html    ← the entire app lives here
```

---

## 🔮 Potential Future Features

- Save/load dino profiles between sessions
- Multi-dino comparison view (compare two creatures side by side)
- Dino name dropdown that auto-sets the correct stat mode and highlights the right priority stats for that species
- Adjustable spike threshold sensitivity (strict / standard / relaxed)
- Export to image / shareable link

---

## 📋 Changelog

### v1.2
- Added **priority spike detection system** — Health, Stamina and Damage are tracked as top priority stats; a significant spike in any of them overrides the overall verdict
- Added **Weight spike detection** — flagged separately as a secondary priority, particularly useful for flyers and hauling dinos
- New **⭐ Star Dino!** verdict (gold, pulsing glow) — fires when any top priority stat has a major spike, regardless of overall stat spread
- New **⭐ Weight Star** verdict (silver) — fires when Weight has a major spike and no primary spike is present
- Spike threshold scales dynamically with level: `max(6, floor(average × 0.3))` — so the bar rises appropriately as dino level increases
- Priority and Notable **stat badges** added to Health, Stamina, Damage and Weight rows so users always know which stats matter
- Gold and silver row highlight styles added for spike rows
- Removed the **"Use (Level − 1) ÷ 6"** offset toggle — simplified to a clean floor division that covers the vast majority of use cases without confusion
- Average stat display now shows a rounded-down integer instead of a decimal

### v1.1
- Added **5-stat mode** for fully aquatic dinos that do not have an Oxygen stat (e.g. Sarco, Deinosuchus, Megalodon)
- Stat count mode pill selector added to the configuration panel
- Oxygen row disables with an N/A overlay when 5-stat mode is active
- Baseline calculation dynamically switches between `÷ 6` (default) and `÷ 5`
- Clear All Stats respects the active mode and skips disabled rows
- Tooltips updated throughout to reflect stat count context

### v1.0
- Initial release
- 6-stat comparator with real-time variance and colour coding
- Breeding verdict system (Strong Breed / Marginal / Cull)
- Floating dino background
- Full tooltip system
- Pistola & Keebs character branding

---

## 👾 Credits

Built for the **Sass House** ARK tribe.
Featuring **Pistola** and **Keebs**.
Keebs likes giraffes.

---

*No dinos were harmed in the making of this tool. Several were culled. One was a Star Dino.*
