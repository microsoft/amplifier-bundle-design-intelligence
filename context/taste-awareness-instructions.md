# Taste Awareness Instructions

**Purpose:** Guide design agents to load, reason with, and evolve user taste profiles and the collective knowledge base during normal design work.

---

## Overview

Design agents have access to two sources of personalization:

1. **User taste profiles** — Markdown files capturing demonstrated preferences with confidence levels
2. **Collective knowledge base** — The `observed-expression/` directory capturing what design elements communicate

This document teaches you how to use both: loading profiles, weaving taste into your design reasoning, proposing profile updates when you notice patterns, and enriching the knowledge base when you discover gaps.

---

## Privacy & Disclosure

**At the start of every design session where taste-awareness is active**, briefly inform the user:

> "I can learn your design preferences over time to personalize suggestions. Preferences are only saved when you explicitly confirm them. You can disable this by setting `taste_tracking: false` in your bundle config."

This disclosure is a **one-time per session** notice — do not repeat it on every interaction. If the user has an existing profile, mention that you've loaded it.

**Opt-out:** If `taste_tracking` is set to `false` in the bundle config, do NOT observe patterns, propose profile updates, or read/write preference files. Proceed with standard design reasoning only.

---

## Loading Taste Profiles

Two profile files may exist:

- **User-global:** `~/.amplifier/design-preferences.md` — The user's general aesthetic sensibility
- **Per-project:** `.design/preferences.md` — Project-specific overrides

**At session start:**
1. Check if `taste_tracking` is disabled in config — if so, skip all taste-related behavior
2. Check if either file exists using `read_file`
3. If both exist, merge them: per-project wins on conflicts, user-global fills gaps
4. If neither exists, proceed normally — no profiles means no taste-informed reasoning, and that's fine
5. Never create profile files preemptively — they're created only when the user confirms a first preference

**Merge rules:**
- Per-project entries always override user-global entries for the same dimension
- User-global entries apply for any dimension not covered by the per-project file
- If only one file exists, use it as-is
- "Avoid" entries from both files combine (both apply)

---

## Three-Mode Reasoning Protocol

When making design decisions, use taste profiles and archive trends to inform your reasoning. Three modes, triggered by different conditions:

### Decide (High confidence + context aligns)

When the user's profile has a High-confidence preference AND the current design context aligns with it, apply the preference and state your reasoning transparently. Don't ask — but do explain.

**Trigger:** Profile entry is High confidence. Current context doesn't conflict.

**Example:**
> "I'm using a muted earth tone palette here. Your profile strongly favors desaturated earth tones, and the editorial tone of this project supports that direction."

**Behavior:** Apply the preference. Explain why. Move on. The user can always override.

### Flag (Medium confidence, or tension between preference and context)

When confidence is Medium, or when a High-confidence preference conflicts with the current design context, present the tension and ask for direction.

**Trigger:** Profile entry is Medium confidence. OR High confidence but context creates tension.

**Example:**
> "Your profile leans toward generous whitespace, but this dashboard needs to display 12 metrics scannable at a glance. I could go tighter spacing with clear grouping, or keep the whitespace and use progressive disclosure. Which direction?"

**Behavior:** Present the competing factors. Offer concrete options. Ask the user to decide. Their choice may trigger a profile update proposal.

### Recommend Evolution (Archive trend intersects with preference)

When current design trends from the archive are relevant to a user's existing preference — either reinforcing it or suggesting an evolution — weave the observation into your design reasoning.

**Trigger:** Archive-index or monthly summary contains a trend that relates to a user preference.

**Example:**
> "You favor serif headlines, and there's a strong current movement toward serif + sans-serif pairings in editorial design. But I'm also seeing condensed bold sans-serifs gaining ground for space-efficient confidence. Worth considering for this project where density matters?"

**Behavior:** Connect the trend to their profile. Explain why it's relevant. Let them decide whether to evolve.

### When No Profile Exists

If no preference files exist, reason normally without taste references. As you observe choices the user makes, you may start proposing initial profile entries (see Profile Updates below) — but only after the session-start disclosure has been given.

---

## Profile Update Proposals

When you notice patterns in the user's choices, propose profile updates. Nothing gets written without explicit user confirmation.

### When to Propose

- **New pattern observed:** User makes a choice with no matching preference (potential new entry after 2+ occurrences)
- **Pattern reinforced:** User's choice aligns with a Low/Medium confidence entry (propose escalation)
- **Pattern contradicted:** User's choice conflicts with an existing preference (flag for resolution)

### When NOT to Propose

- Mid-thought or mid-design-flow — wait for a natural break
- After a single observation — wait for at least 2 occurrences before proposing a new entry
- When the user is frustrated or in a hurry — read the room

### Proposal Format

Be specific, cite evidence, and name the target file:

> "Across this session, you've consistently chosen tight functional spacing for data-heavy interfaces. Your global profile says 'generous whitespace' with High confidence, but that seems to apply more to editorial contexts. Want me to update your project profile (`.design/preferences.md`) to distinguish between editorial (generous) and data-dense (tight, functional) layouts?"

Key properties:
- **Specific and actionable** — not "should I update your profile?" but exactly what you'd change
- **Evidence cited** — what you observed and how many times
- **Target file explicit** — say whether it's `~/.amplifier/design-preferences.md` (user-global) or `.design/preferences.md` (per-project)
- **Phrased as a question** — user confirms or dismisses

### Confidence Escalation Rules

| Situation | Action |
|-----------|--------|
| New observation, no existing entry | Propose at **Low** confidence |
| 2-3 consistent observations | Propose escalation to **Medium** |
| User explicitly confirms a preference | Set to **High** |
| Contradiction with existing entry | Flag for resolution — don't silently overwrite |

### Writing the Update

When the user confirms, write the update to the appropriate file:
- Use `edit_file` to update an existing section
- Use `write_file` to create the file if it doesn't exist yet (first preference ever)
- Follow the established format: Tendency, Confidence, Evidence, and optionally Avoid
- Include the date in the confidence note: e.g., `High (confirmed 2026-02-26)`

**Template for a new preference file:**

```
# Design Preferences

## [Dimension]
- **Tendency:** [What the user prefers]
- **Confidence:** [Low/Medium/High] ([basis and date])
- **Evidence:** [What was observed]
```

---

## Knowledge Base Enrichment

When you encounter design patterns from archive data that aren't captured in the knowledge base, propose additions. Enrichment writes go to a **local overlay directory**, not the shared bundle files.

### Flow

1. **Notice the gap** — You draw on a pattern from archive-index or a monthly summary that isn't in the existing knowledge base
2. **Propose inline** — As part of your normal design reasoning, mention it:
   > "I'm drawing on a current trend here — condensed bold sans-serifs for data density. This isn't in the knowledge base yet. Want me to save this observation locally?"
3. **User confirms or dismisses** — If confirmed, write the addition to the **local overlay**

### Where Enrichment Writes Go

All enrichment writes go to the **user's local project directory**, never to the shared bundle:

- `.design/observed-expression/typography-personalities.md` — New font personality observations
- `.design/observed-expression/` — New files when a category doesn't exist yet (e.g., `color-psychology.md`, `layout-narratives.md`, `motion-emotion.md`)
- `.design/cognitive-tasks.md` — New cognitive task entries when you encounter tasks not in the catalog

**Why local, not shared:** The bundle's `context/observed-expression/` files are part of a shared, version-controlled repository. Writing user-specific observations there would mix individual session data with community knowledge. Local overlay keeps personal observations separate.

When proposing enrichment, **explicitly tell the user** that the observation will be saved to their project's `.design/` directory.

### What Stays Read-Only (in the bundle)

All files in `context/observed-expression/` and `context/research-methodology/` are **read-only reference material**. Agents read them but never write to them:
- `context/observed-expression/*.md` — Shared design knowledge (read-only)
- `context/research-methodology/*.md` — Core methodology (read-only)

### Format for New Entries

Follow the established format from the bundle's reference files. For typography personalities, each entry uses:
- **Examples:** Specific typefaces
- **What they communicate:** Bullet list
- **Emotional associations:** Bullet list
- **Best for:** Bullet list
- **Caution:** One line

For new observed-expression files, follow the README template: `# Title: What X Communicates`, then Purpose/Status metadata, framework section, three-layer model, then categorical entries.

---

## Integration with Design Reasoning

Taste awareness is NOT a separate step or sidebar. It's woven into your normal design thinking. When you explain a design choice, the explanation naturally includes:

- What you decided and why (which may reference a taste preference)
- What you flagged and why (tension between preference and context)
- What trends are relevant (archive + profile intersection)
- What evolution you recommend (when trends and profile align or diverge)

You already explain your design reasoning. Now that reasoning is informed by what you know about this user and what's happening in design right now.
