# Calorie Deficit & Macro Calculator

A simple, shareable web tool that calculates your daily calorie target and macronutrient breakdown to reach your body fat goal. Includes a cycle-based nutrition planner for women.

**Live site:** [zzhu0926-a11y.github.io/calorie-deficit-calculator](https://zzhu0926-a11y.github.io/calorie-deficit-calculator/)

## Features

### Deficit Calculator
- Enter your gender, age, height, weight, body fat %, goal body fat %, timeframe, and activity level
- Get your daily calorie target, macro split (protein/fat/carbs), BMR, and TDEE
- Adjustable protein slider (1.6–2.0 g/kg) with smart defaults based on activity level
- Metric/Imperial support
- Safety warnings for overly aggressive plans

### Cycle-Based Nutrition (Women)
- Adjusts calories and macros across 4 menstrual cycle phases
- Pushes a bigger deficit during high-energy phases (follicular/ovulatory)
- Eases up during low-energy phases (menstrual/luteal) with more carbs to manage cravings
- Total deficit stays the same over the full cycle — you still hit your goal on schedule

## How It Works

### BMR (Basal Metabolic Rate)

We average two established formulas for better accuracy:

**Katch-McArdle** — uses lean body mass (good when you know your body fat %):
```
BMR = 370 + (21.6 × lean body mass in kg)
```

**Mifflin-St Jeor** — uses gender, height, and age:
```
Male:   BMR = (10 × weight_kg) + (6.25 × height_cm) - (5 × age) + 5
Female: BMR = (10 × weight_kg) + (6.25 × height_cm) - (5 × age) - 161
```

Averaging both captures body composition *and* gender/age differences that a single formula would miss.

### TDEE (Total Daily Energy Expenditure)

```
TDEE = BMR × activity multiplier
```

| Activity Level | Multiplier |
|---|---|
| Sedentary | 1.2 |
| Lightly Active (1-3 days/week) | 1.375 |
| Moderately Active (3-5 days/week) | 1.55 |
| Very Active (6-7 days/week) | 1.725 |
| Extremely Active | 1.9 |

### Calorie Target

```
Lean Body Mass = weight × (1 - body_fat% / 100)
Target Weight  = lean body mass / (1 - goal_body_fat% / 100)
Fat to Lose    = current weight - target weight
Daily Deficit  = (fat to lose × 7700 kcal) / (weeks × 7)
Target Calories = TDEE - daily deficit
```

1 kg of body fat ≈ 7,700 kcal of stored energy.

### Macros

| Macro | How It's Calculated | Why |
|---|---|---|
| **Protein** | 1.6–2.0g per kg of lean body mass (user adjustable) | High protein preserves muscle during a deficit. More active people need more. |
| **Fat** | 25% of calories (male) / 28% (female) | Women need more dietary fat for hormonal health (estrogen, progesterone). |
| **Carbs** | Remaining calories ÷ 4 | Carbs are the most flexible macro — adjusted after protein and fat minimums are met. |

### Cycle Phase Adjustments

The deficit is redistributed across menstrual cycle phases so the 28-day total stays the same:

| Phase | Days | Deficit | Protein | Fat | Why |
|---|---|---|---|---|---|
| Menstrual | 1–5 | 60% | 1.6g/kg | 30% | Low energy, focus on recovery and iron-rich foods |
| Follicular | 6–14 | 130% | 1.9g/kg | 22% | Rising estrogen = high energy, good carb tolerance |
| Ovulatory | 15–17 | 130% | 2.0g/kg | 22% | Peak hormones = peak performance |
| Luteal | 18–28 | 70% | 1.7g/kg | 28% | Progesterone rises, energy drops, carb cravings increase |

The multipliers are normalized so the weighted average across 28 days equals exactly 1.0 — meaning you don't lose progress by cycling your intake.

## Safety Warnings

The calculator flags plans that may be unhealthy:
- Daily calories below 1,200 kcal
- Weekly loss rate above 1 kg/week
- Daily deficit above 1,000 kcal
- Carb intake below 50g/day
- Female body fat goal below 15%
- Male body fat goal below 6%

## Disclaimer

Results are estimates based on established formulas. Individual metabolism varies. Adjust based on real-world progress and consult a healthcare professional before starting any diet plan.
