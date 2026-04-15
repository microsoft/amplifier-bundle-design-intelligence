---
bundle:
  name: design-intelligence
  version: 2.3.0
  description: Creative intelligence system for purpose-driven problem-solving across design, engineering, product, and strategy
  sub_bundles:
    - name: baseline
      path: behaviors/design-baseline.yaml
      description: Always-on design quality principles for all UI code generation
    - name: advisory
      path: behaviors/design-intelligence.yaml
      description: 7 specialized design agents (art-director, component-designer, etc.)
    - name: research
      path: behaviors/design-research.yaml
      description: Purpose-driven research and cross-domain pattern discovery
    - name: generation
      path: behaviors/design-generation.yaml
      description: Token generator, spec writer, export packager
    - name: taste
      path: behaviors/taste-awareness.yaml
      description: Personal taste profile awareness and preference learning
    - name: context
      path: behaviors/design-context.yaml
      description: Structured design context (context.json), inference-driven completeness, and design-check self-correction
    - name: skills
      path: behaviors/design-skills.yaml
      description: Design skills discoverable by superpowers and other methodology bundles (brainstorming, planning)

includes:
  # Standalone app bundle - includes foundation for full capabilities
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: design-intelligence:behaviors/design-baseline
  - bundle: design-intelligence:behaviors/design-intelligence
  - bundle: design-intelligence:behaviors/design-research
  - bundle: design-intelligence:behaviors/design-generation
  - bundle: design-intelligence:behaviors/taste-awareness
  - bundle: design-intelligence:behaviors/design-context
  - bundle: design-intelligence:behaviors/design-skills
---

# Design Intelligence

> Creative intelligence for breakthrough problem-solving across domains.

## Architecture Note

**Foundation already includes** the full set of design intelligence capabilities:
- 7 design advisory agents (art-director, component-designer, etc.)
- Design research capabilities (research-runner, research-analyst)
- Design generation capabilities (token-generator, spec-writer, export-packager)

**This standalone bundle adds:**
- Compatible with the Discovery bundle for structured design interviews (optional)
- Taste awareness for preference learning across sessions
- Design-first coordinator messaging and workflow emphasis

**When to use this bundle:**
- You want a dedicated design workflow experience
- You're running full discovery -> research -> design -> generate pipelines
- You prefer design-first language and recipes as the primary interface

**When to use foundation + extension instead:**
- You're primarily developing but want design capabilities available
- You want development-first language with design as an available capability
- You want to add only specific capabilities (research OR generation)

> **Note:** The standalone bundle and the extension bundle do NOT provide identical capabilities. The extension includes research, generation, taste awareness, discovery, and design-context — but omits the design-baseline philosophy context, the design-skills module, and the root context files. See the comparison below.

| Capability | Standalone | Extension |
|------------|:----------:|:---------:|
| 7 advisory agents (art-director, etc.) | via bundle | via foundation |
| Research (research-runner, research-analyst) | yes | yes |
| Generation (token-generator, spec-writer, export-packager) | yes | yes |
| Taste awareness (preference learning) | yes | yes |
| Discovery (structured interviews) | yes | yes |
| Design-context (reconciler, context.json, inference chains) | yes | yes |
| Design-check (self-correction validation) | yes | yes |
| Design-baseline (philosophy context) | yes | **no** |
| Design-skills (tool-skills module) | yes | **no** |
| 11 root @-mention context files | yes | **no** |

---

## What is Design?

**Design** is purpose, planning, or intention behind any action, fact, or material object. It's the thoughtful shaping of systems, experiences, and solutions.

This bundle works for:
- **Visual design**: Interfaces, graphics, layouts, user experiences
- **Engineering design**: Systems, APIs, architectures, data models
- **Product design**: Features, flows, onboarding, engagement patterns
- **Strategic design**: Processes, organizations, go-to-market approaches

**The core capability**: Purpose-driven research that finds breakthrough solutions by discovering proven patterns from unexpected domains.

---

## Quick Start

| Domain | Example Usage |
|--------|---------------|
| **Visual Design** | `"Help me design a dashboard for monitoring system health"` |
| **Engineering** | `"Design an API rate limiting system that handles bursts gracefully"` |
| **Product** | `"Design an onboarding flow that drives feature adoption"` |
| **Strategy** | `"Design a process for handling customer escalations"` |
| **Research** | `"Find inspiration for [any creative problem]"` |
| **Trend Analysis** | `"Update my research"` (fetches RSS from Awwwards, Siteinspire, The FWA) |

---

## The Innovation: Purpose-Driven Research

### Before (Category-Matching)
```
"Design a healthcare dashboard"
→ Research: Other healthcare dashboards
→ Output: Competent remix of existing work
→ Innovation: Low (inherits category assumptions)
```

### After (Purpose-Driven)
```
"Design a healthcare dashboard"
→ Decompose: What cognitive tasks? (rapid assessment, anomaly detection)
→ Map domains: Where else solved? (medical monitors, trading platforms, gaming HUDs)
→ Research: 20% category + 50% purpose-driven + 30% divergent
→ Extract: Level 3-4 patterns (interaction/cognitive, not just visual)
→ Synthesize: WHY each pattern is relevant
→ Output: Dashboard inspired by proven patterns from unexpected sources
→ Innovation: High (cross-pollinated ideas)
```

**Result**: Solutions that feel fresh and innovative while being grounded in proven patterns from mature domains.

---

## Real Examples Across Domains

### Visual Design: Aerospace Dashboard
- **Cognitive tasks**: Rapid status assessment, anomaly detection, timeline understanding
- **Analogous domains**: Hospital patient monitors, trading platforms, gaming HUDs, security ops
- **Patterns extracted**: Gestalt assessment from medical, confidence indicators from trading, flow state from gaming
- **Result**: Dashboard that breaks aerospace conventions in smart ways

### Engineering: API Rate Limiting
- **Problem decomposition**: Fairness, abuse prevention, resource protection, burst tolerance
- **Analogous domains**: Highway traffic metering, electrical grid balancing, network QoS, OS scheduling
- **Patterns extracted**: Entry-point metering from traffic, load shedding from electrical, priority queuing from OS
- **Result**: Sophisticated rate limiting inspired by proven systems engineering patterns

### Product: Feature Onboarding
- **User needs**: Progressive learning, safe exploration, confidence building, retention
- **Analogous domains**: Video game tutorials, driver's education, cooking classes, museum exhibits
- **Patterns extracted**: Learn-by-doing from gaming, sandbox safety from simulations, scaffolded independence from education
- **Result**: Onboarding far more effective than standard tooltips and tours

See `context/examples/` for full walkthroughs.

---

## Visual Design Research

Design trend data collected from **Awwwards**, **Siteinspire**, and **The FWA** RSS feeds.

**What you get:** Featured project metadata, URLs, and trend analysis from three authoritative sources

**When to update:**
- Starting a new project (fresh inspiration)
- Weekly design reviews (stay current)
- Before presentations (latest trends)

**How to update:** Just say `"Update my research"` (~2-5 min to fetch RSS feeds & generate summary)

For deeper visual analysis of specific sites, ask the research-analyst to analyze a URL you provide.

---

## The Workflow

```
1. DISCOVER → What are we building and why?
2. RESEARCH → Where else is this problem solved? (cross-domain)
3. DESIGN   → What should it be? (informed by proven patterns)
4. GENERATE → Produce artifacts (tokens, specs, guides) for execution
```

### Design Quality Gates

**design-check** validates code against the design system: hardcoded colors, wrong spacing, missing component states, AI fingerprint patterns. This runs as silent agent self-correction before presenting work to you.

**Visual verification** (screenshots, pixel comparison, convergence loops) is provided by the **design execution layer** — the companion system that builds things from design intelligence output. See ARCHITECTURE.md for the two-layer model.

---

@design-intelligence:context/design-instructions.md

---

@design-intelligence:context/design-delegation-guide.md

---

## Recipes

| Recipe | What It Does | Domain |
|--------|--------------|--------|
| `design-to-implementation` | Full pipeline: idea → discovery → design → tokens → export | Visual Design |
| `design-discovery` | Discovery → research → design direction | Any Domain |
| `design-system-export` | Generate tokens + component specs + export package | Visual Design |
| `weekly-design-research` | Update trend research via RSS (Awwwards, Siteinspire, The FWA) | Visual Design |

**Run a recipe:**
```
Run the design-discovery recipe for [describe your problem in any domain]
```

---

## How This Augments Your Thinking

This isn't just a tool that gives you answers—it teaches you a **meta-cognitive skill** that great practitioners naturally have:

1. **Decompose problems** into fundamental challenges (not just domain specs)
2. **Think across domains** (where else is this solved?)
3. **Abstract patterns** (what's transferable vs. context-specific?)
4. **Reason explicitly** (why is this relevant to our context?)
5. **Challenge assumptions** (does this actually fit our problem?)

**This is the skill that separates great engineers/designers/product people from good ones**—the methodology makes it systematic and teachable.

### Escaping Cargo Cult Thinking

**Before**: "Everyone uses microservices, so we should too"

**After**: 
- "What problem does distribution solve?" (scale, resilience, autonomy)
- "Where is distribution solved best?" (telecommunications, biological systems)
- "What are the trade-offs?" (complexity, latency, consistency)
- "Does our problem actually need this?" (explicit reasoning)

**Result**: Principled decision-making, not fashion-following.

---

## Design Philosophy

@design-intelligence:context/philosophy/DESIGN-PHILOSOPHY.md
@design-intelligence:context/philosophy/DESIGN-PRINCIPLES.md
@design-intelligence:context/philosophy/DESIGN-FRAMEWORK.md
@design-intelligence:context/philosophy/WRITING-PRINCIPLES.md

---

## Research Methodology

**NEW in v2.2.0**: Complete purpose-driven research methodology

@design-intelligence:context/research-methodology/creative-research-methodology.md
@design-intelligence:context/research-methodology/cognitive-task-catalog.md
@design-intelligence:context/research-methodology/pattern-abstraction-guide.md
@design-intelligence:context/research-methodology/cognitive-discovery-enhancement.md

---

@foundation:context/shared/common-system-base.md
