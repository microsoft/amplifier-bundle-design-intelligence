# Creative Handoff Protocol: AI Explore, Human Refine, Code Scale

## The Pattern

Creative production has three phases with different strengths. Trying to do all three with AI produces mediocre results. The handoff points matter.

```
Phase 1: AI EXPLORES          Phase 2: HUMAN REFINES         Phase 3: CODE SCALES
(breadth, speed, iteration)   (precision, judgment, craft)    (consistency, completeness)
                                                              
nano-banana generates          User traces in Figma/          Script generates all
8+ concept variations    -->   Illustrator/Sketch,      -->   platform variants from
scored by art-director         creating canonical SVG          the canonical source
                               with production precision
```

## Why This Works

Each phase uses the right tool for the right job:

| Phase | Strength | Weakness |
|-------|----------|----------|
| AI generation | Creative breadth, rapid iteration, exploring the space | Pixel precision, clean vectors, consistent geometry |
| Human design tools | Exact control, clean paths, production quality | Slower than AI for exploration, limited by imagination |
| Programmatic scaling | Consistency, completeness, never forgets a format | No creative judgment, no quality assessment |

**The mistake**: Trying to use AI for production assets. AI-generated icons, wordmarks, and illustrations are good enough to EVALUATE direction but not good enough to SHIP. The gap is in vector precision — clean compound paths, consistent stroke weights, mathematically precise curves.

**The insight**: AI is the sketch pad, not the drafting table.

## When to Apply This Pattern

- **Icon design**: AI generates concepts, human traces the winner, code renders all sizes
- **Wordmark/logotype**: AI explores letterform treatments, human refines in type design tools, code outlines and exports
- **Illustration style**: AI generates style variations, human creates master illustrations, code adapts for contexts
- **Brand marks**: AI explores symbol concepts, human creates the canonical vector, code generates all colorways and formats

## When NOT to Apply This Pattern

- **UI component design**: Code IS the final medium — no handoff needed
- **Design tokens**: These are already code — no human refinement phase
- **Layout/composition**: The implementation IS the artifact
- **Motion design**: Defined in code, previewed in code

## The Three Phases in Detail

### Phase 1: AI Explores

**Goal**: Generate a broad field of creative options, fast.

**How**:
- Use nano-banana to generate 4–8 concept variations per round
- Have art-director score each on relevant dimensions (see Icon Evaluation below)
- Run 2–3 rounds, narrowing from many concepts to 2–3 finalists
- Present finalists to the human with scores and rationale

**What good looks like**:
- 8+ distinct concepts explored (not 8 variations of the same idea)
- Clear scoring rationale for why finalists won
- Human can see the creative territory that was explored

**What to avoid**:
- Generating one concept and refining it endlessly (explore breadth first)
- Treating AI output as final (it's a sketch, not a deliverable)
- Skipping scoring (human needs structured comparison, not "which do you like?")

### Phase 2: Human Refines

**Goal**: Turn the winning concept into a production-quality canonical source.

**The handoff**: Give the human:
1. The winning AI-generated concept (as reference image)
2. The scoring rationale (what makes this concept work)
3. The brand constraints (colors, style keywords, technical requirements)
4. The target formats (where this will be used — favicon, app icon, OG image, etc.)

**What the human produces**:
- Clean vector SVG with proper compound paths
- Mathematically consistent geometry (equal radii, aligned strokes)
- Color values matching the brand palette exactly
- Multiple variants if needed (dark/light, with/without background)

**What to avoid**:
- Asking the human to "just clean up the AI output" (they should re-draw, not trace noise)
- Skipping the handoff brief (human needs context, not just "make it better")

### Phase 3: Code Scales

**Goal**: Generate every platform variant from the canonical source.

**What a render pipeline typically produces**:

| Category | Formats | Sizes |
|----------|---------|-------|
| App icons | PNG | 16, 32, 48, 64, 128, 256, 512, 1024px |
| Favicons | .ico (multi-size), PNG | 16, 32px + multi-resolution .ico |
| Apple touch | PNG | 180px |
| PWA icons | PNG | 192, 512px |
| OG images | PNG | 1200x630 |
| Platform | .icns (macOS), .ico (Windows) | Platform-specific |

**What to avoid**:
- Hand-exporting each size (that's what code is for)
- Generating sizes the project doesn't need (ask first)
- Forgetting dark/light variants (if the icon has background-dependent elements)

## Icon Evaluation Scoring

When art-director evaluates icon concepts during Phase 1, score on these dimensions:

| Criterion | Weight | What to assess |
|-----------|--------|----------------|
| **Color harmony** | /10 | Does it use the brand palette effectively? Do colors work together? |
| **Style match** | /10 | Does it match the established aesthetic (geometric, organic, technical, playful)? |
| **Small-size legibility** | /10 | Is it recognizable at 32px (favicon) and 16px (tab icon)? Does detail survive? |
| **Brand coherence** | /10 | Does it communicate what the product does? Does it feel like it belongs to this brand? |

**Score interpretation**:
- 35–40: Strong candidate — advance to finals
- 28–34: Has potential — worth one refinement round
- Below 28: Drop it — fundamental issues won't be fixed with refinement

Present scores in a comparison table so the human can see relative strengths:

```
| Concept | Color | Style | Scale | Brand | Total |
|---------|-------|-------|-------|-------|-------|
| A: Grid | 8     | 9     | 7     | 8     | 32    |
| B: Hub  | 7     | 8     | 9     | 9     | 33    |
| C: Badge| 9     | 9     | 8     | 10    | 36    |
```

## Brand Asset Set Checklist

A complete brand asset set — the deliverable from the full three-phase process — typically includes:

### SVG Sources (canonical, vector)
- [ ] Icon — dark variant (light frame/elements on dark or transparent background)
- [ ] Icon — light variant (dark frame/elements on light or transparent background)
- [ ] Wordmark — on dark (primary text color + accent, transparent background)
- [ ] Wordmark — on light (dark text color + accent, transparent background)
- [ ] Lockup — on dark (icon + wordmark combined, horizontal)
- [ ] Lockup — on light (same, light variant)

### Key Decisions
- [ ] Wordmark uses outlined/converted type (no font dependency in SVG)
- [ ] Colors match brand palette tokens exactly
- [ ] Dark/light variants tested on actual backgrounds (not just inverted)
- [ ] Lockup spacing between icon and wordmark is intentional (not default)

### Generated Assets (from render pipeline)
- [ ] PNG icon set at required sizes
- [ ] Favicon (.ico multi-size + PNG fallbacks)
- [ ] Apple touch icon (180px)
- [ ] PWA icons (192, 512px) if web app
- [ ] OG image (1200x630) for social sharing
- [ ] Platform-specific (.icns, .ico) if native app

### Not Every Project Needs All of This

The checklist above is the FULL set. Most projects need a subset:

| Project Type | Minimum Set |
|-------------|-------------|
| CLI tool | Icon SVG + favicon + OG image |
| Web app | Icon SVGs + wordmark + favicon + PWA icons + OG image |
| Native app | Full set including platform-specific formats |
| Library/package | Icon SVG + OG image (for GitHub/npm) |

## Relationship to Other Workflows

This protocol describes the creative production handoff. It connects to other design-intelligence workflows:

- **Before this**: Brand naming (brand-naming skill), aesthetic direction (art-director), moodboard
- **During Phase 1**: art-director + nano-banana for generation and scoring
- **After Phase 3**: Design system creation (token-generator, design-system-architect) using the brand assets as input
- **Ongoing**: design-check validates that implementations use the brand assets correctly
