# Cognitive Discovery Enhancement

> **Purpose**: Extends the standard discovery process to capture cognitive tasks that feed creative research methodology.

---

## When to Use This

After completing **Layer 1: Purpose & Intent** in discovery, and **before** moving to Layer 2 characteristics, add this cognitive decomposition layer.

This bridges discovery → research by capturing the information research agents need to find purpose-driven inspiration.

---

## Layer 1.5: Cognitive Task Decomposition

**Goal**: Identify the underlying cognitive tasks users perform, not just what the system does.

**Position in flow**: After Layer 1 (Purpose & Intent), before Layer 2 (Key Characteristics)

**Why this matters**: Research by cognitive task (not category) produces breakthrough creative work. To research effectively, we need to know WHAT THE USER'S BRAIN IS DOING.

---

## Essential Questions

### 1. Cognitive Tasks
**Ask**: "What cognitive tasks does the user perform when using this?"

**Not asking for**: Features, functions, capabilities
**Asking for**: Mental operations, judgments, decisions

**Examples**:
- ❌ "They view a dashboard" (feature)
- ✅ "They assess overall health at a glance" (cognitive task: rapid gestalt assessment)

- ❌ "They get notifications" (feature)
- ✅ "They identify what needs attention among many items" (cognitive task: anomaly detection)

- ❌ "They see a timeline" (feature)
- ✅ "They understand where we are in a sequence" (cognitive task: timeline/progress understanding)

**Prompt the user**: "Forget features for a moment. What is your user's brain actually doing? What judgments are they making? What understanding are they forming?"

---

### 2. Decision Points
**Ask**: "What decisions do they make while using this?"

**Examples**:
- Go/no-go decisions (launch? abort? approve?)
- Prioritization decisions (what to focus on first?)
- Investigation decisions (dig deeper? move on?)
- Action decisions (what to do next?)
- Confidence decisions (how certain am I?)

**Why this matters**: Decision-making patterns indicate which analogous domains to research (trading platforms, emergency dispatch, medical triage, etc.)

---

### 3. Information States
**Ask**: "What states can the information be in from the user's perspective?"

**Not the technical states** - the cognitive states the user perceives:
- Normal (everything fine)
- Alert (attention needed)
- Critical (urgent action required)
- Exploratory (discovering what's possible)
- Monitoring (watching for change)
- Comparing (understanding differences)

**Why this matters**: Different cognitive states require different design patterns.

---

### 4. Emotional & Contextual State
**Ask**: "What's the user's emotional state and context when they use this?"

**Dimensions to explore**:
- **Stress level**: Calm, focused, stressed, urgent, crisis
- **Expertise**: Novice, learning, competent, expert
- **Frequency**: First time, occasional, daily, continuous
- **Attention**: Deep focus, monitoring, casual, distracted
- **Risk**: Low stakes, medium stakes, high stakes, critical

**Examples**:
- Healthcare dashboard during emergency → Stressed, expert, high stakes, urgent
- Onboarding flow for new user → Uncertain, novice, low stakes, focused
- Trading platform → Focused, expert, high stakes, continuous monitoring

**Why this matters**: Emotional state determines interaction patterns (calm exploration vs. rapid scanning vs. stress resilience)

---

## Output Format

After capturing cognitive tasks, document as:

```markdown
## Cognitive Task Analysis

### Primary Tasks
1. **[Task Name]** - [Description]
   - Context: [When/how often]
   - Importance: [High/Medium/Low]

2. **[Task Name]** - [Description]
   - Context: [When/how often]
   - Importance: [High/Medium/Low]

### Decision Points
- [Decision type]: [What they're deciding]
- [Decision type]: [What they're deciding]

### Information States
- [State]: [What this means to the user]
- [State]: [What this means to the user]

### Emotional Context
- **Stress level**: [Description]
- **Expertise**: [Description]
- **Frequency**: [Description]
- **Attention**: [Description]
- **Risk level**: [Description]

### Research Implications
Based on these cognitive tasks, research should explore:
- [Analogous domain 1] - [Why relevant]
- [Analogous domain 2] - [Why relevant]
- [Analogous domain 3] - [Why relevant]
```

---

## Example: Mission Launch Dashboard

### User Request
"Design a dashboard for tracking rocket launch status and mission progress."

### Layer 1: Purpose & Intent (Standard Discovery)
- **What**: Public-facing dashboard showing launch schedules and mission updates
- **Why**: Keep public informed and engaged with space program
- **For Whom**: Space enthusiasts, media, general public
- **Success**: Drives engagement, reduces support questions, increases transparency

### Layer 1.5: Cognitive Task Analysis (NEW)

**Primary Cognitive Tasks**:
1. **Rapid Gestalt Assessment** - "Is the launch on schedule at a glance?"
   - Context: Checking throughout the day
   - Importance: HIGH - Primary use case

2. **Anomaly Detection** - "Did something change or go wrong?"
   - Context: Monitoring during critical windows
   - Importance: HIGH - Drives engagement

3. **Timeline Understanding** - "Where are we in the launch sequence?"
   - Context: T-minus countdown periods
   - Importance: HIGH - Creates narrative

4. **Progressive Disclosure** - "Let me drill into details about this mission"
   - Context: After initial glance, for engaged users
   - Importance: MEDIUM - Secondary engagement

**Decision Points**:
- "Should I pay attention now?" (urgency assessment)
- "Is this interesting enough to share?" (social sharing)
- "Do I need to check back soon?" (return behavior)

**Information States**:
- Nominal: All systems go, on schedule
- Hold: Temporary pause, reason given
- Scrubbed: Postponed, new time announced
- In-flight: Active mission underway
- Anomaly: Something unexpected happened

**Emotional Context**:
- **Stress level**: Low to medium (not life-critical, but fans are passionate)
- **Expertise**: Mixed (hardcore fans + casual observers)
- **Frequency**: Varies (daily checks for fans, occasional for casual)
- **Attention**: Casual monitoring with alert-driven deep dives
- **Risk level**: Low personal risk, but high emotional investment

### Research Implications

Now research can target:
- **Rapid gestalt assessment**: Hospital patient monitors, trading platforms, weather apps, automotive dashboards
- **Anomaly detection**: Security ops centers, social media moderation, fraud detection
- **Timeline understanding**: Sports broadcasts, delivery tracking, video editing timelines
- **Progressive disclosure**: News sites, developer tools, email threads

**NOT researching**: Other aerospace dashboards (that's category-matching, not purpose-driven)

---

## Integration with Standard Discovery Flow

**Complete flow**:
1. **Layer 1**: Purpose & Intent (standard discovery)
2. **Layer 1.5**: Cognitive Task Analysis (NEW - this enhancement)
3. **Layer 2**: Key Characteristics (standard discovery, informed by tasks)
4. **Layer 3**: Context & Appropriateness (standard discovery)
5. **Layer 4**: Contextual Adaptation (standard discovery)

**Handoff to research**: The cognitive task analysis becomes input for purpose-driven research (see `creative-research-methodology.md`)

---

## Tips for Effective Cognitive Task Capture

### Do
✅ Focus on mental operations, not features
✅ Ask "What is their brain doing?"
✅ Identify decisions, not just information display
✅ Capture emotional/contextual state
✅ Think about analogous domains immediately

### Don't
❌ List features ("they see a chart")
❌ Describe technical implementation
❌ Stay in the obvious domain category
❌ Skip the "why" behind tasks
❌ Forget to capture emotional state

---

## Quick Reference: Common Cognitive Tasks

Use this as a prompt to help users identify their cognitive tasks:

| Cognitive Task | User is... |
|----------------|-----------|
| **Rapid Gestalt Assessment** | Determining system health at a glance |
| **Anomaly Detection** | Identifying what requires attention |
| **Timeline/Progress** | Understanding sequence and what's next |
| **Progressive Disclosure** | Drilling from overview to detail |
| **Decision Support** | Making a choice with confidence |
| **Real-Time Monitoring** | Tracking continuously changing data |
| **Comparative Analysis** | Understanding similarities/differences |
| **Exploration** | Discovering without specific goal |
| **Focus/Flow State** | Maintaining sustained attention |
| **Error Recovery** | Understanding and fixing problems |

See `cognitive-task-catalog.md` for full list with analogous domains.
