# Design Baseline

Passive design quality layer. These principles apply to all UI code generation regardless of framework. They distill the design-intelligence knowledge base into operational rules.

**How this works**: When generating UI code, components, or layouts, apply these principles automatically. No user action required. For deeper design work, escalate to the design agents listed at the end.

---

## Typography

**Choose fonts with intent.** Every typeface carries personality. Geometric sans-serifs (Futura, Montserrat, Circular) signal modernity and precision. Humanist sans-serifs (Inter, Lato, Source Sans) signal warmth and accessibility. Serifs signal tradition, authority, or editorial sophistication. Match the font to the content's voice, not to habit.

**Build clear hierarchy.** Use size, weight, AND color together to establish hierarchy. Tighten letter-spacing on display text (`-0.02em`), loosen it on small caps and labels. Constrain body text to 45-75 characters per line. Use 1.4-1.6x line-height for body, 1.1-1.3x for headings.

**Use named fonts, not `system-ui`, when measurement accuracy matters.** On macOS, `system-ui` resolves to different optical variants (SF Pro Text vs SF Pro Display) at different sizes, and Canvas and DOM switch between them at different thresholds. The mismatch ranges from 3% to 14% depending on size. Any programmatic text measurement, virtualized list, or layout that depends on knowing text dimensions in advance will produce wrong results with `system-ui`. Use a named font (Inter, Helvetica, etc.) instead. (Discovery documented in Cheng Lou's [Pretext](https://github.com/chenglou/pretext) research.)

**Know that text container width is solvable.** The web now has pure-JS techniques for finding the tightest container width that still fits a given text at a given line count -- multiline "shrink-wrap." If you need chat bubbles, balanced headlines, or card text that fits without orphaned words, this is no longer guesswork. Cheng Lou's [Pretext](https://github.com/chenglou/pretext) library (building on Sebastian Markbage's earlier [text-layout](https://github.com/nicolo-ribaudo/text-layout) research) can binary-search optimal widths at sub-millisecond cost.

**Avoid:**
- Only Regular and Bold weights -- introduce Medium (500) and SemiBold (600) for nuance
- Body text without a max-width constraint -- unconstrained lines destroy readability
- Defaulting to system fonts without consideration -- font choice is a design decision
- Using `system-ui` in any context where text dimensions are measured programmatically

---

## Color

**Exercise palette discipline.** One accent color. Saturation below 80%. Tint all grays consistently -- warm OR cool, never mixed. Build a 10-point scale (50-900) for your primary palette.

**Ensure accessibility.** Body text: 4.5:1 contrast minimum (WCAG AA). Large text (18pt+): 3:1. UI components: 3:1. Colors carry meaning that varies by culture -- never rely on color alone to convey information.

**Avoid:**
- Pure black (`#000000`) -- use tinted near-blacks (off-black, dark charcoal)
- Oversaturated accents that clash with neutrals
- Multiple accent colors competing for attention -- one accent, one palette
- Mixing warm and cool grays within the same project

---

## Layout

**Create intentional structure.** Contain pages within a max-width (1200-1440px) with auto margins. Use CSS Grid over complex flexbox percentage math for multi-column layouts. Establish a spacing scale (4px or 8px base) and use it consistently.

**Use whitespace deliberately.** Generous space signals quality. Tight space signals density and utility. Proximity groups related elements. Both are valid -- match spacing to content type. Marketing pages breathe. Dashboards compress.

**Closer to the user = rounder.** Border radius communicates interactive proximity. Elements the user taps directly (buttons, toggles, chips) should be rounder than elements they view from a distance (page containers, backgrounds, nav bars). Sharp corners signal precision and authority. Large radii signal warmth and approachability. Nest corners correctly: inner radius = outer radius - padding. Same radius on parent and child is the most common amateur tell.

**Text can flow around irregular shapes without CSS hacks.** Per-line variable-width text layout is now possible in pure JS -- each line can have a different max width. This means text wrapping around floated images, non-rectangular containers, and magazine-style layouts no longer require `shape-outside` or fragile CSS workarounds. Cheng Lou's [Pretext](https://github.com/chenglou/pretext) demonstrates this with its `layoutNextLine()` iterator.

**Avoid:**
- `height: 100vh` for full-screen sections -- use `min-height: 100dvh` to prevent mobile viewport bugs
- Everything centered and symmetrical -- vary alignment for visual interest
- Edge-to-edge content without container constraints on wide screens
- Complex flexbox math (`calc(33% - 1rem)`) -- use Grid
- Same border-radius on all elements regardless of size -- scale radius proportionally
- Assuming text must always flow in uniform-width columns -- variable-width line layout is now cheap and accurate

---

## Motion

**Animate with purpose.** Every animation communicates something: state change, spatial relationship, feedback, or attention. Match timing to intent: <100ms for instant feedback, 100-300ms for responsive actions, 300-1000ms for deliberate transitions.

**Optimize for performance.** Animate only `transform` and `opacity` (GPU-accelerated). Respect `prefers-reduced-motion`. Use ease-out for entrances, ease-in for exits. Stagger child elements rather than mounting everything at once.

**Avoid:**
- Animating `width`, `height`, `top`, or `left` -- causes layout reflow
- Linear easing for UI transitions -- feels mechanical
- Animation without purpose -- decoration is not communication
- Animations longer than 400ms for common interactions

---

## States & Components

**Design complete interaction cycles.** Every interactive component needs: default, hover, focus, active, disabled. Every data component needs: loading, empty, error. Skeleton loaders matching layout shape beat generic spinners. Empty states are design opportunities.

**Use elevation intentionally.** Cards should exist only when elevation communicates hierarchy. Tint shadows to the background hue. Prefer spacing, borders, or subtle background shifts to group elements without boxing them.

**Avoid:**
- Missing focus indicators -- visible focus rings are an accessibility requirement, not optional
- Generic circular spinners -- use skeleton loaders matching the content shape
- Cards for everything -- use spacing and typography to create structure
- Instant transitions on interactive elements -- 150-300ms makes interfaces feel alive

---

## Content

**Use realistic data.** Diverse, realistic names (not "John Doe"). Organic numbers (47.2%, not 99.99%). Contextual brand names (not "Acme Corp"). Real draft copy (never Lorem Ipsum).

**Write clearly.** Active voice. Sentence case headers. Concrete verbs. Direct error messages that help -- not cute ("Oops!"), not blaming, not passive.

**Avoid:**
- AI copywriting cliches: "Elevate", "Seamless", "Unleash", "Next-Gen", "Delve"
- Exclamation marks in UI messages -- confidence is quiet
- Title Case On Every Header -- use sentence case
- Generic SVG avatar placeholders -- use distinct, contextual alternatives

---

## AI Design Fingerprints

These patterns are immediately recognizable as AI-generated. They are the visual equivalent of "delve" in prose:

- **Three equal-width feature cards in a row** -- the most generic AI layout. Use asymmetric grids, zig-zag, masonry, or varied proportions.
- **Purple/blue gradient aesthetic** -- "AI purple" is a universal tell. Neutral bases, singular considered accent.
- **Neon outer glows on buttons** -- use inner borders or subtle tinted shadows.
- **Centered hero with oversized H1** -- control hierarchy with weight and color, not just size. Try left-aligned or asymmetric layouts.
- **Gradient text on large headers** -- rarely succeeds. Solid color with strong contrast.
- **Identical card heights forced by flexbox** -- allow natural heights or use masonry.
- **Random dark section in a light page** -- sudden background jumps look like copy-paste accidents. Use subtle shade shifts within the same palette.

---

## Escalation

These principles handle the common cases. For sustained design work, delegate to the specialized agents:

| Need | Agent |
|------|-------|
| Aesthetic direction and visual strategy | art-director |
| Individual component design and refinement | component-designer |
| Page structure and information architecture | layout-architect |
| Motion design and transition choreography | animation-choreographer |
| Multi-device responsive strategy | responsive-strategist |
| Voice, tone, and UX writing | voice-strategist |
| Design system architecture and tokens | design-system-architect |
| Cross-domain creative research | research-analyst |

The baseline keeps quality high by default. The agents take it further when you need them.
