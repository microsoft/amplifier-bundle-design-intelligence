# Shape & Corners: What Geometry Communicates

**Purpose:** This document provides metacognitive understanding of shape expression in UI — what corner radii, edge treatments, and geometric choices *mean*, not just how to implement them. Use this to inform spatial decisions that align with user vision and emotional intent.

**Status:** Curated knowledge - will evolve as research observations accumulate

**Sources:** Arun Venkatesan's analysis of Apple's product geometry, 92learns border-radius research (2026), Universal Principles of Design (contour bias)

---

## The Expression Framework

Shape is not decoration. It is a signal about relationship — between the interface and the user, between elements and each other, between content and its container. Every radius value carries information about proximity, safety, formality, and hierarchy.

### The Three Layers of Shape Expression

1. **Geometry** (what it is) — Radius values, squircles vs. circular arcs, nesting math
2. **Perception** (what it feels like) — Safe, formal, approachable, aggressive, premium
3. **Relationship** (what it means here) — Proximity to the user, hierarchy, brand voice

This document focuses on layers 2 and 3: perception and relationship.

---

## The Proximity Principle

**Closer to the user = rounder.**

This is the foundational insight. Arun Venkatesan measured Apple's entire product line and found a direct, consistent correlation between how close an object is to the human body and how round its corners are:

| Object | Roundness | Distance from body |
|---|---|---|
| Desktop displays | 0% | Furthest (desk) |
| Studio Display | 2-3% | Far (desk, eye level) |
| MacBooks | 7-10% | Medium (lap/desk) |
| iPads | 12-18% | Close (hands) |
| iPhones | ~33% | Very close (hand-held) |
| AirPods / Apple Watch | ~50% | On the body |
| Apple Pencil / earbuds | 100% | Touching skin |

Designer Naoto Fukasawa articulated the underlying principle: the closer an object is to a human, the rounder it should be. Physical objects near the body feel wrong with sharp edges — our hands expect smoothness. Digital interfaces inherit this perception.

### Translating to UI

In interfaces, "closeness" maps to **interactive proximity** — how directly the user engages with an element:

| UI element | Interaction | Radius direction |
|---|---|---|
| Page containers, backgrounds | Viewed, not touched | Minimal or zero radius |
| Cards, panels, sections | Read, occasionally clicked | Moderate radius |
| Buttons, toggles, chips | Tapped/clicked directly | Rounder radius |
| Avatars, status dots, pills | Identity-level, intimate | Full radius |

This is not a rigid scale — it's a thinking tool. When choosing radius, ask: **how directly does the user interact with this element?** More direct = rounder.

---

## The Psychology of Corners

### Contour Bias

Sharp angles activate the amygdala — the brain's fear processing center. This is documented in *Universal Principles of Design* as the **contour bias**: humans perceive rounded objects as safer, more approachable, and less threatening than sharp-cornered equivalents.

This is not aesthetic preference. It is perceptual neuroscience. The same interface with rounded corners is literally perceived as friendlier than the same interface with sharp corners.

### The Personality Spectrum

| Radius | What it communicates | Best for |
|---|---|---|
| 0px (sharp) | Technical precision, editorial authority, structural rigidity | News sites, data dashboards, enterprise tools, developer UIs |
| 2-4px (subtle) | Professional restraint, business-appropriate, structured | B2B SaaS, banking, corporate platforms |
| 8-12px (moderate) | Balanced modernity, versatile, considered | E-commerce, social platforms, general apps |
| 16-24px (large) | Warmth, approachability, friendliness, informality | Consumer apps, wellness, creative tools |
| Full pill | Playful confidence, mobile-native, trend-forward | Chat apps, social media, toggles, tags |

**A 2px change in border radius can shift how an entire interface feels.** Human perception is extremely sensitive to this detail.

### Sharp Corners as Intentional Choice

Sharp corners are not a deficiency. They communicate:
- **Editorial authority** — newspapers, journals, data-dense interfaces
- **Technical precision** — developer tools, terminal UIs, code editors
- **Structural clarity** — tables, grids, data visualization
- **Industrial aesthetic** — hardware-adjacent products, maker tools

Using sharp corners intentionally signals formality and expertise. Using them by default signals nothing.

---

## The Nesting Principle

**Inner radius = Outer radius - Padding.**

When elements are nested (a button inside a card, an image inside a container), the inner element's radius must account for the gap between them. Using the same radius on both parent and child creates visually uneven spacing — the corners appear thicker than the sides.

### Why This Matters for Expression

Correct nesting communicates **craftsmanship**. The gap between parent and child corners is one of the most visible quality signals in UI. Users cannot articulate what's wrong when nesting is off, but they perceive it immediately as "unpolished" or "amateur."

### Edge Cases

When padding exceeds the outer radius, the formula produces a negative number. Use zero, or a small minimum (2-4px). A hard zero sometimes feels abrupt — a slight radius preserves warmth without violating the math.

---

## Continuous Curvature (Squircles)

Standard CSS `border-radius` creates circular arcs that produce a visible "kink" where the straight edge meets the curve. Apple uses **squircles** — continuous curvature shapes that eliminate this discontinuity. The transition from straight to curved is gradual, producing corners that feel smoother and more organic.

### What Squircles Communicate

- **Physical plausibility** — real objects don't have mathematical discontinuities at corners
- **Premium quality** — the smoothness reads as crafted, not computed
- **Organic warmth** — even at small radii, squircles feel softer

### When to Use

- Squircles matter most on larger elements where the kink is visible (cards, modals, hero containers)
- On small elements (badges, chips) the difference is imperceptible
- Figma supports squircles via the "smooth corners" toggle
- CSS does not yet support squircles natively; SVG paths or larger radii on smaller elements approximate the effect

---

## Radius as Scale Signal

**Scale radius proportionally with element size.** A 16px radius on a 32px chip makes it a pill. The same 16px on a 400px card barely registers as rounded. The same radius applied uniformly across different-sized elements creates inconsistency.

### The Grouping Approach

Group elements by their **shortest side**, then assign radius by group:

| Shortest side | Radius range | Examples |
|---|---|---|
| Under 24px | 2-4px | Checkboxes, small badges, inline indicators |
| 24-40px | 4-8px | Chips, tags, small buttons, tooltips |
| 40-64px | 8-12px | Standard buttons, inputs, cards |
| 64-120px | 12-16px | Modals, large cards, dialog boxes |
| 120px+ | 16-24px | Hero sections, bottom sheets, large containers |

This is a starting framework, not a rigid rule. The principle: **bigger elements always get bigger radii.**

---

## Radius Hierarchy Within Components

Within a single component, radius variation communicates internal hierarchy:

- **Container** gets the largest radius (establishes the shape language)
- **Primary interactive elements** get moderate radius (inviting engagement)
- **Secondary elements** get smaller radius (supporting without competing)
- **Data elements** inside containers may use zero radius (precision within warmth)

This creates a natural visual nesting where the eye reads hierarchy through shape, not just size and color.

---

## Using This Knowledge

### In Agent Workflows

When a user describes a feeling, translate to shape decisions:

| User says | Shape direction |
|---|---|
| "Premium" | Moderate radius with correct nesting, possible squircles |
| "Friendly" | Larger radius (12-24px), pill-shaped buttons |
| "Technical" | Minimal radius (0-4px), sharp containers, precise grids |
| "Modern" | Moderate-to-large radius, mixed sharp/round for tension |
| "Trustworthy" | Consistent radius scale, correct nesting, no surprises |
| "Playful" | Large radius, pills, varied shapes, asymmetric rounding |

### Common Anti-Patterns

- **Same radius on everything** — removes hierarchy, makes everything blend together
- **Same radius on parent and child** — the nesting formula exists for a reason
- **Sharp corners by default** — choose sharp intentionally, not by omission
- **Mixing sharp and round at the same hierarchy level** — siblings should match
- **Full pill on everything** — dilutes the pill's meaning as a proximity signal

---

## Community Notes

This document will improve with:
1. **Research validation** — Cross-reference radius trends in archived award-winning designs
2. **Platform-specific patterns** — How iOS, Android, and web radius conventions differ
3. **Cultural considerations** — Whether shape perception varies across cultures
4. **Accessibility insights** — How radius affects cognitive load and target perception

---

*Last updated: 2026-03-05*
*Knowledge source: Arun Venkatesan (Apple geometry analysis), 92learns (border-radius research), Universal Principles of Design (contour bias), curated design expertise*
