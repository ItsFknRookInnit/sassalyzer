# 🦖 Sass House Sassalyzer

> *Dino Breeding · Stat Optimizer · Built by Sass House*

A lightweight, browser-based tool for **ARK: Survival Evolved** players who take their breeding lines seriously. The Sassalyzer calculates the mathematically ideal stat baseline for any tamed or hatched dinosaur and instantly tells you whether each individual stat is above average, average, or wasted — so you can make smarter breeding decisions without doing the maths in your head.

No downloads. No backend. Open the page, enter your numbers, get your answer.

---

## 🎯 Purpose

In ARK, when a creature spawns or hatches, its total level is distributed across **5 or 6 core stats** by the game's RNG engine. A perfectly optimised creature would have those points evenly — or better yet, weighted towards the stats that actually matter (Health, Damage, Weight). In reality, most creatures dump points into useless stats like Oxygen or Food.

The Sassalyzer gives you a **mathematical baseline** — the exact average points per stat if distribution were perfect — and compares every stat you enter against that baseline. At a glance you can see:

- Which stats beat the average (worth breeding on)
- Which stats are wasted (RNG dumped points here)
- Whether this creature is a **Strong Breed**, **Marginal**, or worth **culling**

Crucially, not all dinos have the same stat pool. Many dinos — including Rex, Giga, Therizinosaur, and Wyverns — **do not have an Oxygen stat**, meaning their points are distributed across only 5 stats. The Sassalyzer accounts for this with a dedicated **5-stat mode** that recalculates the baseline accordingly and disables the Oxygen row entirely.

The goal is to help you build cleaner, stronger breeding lines by only selecting creatures with superior point allocation in the stats that matter for your purpose.

---

## ✨ Features

- 🔢 **Instant baseline calculator** — enter any dino level and get the average target stat value immediately
- 🔀 **5-stat / 6-stat mode** — switch between dino types that do or don't have an Oxygen stat; the baseline and comparator update automatically
- 📊 **Visual stat bars** — each stat renders as a bar with a glowing marker showing exactly where the average falls
- 🟢🔴 **Colour-coded rows** — green for above average, red for below, grey for exact
- ➕➖ **Variance display** — shows exactly how many points above or below average each stat is
- 🏆 **Breeding verdict** — automatic Strong Breed / Marginal / Cull verdict based on your entered stats
- 🔄 **Two calculation modes** — toggle between `Level ÷ N` and `(Level − 1) ÷ N` depending on your server settings
- 💬 **Tooltips on everything** — hover over any element for an explanation of what it does
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

### Step 2 — Choose Your Calculation Mode
There is a toggle labelled **"Use (Level − 1) ÷ N"**.

- **Off (default):** Divides the full level by the stat count. Use this for most standard servers.
- **On:** Subtracts 1 before dividing. Use this if your server treats level 1 as a base level with no stat points assigned.

The **Average Target Per Stat** display updates instantly as you change the level or toggle.

### Step 3 — Select Stat Count Mode
At the bottom of the configuration panel is a **Stat Count Mode** pill selector with two options:

| Mode | When To Use |
|------|-------------|
| **6 Stats** (default) | Most aquatic or amphibious dinos that have an Oxygen stat — e.g. Spino, Baryonyx, Sarco, Megalodon, Plesiosaur |
| **5 Stats (No Oxygen)** | Dinos that do not have an Oxygen stat — e.g. Rex, Giga, Therizinosaur, Carno, Allosaurus, Wyvern, Rock Drake, Managarmr |

When you switch to **5 Stats**:
- The baseline recalculates using `Level ÷ 5` (the average per stat goes up)
- The **Oxygen row** in the comparator is greyed out with an "N/A" overlay
- Oxygen is excluded from all calculations, variance, and the final verdict
- The **÷ 5 stats** badge appears next to the toggle confirming the active mode

Switching back to **6 Stats** re-enables the Oxygen row instantly and clears any stale Oxygen input.

> 💡 **Not sure which mode to use?** If you can see an Oxygen value in the dino's stat panel in-game, use 6 Stats. If there's no Oxygen entry at all, use 5 Stats.

### Step 4 — Enter the Stat Points
In the **Stat Comparator** grid, type the **wild/bred stat point values** for each active stat into the input fields.

> ⚠️ These are the **base stat point counts**, not the final in-game values. You can find them by opening the creature's inventory and inspecting the stat breakdown. Some servers require mods like Dino Storage or S+ to view these easily.

The stats tracked are:

| Stat | 6-stat dinos | 5-stat dinos | Why It Matters |
|------|:---:|:---:|----------------|
| ❤️ **Health** | ✅ | ✅ | Total hit points. Critical for tanks and general purpose tames |
| ⚡ **Stamina** | ✅ | ✅ | Energy for sprinting and attacking. Low stamina = dino stops mid-fight |
| ◎ **Oxygen** | ✅ | ❌ | Underwater breath. Not present on many land/air dinos |
| ⬟ **Food** | ✅ | ✅ | Hunger rate. Rarely a breeding priority |
| ⊞ **Weight** | ✅ | ✅ | Carry capacity. Essential for hauling dinos (Argent, Anky, Castoroides) |
| ⚔️ **Damage** | ✅ | ✅ | Melee multiplier. Critical for combat tames |

### Step 5 — Read the Results

As you type, each row updates in real time:

- **Distribution bar** — visualises how many points this stat has relative to the others. The glowing red line marks the average target.
- **Variance column** — shows `+X.X` if above average, `−X.X` if below, `±0.0` if exact.
- **Row colour** — green border = above average, red border = below, grey = exact, dark/faded = disabled (N/A).

### Step 6 — Check the Summary

The summary bar at the bottom shows:

| Field | What It Means |
|-------|---------------|
| **Above Avg** | Number of active stats beating the baseline |
| **At Average** | Active stats that exactly hit the average |
| **Below Avg** | Active stats wasting points on dump categories |
| **Net Points** | Total surplus/deficit across all entered active stats |
| **Verdict** | `✓ Strong Breed` / `~ Marginal` / `✕ Cull It` |

**Verdict logic:**
- **Strong Breed** — more stats are above average than below (by more than 1)
- **Cull It** — more stats are below average than above (by more than 1)
- **Marginal** — roughly balanced; situational depending on which stats are above

### Step 7 — Reset
Click **↺ Clear All Stats** to wipe all active input fields and start fresh for a new creature. Disabled stats (e.g. Oxygen in 5-stat mode) are not affected.

---

## 🧮 The Maths

**6-stat dinos (default):**
```
Average Stat = Level ÷ 6
```

**5-stat dinos (No Oxygen mode):**
```
Average Stat = Level ÷ 5
```

With the offset toggle enabled, subtract 1 from the level first:
```
Average Stat = (Level − 1) ÷ N    (where N = 5 or 6)
```

**Example A — Level 150 Rex (5-stat mode):**
```
150 ÷ 5 = 30.0 points per stat (average target)

Health:  38  → +8.0  ✅ above average
Stamina: 22  → -8.0  ❌ below average
Oxygen:  N/A → disabled
Food:    24  → -6.0  ❌ below average (dump stat, acceptable)
Weight:  32  → +2.0  ✅ above average
Damage:  34  → +4.0  ✅ above average

Net: +8.0  →  Verdict: ✓ Strong Breed
```

**Example B — Level 150 Spino (6-stat mode):**
```
150 ÷ 6 = 25.0 points per stat (average target)

Health:  32  → +7.0  ✅ above average
Stamina: 18  → -7.0  ❌ below average
Oxygen:  14  → -11.0 ❌ below average (dump stat, acceptable)
Food:    20  → -5.0  ❌ below average (dump stat, acceptable)
Weight:  28  → +3.0  ✅ above average
Damage:  38  → +13.0 ✅ above average

Net: +7.0  →  Verdict: ✓ Strong Breed
```

> Notice how the same Rex stats would look very different if accidentally evaluated in 6-stat mode — the baseline would be lower (25.0 vs 30.0), potentially inflating how "good" a dino looks. Always make sure you're in the right mode.

---

## 🦕 Common 5-Stat Dinos (No Oxygen)

These dinos do **not** have an Oxygen stat — use **5 Stats mode** for them:

`Rex` · `Giganotosaurus` · `Therizinosaur` · `Carnotaurus` · `Allosaurus` · `Yutyrannus` · `Spinosaur`* · `Baryonyx`* · `Wyvern` · `Rock Drake` · `Managarmr` · `Snow Owl` · `Shadowmane` · `Noglin` · `Deinonychus` · `Megalosaurus`

> \* *Spino and Baryonyx are semi-aquatic and **do** have Oxygen on some server configs — check in-game to be sure.*

---

## 🛠️ Technical Details

- **Pure HTML / CSS / JavaScript** — zero dependencies, no frameworks, no build step
- **Single file** (`index.html`) — runs locally or from any static host
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
- Presets for common dino types (combat Rex, weight Argent, etc.) that auto-set the correct stat mode and highlight priority stats
- Colour-weight system — mark certain stats as priority so the verdict accounts for *which* stats are above average, not just how many
- Export to image / shareable link
- Auto-detect stat count from a dino name dropdown

---

## 📋 Changelog

### v1.1
- Added **5-stat mode** for dinos without an Oxygen stat
- Stat count mode pill selector added to the configuration panel
- Oxygen row now disables with an N/A overlay when 5-stat mode is active
- Baseline calculation dynamically switches between `÷ 5` and `÷ 6`
- Clear All Stats respects the active mode and skips disabled rows
- Tooltips updated throughout to reflect stat count context

### v1.0
- Initial release
- 6-stat comparator with real-time variance and colour coding
- Breeding verdict system
- Floating dino background
- Full tooltip system
- Pistola & Keebs character branding

---

## 👾 Credits

Built for the **Sass House** ARK tribe.
Featuring **Pistola** and **Keebs**.
Keebs likes giraffes.

---

*No dinos were harmed in the making of this tool. Several were culled.*
