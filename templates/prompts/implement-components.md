# Component Implementation Prompt

Use this prompt to instruct coding agents to implement components from Design Protocol specs.

---

## Prompt Template

```markdown
# Implement Design System Components

You are implementing components for a design system. Follow these specs exactly.

## Design System Context

**Token Reference:**
- Colors: Use `var(--color-*)` or Tailwind `text-primary`, `bg-primary`, etc.
- Typography: Use `var(--font-*)` or Tailwind `font-heading`, `font-body`
- Spacing: Use `var(--spacing-*)` or Tailwind spacing scale
- Radius: Use `var(--radius-*)` or Tailwind `rounded-*`

**Framework:** {{framework}}

## Components to Implement

{{#each components}}
### {{name}}

**Description:** {{description}}

**Variants:** {{variants}}

**Sizes:** {{sizes}}

**Props:**

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
{{#each props}}
| {{name}} | {{type}} | {{required}} | {{default}} | {{description}} |
{{/each}}

**Styling by Variant:**

| Variant | Background | Text | Border |
|---------|------------|------|--------|
{{#each variantStyles}}
| {{variant}} | {{background}} | {{text}} | {{border}} |
{{/each}}

**Accessibility:**
- Role: {{accessibility.role}}
- Focus: {{accessibility.focusVisible}}
- Min touch target: {{accessibility.minTouchTarget}}
- Contrast requirement: {{accessibility.contrastRatio}}

**Behavior:**
{{#each behavior}}
- **{{state}}:** {{description}}
{{/each}}

**Example Usage:**
```jsx
{{examples}}
```

---

{{/each}}

## Implementation Requirements

1. **Use token references** - Never hardcode colors, fonts, spacing
2. **Include all variants** - Each variant listed must be implemented
3. **Handle all states** - default, hover, active, focus, disabled
4. **Meet accessibility** - ARIA roles, focus visible, contrast
5. **Match behavior exactly** - Loading states, disabled states, etc.

## Success Criteria

- [ ] All components render correctly
- [ ] All variants work
- [ ] All sizes work
- [ ] Hover/focus/active states work
- [ ] Disabled state works
- [ ] Loading state works (where applicable)
- [ ] Keyboard navigation works
- [ ] Screen reader announces correctly
```

---

## Usage

1. Replace `{{placeholders}}` with actual values from component specs
2. For Handlebars syntax (`{{#each}}`), expand manually or use templating
3. Paste into your coding agent
4. Agent will implement all components
