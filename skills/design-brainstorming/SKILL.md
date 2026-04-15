---
name: design-brainstorming
description: Use when brainstorming any feature, product, or system that has a user-facing interface, visual component, or experience dimension. Enriches architectural brainstorming with design thinking — aesthetic direction, UX patterns, cross-domain research, and design system awareness.
---

# Design Brainstorming

Enriches brainstorming with design intelligence. Works alongside engineering brainstorming — not instead of it.

## When to Use

- Brainstorming a feature with UI/UX components
- Designing a dashboard, form, page, or interactive element
- Any work where users will SEE or INTERACT with the output
- When `.design/context.json` exists (established design system to respect)
- When aesthetic direction matters ("what should this feel like?")

## When NOT to Use

- Pure backend/infrastructure work with no user-facing output
- Database migrations, CI/CD pipelines, API internals

## The Integration

This skill adds design dimensions to engineering brainstorming. The flow becomes:

```
1. UNDERSTAND CONTEXT (engineering + design)
   - Read project files, docs, architecture (standard)
   - Read .design/context.json if it exists (what's decided)
   - Note design completeness — what's defined vs missing

2. ASK QUESTIONS (engineering + design)
   - Engineering: purpose, constraints, data flow, error handling
   - Design: who uses this? what cognitive tasks? what should it feel like?
   - If the user can't articulate a design preference, PROPOSE one
     based on inference chains — don't leave it blank

3. RESEARCH (the design-intelligence differentiator)
   - Delegate to research-analyst for cross-domain pattern discovery
   - Decompose the problem into cognitive tasks, not just features
   - Map to analogous domains where similar UX challenges are solved
   - Extract Level 3-4 patterns (WHY solutions work, not just WHAT)

4. EXPLORE APPROACHES (engineering + design together)
   - Each approach should address BOTH architecture AND experience
   - "Option A: Tab layout with eager loading — snappy but heavy"
   - NOT architecture options separate from design options

5. PRESENT DESIGN (unified)
   - Architecture sections: components, data flow, error handling
   - Design sections: visual direction, interaction patterns,
     design system compliance, accessibility
   - These are ONE design, not two separate documents
```

## Using Design Agents During Brainstorming

Available agents and when to involve them:

| Agent | Involve when... |
|-------|-----------------|
| **research-analyst** | Always, for any UI work. Cross-domain research is the highest-value brainstorming activity. |
| **art-director** | The brainstorm involves aesthetic decisions — "what should this feel like?" |
| **discovery-interviewer** | Requirements are vague and need structured extraction |

Do NOT involve during brainstorming (these are implementation-phase):
- component-designer, layout-architect, token-generator, design-check

## Design Context Awareness

If `.design/context.json` exists, read it at brainstorm start. This tells you:

- **Defined sections**: Use these as constraints. Don't re-decide what's decided.
- **Inferred sections**: Mention these — "the system inferred X, we can override"
- **Missing sections**: Opportunities to fill gaps through the brainstorm
- **Completeness score**: If low, the brainstorm should address design foundations

If no context.json exists, that's fine — the brainstorm may be the session that creates the first design artifacts.

## Design Sections for the Design Doc

When writing the design document, include these sections alongside the engineering sections:

**Visual Direction** (if aesthetic decisions were made)
- Style keywords, color direction, typography approach
- Reference sites or patterns that inspired the direction

**Interaction Patterns** (if UX was discussed)
- Key user flows and cognitive tasks
- Cross-domain patterns being applied and WHY

**Design System Compliance** (if context.json exists)
- Which established tokens/patterns this feature uses
- Any new patterns this feature introduces
- Gaps in the design system this feature reveals

**Accessibility Requirements**
- Contrast, keyboard navigation, screen reader considerations
- Touch targets if mobile-relevant

## Key Principle

Design and engineering are not sequential phases — they're parallel dimensions of the same brainstorm. Every architectural decision has UX implications. Every design decision has engineering constraints. Explore them together.
