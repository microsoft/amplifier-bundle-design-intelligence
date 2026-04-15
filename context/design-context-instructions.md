# Design Context Protocol

These instructions apply to every design agent. Follow them automatically.

## On Session Start

Check for `.design/context.json` in the project root.

**If it exists**, read it. Note:
- Which sections are `defined` (use as-is, these are authoritative)
- Which sections are `inferred` (use them, but they're adjustable)
- Which sections are `missing` (you may need to propose values)
- Whether `conflicts[]` has entries (you must address these, see below)
- The `meta.completeness` percentage (gives you a sense of design maturity)

**If it doesn't exist**, proceed normally. Your work will contribute to creating it.

## During Work

### Using defined values

Sections marked `defined` are settled decisions. Use them directly without commentary. Don't second-guess tokens or confirmed choices.

### Using inferred values

When you use an inferred value, mention it naturally so the user stays aware:

> "I'm using the warm ochre palette inferred from your aesthetic guide — let me know if you'd prefer a different direction."

One sentence is enough. Don't belabor it.

### Filling missing sections

If a `missing` section is relevant to your current work, **propose a value with brief reasoning**. Don't ask the user to decide from scratch — give them something concrete to react to.

Good:
> "There's no motion timing defined yet. Based on the minimal, calm aesthetic in your guide, I'd suggest 200ms ease-out for micro-interactions and 400ms ease-in-out for layout transitions."

Bad:
> "What animation durations would you like?"

Use inference chains when available. If context.json defines `color.palette` as warm earth tones and `overall.mood` as calm, you can infer that motion should be unhurried. State the chain briefly.

### Promoting inferred → defined

When a user explicitly confirms an inferred value — they say "yes", "that works", "perfect", or they see it in a deliverable and don't object — that value can be promoted to `defined`. Note this in your reconciliation call:

> Reconcile .design/context.json. Promote typography.heading to defined — user confirmed Playfair Display.

## After Writing to .design/

**Every time** you create or modify a file in `.design/`, delegate to the reconciler:

```
Delegate to design-intelligence:design-context:
"Reconcile .design/context.json from current artifacts."
```

This is not optional. The reconciler keeps context.json consistent with all artifacts. Without it, context.json drifts and other agents work from stale data.

If you wrote multiple files, call the reconciler once after all writes — not after each file.

## Handling Conflicts

If `context.json` contains `conflicts[]`, check whether any are relevant to your work.

**Don't silently pick a side.** Present the tension:

> "There's a conflict in your design context: your aesthetic guide calls for serif headings, but your tokens define Inter (sans-serif). I'll work with the token value since it's more specific, but you may want to resolve this — want me to update the aesthetic guide, or should we change the token?"

If a conflict isn't relevant to your current task, leave it alone. Don't enumerate every conflict at session start.

## Reference

| Status | Meaning | Your behavior |
|---|---|---|
| `defined` | Explicit, confirmed value | Use directly |
| `inferred` | Extracted from prose/derived | Use it, mention the source |
| `missing` | No data | Propose with reasoning if relevant |

| Source file | Authority | Typical content |
|---|---|---|
| `tokens.json` | Highest | Concrete values (colors, sizes, fonts) |
| `specs/*.md` | High | Component-level decisions |
| `AESTHETIC-GUIDE.md` | Medium | Design direction, mood, principles |
| `preferences.md` | Broad | Taste constraints, likes/dislikes |

Context schema: `@design-intelligence:specs/schemas/context.schema.json`
