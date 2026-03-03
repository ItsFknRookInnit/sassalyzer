# 🦖 Sass House Sassalyzer

> *Dino Breeding · Stat Optimizer · Built by Sass House*

A lightweight, browser-based tool for **ARK: Survival Evolved** players who take their breeding lines seriously. The Sassalyzer calculates the mathematically ideal stat baseline for any tamed or hatched dinosaur, detects high-value stat spikes in priority stats, and instantly tells you whether a creature is worth keeping — so you can make smarter decisions without doing the maths in your head.

No server. No backend. No dependencies. Open the file, enter your numbers, get your answer.

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
- ⭐ **Priority spike detection** — flags massive Health, Stamina or Damage spikes as Star Dinos
- 🥈 **Weight spike detection** — separately flags major Weight spikes for flyers and haulers
- 🏷️ **Priority stat labels** — Health, Stamina and Damage marked as Priority; Weight as Notable
- 🔀 **5-stat / 6-stat mode** — switch for fully aquatic dinos that don't have an Oxygen stat
- 📊 **Visual stat bars** — each stat rendered as a bar with a red marker at the average baseline
- 🟡🟢🔴 **Colour-coded rows** — gold for spike, green for above average, red for below, grey for exact
- ➕➖ **Variance display** — exact points above or below average per stat
- 🎨 **Dual character themes** — toggle between Pistola mode (red neon) and Keebs mode (teal neon), each with its own full-screen character artwork backdrop
- 💬 **Tooltips on everything** — hover any element for a plain-English explanation
- 📱 **Responsive** — works on desktop and mobile

---

## 🎨 Themes

The toggle at the top of the page switches between two full character themes. The entire colour scheme — accents, glass panels, borders, glows — adapts to match each character's artwork.

### 🤍 Pistola Mode (default)
Dark gaming room with red neon lighting. Red accent colours, deep red glass panels, red glow effects. Pistola is the character in the grey hoodie with red hearts.

### 💙 Keebs Mode
Same gaming room with teal/cyan neon lighting. Teal accent colours, dark teal glass panels, cyan glow effects. Keebs is the character in the blue hoodie.

Both themes use the same frosted glass panel aesthetic layered over the full-screen character artwork. Switching themes is instant and preserves all entered data.

---

## 🦎 The Characters

| Character | Theme | Look | Vibe |
|-----------|-------|------|------|
| **Pistola** | 🔴 Red neon | Grey hoodie with red hearts, bear ears | The aggressive breeder |
| **Keebs** | 🔵 Teal neon | Blue hoodie, blonde hair | The methodical analyst. Loves giraffes. |

---

## 🚀 How To Use

### Step 1 — Pick Your Theme
Use the **🤍 Pistola / 💙 Keebs** toggle at the top to set your preferred colour mode. This is purely cosmetic — all functionality is identical.

### Step 2 — Enter the Dino's Level
Type the creature's **total level** into the level field. This is the number shown on the dino's name tag in-game (e.g. `Rex - Lvl 150`). Use the **▲ / ▼ buttons** to nudge by 1.

The **Average Target Per Stat** updates instantly — calculated as `floor(Level ÷ stat count)`.

### Step 3 — Select Stat Count Mode

| Mode | When To Use |
|------|-------------|
| **6 Stats** (default) | Land, air, and amphibious dinos with an Oxygen stat — Rex, Giga, Wyvern, Spino, Raptor, etc. |
| **5 Stats (No Oxygen)** | Fully aquatic dinos without Oxygen — Sarco, Deinosuchus, Megalodon, Plesiosaur, etc. |

The Oxygen row disables with an N/A overlay in 5-stat mode. The baseline recalculates automatically.

### Step 4 — Enter the Stat Points
Type the **base stat point values** from the dino's stat panel into each input field. These are the raw allocated point counts, not the final multiplied values shown in-game.

> 💡 Mods like Dino Storage or S+ make it easier to view raw stat points.

The stats and their priority levels:

| Stat | Priority | Notes |
|------|----------|-------|
| ❤️ **Health** | ⭐ Top Priority | A spike here is always worth breeding on |
| ⚡ **Stamina** | ⭐ Top Priority | Critical for combat and travel |
| ◎ **Oxygen** | — Dump Stat | Not present on aquatic dinos; a spike here has no breeding value |
| ⬟ **Food** | — Dump Stat | Never a breeding priority |
| ⊞ **Weight** | 🥈 Notable | Especially valuable for flyers and haulers |
| ⚔️ **Damage** | ⭐ Top Priority | A spike here is always worth breeding on |

### Step 5 — Read the Verdict

| Verdict | Meaning |
|---------|---------|
| ⭐ **Star Dino!** (gold, pulsing) | Major spike in Health, Stamina or Damage — **keep this regardless of overall spread** |
| ⭐ **Weight Star** (silver) | Major Weight spike — valuable for flyers even if other stats are poor |
| ✓ **Strong Breed** (green) | Good overall spread above average |
| **~ Marginal** (grey) | Average across the board — situational |
| ✕ **Cull It** (red) | Mostly below average with no redeeming spike |

> A Star Dino with terrible overall stats is still more valuable than a Strong Breed with no spike. The spike is what you breed into your lines.

### Step 6 — Reset
Click **↺ Clear All Stats** to wipe all inputs and start fresh for a new creature.

---

## 🧮 The Maths

**Baseline average:**
```
Average = floor(Level ÷ N)     where N = 6 (default) or 5 (no Oxygen mode)
```

**Spike threshold (scales with level):**
```
Spike = stat variance >= max(6, floor(Average × 0.3))

Level 150, avg = 25:  threshold = max(6, 7)  = +7 above average
Level 300, avg = 50:  threshold = max(6, 15) = +15 above average
```

**Example — Level 150 Rex (6-stat):**
```
floor(150 ÷ 6) = 25 per stat   |   Spike threshold = +7

Health:  38  →  +13  ⭐ SPIKE — priority stat   → ⭐ Star Dino!
Stamina: 16  →   -9  ❌ below average
Oxygen:  12  →  -13  ❌ below average (dump stat)
Food:    18  →   -7  ❌ below average (dump stat)
Weight:  24  →   -1  ≈ average
Damage:  42  →  +17  ⭐ SPIKE — priority stat

Verdict: ⭐ Star Dino! (two priority spikes — exceptional breeding candidate)
```

**Example — Level 150 Sarco (5-stat, no Oxygen):**
```
floor(150 ÷ 5) = 30 per stat   |   Spike threshold = +9

Health:  32  →  +2   ✅ above average, not a spike
Stamina: 20  → -10   ❌ below average
Oxygen:  N/A →  disabled
Food:    22  →  -8   ❌ below average
Weight:  50  → +20   ⭐ SPIKE — secondary stat

Verdict: ⭐ Weight Star (no primary spike, but huge Weight)
```

---

## 🐊 Common 5-Stat Dinos (No Oxygen)

`Sarco` · `Deinosuchus` · `Megalodon` · `Plesiosaur` · `Mosasaurus` · `Manta` · `Ichthyosaurus` · `Electrophorus` · `Tusoteuthis` · `Cnidaria`

## 🦖 Common 6-Stat Dinos (Have Oxygen)

`Rex` · `Giganotosaurus` · `Therizinosaur` · `Carnotaurus` · `Allosaurus` · `Yutyrannus` · `Spinosaur` · `Baryonyx` · `Raptor` · `Wyvern` · `Rock Drake` · `Managarmr` · `Snow Owl` · `Shadowmane` · `Deinonychus` · `Megalosaurus` · `Argentavis` · `Ankylosaurus`

> 💡 When in doubt — if Oxygen appears in the dino's stat screen in-game, use 6-stat mode.

---

## 🛠️ Technical Details

- **Single file** (`index.html`) — the entire app: HTML, CSS, JavaScript, and both background images are all embedded. No external dependencies, no folders, no paths to break
- Both background images embedded as base64 data URIs directly in the CSS — works offline, locally, and on any static host
- Dual theme system via CSS custom properties — switching themes changes a single body class (`pistola` / `keebs`), all colours update instantly via variable inheritance with zero JavaScript style manipulation
- Frosted glass panel effect via `backdrop-filter: blur()` layered over the full-screen background artwork
- Spike threshold scales dynamically with level — no hardcoded values
- Priority system per stat: `1` = top priority (Health/Stamina/Damage), `2` = secondary (Weight), `0` = dump stat
- Fonts loaded from Google Fonts (Fredoka One, Nunito, Share Tech Mono)

---

## 🌐 Deployment

Single file — works anywhere:

- **GitHub Pages** — upload `index.html` to repo root, enable Pages under Settings → Pages
- **Vercel** — connect GitHub repo, auto-deploys on every push
- **Netlify Drop** — drag the single file to netlify.com/drop
- **Locally** — just open `index.html` in any browser, no server needed

---

## 📁 Project Structure

```
sassalyzer/
└── index.html    ← the entire app lives here (HTML + CSS + JS + images, all inline)
```

---

## 🔮 Potential Future Features

- Save/load dino profiles between sessions
- Multi-dino comparison view
- Dino name dropdown that auto-sets stat mode and highlights relevant priority stats
- Adjustable spike threshold sensitivity (strict / standard / relaxed)
- Export result to image / shareable link

---

## 📋 Changelog

### v1.3
- **Dual character themes** — new Pistola / Keebs toggle at the top of the page
- Pistola mode: red neon colour scheme, dark red glass panels, full-screen Pistola character artwork as backdrop
- Keebs mode: teal/cyan neon colour scheme, dark teal glass panels, full-screen Keebs character artwork as backdrop
- Theme toggle is instant and preserves all entered data
- All colours exclusively use CSS custom properties — full theme switching by changing one body class, zero JavaScript style manipulation
- **Back to single file** — reverted from multi-file structure to a single self-contained `index.html`; both background images embedded as base64 data URIs
- Frosted glass panel aesthetic applied consistently across both themes

### v1.2
- Added **priority spike detection** — Health, Stamina and Damage tracked as top priority; a significant spike overrides the overall verdict
- Added **Weight spike detection** — flagged separately as ⭐ Weight Star
- **⭐ Star Dino!** verdict — pulsing gold glow
- **⭐ Weight Star** verdict — silver
- Spike threshold scales dynamically: `max(6, floor(average × 0.3))`
- Priority and Notable stat badges added to Health, Stamina, Damage and Weight rows
- Removed offset toggle — simplified to floor division
- Average display shows rounded-down integer

### v1.1
- Added **5-stat mode** for aquatic dinos without Oxygen (Sarco, Deinosuchus, Megalodon, etc.)
- Stat count mode pill selector in the configuration panel
- Oxygen row disables with N/A overlay in 5-stat mode
- Baseline dynamically switches between `÷ 6` and `÷ 5`

### v1.0
- Initial release
- 6-stat comparator with real-time variance and colour coding
- Breeding verdict system (Strong Breed / Marginal / Cull)
- Floating dino background
- Full tooltip system
- Pistola & Keebs SVG character branding

---

## 👾 Credits

Built for the **Sass House** ARK tribe.
Featuring **Pistola** and **Keebs**.
Keebs likes giraffes.

---

*No dinos were harmed in the making of this tool. Several were culled. One was a Star Dino.*
