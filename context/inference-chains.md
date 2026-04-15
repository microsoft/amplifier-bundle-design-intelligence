# Design System Inference Chains

## Purpose

When a design agent encounters a `missing` section in `.design/context.json` that's relevant to its current work, it should derive a sensible default from what's already established — not ask the user.

This document defines the inference relationships between design system dimensions. These aren't guesses — they're the same judgment calls a senior designer would make when one decision naturally constrains another.

## How to Use This

1. Read `.design/context.json` at session start
2. Note which sections are `defined`, `inferred`, and `missing`
3. When you need a value from a `missing` section, consult the inference chains below
4. Apply the inferred value in your work
5. Explain your reasoning: "Based on your [established value], I'm using [inferred value] because [reasoning]"
6. The user can say nothing (it sticks), confirm (upgrades to `defined`), or override

Never stall work waiting for the user to fill in a missing section. Infer, apply, explain, and move on.

## Core Inference Principle

Design systems have internal gravity — decisions in one dimension constrain and inform others. A warm editorial aesthetic implies different motion timing than a dense data dashboard. A serif heading font pulls toward different spacing density than a geometric sans. These relationships aren't arbitrary; they emerge from the same visual logic that makes a cohesive design feel "right."

When multiple known values converge on the same inference, confidence is high. When they conflict, that conflict itself is useful information worth surfacing.

---

## Inference Tables

### From `style.aesthetic` → Other Sections

The aesthetic is the strongest signal. It represents the most intentional design direction and should be weighted highest when inferring other values.

| Aesthetic keywords | → `motion.timing` | → `spacing.density` | → `radius` | → `voice.tone` |
|---|---|---|---|---|
| warm, editorial, literary, contemplative | deliberate: 200 / 400 / 600ms | editorial (generous) | subtle: 4–8px | measured, confident, no exclamation marks |
| minimal, clean, modern, restrained | smooth: 150 / 300 / 500ms | balanced | moderate: 4–8px | clear, direct, concise |
| bold, expressive, dynamic, energetic | snappy: 100 / 200 / 400ms | balanced to dense | varied: 0–16px (intentional contrast) | confident, punchy, active verbs |
| data-dense, dashboard, functional, utilitarian | quick: 100 / 200 / 300ms | dense (tight grouping) | minimal: 2–4px | terse, status-oriented, no flourish |
| playful, whimsical, friendly, approachable | bouncy: 150 / 300 / 500ms with overshoot | balanced (generous around groups) | generous: 8–16px, pill shapes ok | casual, warm, occasional humor |
| luxury, premium, sophisticated, refined | elegant: 200 / 500 / 800ms | very generous | subtle: 4–8px, precise | formal but not stiff, understated confidence |
| brutalist, raw, industrial, confrontational | instant or very slow: 50 / 100ms or 400 / 800 / 1200ms | tight | sharp: 0–2px | blunt, declarative, zero softening |

### From `color.palette` → Inferred Constraints

The character of the palette — not the specific colors, but their collective feeling — constrains motion and spatial decisions.

| Palette character | → `motion.easing` | → `radius` style | → `spacing` feel |
|---|---|---|---|
| Warm earth tones (ochre, sage, terracotta) | ease-in-out (organic, natural) | rounded but not circular | generous, breathing room |
| Cool neutrals (slate, steel, ice) | ease-out (precise, efficient) | sharp to moderate | structured, grid-aligned |
| High contrast / vibrant accents | ease-out (responsive, immediate) | moderate, consistent | tight around interactive elements |
| Monochromatic / minimal palette | ease-in-out (smooth, unobtrusive) | minimal and consistent | generous, let content breathe |
| Dark mode with neon accents | ease-out (snappy, responsive) | moderate: 4–8px | dense with clear separation |

### From `typography.families` → Inferred Values

Font choices carry strong personality signals. The character of the typeface constrains voice, spacing, and overall feel.

| Font character | → `spacing.density` | → `voice.tone` | → style implications |
|---|---|---|---|
| Serif headlines (Lora, Playfair, Georgia) | editorial / generous | formal to balanced, literary | traditional, authoritative, contemplative |
| Geometric sans (Futura, Montserrat, Circular) | balanced to dense | modern, direct, confident | precision, modernity, technology |
| Humanist sans (Inter, Lato, Source Sans) | balanced | warm, approachable, clear | accessibility, friendliness, readability |
| Monospace (JetBrains Mono, Fira Code) | dense | terse, technical, precise | developer-oriented, utilitarian, data-focused |
| Display / decorative headlines | generous (let them breathe) | expressive, personality-driven | brand-forward, editorial, creative |

### From `spacing.density` → Inferred Values

When density is established (whether defined or inferred), it constrains layout and component-level decisions.

| Density | → `layout.grid.gutter` | → `radius` scale | → `motion` approach |
|---|---|---|---|
| editorial | 24–32px | larger radii ok | deliberate, spacious transitions |
| balanced | 16–24px | moderate 4–8px | standard 150–300ms |
| dense | 8–16px | minimal 2–4px | quick, functional |

---

## Compound Inference Examples

Real projects have multiple known values. When they converge, confidence is high. Here are complete inference walkthroughs.

### Example 1: Warm Editorial Site

**Known values:**
- `color.palette` has warm earth tones (ochre, sage, cream)
- `style.aesthetic` = `["warm", "editorial"]`
- `typography.families.heading` = "Lora" (serif)

**Inference chain:**

All three signals converge strongly:
- Aesthetic "warm, editorial" → deliberate timing, editorial spacing, subtle radius, measured voice
- Warm earth palette → ease-in-out easing, rounded radius, generous spacing
- Serif heading → editorial spacing, formal-to-balanced voice

**Inferred values:**
```
motion:
  timing: { fast: "200ms", normal: "400ms", slow: "600ms" }
  easing:
    default: "cubic-bezier(0.4, 0, 0.2, 1)"
    entrance: "ease-out"
    exit: "ease-in"

spacing:
  density: "editorial"
  base: "8px"

radius:
  scale: { sm: "4px", md: "6px", lg: "8px" }
  nesting_rule: "inner = outer - padding"

voice:
  tone.formality: "balanced"
  personality: ["measured", "confident", "warm"]
```

**Confidence:** High — all three signals agree. No conflicts to resolve.

### Example 2: Dense Data Dashboard

**Known values:**
- `style.aesthetic` = `["data-dense", "dashboard"]`
- `typography.families.body` = "Inter"
- `color.palette` is dark mode with accent colors

**Inference chain:**

Strong convergence toward density and efficiency:
- Aesthetic "data-dense, dashboard" → quick timing, dense spacing, minimal radius, terse voice
- Inter (humanist sans) → balanced spacing, approachable voice — slight tension with dashboard density
- Dark mode with accents → snappy easing, moderate radius, dense with separation

Resolution: The aesthetic is the most intentional signal. Inter's warmth softens the dashboard density slightly (we don't go maximally terse), but density wins for spacing and timing.

**Inferred values:**
```
motion:
  timing: { fast: "100ms", normal: "200ms", slow: "300ms" }
  easing:
    default: "ease-out"

spacing:
  density: "dense"
  base: "4px"

radius:
  scale: { sm: "2px", md: "4px", lg: "6px" }

voice:
  tone.formality: "balanced"
  personality: ["terse", "precise", "status-oriented"]
```

**Confidence:** High for motion, spacing, radius. Moderate for voice — Inter suggests slightly more warmth than pure dashboard terse. We go with the dashboard direction but don't strip all warmth.

### Example 3: Playful Consumer App

**Known values:**
- `style.aesthetic` = `["playful", "friendly"]`
- `color.palette` has vibrant, saturated colors
- `typography.families.heading` = "Nunito" (rounded geometric sans)

**Inference chain:**

Everything points toward approachability and energy:
- Aesthetic "playful, friendly" → bouncy timing with overshoot, balanced spacing, generous radius, casual voice
- Vibrant palette → snappy easing, moderate radius, tight around interactive elements
- Rounded geometric sans → balanced spacing, warm and approachable voice

Resolution: Playful aesthetic and rounded font converge perfectly. The vibrant palette's "tight around interactive elements" translates to clear tap targets with generous padding, not visual density.

**Inferred values:**
```
motion:
  timing: { fast: "150ms", normal: "300ms", slow: "500ms" }
  easing:
    default: "cubic-bezier(0.34, 1.56, 0.64, 1)"  /* spring overshoot */
    entrance: "cubic-bezier(0.34, 1.56, 0.64, 1)"
    exit: "ease-in"

spacing:
  density: "balanced"
  base: "8px"

radius:
  scale: { sm: "8px", md: "12px", lg: "16px", full: "9999px" }

voice:
  tone.formality: "casual"
  personality: ["warm", "encouraging", "playful"]
```

**Confidence:** High — strong convergence across all signals.

### Example 4: Luxury E-Commerce

**Known values:**
- `style.aesthetic` = `["luxury", "refined", "sophisticated"]`
- `typography.families.heading` = "Playfair Display" (high-contrast serif)
- `color.palette` is restrained — ivory, charcoal, muted gold accent

**Inference chain:**

Everything points toward restraint and elegance:
- Aesthetic "luxury, refined" → elegant/slow timing, very generous spacing, subtle radius, formal confidence
- High-contrast serif → editorial spacing, formal voice, traditional/authoritative feel
- Restrained palette → ease-in-out easing, minimal consistent radius, generous breathing room

**Inferred values:**
```
motion:
  timing: { fast: "200ms", normal: "500ms", slow: "800ms" }
  easing:
    default: "cubic-bezier(0.4, 0, 0.2, 1)"
    entrance: "cubic-bezier(0.0, 0, 0.2, 1)"
    exit: "cubic-bezier(0.4, 0, 1, 1)"

spacing:
  density: "editorial"
  base: "8px"

radius:
  scale: { sm: "2px", md: "4px", lg: "6px" }

voice:
  tone.formality: "formal"
  personality: ["understated", "confident", "precise"]
```

**Confidence:** High — luxury, serif, and restrained palette form a tight cluster. The radius is deliberately smaller than what "editorial" density might suggest because luxury prefers precision over softness.

---

## Conflict Resolution

When inference chains point in different directions, don't silently pick a winner. Handle it explicitly:

### Resolution Priority

1. **`style.aesthetic` wins over font implications** — The aesthetic is the most intentional, high-level design decision. Font choice supports the aesthetic, not the other way around.
2. **Explicit beats implicit** — A defined value always overrides an inferred one, even if the inference "makes more sense."
3. **Convergence beats any single signal** — If two out of three signals agree, go with the majority.
4. **When genuinely ambiguous, surface it** — Don't bury the conflict. Name it.

### How to Surface Conflicts

When you detect a conflict, explain it concisely:

> "Your serif typography (Playfair Display) suggests formality, but your playful aesthetic suggests casual. I'm going with casual since the aesthetic is the more intentional choice — push back if you prefer formal."

Keep conflict explanations to one or two sentences. The user needs to understand what you chose and why, not read an essay about design theory.

### Common Conflict Patterns

| Signal A | Signal B | Resolution |
|---|---|---|
| Playful aesthetic | Serif typography | Aesthetic wins → casual tone, but serifs add a literary quality |
| Dense dashboard | Generous palette | Dashboard density wins for spacing, palette softens the motion |
| Luxury aesthetic | Geometric sans font | Aesthetic wins → elegant timing, font adds modern edge |
| Brutalist aesthetic | Warm color palette | Aesthetic wins → sharp radius, blunt voice; warmth shows in color only |

---

## What NOT to Infer

Some values must be explicitly decided by the user. Never infer these — they require deliberate creative judgment and getting them wrong creates significant rework:

- **`color.palette`** — The specific colors. This is always a deliberate choice tied to brand, emotion, and accessibility requirements.
- **`typography.families`** — The specific fonts. Font licensing, loading performance, and brand alignment make this a deliberate decision.
- **`layout.breakpoints`** — These depend on the specific project's content, target devices, and layout complexity. There's no reliable inference from aesthetics.
- **Brand-specific values** — Logos, brand names, specific copy. These aren't designsystem decisions.
- **Any value where getting it wrong would require significant rework** — When in doubt about whether something is safe to infer, ask yourself: "If I'm wrong, is it a 5-minute fix or a 5-hour fix?" Only infer 5-minute-fix values.

### The Safety Test

Before applying an inferred value, check:

1. **Is this value downstream of established decisions?** (Safe to infer)
2. **Is this value a foundational choice that other things depend on?** (Not safe — ask the user)
3. **Could a reasonable designer disagree with this inference?** (If yes, lower your confidence and flag it explicitly)

---

## Inference Confidence Levels

When applying inferred values, calibrate your language to your confidence:

| Confidence | When | Language |
|---|---|---|
| **High** | 3+ signals converge, no conflicts | "Based on your warm aesthetic and serif typography, I'm using editorial spacing." |
| **Moderate** | 2 signals converge, minor tension | "Your aesthetic suggests X, and your palette supports that. Your font choice pulls slightly toward Y, but I'm going with X." |
| **Low** | Single signal, or signals conflict | "I only have your aesthetic to go on here, so I'm using X as a starting point. This is a good one to revisit." |

At low confidence, apply the value but explicitly invite correction. At high confidence, apply and move on — the user will speak up if it's wrong.
