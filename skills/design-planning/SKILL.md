---
name: design-planning
description: Use when writing implementation plans for features that have visual, UX, or design system components. Ensures design tasks are included alongside engineering tasks — design-check validation, context.json updates, and accessibility verification.
---

# Design Planning

Ensures implementation plans include design tasks alongside engineering tasks.

## When to Use

- Writing a plan for a feature with UI components
- The design doc includes visual direction or interaction patterns
- `.design/context.json` exists (design system to validate against)
- The feature introduces new components or visual patterns

## When NOT to Use

- Pure backend implementation with no UI
- The plan is exclusively for API/data work

## What to Add to Plans

### Before Implementation Tasks

If the design doc established aesthetic direction or UX patterns that aren't yet in `.design/`:

```markdown
### Task 0: Establish Design Context

- [ ] Create/update .design/AESTHETIC-GUIDE.md with direction from design doc
- [ ] Run design-context reconciler to generate/update context.json
- [ ] Verify context.json completeness — note any missing sections
```

This ensures the design system is captured BEFORE implementation begins, so design-check can validate against it.

### Within Each UI Implementation Task

Add a design-check step after code is written:

```markdown
- [ ] Write component code
- [ ] Run design-check against the component (agent self-correction)
- [ ] Verify: no hardcoded colors/spacing/fonts — all using tokens
- [ ] Verify: component has all required states (hover, focus, active, disabled, loading, error, empty)
- [ ] Commit
```

### After Implementation Tasks

```markdown
### Task N+1: Design System Verification

- [ ] Run design-check against all new/modified UI files
- [ ] Verify context.json completeness increased (new patterns captured)
- [ ] Verify accessibility: contrast ratios, keyboard nav, focus indicators
- [ ] If visual analysis available: screenshot check against declared aesthetic
```

## Interaction with Existing Plan Structure

Design tasks integrate INTO engineering tasks — they're not a separate phase. A component task isn't done until it passes design-check. This mirrors how spec-review and code-quality-review already gate task completion in superpowers.

```
Standard superpowers task flow:
  implement → spec-review → quality-review → commit

With design intelligence:
  implement → design-check (self-correction) → spec-review → quality-review → commit
```

Design-check runs BEFORE the reviews because it fixes issues silently. The reviewers then see clean, design-system-compliant code.

## Plan Document Additions

When the design doc has design sections, the plan should reference them:

```markdown
**Design System:** .design/context.json (72% complete)
**Visual Direction:** [reference design doc section]
**Design Tokens:** .design/tokens.json (if exists)
```

This gives the implementer agent the context it needs to write design-compliant code from the start.
