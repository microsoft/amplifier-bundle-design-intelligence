# Design System Setup Prompt

Use this prompt to instruct coding agents (Claude Code, Cursor, Copilot) to set up the design system tokens.

---

## Prompt Template

```markdown
# Setup Design System Tokens

You are implementing a design system. Here are the tokens to configure.

## Design Context

**Project:** {{project_name}}
**Aesthetic:** {{adjectives}}
**Primary Color:** {{primary_color}} - {{primary_semantic}}
**Typography:** {{heading_font}} for headings, {{body_font}} for body

## Tokens

{{tokens_json}}

## Your Task

1. **Create token files:**
   - `tokens.css` - CSS custom properties
   - Configure Tailwind if using: `tailwind.config.js`

2. **Verify setup:**
   Create a test page (`design-system-test.html` or component) showing:
   - All color swatches (primary, secondary, neutral scale, semantic)
   - Typography scale (xs through 4xl)
   - Spacing scale visualization
   - Shadow examples
   - Border radius examples

3. **Confirm accessibility:**
   - Primary on white: verify 4.5:1 contrast
   - Text colors on backgrounds: verify readable

## CSS Custom Properties Format

```css
:root {
  /* Colors */
  --color-primary: {{primary_color}};
  --color-secondary: {{secondary_color}};
  /* ... continue with all tokens ... */
}
```

## Success Criteria

- [ ] All token values correctly applied
- [ ] Test page shows all tokens visually
- [ ] Contrast ratios verified
- [ ] Tailwind config working (if applicable)
```

---

## Usage

1. Replace `{{placeholders}}` with actual values from your tokens.json
2. Paste into your coding agent
3. Agent will create token files and verification page
