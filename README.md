![App Dashboard Preview](preview.jpg)

# Sass House Sassalyzer

**Dino Breeding · Stat Optimizer · Built by Sass House**

Single-file, browser-based ARK breeding tool to calculate ideal stat baselines, detect priority spikes, and flag wasted "dump" stats.

---

## Usage


Open the app [here](https://sassalyzer.vercel.app/).


Select the appropriate mode to adjust stat counts and priority logic:

| Mode | Stats | Oxygen Status | Priority Stats |
| :--- | :--- | :--- | :--- |
| **Land / Air** | 6 | Dump stat (orange) | Health · Stamina · Damage |
| **Aquatic** | 5 | Disabled | Health · Stamina · Damage |
| **Light Pet** | 6 | **Priority #2** | **Health · Oxygen · Damage** |

Input the stat points of the creature you are looking at.


**Verdict Reference:**
* **⭐ Star Dino! (gold):** Priority spike—always breed regardless of spread.
* **⭐ Weight Star (silver):** Major Weight spike—valuable for flyers.
* **⚠ Dump Spike! (orange):** Oxygen or Food spiked with no priority spike—cull unless Light Pet.
* **✓ Strong Breed (green):** Good spread, no dump spikes.
* **✕ Cull It (red):** Below average, nothing worth keeping.

---

## Purpose

The Sassalyzer identifies the ideal stat baseline for any creature to ensure RNG isn't wasted on "dump" stats like Food or Oxygen. While Oxygen is ignored for standard dinos, it is treated as priority #2 for Light Pets to improve recharge rates.

---

## Math

Calculations are based on the creature's level and the number of available stat slots (N):

* **Baseline** = floor(Level / N)
* **Spike Threshold** = max(6, floor(Baseline x 0.3))

* **Land/Air & Light Pet:** N = 6
* **Aquatic:** N = 5

---

## Changelog

* **v1.4:** Added 3-way Dino Mode toggle, Light Pet priority logic, and overhauled the JS-driven floating tooltip.
* **v1.3:** Dual Themes (Pistola/Keebs) with neon aesthetics and base64 backgrounds.
* **v1.2:** Implemented Priority Spike detection for Health, Stamina, Damage, and Weight.
* **v1.1:** Added Aquatic Mode (5-stat calculation).
* **v1.0:** Initial Release.

---

## Credits

Built for the Sass House ARK tribe by **Rook**.