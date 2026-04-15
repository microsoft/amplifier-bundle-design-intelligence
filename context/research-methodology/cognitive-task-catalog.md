# Cognitive Task Catalog

> **Purpose**: Quick reference for mapping problems to analogous domains through cognitive task analysis—works for visual design, engineering, product, and strategy.

---

## How to Use This Catalog

1. **Identify the cognitive task or system problem** that needs solving
2. **Look up analogous domains** where this challenge is well-solved
3. **Research across those domains** for proven patterns
4. **Abstract the interaction/cognitive/principle patterns** (Level 3-4, not implementation)
5. **Synthesize with reasoning** about why each source is relevant

**This catalog works for ANY domain**: visual design, engineering, product, strategy, operations.

---

## Visual Design & User Experience Tasks

### Rapid Gestalt Assessment
**Definition**: Determining overall system health/status at a glance without reading details.

**Analogous Domains**:
- Hospital patient monitors (vital signs overview)
- Fitness dashboards (daily health check)
- Server monitoring (infrastructure health)
- Trading platforms (portfolio status)
- Automotive dashboards (vehicle status)
- Smart home apps (home status overview)
- Weather apps (conditions at a glance)

**Key Patterns**:
- Color coding (semantic, not decorative)
- Size/weight indicating importance
- Spatial grouping by criticality
- Progressive disclosure from glance → detail

---

### Anomaly Detection
**Definition**: Identifying what requires attention among many data points.

**Analogous Domains**:
- Security operations centers (threat detection)
- Fraud detection dashboards (transaction monitoring)
- Quality control interfaces (defect identification)
- Air traffic control (conflict detection)
- Medical diagnostics (test result interpretation)
- Social media moderation (content flagging)
- Network monitoring (anomaly alerts)

**Key Patterns**:
- Visual outliers (deliberately breaking patterns)
- Attention-directing mechanisms (animation, color, position)
- Contextual comparison (what's normal vs. current)
- Confidence indicators (how certain is the anomaly)

---

### Timeline/Progress Understanding
**Definition**: Understanding where we are in a sequence and what comes next.

**Analogous Domains**:
- Project management tools (Gantt charts, sprints)
- Video editing software (timeline navigation)
- Music DAWs (track arrangement)
- Sports broadcasts (game progress, scoring timeline)
- Recipe apps (step-by-step progress)
- Delivery tracking (package journey)
- Educational software (course progress)

**Key Patterns**:
- Past/present/future visual distinction
- Milestone markers
- Current position emphasis
- Next action clarity
- Alternative paths/branches

---

### Progressive Disclosure
**Definition**: Drilling from overview to detail without losing context.

**Analogous Domains**:
- Developer tools (collapsible code, stack traces)
- Complex configuration UIs (nested settings)
- Educational software (scaffolded learning)
- Maps applications (zoom levels)
- File system browsers (folder hierarchies)
- Email clients (thread expansion)
- News aggregators (headline → article)

**Key Patterns**:
- Persistent context (breadcrumbs, persistent headers)
- Smooth transitions (maintain spatial relationships)
- Escape hatches (back, close, collapse)
- Preview mechanisms (hover, peek)

---

### Decision Support
**Definition**: Having the right information to make a confident decision.

**Analogous Domains**:
- Trading platforms (buy/sell decisions)
- Military command & control (tactical decisions)
- Emergency dispatch (resource allocation)
- Medical treatment interfaces (diagnosis/treatment)
- E-commerce checkout (purchase decisions)
- Flight booking (itinerary selection)
- Insurance comparison tools (plan selection)

**Key Patterns**:
- Comparison views (side-by-side)
- Confidence indicators (how good is this data?)
- Consequence preview (what happens if I do this?)
- Reversibility cues (can I undo this?)
- Time pressure indicators (decision urgency)

---

### High Information Density
**Definition**: Displaying maximum relevant information in limited space without overwhelming.

**Analogous Domains**:
- Bloomberg Terminal (financial data density)
- Air traffic control (spatial information density)
- Broadcast production (technical monitoring)
- Spreadsheet applications (tabular density)
- IDE interfaces (code + tools)
- CAD software (technical drawings)
- Scientific visualization (data-rich charts)

**Key Patterns**:
- Typographic hierarchy (not just size)
- Strategic color use (semantic, not decorative)
- Spatial grouping (white space = structure)
- Expert-optimized layouts (assumes learning investment)

---

### Real-Time Monitoring
**Definition**: Tracking continuously changing data with awareness of change rate and direction.

**Analogous Domains**:
- Stock tickers (price movement)
- Live sports scores (game state)
- Social media feeds (activity streams)
- System logs (event streams)
- Heart rate monitors (vital trends)
- Traffic maps (congestion changes)
- Cryptocurrency exchanges (market movement)

**Key Patterns**:
- Change indicators (arrows, delta values, trends)
- Rate of change (not just current value)
- Historical context (where we came from)
- Auto-refresh patterns (when/how to update)
- Alert thresholds (when to interrupt)

---

### Comparative Analysis
**Definition**: Understanding similarities and differences between multiple entities.

**Analogous Domains**:
- Product comparison tools (feature matrices)
- A/B testing dashboards (variant comparison)
- Medical imaging (before/after, side-by-side)
- Code diff tools (change identification)
- Design mockup review (version comparison)
- Sports statistics (player comparisons)
- Financial statements (period-over-period)

**Key Patterns**:
- Aligned layouts (same structure for comparison)
- Difference highlighting (what's changed/different)
- Normalization (apples-to-apples metrics)
- Linked interactions (scroll/hover in sync)

---

### Exploration/Discovery
**Definition**: Finding information when you don't know exactly what you're looking for.

**Analogous Domains**:
- Music streaming (discovery playlists)
- E-commerce browsing (category exploration)
- Museum exhibits (spatial discovery)
- Gaming open worlds (environmental exploration)
- Social platforms (feed exploration)
- Recipe discovery (ingredient/technique browsing)
- Travel planning (destination exploration)

**Key Patterns**:
- Serendipitous recommendations
- Multiple entry points
- Progressive refinement (filtering, not rigid search)
- Spatial relationships (nearby, related, similar)
- Low-commitment preview

---

### Focus/Flow State
**Definition**: Minimizing distractions to enable deep work or sustained attention.

**Analogous Domains**:
- Writing apps (distraction-free modes)
- Meditation apps (focus timers)
- Gaming (immersive HUDs)
- Reading apps (reader modes)
- Music production (mixer focus)
- Code editors (zen mode)
- Presentation tools (presenter view)

**Key Patterns**:
- Deliberate reduction (hiding non-essential)
- Single-task focus (one thing at a time)
- Ambient awareness (subtle status indicators)
- Return to full UI when needed

---

### Status Communication
**Definition**: Letting users know what's happening, especially during waits or processes.

**Analogous Domains**:
- Food delivery apps (order status)
- Installation wizards (progress indicators)
- Ride-sharing apps (driver location)
- Package tracking (shipment journey)
- Upload/download managers (transfer progress)
- Form submission (processing states)
- Build tools (compilation progress)

**Key Patterns**:
- Current state clarity
- Expected duration (time remaining)
- What's happening now
- What's next
- Ability to cancel/interrupt

---

### Error Recovery
**Definition**: Understanding what went wrong and how to fix it.

**Analogous Domains**:
- Medical test results (abnormal results with context)
- Customer service scripts (issue resolution)
- Automotive diagnostics (check engine codes)
- Developer tools (error messages, stack traces)
- Form validation (inline error messages)
- 404 pages (dead end navigation)
- Payment failures (transaction errors)

**Key Patterns**:
- What went wrong (specific, not generic)
- Why it matters (consequence)
- How to fix it (specific action)
- Context (what's normal, how far off are we)
- Prevention (how to avoid in future)

---

## Engineering & System Design Problems

### Fairness Under Load
**Problem**: Allocate resources fairly when demand exceeds capacity.

**Analogous Domains**:
- Highway traffic metering (entry control maintains flow)
- Electrical grid load balancing (distribute demand)
- Airport runway scheduling (fair allocation of slots)
- Restaurant seating systems (queue management)
- CPU scheduling in operating systems (time slicing)
- Water distribution systems (pressure regulation)

**Key Patterns**:
- Entry-point metering (control at boundary)
- Token-based allocation (pre-authorized units)
- Priority tiers (important vs routine)
- Queue fairness (FIFO with anti-starvation)

**Engineering Transfer**: API rate limiting, database connection pools, job queues

---

### Failure Isolation
**Problem**: Prevent failures from cascading through the system.

**Analogous Domains**:
- Ship watertight compartments (contain flooding)
- Electrical circuit breakers (isolate faults)
- Fire doors in buildings (contain spread)
- Immune system (inflammation localizes infection)
- Forest fire breaks (prevent spread)
- Network segmentation (VLAN isolation)

**Key Patterns**:
- Bulkheads (physical/logical isolation)
- Fast failure detection (fail quickly, not slowly)
- Graceful degradation (partial service > none)
- Independent failure domains

**Engineering Transfer**: Circuit breakers, microservice boundaries, database sharding

---

### State Transformation Safety
**Problem**: Change system state without downtime or data loss.

**Analogous Domains**:
- Aircraft maintenance (replace components on flying plane)
- Surgical procedures (operate on living patient)
- Live TV equipment changes (switch during broadcast)
- Ship repairs at sea (fix without dry dock)
- Highway construction (rebuild while traffic flows)
- Building renovations (occupied structures)

**Key Patterns**:
- Blue-green deployment (parallel old/new)
- Staged procedures (reversible steps)
- Safety checkpoints (go/no-go gates)
- Maintained redundancy (backup always available)

**Engineering Transfer**: Database migrations, zero-downtime deploys, feature flags

---

### Distributed Coordination
**Problem**: Coordinate without central authority or single point of failure.

**Analogous Domains**:
- Ant colonies (local signals, emergent behavior)
- Market economies (price signals coordinate allocation)
- Immune systems (distributed threat detection)
- Bee swarms (consensus through voting)
- Flock behavior (local rules, global patterns)
- Fungal networks (resource distribution)

**Key Patterns**:
- Gossip protocols (peer-to-peer communication)
- Emergent consensus (local decisions, global agreement)
- Stigmergy (coordinate through environment)
- No single point of failure

**Engineering Transfer**: Distributed databases, service mesh, blockchain consensus

---

### Abuse & Threat Prevention
**Problem**: Detect and stop malicious behavior in real-time.

**Analogous Domains**:
- Immune systems (pathogen recognition)
- Fraud detection (anomaly patterns)
- Security operations (threat intelligence)
- Spam filters (content analysis)
- Quality control (defect detection)
- Border security (threat screening)

**Key Patterns**:
- Pattern recognition (known bad signatures)
- Anomaly detection (deviation from normal)
- Adaptive response (learn from attacks)
- Defense in depth (multiple layers)

**Engineering Transfer**: Rate limiting, fraud detection, DDoS protection, input validation

---

### Graceful Degradation
**Problem**: Maintain service under stress or partial failure.

**Analogous Domains**:
- Electrical grids (brownout prevents blackout)
- Aircraft redundancy (multiple backup systems)
- Human body under stress (prioritize vital organs)
- Military operations (mission-critical focus)
- Emergency services (triage prioritization)
- Traffic management (essential routes first)

**Key Patterns**:
- Load shedding (drop low-priority work)
- Priority preservation (critical functions first)
- Partial availability (some service > none)
- Resource reservation (guarantee for critical)

**Engineering Transfer**: Backpressure, circuit breakers, priority queues, quota systems

---

### Observability & Debugging
**Problem**: Understand system behavior and diagnose issues in production.

**Analogous Domains**:
- Medical diagnostics (symptoms → root cause)
- Aircraft black boxes (post-incident analysis)
- Scientific experiments (hypothesis testing)
- Detective investigation (evidence gathering)
- Automotive diagnostics (sensor data interpretation)
- Quality control (defect root cause analysis)

**Key Patterns**:
- Comprehensive instrumentation (measure everything)
- Correlation IDs (trace across boundaries)
- Time-series analysis (trends over time)
- Hypothesis-driven debugging (test theories)

**Engineering Transfer**: Logging, metrics, tracing, profiling, error tracking

---

## Product & User Engagement Problems

### Progressive Learning & Onboarding
**Problem**: Teach complex functionality without overwhelming users.

**Analogous Domains**:
- Video game tutorials (learn by doing)
- Musical instrument pedagogy (progressive difficulty)
- Cooking classes (guided then independent)
- Driver's education (simulator before real stakes)
- Martial arts (belt progression)
- Language learning (scaffolded complexity)

**Key Patterns**:
- Safe exploration (sandbox environments)
- Immediate feedback (fast learning loops)
- Scaffolded independence (guidance → autonomy)
- Progressive complexity (easy → hard)

**Product Transfer**: Feature onboarding, tutorial flows, in-app guidance

---

### Habit Formation & Retention
**Problem**: Keep users engaged and returning over time.

**Analogous Domains**:
- Physical therapy (gradual progression)
- Fitness programs (visible progress)
- Meditation practices (daily habit building)
- Language learning (spaced repetition)
- Musical practice (consistent improvement)
- Therapy programs (behavioral change)

**Key Patterns**:
- Streak tracking (consistency rewards)
- Visible progress (milestone markers)
- Spaced reinforcement (reminders over time)
- Social accountability (peer pressure)

**Product Transfer**: Daily active usage, notification strategy, progress systems

---

### Feature Discovery
**Problem**: Help users discover capabilities they don't know exist.

**Analogous Domains**:
- Museum exhibits (self-guided discovery)
- Video game exploration (environmental clues)
- Recipe discovery (browsing not searching)
- Music recommendations (algorithmic + editorial)
- Travel planning (inspiration browsing)
- Book recommendations (related items)

**Key Patterns**:
- Contextual suggestions (right time/place)
- Low-commitment preview (try before commit)
- Serendipitous exposure (unexpected finds)
- Progressive revelation (unlock over time)

**Product Transfer**: Feature tips, contextual help, recommendation engines

---

### Confidence Building
**Problem**: Help users feel successful and capable with your product.

**Analogous Domains**:
- Martial arts belt systems (earned progression)
- Gaming achievement systems (visible success)
- Fitness programs (celebrate milestones)
- Educational scaffolding (gradual difficulty)
- Cooking recipe progression (easy → advanced)
- Music lessons (mastery stages)

**Key Patterns**:
- Early wins (quick success)
- Clear progression (path forward)
- Earned status (achievements persist)
- Failure as learning (safe to fail)

**Product Transfer**: Onboarding success, progress indicators, achievement systems

---

### Social Proof & Trust
**Problem**: Build confidence through evidence others succeeded.

**Analogous Domains**:
- Restaurant popularity (line out door)
- Book bestsellers (charts and reviews)
- Academic citations (peer validation)
- Crowdfunding (backer counts)
- Social media (follower counts)
- App store ratings (star reviews)

**Key Patterns**:
- Aggregate evidence (many users)
- Peer similarity (people like me)
- Expert endorsement (authority figures)
- Usage indicators (active community)

**Product Transfer**: Reviews, testimonials, user counts, case studies

---

## Strategy & Operations Problems

### Process Optimization
**Problem**: Improve efficiency without sacrificing quality.

**Analogous Domains**:
- Manufacturing (lean production)
- Restaurant kitchens (mise en place)
- Surgical procedures (standardized protocols)
- Formula 1 pit stops (optimized workflows)
- Emergency response (practiced procedures)
- Assembly lines (continuous improvement)

**Key Patterns**:
- Waste elimination (unnecessary steps)
- Parallel processing (concurrent tasks)
- Standardization (repeatable process)
- Continuous measurement (metrics-driven)

**Strategy Transfer**: Workflow design, team processes, operational efficiency

---

### Resource Allocation
**Problem**: Distribute limited resources across competing needs.

**Analogous Domains**:
- Hospital triage (urgency prioritization)
- Military logistics (supply chain)
- Portfolio investment (risk distribution)
- Time management (priority matrix)
- Budget allocation (ROI optimization)
- Project staffing (skill matching)

**Key Patterns**:
- Priority frameworks (urgent vs important)
- Constraint identification (bottlenecks)
- ROI analysis (value per resource)
- Dynamic reallocation (adapt to change)

**Strategy Transfer**: Budget planning, team allocation, investment decisions

---

### Change Management
**Problem**: Transform organization or process without disruption.

**Analogous Domains**:
- Biological evolution (gradual adaptation)
- Urban planning (phased development)
- Ship-of-Theseus (continuous replacement)
- Software refactoring (incremental improvement)
- Ecosystem succession (natural progression)
- Building renovations (occupied upgrades)

**Key Patterns**:
- Gradual transition (not big bang)
- Parallel old/new (overlap period)
- Reversible steps (rollback capability)
- Communication cadence (stakeholder updates)

**Strategy Transfer**: Organizational change, process transformation, cultural shifts

---

## Using This Catalog

### For ANY Domain (Design, Engineering, Product, Strategy)

**Step 1: Identify Your Core Challenge**
- Visual/Product: What cognitive task does the user perform?
- Engineering: What system problem must be solved?
- Strategy: What coordination or optimization is needed?

**Step 2: Look Up Analogous Domains**
- Don't limit to your category
- Find where this challenge is solved BEST (often unexpected domains)
- Prefer mature domains with decades of refinement

**Step 3: Research Cross-Domain**
- 20% domain-specific (know conventions)
- 50% purpose-driven (proven patterns from analogous domains)
- 30% divergent (deliberately unexpected sources)

**Step 4: Extract Level 3-4 Patterns**
- Skip implementation details (Level 1-2)
- Focus on interaction/architecture patterns (Level 3)
- Seek universal principles (Level 4)

**Step 5: Synthesize with Reasoning**
- WHY is each pattern relevant to your context?
- WHAT is the transferable principle?
- HOW does it need to be adapted?

---

## Expanding This Catalog

As you encounter new problems or discover excellent analogous domains:
1. Add them to this catalog
2. Document why the domain is relevant
3. Identify the key patterns that transfer
4. Note what makes this domain particularly strong at solving this problem
5. Show examples across multiple domains (visual, engineering, product, strategy)

**This catalog is universal** - it works for any domain where you're making purposeful decisions about how things should work.
