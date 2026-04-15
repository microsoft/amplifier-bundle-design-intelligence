# Pattern Abstraction Guide

> **Purpose**: Guide researchers in extracting transferable patterns at the right level of abstraction for cross-domain inspiration.

---

## The Abstraction Ladder

When researching designs, patterns exist at multiple levels. The higher the abstraction level, the more transferable the pattern across domains.

```
Level 4: Cognitive Patterns    [MOST TRANSFERABLE]
    ↑
Level 3: Interaction Patterns
    ↑
Level 2: Component Patterns
    ↑
Level 1: Visual Patterns        [LEAST TRANSFERABLE]
```

**Research priority**: Extract patterns at **Level 3-4** from cross-domain sources for maximum creative value.

---

## Level 1: Visual Patterns (Least Transferable)

### What They Are
Specific visual treatments: colors, fonts, spacing, shadows, borders, textures.

### Transferability
**LOW** - Only transfer within the same brand/system or when aesthetic goals perfectly align.

### Examples
- "Uses 8px grid system"
- "Has 2px border radius on cards"
- "Uses Helvetica Neue at 14px"
- "Dark mode with #1a1a1a background"
- "Has subtle drop shadows at 0 2px 4px rgba(0,0,0,0.1)"

### When to Extract Level 1 Patterns
- Building a specific design system
- Maintaining brand consistency
- Creating mockups for client approval
- **Not for cross-domain inspiration**

### Anti-Pattern
❌ "Trading platforms use dark themes, so we should use a dark theme"
- Copies surface without understanding purpose
- Misses why dark works for trading (eye strain during long sessions, data visualization contrast)

---

## Level 2: Component Patterns (Moderately Transferable)

### What They Are
Structural patterns for UI components: card layouts, navigation patterns, form designs, modal structures.

### Transferability
**MODERATE** - Transfer with adaptation to context, industry conventions, and user expectations.

### Examples
- "Navigation uses hamburger menu on mobile"
- "Cards have image-title-description structure"
- "Forms use single-column layout with inline validation"
- "Modals have persistent header with close button"
- "Tables have sticky headers and zebra striping"

### When to Extract Level 2 Patterns
- Solving common UI problems
- Understanding component conventions
- Learning structural approaches
- **Useful but not breakthrough**

### How to Elevate
Ask: "Why is this component structured this way? What cognitive task does it solve?"

✅ Better:
- "Uses hamburger menu because mobile users expect discoverability over always-visible navigation"
- "Inline validation reduces error recovery cost by catching mistakes early"

---

## Level 3: Interaction Patterns (Highly Transferable)

### What They Are
How users accomplish tasks: discovery mechanisms, learning paths, feedback loops, error prevention, progressive complexity.

### Transferability
**HIGH** - Transfer across domains with context mapping. These are about human behavior, not specific implementations.

### Examples
- **Discovery**: "Users find features through doing, not reading" (video game tutorials)
- **Learning**: "Scaffolded complexity—basic mode first, advanced features unlocked after mastery" (photo editing apps)
- **Feedback**: "Immediate visual feedback on every action, even if processing continues in background" (mobile interfaces)
- **Error Prevention**: "Confirm destructive actions with preview of consequences" (file deletion dialogs)
- **Progressive Complexity**: "Start with sensible defaults, reveal customization options gradually" (email clients)

### When to Extract Level 3 Patterns
- Cross-domain research
- Solving UX challenges
- Understanding user behavior
- **Primary research focus**

### Example Extraction

**Source**: Video game tutorial level
**Level 2 (component)**: "Has tooltips that appear on hover"
**Level 3 (interaction)**: "Teaches by doing in safe environment where failure has no consequence, with immediate feedback on actions"

**Transfer to onboarding flow**:
- Not "add tooltips"
- Instead: "Let users try features in a sandbox state, provide immediate feedback, make mistakes harmless"

---

## Level 4: Cognitive Patterns (Most Transferable)

### What They Are
Fundamental principles about human cognition, attention, memory, and decision-making.

### Transferability
**HIGHEST** - Transfer almost universally. These are about how humans think, not specific designs.

### Examples

#### Attention Management
- "Use visual weight (size, color, position) to direct attention hierarchically"
- "Single focus point per view—decide what matters most"
- "Progressive disclosure reduces cognitive load while maintaining access to complexity"

#### Memory & Recognition
- "Recognition is easier than recall—show options rather than requiring memory"
- "Spatial memory is stronger than abstract memory—keep things in consistent locations"
- "Reduce working memory load—display information instead of requiring memorization"

#### Decision Support
- "Reduce choices to 3-5 options to prevent decision paralysis"
- "Provide context for comparison—what's normal, what's this, what's the difference"
- "Make consequences visible before commitment"

#### Information Hierarchy
- "Most important information first, always"
- "Group related information spatially, not just by visual styling"
- "White space creates structure—absence communicates as much as presence"

#### Error Prevention & Recovery
- "Prevent errors rather than correcting them"
- "Make system state visible—users should always know where they are"
- "Provide escape hatches—undo, back, cancel should always be accessible"

### When to Extract Level 4 Patterns
- Always (this should be automatic)
- When patterns seem universal
- When multiple domains solve the same problem similarly
- **Highest value research output**

### Example Extraction

**Source**: Hospital patient monitor
**Level 2 (component)**: "Has a vital signs panel with numbers and waveforms"
**Level 3 (interaction)**: "Displays real-time data with change indicators and alert thresholds"
**Level 4 (cognitive)**: "Gestalt status assessment—human brain can parse 'everything okay' or 'attention needed' in under 200ms without reading individual values. Uses size/color/position as attention-directing mechanism, not just information encoding."

**Transfer to ANY dashboard**:
The principle of "design for gestalt assessment first, detailed reading second" applies everywhere:
- Trading dashboards (portfolio health at a glance)
- Server monitoring (infrastructure health)
- Project management (project health)
- Fitness apps (daily health check)

---

## Extraction Methodology

### Step 1: Observe the Design
What does it look like? What are the visual elements?

### Step 2: Understand the Interaction
How do users accomplish tasks? What's the flow?

### Step 3: Identify the Cognitive Task
What is the user's brain actually doing? What decision/judgment/understanding are they forming?

### Step 4: Abstract the Principle
What's the universal truth here that transcends this specific implementation?

### Example Walkthrough

**Source**: Poker chip design

**Step 1 - Visual**: Round discs with distinct colors and denominations

**Step 2 - Interaction**: Players stack, count, and move chips. Visual identification must work at a glance from multiple angles.

**Step 3 - Cognitive Task**: Rapid value assessment + tactile importance feedback

**Step 4 - Principle**: "Status/value isn't just color—physical weight and tactile feedback communicate importance. The more valuable, the more 'present' it feels."

**Digital Translation**: Status indicators could have visual "weight" (size, shadow depth, position in z-space) not just color. Important items feel more "solid" or "present" on screen.

**Where This Applies**:
- Priority indicators in task lists
- Notification importance
- Alert severity
- Data point significance
- User reputation/status

---

## Common Abstraction Mistakes

### Mistake 1: Stopping at Visual
❌ "They use glassmorphism"
✅ "Glass effects create hierarchy through depth—is depth a useful metaphor for our information architecture?"

### Mistake 2: Cargo Culting Components
❌ "Bloomberg has dense information, so we should too"
✅ "Bloomberg serves expert users who've invested in learning the interface. Our users are occasional—we need progressive density that adapts to expertise."

### Mistake 3: Missing the Why
❌ "Medical dashboards use green/yellow/red indicators"
✅ "Medical dashboards use universal traffic light semantics because milliseconds matter in triage—patients don't need to learn what colors mean."

### Mistake 4: Transferring Context-Specific Patterns
❌ "Gaming UIs use flashy animations and sound effects for feedback"
✅ "Gaming UIs provide immediate, multi-sensory feedback because engagement is the primary goal. For productivity tools, subtle feedback prevents disruption while maintaining awareness."

---

## Research Documentation Template

When documenting research findings, use this structure:

```markdown
### [Source Example]

**Domain**: [Where did this come from]
**Context**: [What problem does it solve, for whom]

**Visual Pattern (L1)**: [What it looks like]
**Component Pattern (L2)**: [How it's structured]
**Interaction Pattern (L3)**: [How users accomplish tasks]
**Cognitive Pattern (L4)**: [Universal principle]

**Transferability**: [Why this is relevant to our project]
**Adaptation Notes**: [What changes when applied to our context]
```

### Example

```markdown
### Video Game Tutorial Levels

**Domain**: Gaming (onboarding new players)
**Context**: Teaching complex mechanics to players with varying experience, where poor onboarding leads to abandonment

**Visual Pattern (L1)**: Simplified art style, bright highlighting on interactive objects
**Component Pattern (L2)**: Tooltips, step-by-step prompts, practice areas
**Interaction Pattern (L3)**: Learn by doing in safe environment where failure has no consequence, immediate feedback on actions, progressive complexity
**Cognitive Pattern (L4)**: Humans learn motor skills and patterns better through practice than instruction. Safe failure reduces anxiety and increases exploration.

**Transferability**: Highly relevant for our SaaS onboarding—users currently read slides then feel lost in the actual interface.
**Adaptation Notes**: Can't gamify everything, but can create "practice mode" where actions don't affect real data, provide immediate feedback, and encourage exploration without fear of breaking things.
```

---

## Level 3-4 Extraction Practice

### Exercise: Trading Platform
Look at a trading platform dashboard.

**Don't extract**: "Has red/green for up/down"
**Do extract**: "Uses preattentive color processing (red/green) for rapid pattern scanning across 100+ data points. Human visual system detects these colors 40-80ms faster than reading numbers. Only works because of universal semantic association."

**Transfer**: Any interface requiring rapid scanning of many items for specific patterns (log monitoring, test results, inventory status).

### Exercise: IKEA Instructions
Look at IKEA assembly instructions.

**Don't extract**: "Uses simple line drawings"
**Do extract**: "Eliminates language barrier through universal visual language. Shows transformation state-by-state with explicit before/after. Highlights new elements in each step. Assumes no prior knowledge."

**Transfer**: Any instructional content for international or novice audiences. Principle works for UI tutorials, error recovery guides, setup flows.

### Exercise: Road Signs
Look at highway warning signs.

**Don't extract**: "Uses yellow triangles"
**Do extract**: "Hierarchy of attention: Shape communicates urgency (triangle = warning) before symbol is processed, symbol before text. Redundant encoding (shape + color + symbol + text) ensures message received even with impaired vision, lighting, or attention."

**Transfer**: Error states, alerts, notifications. Layer urgency through multiple channels, not just text or color alone.

---

## Quick Reference

| Level | Focus | Question to Ask | Transferability |
|-------|-------|-----------------|-----------------|
| **L1: Visual** | What it looks like | "What colors/fonts/spacing?" | Low (brand-specific) |
| **L2: Component** | Structure | "How is it organized?" | Moderate (needs adaptation) |
| **L3: Interaction** | User accomplishment | "How do users achieve goals?" | High (with context mapping) |
| **L4: Cognitive** | Universal principle | "Why does this work for humans?" | Highest (near-universal) |

**Research goal**: Spend 80% of effort extracting L3-4 patterns from cross-domain sources.

---

## Summary

- **Visual patterns** (L1) are surface-level and rarely transfer
- **Component patterns** (L2) are useful references but not breakthrough
- **Interaction patterns** (L3) reveal how users accomplish tasks—highly transferable
- **Cognitive patterns** (L4) are universal truths about human cognition—most valuable

**The best research** identifies L3-4 patterns from unexpected domains and synthesizes them with clear reasoning about why they're relevant.
