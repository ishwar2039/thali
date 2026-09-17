# Thali — Personal Fitness & Nutrition Tracker

A single-file, offline-first fitness and nutrition tracker built for Indian eating habits and gym training. Double-click `thali.html` to open — no install, no server, no account.

---

## Quick Start

1. Open `thali.html` in Chrome or Safari (double-click)
2. Go to **Profile** → fill in weight, height, age, sex, activity level, goal weight
3. Start logging meals in **Food** and workouts in **Workout**

Data is saved automatically in your browser's localStorage and survives reloads. Clearing browser data will erase it.

---

## Tabs

| Tab | What it does |
|-----|-------------|
| **Profile** | Set your stats. App calculates BMR → TDEE → safe calorie deficit → weekly loss estimate. |
| **Workout** | Log exercises by muscle group. Paste workouts directly from the Hevy app. |
| **Food** | Log meals by type (Breakfast / Lunch / Dinner / Snack). See calorie ring, macros, and micronutrients — all on one screen. |
| **Awards** | Daily badges, food vs workout comparison, weight trend, InBody composition, volume by muscle group. |

A **date picker** above the tabs lets you log or review any past date.

---

## Food Logging — Three Ways

### 1. AI Paste (recommended)
Copy the prompt from the AI Paste tab → paste into ChatGPT or Gemini → paste the response back. The app parses the full day's meals automatically.

Prompt template included in the app covers Breakfast / Lunch / Dinner / Snacks and asks for all 9 nutrients (kcal, protein, carbs, fat, fiber, iron, calcium, sodium, potassium).

### 2. Local Database
Search 150+ Indian and common foods already in the app. Anything you look up online or via AI Paste is saved to the local list automatically — you only search once.

Supports **piece count mode** for countable foods (eggs, rotis, etc.): enter pieces × grams-per-piece instead of total grams.

### 3. Open Food Facts (🌐 OFF)
Search the Open Food Facts database for packaged or international foods. Results are saved to your local list on log.

> **Note:** Safari blocks cross-origin requests from `file://`. If the online search fails, open the file in Chrome or use AI Paste instead.

---

## Workout Logging

**Hevy import:** Copy a workout as text from the Hevy app and paste it — the app parses exercise names, sets, reps, and weights automatically.

**Manual entry:** Search the exercise database (250+ exercises across Legs, Back, Chest, Shoulders, Arms, Core, Cardio, Full Body, Yoga) or add a custom exercise.

**Cardio exercises include:** Walking (Outdoor), Walking (Treadmill), Incline Walk (Treadmill), Running (Treadmill/Outdoor), Cycling, Rowing, Elliptical, Stairmaster, HIIT, Swimming, and more.

---

## Nutrition Targets

All targets are calculated from your profile — nothing is hardcoded.

| Nutrient | Formula |
|----------|---------|
| Calories | TDEE − deficit (max 750 kcal or 25% of TDEE, floored at 1500 kcal men / 1200 kcal women) |
| Protein | 1.6 g × bodyweight kg (muscle preservation during weight loss) |
| Carbs | 40% of calorie target ÷ 4 |
| Fat | 30% of calorie target ÷ 9 |
| Fiber | 14 g per 1000 kcal (IOM recommendation) |
| Iron | Men 8 mg · Women under 50: 18 mg · Women 50+: 8 mg |
| Calcium | 1000 mg (1200 mg for women 51+ and everyone 71+) |
| Sodium | 2300 mg upper limit |
| Potassium | Men 3400 mg · Women 2600 mg |

---

## Saved Meals

Create named meal templates (e.g. "My Breakfast") with fixed items and quantities. Log the entire meal in one tap. Useful for meals you eat regularly.

---

## Data & Privacy

- All data stored locally in `localStorage` under the key `thali-app-state-v1`
- Nothing is sent to any server (the app has no backend)
- Open Food Facts searches go directly to `world.openfoodfacts.org` (their public API, CC BY-SA)
- No analytics, no tracking, no account required

**To reset all data:** Profile tab → scroll to bottom → Reset All Data.

---

## Technical Notes

- Single HTML file — React 18 + Babel Standalone loaded from CDN, compiled at runtime
- Works from `file://` — no build step, no Node, no bundler
- State persisted to `localStorage` on every change
- Mobile-first layout (max-width 420 px), safe-area padding for iPhone home indicator

---

## Known Limitations

- Nutrition values are estimates (NIN / USDA / ICMR reference data), not lab-verified
- Calorie burn from workouts is a MET-based approximation — never fed into the calorie deficit math
- Data is per-browser and per-device — no cross-device sync
- Safari from `file://` blocks cross-origin fetch; use Chrome for the 🌐 OFF search tab
