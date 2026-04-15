# Design Check: Self-Correction Instructions

These instructions apply to all design agents that produce code: component-designer, design-system-architect, layout-architect, responsive-strategist.

---

## The Self-Correction Loop

After generating code, you run validation against the project's design context before presenting work to the user. This catches drift from the design system while the code is still fresh.

### Step 1: Generate Code

Write the code as normal. Do your best work. The check isn't a crutch — it's a safety net.

### Step 2: Run Design Check

Before presenting to the user, delegate to `design-intelligence:design-check` with the file path(s) you just wrote. The check agent will run Layer 1 (static) and Layer 2 (structural) analysis against `.design/context.json`.

### Step 3: Process Findings

Handle findings by severity:

**`error`** — Fix immediately. Do not tell the user you found an error and fixed it. Just fix it. Re-run the check to confirm the fix didn't introduce new issues.

**`warning`** — Fix if the fix is straightforward and doesn't alter design intent. If fixing would change the visual or behavioral intent of what you built, flag it to the user as a tension between your implementation and the declared context.

**`info`** — Note internally. Do not block on info-level findings. Do not mention them unless the user asks for a full audit.

### Step 4: Iterate (Max 3 Cycles)

Run up to three check-fix cycles:

```
generate → check → fix → check → fix → check → fix → present
```

After three cycles, stop iterating. Present the work. If info-level findings remain, mention them conversationally ("I used slightly tighter spacing here because...") rather than as a formal report.

If error-level findings persist after three cycles, something is structurally wrong. Present the work with the unresolved errors noted explicitly so the user can make a judgment call.

---

## When to Skip Visual Analysis

Layer 3 (visual analysis) requires a running dev server or accessible URL. Skip it when:

- You're writing code without a render target
- The user hasn't mentioned a dev server or URL
- You're working on non-visual code (tokens, configs, utilities)

Don't ask the user to start a dev server just for validation. If a server is already running and you know the URL, include Layer 3.

---

## What to Surface to the User

**Default: surface nothing.** Fix silently, present clean work.

Surface findings only when:

1. **A fix conflicts with an inferred value.** If context.json has `"status": "inferred"` on a section, and your implementation conflicts with it, present the tension. The user may want to confirm or override the inferred value. Example: "The inferred type scale uses 14px body text, but this component reads better at 15px. Want me to update the context or adjust the component?"

2. **The user explicitly asks for a design audit.** When they say "check this against the design system" or "run a design audit," return the full structured report from design-check and walk through the findings.

3. **Errors persist after 3 cycles.** Something structural is wrong. Tell the user what's unresolved and why your fixes aren't sticking.

---

## Working Without Context

If `.design/context.json` doesn't exist or has most sections as `missing`, fall back to design-baseline.md principles only. Don't invent context values. Note to the user that validation was limited:

"I applied design-baseline principles but couldn't validate against project-specific tokens since the design context hasn't been established yet. Run the art-director to set up `.design/context.json` when you're ready."

---

## Key Principles

- **Silent quality, not theater.** The user sees clean work, not your process.
- **Context over opinion.** Check against declared values, not taste.
- **Defined > inferred > missing.** Trust defined values. Question inferred ones. Ignore missing ones.
- **Three cycles max.** Perfectionism kills momentum. Ship good work.
