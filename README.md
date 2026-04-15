# Design Intelligence

> **Creative intelligence for purposeful problem-solving across design, engineering, product, and strategy.**

When you need to make intentional decisions about how things should work—whether designing an API, building a dashboard, architecting a system, or optimizing a process—this bundle helps you think deeper, research broader, and solve better.

---

## Already Included in Foundation

**Good news:** If you're using `amplifier-foundation`, you already have the core design intelligence capabilities:

- **7 Design Advisory Agents** - art-director, design-system-architect, component-designer, layout-architect, animation-choreographer, responsive-strategist, voice-strategist
- **Design Research** - research-runner, research-analyst for trend analysis
- **Design Generation** - token-generator, spec-writer, export-packager
- **Design Frameworks** - Nine Dimensions, Five Pillars, Creative Research Methodology

**Just start using them:**
```
"Design a component library for my healthcare dashboard"
"What aesthetic direction fits a fintech application?"
"Find design inspiration for [any creative problem]"
"Generate design tokens from this direction"
```

**No bundle switching required** - these agents are available in every foundation session.

### Want More? Use the Extension or Standalone Bundle

| Need | Use |
|------|-----|
| Design advice and direction | Foundation (already included) |
| Research + generation + discovery | Extension: `amplifier bundle use foundation design-studio-extension` |
| Design-first dedicated workflow | Standalone: `amplifier bundle use design-intelligence` |

---

## The Core Problem

You're building something important. You know it should be **purposeful**, not arbitrary. But how do you:

- **Discover** what actually matters (not what you assume)
- **Research** proven patterns across domains (not just your silo)
- **Extract** principles that apply to your specific problem
- **Synthesize** solutions that are both novel and grounded

AI can generate code fast. But **design**—the purpose, planning, and intention behind what you build—requires a different approach.

---

## The Solution: Creative Research Methodology

This bundle embodies a universal methodology for purposeful problem-solving:

```
1. DECOMPOSE    → Break problems into cognitive tasks, system challenges, or coordination needs
2. MAP DOMAINS  → Find analogous problems in unexpected places
3. RESEARCH     → Study how other domains solved similar challenges (L3-4 principles)
4. SYNTHESIZE   → Apply extracted patterns to your specific context
```

**Works across domains:**
- **Visual/Product**: Dashboard design, user flows, interface patterns
- **Engineering**: API design, database migrations, distributed systems
- **Strategy**: Process optimization, resource allocation, organizational design

**The key insight:** Every domain has solved problems similar to yours. Cross-domain research reveals principles (L3-4 understanding) you can adapt.

---

## Version 2.2.0: Universal Applicability

**NEW**: Explicitly supports engineering, product, and strategy work—not just visual design.

**What changed:**
- Domain detection (visual/engineering/strategy) with adapted approaches
- Engineering examples: API rate limiting, database migrations, distributed coordination
- Cognitive task catalog expanded: fairness under load, failure isolation, habit formation
- Research analyst adapts questions based on detected domain

**Core philosophy:**
> Design is purpose, planning, and intention behind any action, system, or process. This methodology works wherever you need to make thoughtful decisions.

---

## Quick Start

### Installation

```bash
# Add to Amplifier (works with any bundle)
amplifier bundle add git+https://github.com/microsoft/amplifier-bundle-design-intelligence@main --app

# Set as active bundle (optional)
amplifier bundle use design-intelligence

# Start session
amplifier
```

### Your First Creative Research Session

**For visual/product work:**
```
"I need to design a dashboard showing system health. 
Help me research how other domains handle rapid anomaly detection."
```

**For engineering work:**
```
"I'm designing a rate limiting system for our API.
Research analogous fairness problems in other domains."
```

**For strategy work:**
```
"We need to optimize our deployment process.
Find patterns from how other domains handle coordination under constraints."
```

The agents will:
1. Detect your domain (visual/engineering/strategy)
2. Decompose the problem into core challenges
3. Research analogous solutions across domains
4. Extract L3-4 principles (not just surface patterns)
5. Help you synthesize a purposeful solution

---

## What's Included

### Discovery (Structured Interviewing — Optional)

Compatible with the [Discovery bundle](https://github.com/microsoft/amplifier-bundle-discovery) for structured design interviews. When both bundles are loaded, structured interviewing captures what matters through systematic questioning:
- **Visual/Product**: Cognitive tasks, decision points, emotional context
- **Engineering**: System guarantees, failure modes, trade-offs
- **Strategy**: Coordination needs, resource constraints, optimization targets

**Output:** Problem decomposition with clear understanding of what you're solving

> The Discovery bundle is optional — the research-analyst can handle initial problem decomposition without it.

### Research (Cross-Domain Intelligence)

On-demand research using creative methodology:
- **Analogous domain mapping**: Find similar problems in unexpected fields
- **Pattern extraction**: Identify L3-4 principles (why solutions work)
- **Trend awareness**: Current best practices (RSS feeds from Awwwards, Siteinspire, The FWA for visual design)

**Output:** Research context with cross-domain patterns and principles

### Design Agents (Specialized Expertise)

10 specialized agents applying rigorous frameworks:

| Agent | Domain Focus | Use For |
|-------|--------------|---------|
| **research-analyst** | Cross-domain research | Problem decomposition, analogous domain research |
| **art-director** | Visual strategy | Aesthetic direction, visual coherence |
| **design-system-architect** | System architecture | Tokens, patterns, foundations |
| **component-designer** | Component design | Individual UI elements, variants |
| **layout-architect** | Spatial composition | Page structure, grids, IA |
| **animation-choreographer** | Motion design | Timing, transitions, feedback |
| **responsive-strategist** | Adaptation strategy | Breakpoints, multi-device patterns |
| **voice-strategist** | Communication strategy | Tone, messaging, microcopy |
| **design-context** | System intelligence | Maintains structured design context, reconciles artifacts |
| **design-check** | Quality validation | Three-layer design system compliance checking |

**Frameworks applied:**
- **Nine Dimensions** (visual work): Style, Motion, Voice, Space, Color, Typography, Proportion, Texture, Body
- **Five Pillars** (all domains): Purpose, Craft, Constraints, Incompleteness, Humans

### Design Context System (NEW)

The design system builds itself as you work. No questionnaires, no forms.

**Structured Design Context** (`.design/context.json`) — A machine-readable snapshot of your project's design system state, maintained automatically. When the art-director picks colors or the design-system-architect defines tokens, the reconciler agent extracts those decisions into a structured format that every other agent can read.

**Opinionated Gap-Filling** — When an agent needs a value that hasn't been established yet (e.g., motion timing), it doesn't ask you — it proposes a sensible default based on what's already decided. Warm editorial aesthetic? You get deliberate 200/400/600ms timing. Dense data dashboard? Quick 100/200/300ms. You can override anything, but the system keeps moving.

**Design Check** — Before presenting work to you, agents validate their own output against your design system:
- **Static analysis**: Hardcoded values, missing tokens, contrast ratios
- **Structural analysis**: AI fingerprint patterns, missing component states, spacing consistency
- **Visual analysis**: Screenshot capture + vision AI checking palette, typography, and style compliance

You never see a report. You see finished work that already passes.

### Verification (Visual Validation)

Prevent circular fix loops with visual verification:
- **visual-verify**: Screenshot capture and comparison
- **layout-context**: Computed layout extraction
- **design-validate**: Systematic validation against specs
- **design-validator agent**: Orchestrates verification workflow

**Requires:** Playwright for visual verification only (`pip install playwright && playwright install chromium`)

**Use when:** Verifying live implementations, validating against specifications

---

## Example Workflows

### Engineering: API Rate Limiting

```
> "I'm designing rate limiting for our API. It needs to be fair, prevent abuse, 
   but not block legitimate heavy users."

→ Research analyst detects engineering domain
→ Decomposes into: fairness under load, abuse prevention, graceful degradation
→ Maps to analogous domains: highway traffic management, electrical grid load balancing, 
  network QoS
→ Extracts L3-4 principles: token buckets, priority queues, backpressure signals
→ Synthesizes: Adaptive rate limiting with client reputation scoring
```

### Visual: Dashboard Design

```
> "Design a monitoring dashboard for DevOps teams. They need to spot anomalies 
   fast during incidents."

→ Research analyst detects visual/product domain
→ Decomposes cognitive tasks: rapid gestalt assessment, anomaly detection, 
  drill-down investigation
→ Maps to analogous domains: air traffic control, medical monitoring, financial trading
→ Extracts L3-4 principles: alert hierarchy, gestalt patterns, progressive disclosure
→ Art director + layout architect synthesize: Dashboard with alert-driven hierarchy 
  and contextual drill-down
```

### Strategy: Process Optimization

```
> "We need to optimize our code review process. Reviews are slow and creating 
   bottlenecks."

→ Research analyst detects strategy/operations domain
→ Decomposes: coordination challenge, resource allocation, quality vs speed trade-off
→ Maps to analogous domains: manufacturing flow, emergency triage, agile sprints
→ Extracts L3-4 principles: WIP limits, priority systems, parallel paths
→ Synthesizes: Tiered review system with automated pre-checks and fast-path for 
  low-risk changes
```

---

## Superpowers Integration

Design-intelligence works seamlessly with the superpowers bundle. When both are loaded, design thinking becomes a natural part of the engineering workflow:

- **Brainstorming**: The `design-brainstorming` skill is auto-discovered when superpowers enters `/brainstorm` mode. It adds design dimensions (aesthetic direction, UX patterns, cross-domain research) alongside engineering architecture.
- **Planning**: The `design-planning` skill enriches `/write-plan` mode with design tasks — design-check validation steps, context.json updates, and accessibility verification.
- **Implementation**: Design-check runs as agent self-correction during `/execute-plan`, catching hardcoded values and design system violations before code is presented.

**No configuration needed.** If both bundles are in the session, the skills register automatically. Superpowers' `load_skill(search="brainstorm")` finds the design skill. Design agents are available for delegation during brainstorming.

---

## Recipes

| Recipe | What It Does |
|--------|--------------|
| `design-discovery` | Full discovery → research → design direction workflow |
| `weekly-design-research` | Automated trend research via RSS (Awwwards, Siteinspire, The FWA) |

**Run a recipe:**
```
"Run the design-discovery recipe for a healthcare monitoring system"
```

---

## Philosophy

This bundle follows Amplifier's principles and adds creative research methodology:

- **Decompose before design** — Understand the problem deeply first
- **Research cross-domain** — Analogous solutions reveal universal principles
- **Extract L3-4 principles** — Not what works, but WHY it works
- **Synthesize with reasoning** — Apply patterns thoughtfully to your context
- **Design is universal** — Purpose and intention matter in every domain

**Design is not decoration.** It's the thoughtful consideration of purpose, constraints, and humans that makes systems work well.

---

## Who It's For

**Engineers who think deeply** — You want your systems to be purposeful, not just functional. You research before building.

**Builders with vision** — You know what you want but need help articulating it, researching proven patterns, and refining your approach.

**Teams making critical decisions** — You need a structured way to explore options, research best practices, and make informed choices.

**Anyone solving novel problems** — You need to synthesize solutions from proven patterns across domains, not reinvent from scratch.

---

## Documentation

- **[Creative Research Methodology](context/research-methodology/creative-research-methodology.md)** — The full methodology with examples
- **[Cognitive Task Catalog](context/research-methodology/cognitive-task-catalog.md)** — Library of decomposed problems
- **[Engineering Examples](context/examples/engineering-examples.md)** — Complete engineering walkthroughs
- **[Design Context System](docs/specs/2026-03-12-design-context-system.md)** — Structured context, inference chains, design-check
- **[Verification Guide](docs/archive/VERIFICATION_GUIDE.md)** — Visual verification setup and usage
- **[Privacy & Data Handling](PRIVACY.md)** — What data is collected, stored, and how to opt out

---

## Roadmap

| Phase | Status | What |
|-------|--------|------|
| **2.0 Foundation** | ✅ Complete | Discovery integration, research capability, design agents |
| **2.1 Verification** | ✅ Complete | Visual verification tools, validation workflow |
| **2.2 Universalization** | ✅ Complete | Engineering/product/strategy support, domain detection |
| **2.3 Context + Generation** | ✅ Complete | Structured design context, design-check, token generation, artifact export |
| **3.0 Feedback** | ⏳ Planned | Taste refinement, continuous improvement |

---

## Acknowledgments

The design baseline and research methodology incorporate insights from external projects:

- **[Pretext](https://github.com/chenglou/pretext)** by Cheng Lou (building on Sebastian Markbage's [text-layout](https://github.com/nicolo-ribaudo/text-layout) research) -- a pure-JS text measurement and layout engine. Pretext's empirical work on browser font rendering informed our typography guidance (`system-ui` measurement safety, multiline shrink-wrap, variable-width text flow), and its RESEARCH.md format inspired the Exploration Log Pattern in our creative research methodology.

---

## Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit [https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

**Philosophy contributions especially welcome:** If you discover new cross-domain patterns, L3-4 principles, or cognitive task decompositions that extend the creative research methodology, please open an issue or PR — we'd love to learn from your research.

---

## License

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. See LICENSE for details.
