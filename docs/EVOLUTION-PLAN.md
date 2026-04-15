# Design Intelligence Enhanced - Evolution Plan

**Status:** Living Document  
**Last Updated:** 2026-01-28  
**Current Version:** 2.2.0  
**Goal:** Transform from advisory-only to a complete design-to-implementation pipeline

---

## Executive Summary

Design Intelligence Enhanced provides a universal creative research methodology for purposeful problem-solving across design, engineering, product, and strategy domains. This plan outlines the evolution from advisory agents to artifact generation.

**What We Are:**
- Enhanced fork of Microsoft's design-intelligence bundle
- Universal methodology (not just visual design)
- Research-driven problem-solving
- Cross-domain pattern extraction

**Integration:**
1. **Discovery** - Structured problem decomposition (via discovery bundle or built-in research-analyst)
2. **Research** - Cross-domain analogous pattern research (creative research methodology)
3. **Design** - Specialized agents applying frameworks (Nine Dimensions, Five Pillars)
4. **Verify** - Visual verification (v2.1.0) prevents circular fix loops
5. **Generate** - Artifact generation for implementation (v2.3.0 planned)

---

## The Vision

```
┌─────────────────────────────────────────────────────────────────────┐
│  1. DECOMPOSE (research-analyst)                                    │
│     "What's the core problem?"                                      │
│     Cognitive tasks • System challenges • Coordination needs        │
│     Output: Problem decomposition                                   │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  2. RESEARCH (research-analyst)                                     │
│     "What analogous solutions exist?"                               │
│     Cross-domain mapping • L3-4 principle extraction                │
│     Output: Research Context with patterns                          │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  3. SYNTHESIZE (specialized agents)                                 │
│     "Apply patterns to specific context"                            │
│     Domain-specific frameworks • Rigorous methodology               │
│     Output: Design Decisions / System Architecture                  │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  4. VERIFY (design-validator) [v2.1.0]                              │
│     "Does it work as specified?"                                    │
│     Visual verification • Layout analysis • Spec validation         │
│     Output: Validated implementations                               │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  5. GENERATE (coming v2.3.0)                                        │
│     "Produce implementation artifacts"                              │
│     Tokens • Specs • Components • Export packages                   │
│     Output: Design Protocol Artifacts                               │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  6. IMPLEMENT (coding agents)                                       │
│     Claude Code • Cursor • Copilot • Any agent                      │
│     Consumes protocol artifacts                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Version History

### v2.2.0 - Universal Applicability (Current)

**Completed:** 2026-01-28

**Changes:**
- Domain detection (visual/engineering/strategy)
- Engineering examples: API rate limiting, database migrations, distributed systems
- Cognitive task catalog expansion
- Research-analyst domain-aware questioning
- Documentation updated for universal scope

**Impact:** Bundle now explicitly supports engineering, product, and strategy work—not just visual design.

### v2.1.0 - Visual Verification

**Completed:** 2026-01-22

**Changes:**
- Visual verification tools (visual-verify, layout-context, design-validate)
- Design-validator agent for orchestrated verification
- Playwright integration for screenshot capture
- Prevents circular "fix it again" loops

**Impact:** Agents verify before presenting, reducing QA burden on users.

### v2.0.0 - Foundation

**Completed:** 2026-01-16

**Changes:**
- 8 specialized design agents
- Creative research methodology
- Nine Dimensions + Five Pillars frameworks
- Weekly trend scraping (Awwwards, Siteinspire, The FWA)
- Design-discovery recipe

**Impact:** Complete design thinking capability for visual work.

---

## Phase 2.3: Generation (In Progress)

**Timeline:** Week 1-3 of Q1 2026

### 2.3.1 Define Design Protocol Spec

**Goal:** Create specification for design artifacts (inspired by A2UI)

```
design-intelligence-enhanced/specs/
├── DESIGN-PROTOCOL.md           # Overall specification
├── schemas/
│   ├── design-brief.schema.json # Discovery output
│   ├── tokens.schema.json       # Design tokens
│   ├── components.schema.json   # Component specs
│   └── system.schema.json       # Full system export
└── examples/
    ├── minimal-tokens.json
    ├── full-system.json
    └── component-spec.json
```

**Design Protocol Principles:**
- Declarative, not executable
- Framework-agnostic
- LLM-friendly (flat, streaming-capable)
- Progressively renderable
- Universal (works for visual AND engineering artifacts)

### 2.3.2 Token Generation

**Schema: `tokens.schema.json`**

Covers:
- Color systems (primary, secondary, semantic, neutral scales)
- Typography (families, scale, weights)
- Spacing (base unit, scale)
- Motion (duration, easing)
- Shadows, borders, radii
- Breakpoints (responsive)

### 2.3.3 Add Generation Agent

**Action:** Create `token-generator` agent

- Inputs: Discovery brief, design direction, research context
- Outputs: tokens.json, tokens.css, tokens.tailwind.js, tokens.scss
- Generation rules for translating decisions to tokens

### 2.3.4 Add Spec Writer Agent

**Action:** Create `spec-writer` agent

- Outputs: Component specifications
- Includes: Purpose, variants, props/API, accessibility, behavior, visual specs

---

## Phase 3.0: Export & Handoff (Planned)

**Timeline:** Q2 2026

### 3.1 Export Package Generator

**Recipe:** `design-system-export.yaml`

Steps:
1. Generate tokens from design context
2. Write component specs
3. Package for target environment

### 3.2 Export Formats

| Format | Output | Use Case |
|--------|--------|----------|
| **Tailwind** | `tailwind.config.js` + components | Tailwind projects |
| **CSS Variables** | `tokens.css` + component CSS | Vanilla/any framework |
| **Style Dictionary** | SD config + transforms | Design tooling |
| **Figma Tokens** | JSON for Figma plugins | Designer handoff |
| **Coding Agent** | Prompts + instructions | Claude Code, Cursor |
| **API Spec** | OpenAPI/AsyncAPI | Engineering projects |
| **Architecture Diagrams** | Mermaid/PlantUML | System design |

### 3.3 Universal Artifact Types

**Visual Design:**
- Design tokens
- Component specifications
- Layout systems
- Interaction patterns

**Engineering:**
- API specifications
- Data models
- System architecture diagrams
- Integration contracts

**Strategy:**
- Process diagrams
- Decision frameworks
- Resource allocation models
- Optimization strategies

---

## Phase 4.0: Feedback Loop (Future)

**Timeline:** Q3 2026

### 4.1 Validation Agent

**Enhanced:** `design-validator` agent

Validates:
- Token usage compliance
- Typography compliance
- Spacing compliance
- Component structure
- Accessibility
- Performance (engineering)
- Resource efficiency (strategy)

Output:
- Compliance score
- Specific violations
- Remediation suggestions

### 4.2 Taste Refinement

**Recipe:** `taste-refinement.yaml`

Steps:
1. Generate variations
2. Gather feedback (approval gate)
3. Refine direction based on preferences

Learns user preferences over time for:
- Aesthetic choices (visual)
- Architecture patterns (engineering)
- Process optimization (strategy)

---

## File Structure (Current State)

```
amplifier-bundle-design-intelligence-enhanced/
├── bundle.md                           # Main bundle
├── README.md                           # Clear value prop, universal scope
│
├── docs/
│   ├── WORKFLOW.md                     # Step-by-step guide (needs update)
│   └── EVOLUTION-PLAN.md               # This document
│
├── specs/                              # Coming in v2.3.0
│   └── schemas/
│       ├── tokens.schema.json
│       ├── components.schema.json
│       └── system.schema.json
│
├── agents/
│   ├── research-analyst.md             # ✅ Universal domain support (v2.2.0)
│   ├── art-director.md                 # ✅ Visual strategy
│   ├── design-system-architect.md      # ✅ System architecture
│   ├── component-designer.md           # ✅ Component design
│   ├── layout-architect.md             # ✅ Spatial composition
│   ├── animation-choreographer.md      # ✅ Motion design
│   ├── responsive-strategist.md        # ✅ Adaptation strategy
│   ├── voice-strategist.md             # ✅ Communication strategy
│   ├── design-validator.md             # ✅ Visual verification (v2.1.0)
│   ├── token-generator.md              # Coming v2.3.0
│   ├── spec-writer.md                  # Coming v2.3.0
│   └── export-packager.md              # Coming v2.3.0
│
├── behaviors/
│   ├── design-core.yaml                # Core design philosophy
│   ├── design-research.yaml            # Research capability
│   └── design-generation.yaml          # Coming v2.3.0
│
├── recipes/
│   ├── weekly-design-scrape.yaml       # ✅ Trend research
│   ├── design-discovery.yaml           # ✅ Discovery → Design
│   ├── design-system-export.yaml       # Coming v2.3.0
│   └── taste-refinement.yaml           # Coming v4.0
│
├── context/
│   ├── philosophy/                     # Design frameworks
│   ├── research-methodology/           # ✅ Creative research (v2.2.0)
│   │   ├── creative-research-methodology.md
│   │   └── cognitive-task-catalog.md
│   ├── examples/                       # ✅ Domain examples (v2.2.0)
│   │   └── engineering-examples.md
│   ├── generation-protocols.md         # Coming v2.3.0
│   └── design-protocol-guide.md        # Coming v2.3.0
│
├── templates/                          # Example outputs
│   └── discovery-brief-template.md
│
├── archive/                            # Research archive
│   └── trends/
│
└── VERIFICATION_GUIDE.md               # ✅ Visual verification setup (v2.1.0)
```

---

## Success Metrics

### Quantitative
- Problem decomposition in <5 exchanges
- Research context gathered in <10 minutes
- Export package generation in <5 minutes (v2.3.0)
- Implementation compliance score >90% (v4.0)

### Qualitative
- "I got deep insights, not just surface patterns"
- "The cross-domain research revealed solutions I'd never considered"
- "It works for engineering problems, not just visual design"
- "I got complete artifacts, not just advice" (v2.3.0)

---

## Dependencies

| Dependency | Status | Action |
|------------|--------|--------|
| Discovery integration | ✅ Built | research-analyst handles decomposition |
| Research methodology | ✅ Built | Creative research methodology (v2.2.0) |
| Design agents | ✅ Built | 8 specialized agents |
| Visual verification | ✅ Built | Playwright integration (v2.1.0) |
| Universal scope | ✅ Built | Domain detection (v2.2.0) |
| Generation agents | 🔄 In Progress | token-generator, spec-writer (v2.3.0) |
| Design Protocol spec | 📋 Planned | Define schemas (v2.3.0) |
| Export capability | 📋 Planned | Multi-format export (v3.0) |
| Validation loop | 📋 Planned | Enhanced validator (v4.0) |

---

## Risk Mitigation

| Risk | Mitigation |
|------|------------|
| Protocol too complex | Start minimal, iterate based on usage |
| Generation quality | Use existing knowledge bases, add examples |
| Framework compatibility | Test with Tailwind, CSS, and one other |
| Scope creep | Ship incrementally, validate, then expand |
| Universal claims | Extensive testing across domains |

---

## Next Steps

### Immediate (This Month)
1. ✅ Complete v2.2.0 documentation updates
2. ✅ Update README with universal messaging
3. Define minimal Design Protocol spec (v2.3.0)

### Near Term (Next Month)
1. Build token-generator agent
2. Build spec-writer agent
3. Create design-system-export recipe
4. Test with real projects

### Future (Q2-Q3 2026)
1. Multi-format export (v3.0)
2. Enhanced validation (v4.0)
3. Taste refinement (v4.0)
4. Community feedback integration

---

## References

- Discovery bundle - Structured interviewing (optional companion)
- [A2UI Protocol](https://a2ui.org) - Inspiration for protocol design
- [Creative Research Methodology](../context/research-methodology/creative-research-methodology.md) - Our methodology
- [Cognitive Task Catalog](../context/research-methodology/cognitive-task-catalog.md) - Problem library
- [Engineering Examples](../context/examples/engineering-examples.md) - Engineering walkthroughs

---

## Philosophy Note

**This is design-intelligence-enhanced** - a community-maintained fork that expands on Microsoft's design-intelligence bundle with:
- Visual verification tools (v2.1.0)
- Universal domain applicability (v2.2.0)
- Creative research methodology
- Future artifact generation (v2.3.0+)

We maintain compatibility while pushing boundaries of what design intelligence can be.
