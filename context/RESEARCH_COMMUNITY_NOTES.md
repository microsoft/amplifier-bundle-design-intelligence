# Design Research Capability - Community Notes

**Status:** Foundational implementation - significant opportunities for community improvement

This document outlines the current state of the design research capability and identifies areas where community contributions would be especially valuable.

---

## Current Implementation

### What's Working

- **Research agents** (research-runner, research-analyst) for data collection and analysis
- **RSS feed collection** from Awwwards, Siteinspire, and The FWA
- **Archive structure** for storing observations by date
- **Research-aware design agents** that can load archive-index.md on demand
- **Weekly research recipe** for automated trend data collection
- **Observed-expression directory** for metacognitive design knowledge
- **User-directed URL analysis** via web_fetch for on-demand site investigation

### Design Principles

- **RSS feeds over scraping** — We use publicly available RSS feeds as the intended syndication format. No headless browsers, no DOM scraping, no CSS selectors targeting third-party site structure.
- **User-directed visual analysis** — Screenshot analysis is available on-demand when users provide URLs or images. No automated visiting or screenshotting of external sites.
- **Privacy by default** — See PRIVACY.md for data handling details.

---

## Community Improvement Opportunities

### 1. Data Collection

**Current:** RSS feed parsing with web_fetch

**Opportunities:**
- [ ] **Structured RSS parsing** — Better XML/RSS parsing for richer metadata extraction
- [ ] **Additional RSS sources** — Landbook, CSS Design Awards, Behance (if RSS available)
- [ ] **API integration** — Use official APIs where available (some sites offer developer APIs)
- [ ] **Change detection** — Alert when RSS feed format changes
- [ ] **Feed validation** — Verify feed health and report stale/broken feeds

### 2. Vision Analysis

**Current:** User-directed screenshot analysis via image-vision

**Opportunities:**
- [ ] **Structured output** — Consistent JSON schema for visual analysis
- [ ] **Color extraction** — Automated palette extraction from user-provided images
- [ ] **Typography detection** — Font identification (if technically feasible)
- [ ] **Layout classification** — Automated categorization of layout patterns
- [ ] **Comparison analysis** — Track how specific design patterns evolve over time

### 3. Archive Management

**Current:** Manual archive structure with monthly summaries

**Opportunities:**
- [ ] **Automated indexing** — Better search across historical observations
- [ ] **Deduplication** — Detect when same site appears across sources
- [ ] **Tagging system** — Consistent taxonomy for categorizing observations
- [ ] **Archive rotation** — Automated cleanup of old data while preserving summaries
- [ ] **Export formats** — Generate reports in various formats (PDF, HTML, etc.)

### 4. Trend Analysis

**Current:** LLM-generated summaries from RSS feed data

**Opportunities:**
- [ ] **Quantitative tracking** — Count occurrences of specific patterns over time
- [ ] **Trend visualization** — Charts showing pattern evolution
- [ ] **Predictive insights** — Identify emerging vs. fading trends
- [ ] **Industry segmentation** — Track trends by industry vertical

### 5. Knowledge Base Enhancement

**Current:** typography-personalities.md as initial observed-expression document

**Opportunities:**
- [ ] **Color psychology** — What colors communicate in different contexts
- [ ] **Spacing expression** — How whitespace conveys meaning
- [ ] **Motion vocabulary** — Animation styles and their emotional impact
- [ ] **Layout narratives** — How structure tells stories
- [ ] **Research validation** — Cross-reference knowledge base with actual observations

### 6. Integration Improvements

**Current:** Agents load archive-index.md on demand

**Opportunities:**
- [ ] **Semantic search** — Query archive with natural language
- [ ] **Example retrieval** — "Show me sites like X" from archive
- [ ] **Automatic suggestions** — Surface relevant examples during design work
- [ ] **Reference linking** — Connect observations to knowledge base concepts

### 7. Recipe Enhancement

**Current:** Basic weekly-design-research.yaml recipe

**Opportunities:**
- [ ] **Incremental updates** — Only process new content since last run
- [ ] **Quality gates** — Validation steps before archiving
- [ ] **Notification hooks** — Alert on interesting findings
- [ ] **Scheduled execution** — Integration with cron/scheduling systems

---

## Technical Debt / Known Limitations

### Things That Need Improvement

1. **RSS parsing is basic** — Could benefit from dedicated XML parsing for richer metadata
2. **Vision analysis is prompt-only** — No structured parsing of vision outputs
3. **Archive index is static** — Needs manual regeneration; could be dynamic
4. **No error recovery** — Failed feed fetches don't have retry logic

### Architectural Decisions Open for Discussion

1. **Archive format** — Currently flat files; database might scale better
2. **Research freshness** — 30-day rolling window; configurable retention?
3. **Agent boundaries** — research-runner vs research-analyst split could be refined

---

## Contributing

### Quick Wins (Good First Issues)

- Improve RSS feed parsing for richer metadata
- Add more typography personalities to observed-expression
- Create templates for monthly summary format
- Add validation for archive JSON files

### Medium Effort

- Add official API integration for sites that offer one
- Create color-psychology.md in observed-expression
- Implement archive search functionality
- Add quantitative trend tracking

### Larger Projects

- Semantic search across research archive
- Visualization dashboard for trends
- Integration with design tool plugins

---

## Design Philosophy Alignment

This research capability follows the Amplifier design philosophy:

1. **Mechanism, not policy** — Provide research infrastructure; let users decide how to use it
2. **Ruthless simplicity** — Start simple, add complexity only when justified
3. **Composable** — Research components should work independently
4. **Observable** — Research process should be transparent and debuggable
5. **Respectful** — Use public syndication formats (RSS), not automated scraping

When contributing, prefer:
- Simple implementations that work over complex ones that might
- Clear documentation over clever code
- Explicit behavior over implicit magic
- Public APIs and feeds over DOM scraping

---

## Questions for Community Discussion

1. **How often should research run?** Weekly? Daily? On-demand only?
2. **What sources are most valuable?** Focus on few high-quality or many varied?
3. **How much historical data to keep?** Rolling window vs. full archive?
4. **Should trend analysis be automated or human-curated?**
5. **Integration depth** — How tightly should research connect to design agents?

---

*This document should evolve as the community contributes. Update it when making significant changes to the research capability.*
