# Design Research Capability - Usage Instructions

This document explains how to use the design research capability for creative, purpose-driven trend analysis.

---

## Overview

The design research capability provides:

1. **Purpose-driven research** - Research by cognitive task across domains (not just category-matching)
2. **RSS feed collection** - Awwwards, Siteinspire, The FWA
3. **Visual analysis** - AI-powered screenshot analysis (user-directed)
4. **Trend synthesis** - Actionable insights with reasoning
5. **Conversational queries** - Natural language research requests

---

## What's New: Creative Research Methodology

**Design-intelligence now researches by PURPOSE, not CATEGORY.**

### The Old Way (Category-Matching)
```
User: "Design a healthcare dashboard"
Research: Healthcare dashboard examples
Output: Competent remix of existing healthcare UIs
```

### The New Way (Purpose-Driven)
```
User: "Design a healthcare dashboard"
Decompose: Cognitive tasks > "rapid assessment", "anomaly detection", "decision support"
Map: Analogous domains > medical monitors, trading platforms, security ops, gaming HUDs
Research: 20% healthcare + 50% purpose-driven + 30% divergent
Extract: Level 3-4 patterns (interaction/cognitive, not just visual)
Output: Creative work grounded in proven patterns from unexpected sources
```

**Result**: Designs that feel fresh and innovative while being grounded in proven patterns — just from unexpected places.

---

## Core Methodology

Design research follows **Creative Research Methodology**:

See: `@design-intelligence:context/research-methodology/creative-research-methodology.md`

### Key Resources
- **Creative Research Methodology** - Purpose-driven research approach
- **Cognitive Task Catalog** - Common tasks + analogous domains
- **Pattern Abstraction Guide** - Extracting Level 3-4 patterns
- **Cognitive Discovery Enhancement** - Bridging discovery to research

All in: `context/research-methodology/`

---

## Components

### Agents

**research-analyst** - Creative research specialist
- Conducts purpose-driven research by cognitive task
- Extracts Level 3-4 patterns from unexpected sources
- Synthesizes with explicit reasoning
- Conversational interface for design insights
- **Uses**: Creative research methodology (multi-vector research)

**research-runner** - Technical execution agent
- Fetches design trend data from RSS feeds
- Generates summaries and updates archive
- Used via recipes or direct invocation

### Recipe

**weekly-design-research** - Automated research workflow
- Fetches RSS feeds from Awwwards, Siteinspire, The FWA
- Generates monthly summary
- Updates 30-day archive index
- Takes 2-5 minutes to complete

### Skills Required

**image-vision** - Visual analysis of design screenshots
- Used on-demand when user provides URLs or screenshots for analysis
- See: `~/.amplifier/skills/robotdad/image-vision/SKILL.md`

---

## Usage Patterns

### Pattern 1: Creative Project Research

**When**: Starting a new design project

**What you get**: Cross-domain inspiration with explicit reasoning

**How**:
```
In a design-intelligence session:

> I need to design a launch status dashboard for rocket missions

Research-analyst will:
1. Ask about cognitive tasks ("What is the user's brain doing?")
2. Map to analogous domains (medical monitors, trading platforms, gaming HUDs)
3. Conduct multi-vector research (domain-specific, purpose-driven, divergent)
4. Extract Level 3-4 patterns (interaction/cognitive, not visual)
5. Synthesize with reasoning about WHY each source is relevant
```

**Output**: Research report with unexpected sources and transferable patterns

---

### Pattern 2: Current Trend Analysis

**When**: Need to know "what's trending now?"

**What you get**: Recent patterns from award-winning sites

**How**:
```
In a design-intelligence session:

> What are current trends in web animation?
> Show me examples of dark mode with vibrant accents
> How have grid layouts evolved in the last 3 months?
```

**Output**: Trend analysis from archive with specific examples

---

### Pattern 3: Running Periodic Research Updates

**When**: Weekly or bi-weekly to maintain current data

**Prerequisites**: Recipes tool required (included in foundation)

**Option 1: Using the Recipe (Recommended)**

Conversational:
```
execute design-intelligence:recipes/weekly-design-research.yaml with year=2026 month=01 month_name=january date=2026-01-27
```

CLI:
```bash
amplifier tool invoke recipes \
  operation=execute \
  recipe_path=design-intelligence:recipes/weekly-design-research.yaml \
  context='{"year": "2026", "month": "01", "month_name": "january", "date": "2026-01-27"}'
```

The recipe automatically:
- Creates directory structure
- Fetches RSS feeds from all sources (Awwwards, Siteinspire, The FWA)
- Generates summaries
- Updates archive index

**Option 2: Manual Execution**

Use the task tool to invoke research-runner:
```
Use the research-runner agent to fetch RSS feeds from Awwwards for this week
Use the research-runner agent to generate the monthly summary
```

---

## Example Workflows

### Workflow 1: Purpose-Driven Project Research

**Goal**: Get creative inspiration for a new project

**Steps**:
```
1. Start design-intelligence session

2. Request research:
   > I need to design a mission launch dashboard

3. Answer cognitive task questions:
   - What is the user's brain doing? (rapid assessment, anomaly detection)
   - What decisions do they make? (go/no-go, investigate, share)
   - What's their emotional state? (focused monitoring with alert-driven urgency)

4. Receive multi-vector research:
   - Domain-specific: NASA, SpaceX dashboards (know the conventions)
   - Purpose-driven: Medical monitors, trading platforms, gaming HUDs (proven patterns)
   - Divergent: Game studios, luxury brands, physical analogs (breakthrough ideas)

5. Get pattern synthesis with reasoning:
   - "From hospital monitors: Gestalt assessment principle - design for 200ms comprehension"
   - "From trading platforms: Real-time anomaly highlighting with confidence indicators"
   - "From gaming HUDs: Critical info hierarchy without disrupting flow state"
```

---

### Workflow 2: Weekly Research Update

**Goal**: Maintain current trend data

**Steps**:
```bash
# 1. Run RSS feed collection (takes 2-5 min)
amplifier tool invoke recipes \
  operation=execute \
  recipe_path=design-intelligence:recipes/weekly-design-research.yaml \
  context='{"year": "2026", "month": "01", "month_name": "january", "date": "2026-01-27"}'

# 2. Review results
amplifier tool invoke recipes operation=list

# 3. Query insights (in a session)
> What trends emerged from this week's research?
```

---

### Workflow 3: Competitive Analysis

**Goal**: Understand patterns in a specific domain

**Steps**:
```
In a design-intelligence session:

> Show me all e-commerce sites from the last 2 months
> How do they handle product galleries?
> What's the most common navigation pattern?

Analyst searches archive and synthesizes patterns.
```

---

## Research Modes Available

### Mode A: Archive Analysis (Current Trends)
Query the design archive for recent visual patterns.

**Use when**: "What's trending now?" or examples from award-winning sites

### Mode B: User-Directed URL Analysis
Analyze a specific site the user provides using web_fetch and optional screenshot analysis.

**Use when**: User shares a URL and wants pattern extraction. The user provides the URL, and the system fetches and analyzes the page content. If the user provides a screenshot, vision analysis is also applied.

### Mode C: Cross-Domain Research (Purpose-Driven)
Multi-vector research by cognitive task.

**Use when**: Starting a design project, need creative inspiration

**This is the breakthrough mode** - produces genuinely creative work.

---

## Archive Structure

```
archive/
+-- 2026/
|   +-- 01-january/
|   |   +-- raw/
|   |   |   +-- awwwards-2026-01-27.json
|   |   |   +-- siteinspire-2026-01-27.json
|   |   |   +-- thefwa-2026-01-27.json
|   |   +-- visual-analysis.json
|   |   +-- summary.md
|   +-- 02-february/
|       +-- ...
+-- archive-index.md
```

### File Descriptions

**raw/*.json** - Structured project data from RSS feeds (titles, URLs, categories, tags)
**visual-analysis.json** - Vision AI analysis results (colors, layouts, elements) — populated when user provides screenshots or URLs for visual analysis
**summary.md** - Monthly trend summary (LLM-optimized)
**archive-index.md** - 30-day rolling summary (<500 tokens)

---

## Best Practices

### For Creative Research

1. **Clarify cognitive tasks** before researching visuals
2. **Research outside obvious categories** (purpose over category)
3. **Extract Level 3-4 patterns** (interaction/cognitive, not visual)
4. **Synthesize with reasoning** (WHY each source is relevant)
5. **Challenge assumptions** from domain-specific research

### For Running Research Updates

1. **Run weekly** to maintain current data
2. **Review summary.md** after each update to verify quality
3. **Monitor archive size** - consider archiving old months after 6 months
4. **Validate outputs** before relying on summaries

### For Querying Insights

1. **Start with archive-index.md** for quick trends
2. **Ask specific questions** for better responses
3. **Request examples** to see real implementations
4. **Compare across time** to understand evolution
5. **Load monthly summaries** only when needed for deep dives

---

## Cognitive Task Examples

Common cognitive tasks that map to analogous domains:

| Cognitive Task | User is... | Analogous Domains |
|----------------|-----------|-------------------|
| **Rapid Gestalt Assessment** | Determining system health at a glance | Medical monitors, trading platforms, automotive dashboards |
| **Anomaly Detection** | Identifying what requires attention | Security ops, fraud detection, quality control |
| **Timeline/Progress** | Understanding sequence and what's next | Sports broadcasts, delivery tracking, video editing |
| **Progressive Disclosure** | Drilling from overview to detail | Developer tools, maps, email threads |
| **Decision Support** | Making a choice with confidence | Trading platforms, emergency dispatch, medical treatment |

Full catalog: `context/research-methodology/cognitive-task-catalog.md`

---

## Troubleshooting

### Vision Analysis Issues

**Problem**: Many images failed analysis
- Check API keys are set (ANTHROPIC_API_KEY, GOOGLE_API_KEY, etc.)
- Verify image files aren't corrupted
- Check image sizes (resize if > 5MB)
- Review timeout settings

### Research Quality Issues

**Problem**: Research feels generic or obvious
- Ensure cognitive tasks were identified (not just features)
- Verify multi-vector approach was used (not just category-matching)
- Check that Level 3-4 patterns were extracted (not just visual)
- Request more divergent sources

### RSS Feed Issues

**Problem**: Feed data is empty or incomplete
- Verify network connectivity
- Check that feed URLs are still valid (sites occasionally change feed paths)
- Review raw/*.json files to confirm data was captured
- Try running the recipe again — transient failures are common with feeds

---

## Configuration

### Vision Analysis Settings

Default providers (in order of fallback):
1. **Gemini Flash** - Fastest (3-10s), good quality
2. **Anthropic Claude** - Balanced (5-15s)
3. **OpenAI GPT-4** - Slowest (8-20s), highest quality

### Archive Retention

Default: Keep all data indefinitely
Recommended: Archive months older than 6 months to compressed storage

---

## Additional Resources

### Core Methodology
- **Creative Research Methodology**: `context/research-methodology/creative-research-methodology.md`
- **Cognitive Task Catalog**: `context/research-methodology/cognitive-task-catalog.md`
- **Pattern Abstraction Guide**: `context/research-methodology/pattern-abstraction-guide.md`
- **Cognitive Discovery Enhancement**: `context/research-methodology/cognitive-discovery-enhancement.md`

### Agents & Tools
- **Research Analyst Agent**: `agents/research-analyst.md`
- **Research Runner Agent**: `agents/research-runner.md`
- **Weekly Research Recipe**: `recipes/weekly-design-research.yaml`
- **Archive Index**: `context/archive-index.md`

### Skills
- **Image-Vision Skill**: `~/.amplifier/skills/robotdad/image-vision/SKILL.md`

---

**The Key Difference**: Design-intelligence now produces breakthrough creative work by researching PURPOSE (cognitive tasks) across domains, not just matching categories. This is the innovation that sets it apart.