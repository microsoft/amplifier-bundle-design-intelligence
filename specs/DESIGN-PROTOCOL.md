# Design Protocol Specification

**Version:** 0.1.0  
**Status:** Draft  
**Inspired by:** [A2UI Protocol](https://a2ui.org)

---

## Overview

The Design Protocol is a standard format for design artifacts that any coding agent can consume. Like A2UI enables agents to generate UIs across trust boundaries, Design Protocol enables design intelligence to communicate design decisions to implementation agents.

**The problem it solves:** Design decisions made in conversation get lost or interpreted inconsistently by coding agents. Design Protocol captures decisions in a machine-readable format that produces consistent implementations.

---

## Design Principles

### 1. Declarative, Not Executable
Artifacts describe *what* the design should be, not *how* to implement it. Implementation is left to the consuming agent/framework.

### 2. Framework-Agnostic
One Design Protocol artifact should work for Tailwind, vanilla CSS, CSS-in-JS, or any other approach. Framework-specific exports are transforms, not the source of truth.

### 3. LLM-Friendly
- Flat, predictable structure
- No deeply nested hierarchies
- Can be generated incrementally/streaming
- Human-readable for debugging

### 4. Progressive
Artifacts can be partially complete. A system with only colors defined is valid. Components can reference tokens that will be defined later.

### 5. Traceable
Every decision can trace back to its source (discovery brief, user feedback, research reference).

---

## Artifact Types

| Artifact | File | Purpose |
|----------|------|---------|
| **Design Brief** | `design-brief.json` | Discovery output - intent, constraints, direction |
| **Tokens** | `tokens.json` | Design tokens - colors, typography, spacing, motion |
| **Components** | `components/*.json` | Component specifications |
| **System** | `system.json` | Full system manifest linking everything |

---

## Schema: Design Brief

The output of the discovery phase. Captures intent and constraints.

```json
{
  "$schema": "https://design-protocol.org/schemas/design-brief.json",
  "version": "0.1.0",
  "meta": {
    "project": "Project Name",
    "created": "2026-01-16T00:00:00Z",
    "source": "discovery:discovery-interviewer"
  },
  "intent": {
    "purpose": "What is this for?",
    "audience": "Who is it for?",
    "goals": ["Goal 1", "Goal 2"],
    "success_criteria": ["Criterion 1", "Criterion 2"]
  },
  "direction": {
    "adjectives": ["modern", "warm", "accessible"],
    "embrace": ["What to lean into"],
    "avoid": ["What to stay away from"]
  },
  "constraints": {
    "accessibility": "WCAG AA",
    "platforms": ["web", "mobile"],
    "existing_brand": "URL or description if applicable"
  },
  "references": [
    {
      "url": "https://example.com",
      "what_to_take": "Clean navigation pattern",
      "what_to_avoid": "Color scheme"
    }
  ]
}
```

---

## Schema: Tokens

Design tokens organized by category. See `schemas/tokens.schema.json` for full JSON Schema.

```json
{
  "$schema": "https://design-protocol.org/schemas/tokens.json",
  "version": "0.1.0",
  "meta": {
    "name": "My Design System",
    "generated": "2026-01-16T00:00:00Z",
    "source_brief": "./design-brief.json"
  },
  "color": {
    "primary": {
      "value": "#2563EB",
      "semantic": "trust, action",
      "usage": "Primary actions, links, focus states"
    },
    "secondary": {
      "value": "#7C3AED",
      "semantic": "creativity, accent",
      "usage": "Secondary actions, highlights"
    },
    "neutral": {
      "50": "#FAFAFA",
      "100": "#F4F4F5",
      "200": "#E4E4E7",
      "300": "#D4D4D8",
      "400": "#A1A1AA",
      "500": "#71717A",
      "600": "#52525B",
      "700": "#3F3F46",
      "800": "#27272A",
      "900": "#18181B",
      "950": "#09090B"
    },
    "semantic": {
      "success": { "value": "#22C55E", "usage": "Success states, confirmations" },
      "warning": { "value": "#F59E0B", "usage": "Warnings, cautions" },
      "error": { "value": "#EF4444", "usage": "Errors, destructive actions" },
      "info": { "value": "#3B82F6", "usage": "Informational messages" }
    }
  },
  "typography": {
    "families": {
      "heading": {
        "name": "Inter",
        "fallback": "system-ui, sans-serif",
        "personality": "modern, clean, geometric"
      },
      "body": {
        "name": "Inter",
        "fallback": "system-ui, sans-serif",
        "personality": "readable, neutral"
      },
      "mono": {
        "name": "JetBrains Mono",
        "fallback": "monospace",
        "personality": "technical, precise"
      }
    },
    "scale": {
      "xs": { "size": "0.75rem", "lineHeight": "1rem" },
      "sm": { "size": "0.875rem", "lineHeight": "1.25rem" },
      "base": { "size": "1rem", "lineHeight": "1.5rem" },
      "lg": { "size": "1.125rem", "lineHeight": "1.75rem" },
      "xl": { "size": "1.25rem", "lineHeight": "1.75rem" },
      "2xl": { "size": "1.5rem", "lineHeight": "2rem" },
      "3xl": { "size": "1.875rem", "lineHeight": "2.25rem" },
      "4xl": { "size": "2.25rem", "lineHeight": "2.5rem" }
    },
    "weights": {
      "normal": 400,
      "medium": 500,
      "semibold": 600,
      "bold": 700
    }
  },
  "spacing": {
    "base": "4px",
    "scale": ["0", "1px", "2px", "4px", "6px", "8px", "12px", "16px", "20px", "24px", "32px", "40px", "48px", "64px", "80px", "96px"]
  },
  "radius": {
    "none": "0",
    "sm": "2px",
    "default": "4px",
    "md": "6px",
    "lg": "8px",
    "xl": "12px",
    "2xl": "16px",
    "full": "9999px"
  },
  "shadow": {
    "sm": "0 1px 2px 0 rgb(0 0 0 / 0.05)",
    "default": "0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)",
    "md": "0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)",
    "lg": "0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)",
    "xl": "0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)"
  },
  "motion": {
    "duration": {
      "instant": "0ms",
      "fast": "150ms",
      "normal": "300ms",
      "slow": "500ms",
      "slower": "700ms"
    },
    "easing": {
      "default": "cubic-bezier(0.4, 0, 0.2, 1)",
      "in": "cubic-bezier(0.4, 0, 1, 1)",
      "out": "cubic-bezier(0, 0, 0.2, 1)",
      "inOut": "cubic-bezier(0.4, 0, 0.2, 1)",
      "bounce": "cubic-bezier(0.68, -0.55, 0.265, 1.55)"
    }
  }
}
```

---

## Schema: Component

Individual component specifications. Each component gets its own file.

```json
{
  "$schema": "https://design-protocol.org/schemas/component.json",
  "version": "0.1.0",
  "meta": {
    "name": "Button",
    "description": "Primary interactive element for actions",
    "category": "actions"
  },
  "variants": ["primary", "secondary", "ghost", "destructive"],
  "sizes": ["sm", "md", "lg"],
  "states": ["default", "hover", "active", "focus", "disabled", "loading"],
  "props": {
    "children": { "type": "ReactNode", "required": true },
    "variant": { "type": "string", "default": "primary" },
    "size": { "type": "string", "default": "md" },
    "disabled": { "type": "boolean", "default": false },
    "loading": { "type": "boolean", "default": false },
    "onClick": { "type": "function" }
  },
  "tokens": {
    "primary": {
      "background": "color.primary.value",
      "text": "#FFFFFF",
      "border": "none",
      "hover": { "background": "color.primary.value @ 90%" }
    },
    "secondary": {
      "background": "transparent",
      "text": "color.primary.value",
      "border": "1px solid color.primary.value"
    }
  },
  "accessibility": {
    "role": "button",
    "focusVisible": true,
    "minTouchTarget": "44px",
    "contrastRatio": "4.5:1"
  },
  "behavior": {
    "loading": "Replace content with spinner, maintain width",
    "disabled": "Reduce opacity to 50%, remove pointer events"
  },
  "examples": [
    { "props": { "variant": "primary" }, "label": "Primary Button" },
    { "props": { "variant": "secondary" }, "label": "Secondary Button" },
    { "props": { "variant": "destructive" }, "label": "Delete" }
  ]
}
```

---

## Schema: System Manifest

Links all artifacts together into a complete system.

```json
{
  "$schema": "https://design-protocol.org/schemas/system.json",
  "version": "0.1.0",
  "meta": {
    "name": "My Design System",
    "version": "1.0.0",
    "generated": "2026-01-16T00:00:00Z"
  },
  "artifacts": {
    "brief": "./design-brief.json",
    "tokens": "./tokens.json",
    "components": [
      "./components/button.json",
      "./components/input.json",
      "./components/card.json"
    ]
  },
  "exports": {
    "css": "./exports/tokens.css",
    "tailwind": "./exports/tailwind.config.js",
    "scss": "./exports/tokens.scss",
    "json": "./exports/tokens.flat.json"
  }
}
```

---

## Export Formats

Design Protocol artifacts can be transformed into framework-specific formats:

### CSS Custom Properties
```css
:root {
  --color-primary: #2563EB;
  --color-secondary: #7C3AED;
  --font-heading: 'Inter', system-ui, sans-serif;
  --spacing-base: 4px;
  /* ... */
}
```

### Tailwind Config
```js
module.exports = {
  theme: {
    colors: {
      primary: '#2563EB',
      secondary: '#7C3AED',
      // ...
    },
    fontFamily: {
      heading: ['Inter', 'system-ui', 'sans-serif'],
      // ...
    }
  }
}
```

### SCSS Variables
```scss
$color-primary: #2563EB;
$color-secondary: #7C3AED;
$font-heading: 'Inter', system-ui, sans-serif;
$spacing-base: 4px;
```

---

## Implementation Notes

### For Generating Agents

When generating Design Protocol artifacts:
1. Start with the design brief from discovery
2. Generate tokens based on brief direction and constraints
3. Generate component specs that reference tokens by path (e.g., `color.primary.value`)
4. Create system manifest linking everything

### For Consuming Agents

When implementing from Design Protocol artifacts:
1. Read system manifest to understand available artifacts
2. Parse tokens and apply to framework (Tailwind, CSS, etc.)
3. Implement components following specs
4. Validate against accessibility requirements in specs

### Validation

Artifacts should be validated against JSON schemas before use. Invalid artifacts should fail early with clear error messages.

---

## Versioning

Design Protocol uses semantic versioning:
- **Major:** Breaking changes to schema structure
- **Minor:** New optional fields, new artifact types
- **Patch:** Documentation, examples, clarifications

Artifacts include version field for compatibility checking.

---

## Future Considerations

- **Animation sequences:** More complex motion choreography
- **Responsive variants:** Breakpoint-specific token overrides
- **Dark mode:** Color scheme switching
- **Component composition:** How components combine
- **Design decisions log:** Why decisions were made (traceability)
