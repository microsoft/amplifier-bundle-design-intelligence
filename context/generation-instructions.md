# Generation Instructions

This document provides guidance for Design Protocol artifact generation.

## The Generation Pipeline

```
Discovery Brief → Tokens → Component Specs → Export Package
```

Each step builds on the previous. Don't skip steps.

## Available Generation Agents

| Agent | Produces | Consumes |
|-------|----------|----------|
| `token-generator` | tokens.json, CSS, Tailwind, SCSS | Discovery brief, design direction |
| `spec-writer` | Component JSON specs | Tokens, design direction |

## Design Protocol Artifacts

All generated artifacts follow the Design Protocol specification. See `specs/DESIGN-PROTOCOL.md` for full schema details.

### Token File Structure

```
tokens.json
├── meta (name, generated, source)
├── color (primary, secondary, neutral, semantic)
├── typography (families, scale, weights)
├── spacing (base, scale)
├── radius
├── shadow
└── motion (duration, easing)
```

### Component Spec Structure

```
component.json
├── meta (name, description, category)
├── variants
├── sizes
├── states
├── props
├── tokens (per-variant styling)
├── accessibility
├── behavior
└── examples
```

## Generation Best Practices

### 1. Always Reference Tokens

Component specs must reference tokens, never hardcode values:

```json
// ✅ Correct
"background": "color.primary.value"

// ❌ Incorrect
"background": "#2563EB"
```

### 2. Complete or Nothing

Generate complete artifacts. Partial tokens or specs cause implementation issues.

### 3. Include Accessibility

Every component spec must include:
- ARIA role
- Focus handling
- Contrast requirements
- Touch target sizes

### 4. Trace to Source

Include `source_brief` in meta to enable traceability:

```json
"meta": {
  "source_brief": "./design-brief.json",
  "generator": "design-intelligence:token-generator"
}
```

## Export Formats

After generating `tokens.json`, produce these exports:

| Format | File | Use Case |
|--------|------|----------|
| CSS Variables | `tokens.css` | Any framework |
| Tailwind | `tailwind.config.js` | Tailwind projects |
| SCSS | `tokens.scss` | SCSS projects |
| Flat JSON | `tokens.flat.json` | Style Dictionary, tooling |

## Validation

Before finalizing:

1. **Schema validation** - Artifacts match Design Protocol schemas
2. **Token references** - All component token refs resolve
3. **Accessibility** - Contrast ratios meet requirements
4. **Completeness** - No missing required fields

## Handoff to Coding Agents

Generated artifacts are designed for direct consumption by coding agents:

1. Tokens provide the design language
2. Component specs provide the implementation blueprint
3. Export formats provide framework-ready code

Coding agents should:
- Apply tokens first (CSS variables, Tailwind config)
- Implement components per spec
- Validate against accessibility requirements
