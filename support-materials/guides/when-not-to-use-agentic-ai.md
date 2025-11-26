# When Scripting and RPA Are Preferred Over Agentic AI

Not every automation problem requires agentic AI. In many cases, traditional scripting or Robotic Process Automation (RPA) tools are simpler, faster, cheaper, and more reliable solutions.

**Related Resources:**
- [Opportunity Checklist](../templates/template-opportunity-checklist.md) - Assess if agentic AI is appropriate
- [VSM Guide](vsm-guide.md) - Identify automation opportunities systematically
- [Technology Decision Matrix](../references/reference-technology-decisions.md) - Compare automation approaches

---

## Decision Framework: When NOT to Use Agentic AI

Use this framework to determine if traditional automation is a better fit than agentic AI.

### Choose Scripting or RPA When:

#### 1. **Fully Deterministic Logic**
**Use Traditional Automation If:**
- Every decision follows explicit, documented rules
- No interpretation or judgment required
- Same inputs always produce same outputs
- Logic fits in flowchart or decision tree

**Examples:**
- Data format conversions (CSV → JSON)
- File backups on schedule
- Batch report generation
- Database ETL pipelines
- Configuration deployments

**Why Not Agentic AI:**
- LLMs add unnecessary cost and latency
- Non-deterministic behavior is a bug, not a feature
- Simpler tools are more maintainable and debuggable

---

#### 2. **Strict Real-Time Requirements**
**Use Traditional Automation If:**
- Response time must be <100ms consistently
- Predictable latency is critical
- Cannot tolerate variable processing time

**Examples:**
- API gateways and request routing
- High-frequency trading systems
- Real-time sensor data processing
- Network packet filtering
- Manufacturing control systems

**Why Not Agentic AI:**
- LLM inference adds 500ms–5s latency per call
- Cloud API calls have network overhead
- Cannot guarantee response time SLAs

---

#### 3. **Zero Error Tolerance**
**Use Traditional Automation If:**
- Errors are unacceptable and unrecoverable
- Safety-critical system (medical, aviation, financial)
- Legal/regulatory requirement for 100% accuracy
- No human review is possible

**Examples:**
- Financial transaction processing
- Medical device control
- Aircraft autopilot systems
- Nuclear plant monitoring
- Legal contract execution

**Why Not Agentic AI:**
- LLMs are probabilistic and can "hallucinate"
- Even with guardrails, cannot guarantee 100% accuracy
- Deterministic systems provide formal verification

---

#### 4. **Simple, Repetitive UI Automation**
**Use RPA Tools If:**
- Task is clicking/typing in legacy desktop apps
- No APIs available, only GUI interaction
- Logic is simple and follows exact steps
- Process rarely changes

**Examples:**
- Data entry into legacy ERP systems
- Copying data between desktop applications
- Generating reports from old client-server apps
- Form filling with fixed field mappings

**Recommended Tools:**
- UiPath, Automation Anywhere, Blue Prism
- Python + Selenium for web
- AutoHotkey for desktop

**Why Not Agentic AI:**
- RPA tools are purpose-built for UI automation
- No reasoning required, just playback of steps
- Cheaper and more reliable for simple tasks

---

#### 5. **Pure Mathematical or Algorithmic Tasks**
**Use Traditional Programming If:**
- Task is mathematical computation
- Algorithmic solution exists and is efficient
- Precision and speed are paramount

**Examples:**
- Statistical calculations
- Image processing (resizing, filtering)
- Encryption/decryption
- Sorting and searching
- Graph algorithms

**Why Not Agentic AI:**
- LLMs are not calculators (they approximate)
- Purpose-built algorithms are 1000x faster
- Deterministic results with no risk of error

---

#### 6. **High-Volume, Cost-Sensitive Operations**
**Use Traditional Automation If:**
- Millions of operations per day
- Per-unit cost must be <$0.001
- Margin pressure requires extreme efficiency

**Examples:**
- Log file parsing and aggregation
- Large-scale data validation
- Bulk email sending
- CDN cache invalidation
- Metrics collection and rollup

**Why Not Agentic AI:**
- LLM API costs add up fast at scale
- $0.01–$0.10 per API call makes ROI negative
- Simple scripts cost nearly zero to run

---

## Comparison Table: Agentic AI vs. Traditional Automation

| Dimension | Scripting/RPA | Agentic AI |
|-----------|---------------|------------|
| **Best For** | Deterministic, rule-based tasks | Judgment, reasoning, ambiguity |
| **Accuracy** | 100% (when coded correctly) | 85-99% (probabilistic) |
| **Latency** | <10ms | 500ms–5s |
| **Cost per Operation** | ~$0.0001 | ~$0.01–$0.10 |
| **Development Speed** | Moderate (requires coding) | Fast (prompt engineering) |
| **Maintenance** | Breaks when process changes | Adapts to variation better |
| **Scalability** | Linear cost scaling | Linear cost + API limits |
| **Explainability** | Perfect (code is the doc) | Requires logging/tracking |
| **Error Handling** | Explicit try/catch logic | Requires guardrails/validation |

---

## Hybrid Approaches: Best of Both Worlds

Often the optimal solution combines both approaches:

### Pattern 1: Agent Orchestrates Scripts
- Agent handles high-level reasoning and planning
- Calls traditional scripts as tools for deterministic steps
- Example: Agent decides what reports to run, Python script generates them

### Pattern 2: RPA for Data Collection, Agent for Analysis
- RPA extracts data from legacy UIs
- Agent analyzes data and makes recommendations
- Example: RPA pulls customer tickets, agent prioritizes and drafts responses

### Pattern 3: Agent Generates Code, Scripts Execute
- Agent writes/modifies automation scripts based on requirements
- Scripts execute independently for reliability and speed
- Example: Agent generates SQL query, database runs it deterministically

### Pattern 4: Traditional Automation with Agent Fallback
- Scripts handle 90% of cases with known patterns
- Agent handles exceptions requiring judgment
- Example: Invoice processing script calls agent when confidence is low

---

## Decision Tree

```
START: Do I need to automate a task?
│
├─ Is the logic 100% deterministic and rule-based?
│  ├─ YES → Use Scripting or RPA
│  └─ NO → Continue
│
├─ Does it require <100ms response time?
│  ├─ YES → Use Scripting
│  └─ NO → Continue
│
├─ Is 100% accuracy legally/safety required?
│  ├─ YES → Use Scripting or RPA
│  └─ NO → Continue
│
├─ Is it pure math, logic, or algorithmic?
│  ├─ YES → Use Traditional Programming
│  └─ NO → Continue
│
├─ Is cost per operation critical (<$0.001)?
│  ├─ YES → Use Scripting
│  └─ NO → Continue
│
├─ Does it require language understanding, reasoning, or judgment?
│  ├─ YES → Consider Agentic AI ✅
│  └─ NO → Use RPA or Scripting
│
└─ Does it benefit from adaptability to variations?
   ├─ YES → Consider Agentic AI ✅
   └─ NO → Use RPA or Scripting
```

---

## Examples: Right Tool for the Job

### Case 1: Monthly Financial Report Generation
**Task:** Pull data from database, calculate metrics, generate PDF report  
**Best Approach:** Python script  
**Why:** Deterministic logic, runs on schedule, no LLM needed  
**Cost:** ~$0 per run  

### Case 2: Customer Email Triage and Routing
**Task:** Read incoming emails, understand intent, route to correct department  
**Best Approach:** Agentic AI  
**Why:** Requires language understanding, context, and judgment  
**Cost:** ~$0.05 per email (acceptable for high-value interactions)  

### Case 3: Data Entry from Scanned Invoices
**Task:** Extract vendor, amount, date from invoice images  
**Best Approach:** Hybrid (OCR + validation script + agent for exceptions)  
**Why:** Structured data extraction is rule-based, but handwriting/quality issues need judgment  
**Cost:** ~$0.01 per invoice  

### Case 4: Nightly Database Backup
**Task:** Backup production database to S3 every night at 2 AM  
**Best Approach:** Cron job + bash script  
**Why:** Zero ambiguity, must be 100% reliable, no reasoning required  
**Cost:** ~$0 per backup  

### Case 5: Code Review Comment Analysis
**Task:** Read code review comments, summarize feedback, suggest action items  
**Best Approach:** Agentic AI  
**Why:** Natural language, context-dependent, benefits from reasoning  
**Cost:** ~$0.10 per review (high ROI for developer productivity)  

---

## Checklist: Should I Use Traditional Automation?

Use this checklist to validate your choice of automation approach.

- [ ] **Logic is fully deterministic** (no judgment calls)
- [ ] **Same inputs always produce same outputs**
- [ ] **No natural language understanding required**
- [ ] **Response time <100ms required** OR **cost per operation must be <$0.001**
- [ ] **Error rate must be <0.01%** (near-perfect accuracy)
- [ ] **Task does not benefit from adaptability to variation**
- [ ] **Existing algorithm or tool solves the problem well**

**If 4+ boxes checked → Use Scripting or RPA, not Agentic AI**

---

## When to Reconsider Agentic AI Later

Even if traditional automation is better today, revisit the decision if:

- **Process changes frequently** - maintaining scripts becomes expensive
- **Exceptions are common** - script logic becomes unwieldy with edge cases
- **Natural language input/output is added** - users want to interact in plain English
- **Judgment requirements emerge** - stakeholders want context-aware decisions
- **LLM costs drop significantly** - economics shift in favor of AI

---

## Tools and Technologies by Use Case

### Scripting (Deterministic Logic)
- **Python** - General-purpose automation, data processing
- **Bash/Shell** - System admin tasks, file operations
- **JavaScript/Node.js** - Web automation, API integration
- **PowerShell** - Windows system automation

### RPA (UI Automation)
- **UiPath** - Enterprise-grade, visual workflow builder
- **Automation Anywhere** - Cloud-native, scalable
- **Blue Prism** - Banking/finance focus, audit trail
- **Selenium** - Open-source web browser automation
- **AutoHotkey** - Windows desktop app automation

### Workflow Orchestration
- **Apache Airflow** - Data pipelines, scheduling
- **Prefect** - Modern Python workflows
- **n8n** - Low-code automation platform
- **Zapier/Make** - No-code integration for SaaS tools

### When to Add Agentic AI Layer
- **LangChain** - Wrap agents around existing scripts as tools
- **CrewAI** - Multi-agent orchestration of mixed automation
- **LangGraph** - State machine for complex agent flows

---

## Key Takeaways

1. **Agentic AI is not a replacement for all automation** - it's one tool in the toolbox
2. **Simpler is better** - use the least complex solution that meets requirements
3. **Cost and reliability matter** - LLMs are expensive and probabilistic
4. **Hybrid approaches are powerful** - combine deterministic and agentic components
5. **Reassess as technology evolves** - what's expensive today may be cheap tomorrow

---

**Last Updated:** _[Date]_  
**Next Review:** _[Date]_

---

**Navigation:**
- [← Back to Opportunity Checklist](../templates/template-opportunity-checklist.md)
- [→ Technology Decision Matrix](../references/reference-technology-decisions.md)
- [↑ Support Materials Home](../README.md)
