# Agentic AI Opportunity Checklist

Use this checklist to quickly assess whether a workflow step or process is a good candidate for agentic AI automation.

**Related Resources:**
- [VSM Guide](../guides/vsm-guide.md) - Systematic approach to finding opportunities
- [When NOT to Use Agentic AI](../guides/when-not-to-use-agentic-ai.md) - Alternative automation approaches
- [Use Case Card Template](template-use-case-card.md) - Document validated opportunities

---

## Quick Screening Questions

Answer these first to determine if deeper analysis is warranted:

### Must-Have Criteria (All must be YES)
- [ ] Is this task currently performed by humans?
- [ ] Does the task require some form of reasoning, judgment, or decision-making?
- [ ] Is there a clear way to measure success/quality of outcomes?
- [ ] Is the cost/impact of occasional errors acceptable with proper guardrails?

**If any answer is NO, consider [alternative automation approaches](../guides/when-not-to-use-agentic-ai.md) instead.**

---

## Detailed Opportunity Assessment

### 1. Task Characteristics (Strong Indicators)

#### Cognitive Requirements
- [ ] Requires natural language understanding
- [ ] Involves interpretation of ambiguous information
- [ ] Needs context-aware decision making
- [ ] Requires reasoning across multiple information sources
- [ ] Benefits from domain expertise or learned patterns

#### Process Attributes
- [ ] High-volume repetitive task (>100 instances/month)
- [ ] Time-consuming for humans (>30 min per instance)
- [ ] Causes bottlenecks or delays in value stream
- [ ] Requires 24/7 availability or fast response time
- [ ] Involves coordination across multiple systems

#### Value Indicators
- [ ] High labor cost (expensive skilled workers)
- [ ] Quality inconsistency due to human variability
- [ ] Employee dissatisfaction with task (boring/tedious)
- [ ] Current delays impact customer satisfaction
- [ ] Process scales poorly with growth

**Scoring:** 10+ checked boxes = Strong candidate

---

### 2. Technical Feasibility

#### Data Availability
- [ ] Input data is digitally accessible
- [ ] Sufficient training/reference data exists
- [ ] Data quality is adequate (>80% accuracy)
- [ ] Clear data access paths (APIs, databases)
- [ ] No major data privacy/security blockers

#### System Integration
- [ ] Target systems have APIs or integration options
- [ ] Authentication/authorization is manageable
- [ ] Required tools can be developed or accessed
- [ ] Latency requirements are reasonable
- [ ] No architectural blockers identified

#### LLM Suitability
- [ ] Task requires language/reasoning (not just math/logic)
- [ ] Output format can be structured/validated
- [ ] Acceptable accuracy achievable (based on similar use cases)
- [ ] Prompt engineering can provide sufficient context
- [ ] Token costs are economically viable

**Scoring:** 10+ checked boxes = Technically feasible

---

### 3. Risk & Governance Assessment

#### Error Tolerance
- [ ] Errors are detectable by automated checks
- [ ] Human review process can catch errors
- [ ] Impact of errors is limited/recoverable
- [ ] No safety-critical implications
- [ ] Gradual rollout is possible

#### Compliance & Control
- [ ] Regulatory requirements are understood
- [ ] Audit trail can be maintained
- [ ] Bias/fairness concerns are manageable
- [ ] Explainability requirements can be met
- [ ] Data retention policies are compatible

#### Organizational Readiness
- [ ] Stakeholders are supportive/open
- [ ] Resources (budget, talent) are available
- [ ] No major change management blockers
- [ ] Success metrics are agreed upon
- [ ] Failure/rollback plan is viable

**Scoring:** 10+ checked boxes = Acceptable risk profile

---

### 4. Business Impact Potential

#### Cost Reduction
- [ ] Annual labor savings > $50K
- [ ] Operational cost reduction > 30%
- [ ] Payback period < 18 months
- [ ] Scales to multiple use cases

#### Quality Improvement
- [ ] Error rate reduction > 50%
- [ ] Cycle time reduction > 40%
- [ ] Throughput increase > 2x
- [ ] Consistency improvement measurable

#### Strategic Value
- [ ] Enables new capabilities/offerings
- [ ] Competitive differentiation opportunity
- [ ] Improves customer experience significantly
- [ ] Frees humans for higher-value work
- [ ] Creates reusable patterns/assets

**Scoring:** 6+ checked boxes = High business impact

---

## Overall Opportunity Score

### Summary
| Category | Score | Weight | Weighted Score |
|----------|-------|--------|----------------|
| Task Characteristics | ___/15 | 25% | ___ |
| Technical Feasibility | ___/15 | 30% | ___ |
| Risk & Governance | ___/15 | 20% | ___ |
| Business Impact | ___/12 | 25% | ___ |
| **TOTAL** | | **100%** | **___** |

### Interpretation
- **75-100%**: Excellent candidate - prioritize for development
- **60-74%**: Good candidate - worth further analysis
- **45-59%**: Marginal - consider after higher-priority opportunities
- **<45%**: Poor fit - explore alternative automation approaches

---

## Red Flags (Stop Signals)

If ANY of these apply, carefully reconsider or defer:

- [ ] **Safety-critical:** Errors could cause physical harm or major financial loss
- [ ] **Heavily regulated:** Approval process unclear or likely to block
- [ ] **Fully deterministic:** Task is purely rule-based with no judgment required (use RPA instead)
- [ ] **Real-time requirements:** Latency <100ms required (LLM too slow)
- [ ] **No human oversight:** Cannot implement human-in-the-loop
- [ ] **Data unavailable:** Critical inputs not digitally accessible
- [ ] **Stakeholder resistance:** Strong political/organizational opposition
- [ ] **Unclear success criteria:** Cannot define measurable outcomes

---

## Prioritization Matrix

Plot your use cases based on:
- **X-axis:** Implementation Complexity (Low → High)
- **Y-axis:** Business Value (Low → High)

### Recommended Priority Order:
1. **Quick Wins:** High value, low complexity - do first
2. **Strategic Bets:** High value, high complexity - plan carefully
3. **Fill-ins:** Low value, low complexity - do if resources available
4. **Money Pits:** Low value, high complexity - avoid

---

## Decision & Next Steps

### Recommendation
- [ ] **Proceed to Use Case Development** - Complete [Use Case Card](template-use-case-card.md)
- [ ] **Request Further Analysis** - Specify what's needed: ___________
- [ ] **Defer** - Reason: ___________
- [ ] **Pursue Alternative Automation** - See [When NOT to Use Agentic AI](../guides/when-not-to-use-agentic-ai.md)

### Immediate Next Steps
1. ___________________________________________
2. ___________________________________________
3. ___________________________________________

### Stakeholders to Involve
- ___________________________________________
- ___________________________________________

---

**Use Case Name:** _[Enter name]_  
**Assessed By:** _[Name]_  
**Date:** _[Date]_  
**Review Date:** _[Date]_
