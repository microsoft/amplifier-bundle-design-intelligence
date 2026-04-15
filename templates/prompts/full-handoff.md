# Full Design System Handoff Prompt

The complete prompt for handing off a design system to coding agents. Combines tokens + components + implementation guidance.

---

## Prompt Template

```markdown
# Implement Design System: {{project_name}}

You are implementing a complete design system. This document contains everything you need.

## 1. Design Context

**Project:** {{project_name}}
**Description:** {{project_description}}

**Aesthetic Direction:**
- Adjectives: {{adjectives}}
- Embrace: {{embrace}}
- Avoid: {{avoid}}

**Quality Standard:** 9.5/10 - Production-ready, polished, accessible

---

## 2. Design Tokens

Apply these tokens first. They are the foundation.

### Colors

| Token | Value | Usage |
|-------|-------|-------|
| `--color-primary` | {{primary}} | Primary actions, links, focus |
| `--color-secondary` | {{secondary}} | Secondary actions, accents |
| `--color-success` | {{success}} | Success states, confirmations |
| `--color-warning` | {{warning}} | Warnings, cautions |
| `--color-error` | {{error}} | Errors, destructive actions |
| `--color-info` | {{info}} | Information, neutral alerts |

**Neutral Scale:** {{neutral_scale}}

### Typography

| Token | Value |
|-------|-------|
| `--font-heading` | {{heading_font}} |
| `--font-body` | {{body_font}} |
| `--font-mono` | {{mono_font}} |

**Scale:** xs (0.75rem) → sm (0.875rem) → base (1rem) → lg (1.125rem) → xl (1.25rem) → 2xl (1.5rem) → 3xl (1.875rem) → 4xl (2.25rem)

### Spacing

**Base:** 4px

**Scale:** 0, 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px

### Border Radius

| Token | Value |
|-------|-------|
| `--radius-sm` | 2px |
| `--radius-default` | 4px |
| `--radius-md` | 6px |
| `--radius-lg` | 8px |
| `--radius-xl` | 12px |
| `--radius-full` | 9999px |

### Shadows

| Token | Value |
|-------|-------|
| `--shadow-sm` | 0 1px 2px 0 rgb(0 0 0 / 0.05) |
| `--shadow-default` | 0 1px 3px 0 rgb(0 0 0 / 0.1) |
| `--shadow-md` | 0 4px 6px -1px rgb(0 0 0 / 0.1) |
| `--shadow-lg` | 0 10px 15px -3px rgb(0 0 0 / 0.1) |

### Motion

| Duration | Value | Use For |
|----------|-------|---------|
| Fast | 150ms | Micro-interactions, hovers |
| Normal | 300ms | Most transitions |
| Slow | 500ms | Page transitions, modals |

| Easing | Value |
|--------|-------|
| Default | cubic-bezier(0.4, 0, 0.2, 1) |
| In | cubic-bezier(0.4, 0, 1, 1) |
| Out | cubic-bezier(0, 0, 0.2, 1) |

---

## 3. Token Files to Create

### tokens.css

```css
:root {
  /* Paste generated CSS here */
}
```

### tailwind.config.js (if using Tailwind)

```javascript
module.exports = {
  theme: {
    extend: {
      /* Paste generated config here */
    }
  }
}
```

---

## 4. Components to Implement

{{component_specs}}

---

## 5. Implementation Checklist

### Tokens Setup
- [ ] Create tokens.css with all custom properties
- [ ] Configure Tailwind (if applicable)
- [ ] Create token preview/test page
- [ ] Verify color contrast ratios

### Component Implementation
- [ ] Implement each component per spec
- [ ] All variants working
- [ ] All sizes working
- [ ] All states (hover, focus, active, disabled, loading)
- [ ] Keyboard navigation
- [ ] Screen reader testing
- [ ] Responsive behavior

### Quality Verification
- [ ] Visual matches spec
- [ ] Interactions feel right
- [ ] No accessibility warnings
- [ ] Performance is good
- [ ] Code is clean and maintainable

---

## 6. Success Criteria

The implementation is complete when:

1. **Tokens are applied** - All components use token references
2. **Specs are followed** - Components match specifications exactly
3. **Accessibility passes** - WCAG AA compliance
4. **Behavior is correct** - All states and interactions work
5. **Quality is high** - Looks polished, feels professional
```

---

## How to Use

1. Run the `design-system-export` recipe to get tokens and specs
2. Fill in placeholders with generated values
3. Paste into your coding agent (Claude Code, Cursor, etc.)
4. Agent implements the full design system

## Generating the Filled Prompt

The `export-packager` agent produces a filled version of this template based on your tokens and component specs.
