# Guide to Identifying Agentic AI Use Cases
## Using Value Stream Mapping (VSM) and Measurable ROI

[← Back to Main Guide](./README.md)

---

## Table of Contents

1. [Introduction](#introduction)
2. [Value Stream Mapping Basics](#value-stream-mapping-basics)
3. [Step-by-Step Process](#step-by-step-process)
4. [Templates & Tools](#templates--tools)
5. [Next Steps](#next-steps)

---

## Introduction

### Purpose of this Guide

This guide is a **practical playbook** to:

- Use **Value Stream Mapping (VSM)** to understand how value flows through a process
- Identify **"agentic hotspots"** where agentic AI can:
  - Improve **value** and **progress** (outcomes delivered)
  - Increase **effectiveness** (quality, right-first-time)
  - Boost **efficiency** and **productivity** (time, cost, throughput)
  - Strengthen **compliance** (controls, audit trails, regulatory alignment)
- Tie each potential use case to a **simple, explicit ROI estimate**
- Decide **when agentic AI is appropriate** vs when **simple scripts or RPA** are better

You can use this as a **workshop guide** with business, operations, and technology stakeholders.

---

### What Is Agentic AI (In Simple Terms)?

**Agentic AI** refers to AI systems that don't just answer a single question but can:

- **Operate in an environment** (systems, APIs, documents, workflows)
- **Use tools** (search, update records, trigger workflows, send emails, generate documents)
- **Pursue goals over multiple steps** (plan, act, observe results, adjust)
- **Collaborate with humans** (ask for clarification, request approvals, escalate)

Instead of being a passive assistant, an agent is more like a **junior digital colleague**: it can reason, observe, decide, and act within well-defined constraints.

---

## Value Stream Mapping Basics

### What Is a Value Stream?

A **value stream** is the **end-to-end set of activities** an organization performs to deliver value to a customer (internal or external).

**Examples:**

- "Customer loan origination" – from application to approval/decline and customer notification
- "AML investigation and reporting" – from anomaly detection to regulatory report submission
- "Incident to resolution" – from ticket creation to problem remediation and closure
- "Order-to-cash" – from customer order to payment received

**Key idea:** We are not mapping **departments**; we are mapping **flows of value**.

---

### What Is Value Stream Mapping?

**Value Stream Mapping (VSM)** is a visual technique to:

- Show **every step** in the value stream
- Make **time** visible:
  - Processing time (when work is being done)
  - Waiting time (when work is idle in queues)
- Show **information flow**:
  - Where requests, approvals, and decisions travel
- Reveal **waste, friction, and failure modes**:
  - Rework, errors, bottlenecks, unnecessary handoffs

The outcome is a **map** of how value flows from trigger to final outcome, and where it gets stuck, delayed, or distorted.

---

### Core VSM Components

A simple value stream map typically includes:

#### 1. Timeline
- Sequence of steps from **Trigger** to **Done**
- For each step:
  - **Processing time** (how long active work takes)
  - **Waiting time** (queues, approvals, handoffs)

#### 2. Process Steps
- Step name (e.g., "Review documents", "Triage alert", "Draft report")
- Actor(s):
  - Roles or teams, not individuals (e.g., "KYC analyst", "Ops agent", "Batch job")
- Inputs and outputs:
  - Documents, data, decisions, approvals

#### 3. Information Flow
- How instructions and data move:
  - Requests, approvals, tickets, emails, messages, API calls
- Systems used:
  - CRM, core banking, ticketing, email, spreadsheets, shared drives, etc.

#### 4. Performance & Health Indicators
- Lead time (total time from start to finish)
- Touch time (sum of active work time)
- Work-in-progress (WIP)
- Error rate, rework rate
- SLA compliance, regulatory findings, customer satisfaction

---

### Why VSM Is Reliable for Finding Agentic AI Use Cases

VSM is powerful for agentic AI discovery because it:

**1. Exposes end-to-end reality**, not just isolated tasks  
Agentic AI rarely adds the most value on a single microtask; it shines when it can **coordinate multiple steps and tools**. VSM reveals where coordination and orchestration actually happen.

**2. Makes bottlenecks and waste visible**  
- Long waiting times → opportunities for agents to **chase status**, **auto-progress work**, or **pre-stage decisions**
- Rework and errors → opportunities for agents to **validate inputs**, **cross-check data**, and **enforce policies**

**3. Highlights cognitive load and complexity**  
Wherever humans must:
- Search across many systems
- Apply complex rules
- Interpret messy information
- Perform multi-step reasoning

…you likely have a candidate for **agentic intelligence + tool use**.

**4. Connects directly to measurable outcomes**  
Because VSM tracks **time, throughput, errors, and compliance**, any agentic AI intervention can be tied back to:
- Reduced lead time
- Reduced cost per case
- Reduced errors or SLA breaches
- Increased throughput or revenue capacity

**5. Aligns business, ops, and technology**  
VSM is visual and intuitive. Business and technical teams can point to the **same map** and agree:
- "This is painful"
- "This is slow"
- "This is risky"

That shared view makes agentic AI discussions concrete and grounded in reality.

---

## Step-by-Step Process

### Step 1 – Prepare the Ground

**Goal:** Agree on scope, purpose, and metrics.

#### 1. Choose a value stream
Pick one **end-to-end flow**, not a department:
- ✅ Example: "AML investigation and reporting"
- ❌ Not: "Compliance department tasks"

#### 2. Define the boundaries
- **Trigger:** What starts the stream?
  - e.g., "Suspicious transaction anomaly detected"
- **Final outcome:**
  - e.g., "Regulatory report submitted and acknowledged"
- **Customer (internal/external):**
  - e.g., "Regulator", "Risk management function", "End customer"

#### 3. Define high-level metrics (stream level)
Pick **1–3 primary metrics** that matter most:

- **Value / Progress**
  - Cases completed per month, volume processed, revenue per case
- **Effectiveness / Quality**
  - Right-first-time %, false positive/negative rate, rework
- **Efficiency / Productivity**
  - Lead time, touch time, throughput, cost per case
- **Compliance / Risk**
  - SLA breaches, audit findings, policy violations, fines

These become your **baseline** for later ROI discussions.

---

### Step 2 – Map the Current Value Stream

Create a simple left-to-right map of the process.

For each step:

1. **Name of step**
   - Example: "Collect missing customer documents"

2. **Actor(s)**
   - e.g., "KYC analyst", "AML investigator", "Automated detection engine"

3. **Systems / Tools**
   - e.g., "Core banking", "Case management system", "Email", "Shared drive"

4. **Timing**
   - **Processing time:** How long the person/agent is actively working
   - **Waiting time:** Queues, delays, approvals, "waiting on someone else"
   - Use approximate values if needed: e.g., "Processing: 10 min; Waiting: 1–2 days"

5. **Inputs & Outputs**
   - Inputs: Alerts, forms, documents, structured data
   - Outputs: Decisions, approvals, next-step triggers, reports

6. **Quality & Friction**
   - Rework (how often does it come back?)
   - Errors or disputes
   - Escalations, exceptions, manual overrides

**💡 Tip:** Don't chase perfection. A "good enough" current-state map is more valuable than a "perfect but never finished" one.

---

### Step 3 – Mark Agentic Hotspots

Now, overlay an **agentic AI lens** and mark steps where an agent could realistically help.

Look for steps with one or more of these characteristics:

#### 3.1 High cognition + multi-step + tool use

People must:
- Look up data in multiple systems
- Interpret complex rules or policies
- Combine structured and unstructured information to decide
- Manually coordinate 3+ steps in different tools

> **Agentic fit:** A goal-driven agent that can **search**, **analyze**, **reason**, and **take actions** via tools.

---

#### 3.2 Many handoffs and status chasing

Frequent:
- "Did you update this?"
- "What's the status?"
- "Who owns this now?"

The process spends a lot of time waiting for someone to:
- Update a ticket
- Move a case forward
- Confirm a small piece of information

> **Agentic fit:** An **orchestrator agent** that tracks state, updates systems, and sends prompts/notifications.

---

#### 3.3 Data & document heavy steps

- Reading long PDFs, emails, forms
- Extracting key fields
- Validating information
- Comparing multiple documents or systems

> **Agentic fit:** A **document understanding + validation agent** that uses extraction tools, retrieval, and rules to prepare or validate work before humans spend time on it.

---

#### 3.4 Monitoring & compliance heavy areas

Checking if:
- Policies are followed per case
- All required steps are completed
- Documentation is complete for audit

Producing:
- Logs, trails, reports, dashboards

> **Agentic fit:** A **watcher/monitor agent** that observes logs/events and compiles compliance evidence or alerts.

---

#### 3.5 High-volume, repetitive customer interactions

- Similar questions, long scripts, and data lookups
- Standard decisions with clear guardrails
- Frequent cut-and-paste between systems

> **Agentic fit:** A **frontline assistant agent** (with human-in-the-loop) that can handle first drafts, responses, or case triage.

Mark these steps on the map with a **distinct color or icon** – these are your **agentic hotspots**.

---

### Step 4 – Turn Hotspots into Structured Use Cases

For each hotspot, create a **1-page use case card** using the [Use Case Card Template](./template-use-case-card.md).

#### Key elements:

**Basic Information**
- Use case name
- Location in value stream
- Business owner/sponsor

**Agent Role** (Agent → Environment → Tools → Goals)
- **Environment:** Systems and data it can see
- **Context:** Policies, regulations, risk thresholds, SLAs, playbooks
- **Tools:** Read/write actions available
- **Goals:** What "success" looks like

**Current vs Target Performance**
- Focus on the **subset of the stream** this agent touches
- Define local metrics with baseline and targets

---

### Step 5 – Tie Each Use Case to Measurable ROI

Use the [ROI Estimation Template](./template-roi-estimation.md) to calculate:

#### Benefit Buckets

1. **Efficiency / Productivity (Cost Savings)**
   - Time saved per case × number of cases × cost per hour

   **Example:**
   - 20 minutes saved per case
   - 10,000 cases/year
   - Loaded cost per analyst hour: $40
   - Annual efficiency benefit: `20/60 × 10,000 × $40 = $133,333`

2. **Effectiveness / Quality**
   - Fewer errors → fewer corrections → additional time saved
   - Fewer downstream incidents → lower operational strain

3. **Compliance / Risk**
   - Fewer SLA breaches → quantify avoided penalties
   - Stronger documentation → lower risk of fines

4. **Value / Revenue / Progress**
   - Increased throughput capacity
   - Faster processing → improved customer retention

#### Cost Estimation

- **One-time costs:** Design, build, integration, training
- **Recurring costs:** Model usage, infrastructure, operations

#### Simple ROI View

| Item | Year 1 Estimate |
|------|-----------------|
| Time savings | $XXX |
| Error reduction | $XXX |
| Compliance benefit | $XXX |
| Revenue uplift | $XXX |
| **Total annual benefit** | **$XXX** |
| One-time build cost | -$XXX |
| Annual run cost | -$XXX |
| **Net Year-1 benefit** | **$XXX** |
| **Payback period** | **X months** |

---

### Step 6 – Prioritize Use Cases

Use a simple scoring model based on:

1. **Impact on value stream**
   - How strongly this use case moves key metrics

2. **Feasibility**
   - Data availability, system access, API maturity
   - Organizational readiness, sponsors, champions

3. **Risk & compliance sensitivity**
   - Higher-risk areas require stronger guardrails

4. **Time-to-value**
   - How quickly you can pilot and get meaningful results

Score each dimension (e.g., 1–5) and pick:
- **1–3 high-impact, feasible use cases** as initial pilots
- Additional candidates for later waves

Use the [Opportunity Checklist](./template-opportunity-checklist.md) to ensure completeness.

---

### Step 7 – Design the Minimal Viable Agent

For each prioritized use case, define a **Minimal Viable Agent (MVA)**:

1. **Primary goal**
   - "The agent is done when ___ is achieved"

2. **Inputs & tools**
   - What it needs to read
   - What it is allowed to modify or trigger

3. **Agent type**
   - **Reactive:** Responds quickly to events (e.g., alerts, tickets)
   - **Deliberative:** Plans multi-step actions to reach a goal
   - **Hybrid:** Fast reactions with occasional deeper reasoning/planning

4. **Memory & context**
   - What it should remember per case
   - What long-term knowledge it needs

5. **Guardrails & compliance**
   - Non-negotiable rules ("never do X", "always log Y")
   - When human approval or review is mandatory

6. **Human-in-the-loop design**
   - Points where humans:
     - Approve decisions
     - Provide missing info
     - Handle exceptions

7. **Operational monitoring & success metrics**
   - Task success rate
   - Time per case
   - Escalation rate
   - Error/rework rate
   - User satisfaction

Make sure these metrics connect back to the **value stream baseline** and **ROI estimates**.

---

## Templates & Tools

### Available Templates

1. **[Use Case Card Template](./template-use-case-card.md)**
   - Document agent role, environment, tools, goals
   - Define current vs target performance metrics

2. **[ROI Estimation Template](./template-roi-estimation.md)**
   - Calculate benefits (time, quality, compliance, revenue)
   - Estimate costs and payback period

3. **[Opportunity Checklist](./template-opportunity-checklist.md)**
   - Ensure all critical elements are covered
   - Track progress through VSM analysis

### Value Stream Overview Template

```markdown
## Value Stream Overview

- **Name:** [Your value stream name]
- **Trigger:** [What starts this process]
- **Final Outcome ("Done"):** [End state definition]
- **Primary Customer (Internal/External):** [Who receives value]

### Stream-Level Metrics (Baseline)

- **Value / Progress:** [Cases/month, revenue, throughput]
- **Effectiveness / Quality:** [Error rate, rework, right-first-time %]
- **Efficiency / Productivity:** [Lead time, cost per case, FTE hours]
- **Compliance / Risk:** [SLA %, audit findings, violations]

### High-Level Steps

1. [Step 1 name] – [Actor(s)] – [Systems] – [Process time / Wait time]
2. [Step 2 name] – [Actor(s)] – [Systems] – [Process time / Wait time]
3. [Step 3 name] – [Actor(s)] – [Systems] – [Process time / Wait time]
...
```

---

## Next Steps

### For Individual Developers
1. Start with a simple value stream in your own work
2. Identify 1-2 agentic hotspots
3. Create a use case card for the most promising one
4. Build a prototype using [CrewAI Quick Start](./quick-start-individual.md)

### For Teams
1. Run a VSM workshop with cross-functional stakeholders
2. Map current state and identify 3-5 hotspots
3. Create use case cards and ROI estimates for each
4. Prioritize and start with highest-value, lowest-risk pilot

### For Organizations
1. Select strategic value streams aligned with business goals
2. Conduct formal VSM analysis with governance oversight
3. Build business cases with full ROI analysis
4. Establish pilot program with clear success metrics
5. Plan for scaling successful pilots

### Related Resources

- [When NOT to Use Agentic AI](./when-not-to-use-agentic-ai.md) - Understand when scripts or RPA are better choices
- [Individual Developer Guide](./1-individual-level.md) - Build your first agent
- [Organization Level Guide](./3-organization-level.md) - Enterprise deployment

---

[← Back to Main Guide](./README.md)
