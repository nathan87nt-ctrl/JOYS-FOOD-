# Joy Fuel — install on your phone

A self-contained food tracker. No build step, no framework, no server code. Five files, same shape as Fuel Log.

## What you've got

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `manifest.json` | Makes it installable |
| `sw.js` | Offline support |
| `icon-192.png` / `icon-512.png` | Home screen icon |

## Features

**Today** — daily log. Calorie ring showing kcal left (or over), plus protein / carbs / fat bars against the day's targets. Every meal listed with its photo, time and macros. Tap a meal to see the full breakdown or delete it.

**Log a meal (＋)** — two ways, her choice each time:
- **Before + After** — photo the food as served, then photo the leftovers. The AI subtracts what's left and logs only what she actually ate. Built for the Thai habit of putting out more than gets eaten.
- **Single photo** — one photo of the meal, logged as the whole portion.
An optional note ("shared with someone", "extra rice") is passed to the AI. Every estimate comes back itemised and fully editable before saving.

**Week** — last 7 days as a stacked protein/carbs/fat bar chart, with average kcal, days logged, and the daily target.

**Body** — weight with current / change / goal, a trend line with the goal marked, plus the daily macro targets. Log a weight per day; goal weight draws a dashed line on the chart.

**How-to card** — a short 4-step guide shows on the Today screen the first time. Tap *Got it* to hide it; bring it back any time from Body → Appearance.

**Appearance** (Body tab) — seven themes including Thai-inspired ones (Orchid, Mango Sticky, Jade Temple, Chili Basil, Lotus) plus plain Dark and Light, and a text-size control (Normal / Large / Extra large) for bigger fonts.

**Language** — EN / ไทย toggle top-right. Switches the whole interface, the theme names and the AI's dish names.

## Data notes

**Meal photos** are stored in IndexedDB (too big for localStorage) and are kept on the device only — they are **not** in the JSON backup. Everything else (meals, macros, weights, targets) is in localStorage and **is** in the backup.

## Getting it on her phone (10 minutes, free)

It needs **https** to install and to reach the AI. Easiest route is GitHub Pages:

1. **github.com** → **New repository** → name it `joy-fuel` → **Public** → Create.
2. **uploading an existing file** → drag in all five files (the files, not the folder).
3. Commit.
4. **Settings** → **Pages** → Source **Deploy from a branch**, branch `main`, folder `/ (root)` → Save.
5. Wait ~1 minute. App is at `https://YOURNAME.github.io/joy-fuel/`

### Install it

Open that URL in **Safari on her iPhone** → Share → **Add to Home Screen**. Full-screen, own icon, works offline (except the AI estimate, which needs signal).

Alternative: **Netlify Drop** (app.netlify.com/drop) — drag the folder on, get a URL instantly.

## AI setup

Photo estimates need an Anthropic API key.

1. Get one at **console.anthropic.com** → API keys. Set a low monthly spend limit — the key sits in plain text on her phone.
2. In the app: **⇅** → paste into the **Claude API key** box → Save key. Model defaults to `claude-sonnet-5`; change it in the box below if you want.

Cost is a fraction of a cent per meal (photos are downscaled to 1200px before sending).

## Backup

**⇅** → Download file to save a backup, or paste one into Restore to load it. Photos don't travel with it — the log does.

## Changing things

`index.html` is plain HTML/CSS/JS. Targets default to 1600 kcal / 120P / 130C / 55F — she can change them under Body, or edit `EMPTY.targets` at the top of the script. Accent colour is `--accent` in `:root`. Re-upload the file to GitHub and it goes live in a minute.
