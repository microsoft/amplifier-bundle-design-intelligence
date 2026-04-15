# Motion & Emotion: What Animation Communicates

**Purpose:** This document provides metacognitive understanding of motion expression — what animation choices *communicate* emotionally and what brand signals they produce. Use this to translate user vision ("It should feel alive but not distracting") into specific motion decisions.

**Status:** Curated knowledge - will evolve as research observations accumulate

**Relationship to animation-principles.md:** That file covers the mechanics and science of animation (timing thresholds, easing math, GPU performance). This file covers what animation *communicates* — the emotional and brand signals that different motion styles produce.

---

## The Expression Framework

Motion is the most emotionally charged design dimension. Color establishes mood; typography establishes voice; shape establishes personality. But motion is the only dimension that communicates *character over time* — it reveals how an interface responds, breathes, and behaves under user action.

Users describe poor motion instinctively: "clunky," "soulless," "jittery," "sluggish," "jumpy." They describe good motion just as instinctively: "smooth," "alive," "snappy," "considered." These are emotional judgments, not technical ones.

### The Three Layers of Motion Expression

1. **Mechanics** (what it is) — Duration, easing curve, properties animated
2. **Personality** (what it feels like) — Snappy, flowing, bouncy, calm, mechanical
3. **Intent** (what it communicates) — Brand character, interface confidence, user relationship

This document focuses on layers 2 and 3.

---

## Duration as Weight Signal

Duration is the primary axis of motion communication. It maps to perceived weight, importance, and confidence.

### The Duration Personality Map

| Duration range | Personality | Communicates | Best for |
|---|---|---|---|
| <100ms | Invisible | Instant, direct, mechanical | Hover highlights, focus rings, cursor tracking |
| 100–200ms | Snappy | Responsive, confident, professional | Toggle switches, checkbox clicks, quick feedback |
| 200–300ms | Considered | Deliberate, polished, balanced | Button presses, dropdown open, tab switches |
| 300–500ms | Deliberate | Important, significant, weighted | Modal entrances, drawer slides, major transitions |
| 500–800ms | Expressive | Narrative, editorial, experiential | Onboarding sequences, page transitions, hero animations |
| >800ms | Cinematic | Showcase, brand moment, storytelling | Splash screens, product reveals, marketing |

### The Weight Implication

Duration communicates how much something *matters*:
- Short duration = "This is a quick, confident response to your action"
- Long duration = "This is a significant transition worth your attention"

When duration doesn't match content significance — a trivial hover taking 600ms, or a major error appearing in 80ms — users perceive a mismatch between the interface's behavior and the actual significance of events.

---

## Easing as Personality

If duration controls weight, easing controls personality. The easing curve is the single most impactful motion parameter for brand character.

### The Easing Personality Spectrum

**Linear**
- What it feels like: Mechanical, robotic, unnatural
- What it communicates: Digital precision, lack of physicality, "this is a computer"
- When to use: Loading bars (progress is linear), data visualizations, very subtle micro-interactions
- Risk: Feels unpolished everywhere else — linear motion reads as "unfinished" to users trained on physical physics

**Ease-in (slow start, fast end)**
- What it feels like: Building momentum, gathering energy
- What it communicates: Exit animations, elements leaving the stage — the element is departing
- When to use: Elements exiting the scene (modals closing, toasts disappearing)
- Risk: Entry animations with ease-in feel like an element crashing into place

**Ease-out (fast start, slow end)**
- What it feels like: Natural deceleration, graceful arrival
- What it communicates: Confidence — the element arrives decisively and settles
- When to use: Entry animations, sliding elements into view, the default for most UI motion
- What makes it "natural": Matches how physical objects decelerate (friction, air resistance)

**Ease-in-out (slow start, fast middle, slow end)**
- What it feels like: Smooth, considered, even-tempered
- What it communicates: Sophisticated polish, nothing rushed, nothing harsh
- When to use: Between-state transitions (tabs, selections), elements repositioning within the screen
- Character: The most "polished" feeling curve for in-place transitions

**Spring / bounce (overshoots, settles)**
- What it feels like: Alive, physical, elastic
- What it communicates: Playfulness, physicality, tactile reality, energy
- When to use: Elements responding to direct manipulation (pull-to-refresh, drag feedback), mobile-first interactions, playful/consumer brands
- Character: Spring animations feel *alive* in a way no other curve achieves
- Risk: Inappropriate in contexts requiring seriousness — springs on error dialogs feel wrong

**Custom curves (fine-tuned for brand)**
- What it communicates: Craft, care, distinctiveness
- Example: Apple's custom spring curves that make iOS feel uniquely "Apple"
- When to invest: When the brand has a specific motion personality that standard curves don't capture

### The Easing-to-Brand Mapping

| Brand character | Easing choice |
|---|---|
| Enterprise / B2B | Ease-out (entry), ease-in-out (transitions) — confident, professional |
| Consumer / lifestyle | Spring / ease-out — warm, physical, alive |
| Finance / healthcare | Ease-out — professional, controlled, no bounce |
| Creative / playful | Spring, slight overshoot — energetic, expressive |
| Luxury / editorial | Ease-in-out with longer duration — deliberate, precious |
| Utility / developer | Faster ease-out, possibly linear — functional, no ceremony |

---

## The Physicality Signal

Motion that mirrors physical reality produces a specific emotional response: the interface feels *real*. This is the core of what separates "alive" from "mechanical."

**Physical motion signals:**
- Objects decelerate when they stop (ease-out)
- Pushed objects overshoot slightly and settle (spring)
- Heavy objects move more slowly than light ones (duration variation by element size/importance)
- Objects have momentum — they don't start and stop instantly

**Non-physical motion signals:**
- Linear timing (machines, not reality)
- Identical duration for large and small elements
- Instant starts and stops

The more physical the motion, the more the interface reads as an extension of the real world. The more mechanical, the more it reads as a purely digital artifact. Neither is categorically wrong — but the choice communicates something about the brand's relationship with technology.

---

## Motion Quantity as Brand Signal

How much an interface animates is as communicative as how it animates.

### High Motion (Many animations, expressive transitions)
**Communicates:** Alive, expressive, modern, invested in experience
**Brand signal:** Consumer-focused, emotional, feature-rich, shows off
**Risk:** Distracting, performance cost, accessibility issues, can feel excessive
**Best for:** Marketing, consumer apps, entertainment, onboarding

### Moderate Motion (Key transitions animated, micro-interactions present)
**Communicates:** Polished, considered, professional without showing off
**Brand signal:** Mature product, user-respecting, functional with care
**Best for:** Most SaaS products, e-commerce, professional consumer apps

### Low Motion (Minimal animation, purposeful only)
**Communicates:** Disciplined, fast, focused on content over chrome
**Brand signal:** Confident, utility-focused, respects user time
**Best for:** B2B tools, data dashboards, developer products, productivity software

### The Quiet Confidence Pattern
The highest-quality products often have the *least* motion — but what they do animate is *precisely* right. This communicates mastery: "We know exactly what needs to move and what doesn't." Excessive animation often signals uncertainty (covering up a weak visual design with motion).

---

## Specific Motion Types and Their Communication

### Entrance Animations
What enters, and how it enters, communicates priority. A modal that slides from the bottom (mobile-native) communicates "close to the body." A modal that fades in communicates "less intrusive." A modal that scales up from the trigger point communicates "here's what you clicked."

**Fade in:** Soft, unobtrusive, neutral — doesn't impose a direction or source
**Slide from bottom:** Mobile, close, dismissible — modal sheet pattern
**Slide from right/left:** Navigation, sequential — implies a hierarchy or journey
**Scale up from origin:** Direct spatial connection to trigger — confident, spatial
**Scale up from center:** App launch, key moment — dramatic, impactful

### Exit Animations
Exits communicate finality and transition quality. Poor exit animations are more damaging than poor entrance animations — they're the last impression of a completed interaction.

**Fade out:** Clean, simple, unobtrusive
**Slide away:** Spatial — the content goes somewhere
**Scale down to origin:** Returns to where it came from — spatial integrity

### State Transitions (hover, active, focus)
These micro-interactions are the most frequent motion in an interface and the largest contributor to "how the product feels" day-to-day.

- **Hover:** Subtle (10-15% lightness change or slight scale) — communicates "I see you"
- **Active/pressed:** More pronounced (scale down to 97-98%) — physical feedback, "you pressed this"
- **Focus ring:** Immediate appearance, no delay — accessibility and confidence signal
- **Loading spinner placement and style:** Communicates whether waiting is expected or unexpected

### Stagger (Sequential Timing)
Staggered animations — where list items, cards, or elements enter with slight offset timing — communicate:
- **Narrative control:** "I'm guiding your attention through this content"
- **Richness:** "There's real content here, not a single flat load"
- **Brand care:** Stagger is a signal of motion sophistication

Stagger should be short (30-80ms between items) and reduce in size over the list. Long stagger feels like a performance — short stagger feels like grace.

---

## Motion and Trust

One underappreciated dimension of motion communication: it signals how confident the interface is in its own decisions.

**High-confidence motion patterns:**
- Decisive entries (ease-out, arrives and settles)
- No "thinking" states between interactions
- Smooth state transitions without jank

**Low-confidence motion signals:**
- Jerky or inconsistent timing
- Long hesitations between actions
- Transitions that feel incomplete or abandoned

Users read motion fluency as a proxy for the product's overall quality and reliability. An interface with fluid, consistent motion feels like it was built by people who care. An interface with inconsistent, janky transitions feels like it wasn't finished — regardless of the actual functionality.

---

## Practical Application Guidelines

### Translating User Language to Motion Decisions

| User says | Motion direction |
|---|---|
| "Alive" | Add spring easing; animate more state transitions; add presence |
| "Snappy" | Reduce durations (150-250ms range); keep ease-out |
| "Smooth" | Ease-in-out; increase durations slightly; remove abrupt transitions |
| "Premium" | Fewer, more precise animations; longer durations where used; ease-in-out |
| "Playful" | Spring easing; slight overshoots; stagger entrance animations |
| "Professional" | Ease-out; 200-300ms range; no bounce; confident but not flashy |
| "Heavy" (problem) | Reduce durations; increase speed; check for >300ms animations that shouldn't be |
| "Distracting" (problem) | Reduce quantity; use motion only at interaction moments; remove decorative animations |
| "Mechanical" (problem) | Replace linear curves; add ease-out; consider spring for direct manipulation |

---

## Common Pitfalls

**Animating everything at the same duration**
A 250ms transition on a tooltip, a tab switch, and a full-page transition all feel wrong. Duration communicates significance — calibrate per element type.

**Using linear timing by default**
Linear timing is the default in many CSS properties. It's almost always wrong for UI motion. Always explicitly set an easing curve.

**Over-animating to compensate for weak visual design**
Motion cannot fix a visually weak interface. If animation is being added to make something feel "more alive," check whether the static design is strong enough first.

**Ignoring prefers-reduced-motion**
Users with vestibular disorders, epilepsy, or motion sensitivity rely on `prefers-reduced-motion`. All motion should degrade gracefully. The reduced-motion version should use instantaneous or opacity-only transitions.

**Mismatched exit vs. entry timing**
Entry animations are often tuned carefully; exit animations get the same parameters by default. Exits should typically be faster than entries — the user has moved on and doesn't want to wait for content to leave.

**Spring on everything**
Spring easing is effective because it mimics physical behavior. Applying it to every transition dilutes its effect and can make an interface feel shaky or unpredictable. Reserve spring for direct-manipulation moments.

---

## Using This Knowledge

### In Agent Workflows

When reading an AESTHETIC-GUIDE.md or discovery brief, use this framework to:
1. Determine the motion intensity level appropriate for the product type
2. Select easing curves that match the brand personality
3. Establish whether the motion should feel physical/alive or controlled/precise
4. Define the duration range based on the product's positioning

### In Token Generation

Translate these signals into specific choices:
- **Duration tokens:** fast (100-150ms), normal (200-300ms), slow (350-500ms) — calibrate ranges to brand personality
- **Easing tokens:** default (ease-out), in, out, in-out, spring — name them by personality not math
- **Named transitions:** consider naming semantic transitions (hover-feedback, modal-enter, page-transition) as composites of duration + easing

---

## Community Notes

This document will improve with:
1. **Research validation** — Cross-reference motion choices in archived award-winning interface studies
2. **Platform conventions** — iOS vs Android vs web motion conventions and how to signal platform native-ness
3. **Accessibility patterns** — How to achieve expressive motion within reduced-motion constraints
4. **Dark mode motion** — Whether motion communication changes in dark contexts

---

*Last updated: 2026-04-14*
*Knowledge source: Curated design expertise, to be enhanced with research observations*
