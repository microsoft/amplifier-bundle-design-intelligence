# Design Context System

> Spec for the design-intelligence Amplifier bundle.
> Three capabilities forming one cohesive system: structured design context,
> active completeness with opinionated gap-filling, and agent self-correction
> through design check.

---

## Goal

Give every design agent automatic awareness of what's been decided, what's been inferred, and what's missing — then drive toward completeness through normal work rather than questionnaires.

## Background

Design agents currently operate without shared state. The art-director picks colors; the component-designer builds cards; neither knows what the other decided unless the user manually bridges the gap. This leads to inconsistency, repeated questions, and agents that can't build on each other's work.

The Design Context System solves this with three interlocking capabilities:

1. **Structured Design Context** — A machine-readable `context.json` maintained automatically in `.design/`
2. **Active Completeness with Opinionated Gap-Filling** — Agents infer missing values from established ones and propose them with reasoning, rather than asking questions
3. **Design Check** — Three-layer validation (static + structural + visual) used as agent self-correction before presenting work to the user

---

## Capability 1: Structured Design Context

### `.design/context.json`

A machine-readable snapshot of the project's design system state. Every design agent reads it on session start.

### Schema

```
meta
  version          — schema version (for forward compat)
  last_updated     — timestamp
  completeness     — percentage + list of defined vs missing sections
  sources          — which files/agents contributed each section

color
  palette          — named colors with hex values
  semantic         — role mappings (primary, secondary, accent, error, etc.)
  constraints      — "warm only", "saturation < 60%", specific avoid-list
  rationale        — why these choices (cited from aesthetic guide)

typography
  families         — heading font, body font, mono font
  scale            — the type scale ratio + computed sizes
  weights          — which weights are in use
  constraints      — "serif headlines only", "max 2 families"

spacing
  base             — base unit (4px, 8px)
  scale            — the spacing scale values
  density          — editorial (generous) vs data-dense (tight)

motion
  timing           — duration scale (fast/normal/slow)
  easing           — default easing curves
  reduced_motion   — strategy (respect prefers-reduced-motion)

radius
  scale            — radius values by size
  nesting_rule     — inner = outer - padding

layout
  max_width        — container max-width
  grid             — column system, gutter sizes
  breakpoints      — responsive breakpoint values

style
  aesthetic        — declared style keywords ("warm minimal", "editorial")
  influences       — reference sites/brands
  avoid            — explicit anti-patterns ("no neon glows", "no purple gradients")

voice
  tone             — formality level, personality traits
  patterns         — error message style, CTA style, empty state style
```

Every field is optional. A brand new project starts with `context.json` containing just `meta` with 0% completeness. Sections fill in as users work with design agents.

### Key Principle

Agents don't write to `context.json` directly. They write their normal outputs (aesthetic guides, token files, specs). A reconciliation hook reads those artifacts and maintains `context.json`. Agents are consumers, not producers.

---

## Capability 2: Reconciliation Hook

A hook module that fires whenever any agent writes to `.design/`. It reads all artifacts and updates `context.json`.

### Trigger

Event: `file_write` to any path matching `.design/**`

### Process

1. Read all `.design/` artifacts that exist
2. Extract structured data from each:
   - `AESTHETIC-GUIDE.md` → color, style, typography, voice sections
   - `tokens.json` → color, typography, spacing, radius, motion (direct copy)
   - `preferences.md` → taste profile constraints
   - `specs/*.md` → component inventory, pattern usage
3. For markdown files, use a lightweight LLM call to extract structured assertions
4. Merge into `context.json` (additive — never deletes unless source deleted)
5. Recompute completeness score
6. Update `meta.last_updated` and `meta.sources`

### Edge Cases

- **Conflicting sources** → flagged as `conflicts[]` in `context.json`
- **Partial information** → completeness reflects exactly what's defined
- **No `.design/` directory yet** → hook is dormant, no overhead

---

## Capability 3: Active Completeness (Opinionated Gap-Filling)

The system drives toward completeness by making informed proposals — not asking questions.

### Section Statuses

Each section in `context.json` carries one of:

| Status | Meaning |
|---|---|
| `defined` | Established by an agent, confirmed by user |
| `inferred` | Extracted from existing choices, not explicitly decided |
| `missing` | No source artifact addresses this section |
| `conflicted` | Multiple sources disagree |

**Completeness score** = `defined / (defined + missing)`. Inferred and conflicted don't count — they need resolution.

### Agent Behavior

When an agent encounters a `missing` section relevant to its current work, it:

1. Derives a sensible default from inference chains (established choices → implied values)
2. Applies the inferred value to its output
3. Explains its reasoning transparently
4. Writes to the relevant artifact
5. Reconciliation hook picks it up, status becomes `inferred`

The user can say nothing (inferred sticks), confirm (upgrades to `defined`), or override (`defined` with their value).

### Inference Chains

**Warm editorial project:**
Known: warm earth tones, editorial aesthetic, serif headlines
- → motion: deliberate (200/400/600ms)
- → spacing: generous (editorial density)
- → radius: subtle (4–8px, not pill-shaped)
- → voice: measured, confident, no exclamation marks

**Dense dashboard project:**
Known: data-dense dashboard, monospace accents, dark mode
- → motion: quick and functional (100/200/300ms)
- → spacing: tight with clear grouping
- → radius: minimal (2–4px)
- → voice: terse, status-oriented

### Principle

Agents are opinionated by default, overridable on request. Not "what do you want?" but "here's what I think, push back if I'm wrong." The system fills itself in through normal work, not through questionnaires.

---

## Capability 4: Design Check (Agent Self-Correction)

Three-layer validation used as an internal feedback loop. Agents validate their own work and fix issues before presenting to the user. The user never sees a report — they see finished work that already passes.

### Agent Internal Loop

```
1. Agent generates output
2. Agent runs Design Check against its own output
3. Issues found? Agent fixes them silently.
4. Runs Design Check again.
5. Clean pass? Present to user.
6. Max 3 check-fix cycles, then present with remaining info-level notes.
```

### Layer 1: Static Analysis

Deterministic checks, no LLM required.

- Hardcoded color values not in `context.json` palette
- Hardcoded spacing values not on the spacing scale
- Hardcoded font families not in the typography section
- Hardcoded border-radius not on the radius scale
- Hardcoded z-index, shadow, or timing values
- Missing CSS custom property usage where tokens exist
- Accessibility: contrast ratios computed from declared colors

### Layer 2: Structural Analysis

Pattern matching with light LLM assistance.

- AI fingerprint patterns from design-baseline (three equal cards, centered-everything, gradient text, same radius everywhere)
- Component state completeness (missing hover/focus/active/disabled/loading/empty/error)
- Border-radius nesting rule compliance
- Spacing consistency against declared density
- Typography hierarchy (sequential heading levels, declared scale)

### Layer 3: Visual Analysis

Screenshot capture via existing Playwright verification tools + vision LLM. Captures rendered output, validates against declared aesthetic direction with specific checkable assertions constructed from `context.json`:

- Palette compliance (colors outside declared range)
- Typography compliance (wrong font families)
- Style compliance (elements contradicting declared aesthetic)
- Spacing compliance (density mismatch)
- Avoid-list compliance (patterns on the explicit avoid list)

### Finding Format

Every finding includes:

| Field | Purpose |
|---|---|
| layer | Which analysis layer produced it |
| severity | `error` / `warning` / `info` |
| file/location | Where in the output the issue appears |
| rule violated | Which design system rule was broken |
| suggestion | Actionable fix |
| citation | Source decision — which agent, which date, which artifact |

### When Findings Reach the User

Findings surface to the user in only two cases:

1. **Conflicted context** — output violates an inferred value the user never confirmed. Agent flags the tension conversationally.
2. **Explicit audit** — user asks "check this page against our design system." Agent narrates findings conversationally.

### Incomplete Context Behavior

Design Check only validates against what's defined. Missing sections are skipped entirely. No false positives from checking against things the user hasn't decided.

---

## The `.design/` Directory Schema

```
.design/
  context.json              — Auto-maintained structured context (never hand-edit)
  preferences.md            — Taste profile (per-project)
  AESTHETIC-GUIDE.md         — Visual direction (art-director output)
  tokens.json               — Design tokens (token-generator output)
  tokens.css                — CSS export
  specs/
    [feature]-[date].md     — Component/feature specs
  observed/
    *.md                    — Local knowledge enrichment overlay
  history/
    [date]-[decision].md    — Decision log entries (future, not in this spec)
```

Everything except `context.json` is authored by humans or agents as they work. `context.json` is the only auto-maintained file.

---

## Components to Build

| Component | Type | Purpose |
|---|---|---|
| Reconciliation hook | Hook module | Watches `.design/` writes, maintains `context.json` |
| design-check agent | Agent | Runs three-layer validation, used internally by other agents |
| `context.json` schema | JSON Schema | Defines the structure, validates the file |
| Inference engine | Context/instructions | Maps known values to inferred defaults |
| Gap-filling behavior | Context addition | Instructions for existing agents to propose inferred values with reasoning |

---

## Impact on Existing Agents

None of the 12 existing agents change their outputs. They keep writing aesthetic guides, tokens, specs, and preferences exactly as they do now. What changes is they gain a new input — `context.json` loaded at session start — which makes them smarter about what's already decided, what's inferred, and what's missing.

---

## Integration Points

- Reconciliation hook fires automatically on `.design/` writes
- All design agents read `context.json` at session start
- Design Check runs internally within agent loops (self-correction)
- Design Check can be a gate step in design-to-implementation recipes
- Corrections flow back through normal write path → hook → `context.json` updates

---

## User Experience

**Session 1:** Work with art-director on color and style. Behind the scenes, `context.json` is born with color and style sections defined.

**Session 2:** Ask component-designer to build a card. Agent reads `context.json`, knows the palette and style, infers spacing and radius from the editorial direction, builds the card, runs design-check against its own output, fixes issues silently, presents clean component.

**Session 3:** Building a data table, user overrides inferred generous spacing with tight functional spacing. Agent writes updated context, reconciler updates `context.json`, future data-dense components inherit the override.

Over time, the design system fills itself in through the work. No questionnaires, no forms, no "please define your spacing scale before proceeding."
