---
name: brand-naming
description: Use when naming a product, project, feature, or brand. Runs parallel creative agents with cross-critique, distills to a shortlist, validates availability across package registries, and produces a final recommendation with rationale.
---

# Brand Naming

Structured naming workflow using parallel creative agents, adversarial cross-critique, and registry validation. Produces a shortlist of 5–7 names with one recommended pick.

## When to Use

- Naming a new product, project, or open-source tool
- Renaming something that outgrew its working name
- Naming a feature, service, or sub-brand within a larger system
- Any time a name needs to survive in public (registries, GitHub, docs, conversation)

## When NOT to Use

- Naming internal variables, functions, or files (that's code style, not branding)
- The name is already decided and you're doing visual identity work (use art-director)

## The Workflow

```
1. BRIEF (what does this thing DO and WHO is it for?)
   - One sentence: what the product does
   - Target audience: developers? consumers? enterprise?
   - Personality: serious? playful? technical? approachable?
   - Constraints: max length, must contain a word, must avoid a word
   - Existing working name (if any) — note what works and what doesn't about it

2. PARALLEL GENERATION (two agents, independent)
   - Dispatch voice-strategist and art-director IN PARALLEL
   - Each generates 10–15 candidates independently
   - voice-strategist optimizes for: phonetics, memorability, tone, verbal clarity
   - art-director optimizes for: visual potential, logo-ability, typographic character
   - Neither sees the other's list during generation

3. CROSS-CRITIQUE (adversarial refinement)
   - Each agent receives the OTHER's full candidate list
   - Each critiques every name on the other's list: keep, maybe, kill — with reasoning
   - Each agent also defends or withdraws their own candidates based on the critique
   - The cross-critique surfaces names that survive scrutiny from BOTH perspectives

4. DISTILL (human-ready shortlist)
   - Merge surviving candidates from both agents
   - Remove duplicates (both agents often converge on the same strong names)
   - Rank by: survived both critiques > survived one > neither
   - Present 5–7 finalists with:
     - Name
     - Who proposed it (voice/art/both)
     - One-line pitch (why this name works)
     - One-line risk (the strongest argument against it)

5. REGISTRY VALIDATION (before committing)
   - For each finalist, check availability across relevant registries
   - Use web-research agent to check: npm, PyPI, crates.io, Homebrew, Docker Hub, GitHub
   - Not all registries matter for every project — ask which ones to check
   - Flag conflicts: "taken" vs "abandoned" vs "different domain" matters
   - An abandoned GitHub repo with 0 stars is different from an active npm package

6. FINAL RECOMMENDATION
   - Present the validated shortlist with registry status
   - Recommend a top pick with reasoning
   - Human makes the final call — always
```

## Agent Dispatch

### Generation Phase

Dispatch both agents in parallel with identical briefs but different evaluation lenses:

**voice-strategist prompt:**
> Generate 10–15 name candidates for [brief]. Optimize for: how the name SOUNDS when spoken aloud, phonetic memorability, tone match with [personality], verbal clarity (can someone hear it once and spell it?), distinctiveness in conversation. Include word-blends, portmanteaus, and invented words alongside straightforward names.

**art-director prompt:**
> Generate 10–15 name candidates for [brief]. Optimize for: how the name LOOKS as a wordmark, typographic character (which fonts would suit it?), logo potential (does it suggest a visual mark?), visual distinctiveness at small sizes (favicon, tab title), aesthetic personality match with [personality]. Include word-blends, portmanteaus, and invented words alongside straightforward names.

### Cross-Critique Phase

Send each agent the other's list:

**To voice-strategist:**
> Art director generated these candidates: [list]. For each: keep/maybe/kill with one sentence explaining why. Consider phonetics, memorability, and tone. Then review your own list — withdraw any of yours that the art director's critique would validly challenge.

**To art-director:**
> Voice strategist generated these candidates: [list]. For each: keep/maybe/kill with one sentence explaining why. Consider visual identity, wordmark potential, and aesthetic character. Then review your own list — withdraw any of yours that the voice strategist's critique would validly challenge.

## Registry Validation

Check only the registries relevant to the project:

| Project Type | Check These |
|-------------|-------------|
| CLI tool | npm, PyPI, crates.io, Homebrew, GitHub |
| Web app | npm, GitHub, domain availability |
| Python library | PyPI, GitHub |
| Rust crate | crates.io, GitHub |
| General / unsure | npm, PyPI, GitHub (minimum) |

### Interpreting Results

| Status | Meaning | Action |
|--------|---------|--------|
| Available | Name is free | Green light |
| Taken, active | Active project with users | Hard conflict — drop the name |
| Taken, abandoned | 0 stars, no commits in 2+ years | Soft conflict — note it, human decides |
| Taken, different domain | Same name but completely different thing | Context-dependent — "muxplex" the npm package vs "muxplex" the restaurant |

## Quality Signals in Names

Names that survive cross-critique tend to share these qualities:

- **Speakable**: Someone can hear it once and type it correctly
- **Searchable**: Googling the name finds the project, not noise
- **Verbal shorthand**: Works in conversation ("just muxplex into it")
- **Visual character**: Suggests a typeface, a color, a mood
- **Extendable**: Supports sub-products or features (muxplex-cli, muxplex-web)

Names that get killed in cross-critique tend to fail on:

- **Vowel-dropping trends**: "tumblr-era" tricks that age poorly (tmuxr, muxy)
- **Generic compounds**: Names that describe the category, not the product (web-terminal, pane-manager)
- **Unpronounceable**: Consonant clusters nobody can say in conversation
- **Already saturated**: Too many existing projects with similar names

## What This Skill Does NOT Cover

- **Visual identity** (logo, icon, wordmark) — that's art-director + nano-banana after the name is chosen
- **Domain registration** — we check availability, we don't purchase
- **Trademark search** — legal trademark clearance is beyond this workflow; flag it as a next step for names entering production

## Key Principle

A good name survives adversarial critique from two different perspectives — how it sounds AND how it looks. The parallel generation ensures creative breadth; the cross-critique ensures only the strongest survive. The human always makes the final call, but they choose from a shortlist that's been pressure-tested.
