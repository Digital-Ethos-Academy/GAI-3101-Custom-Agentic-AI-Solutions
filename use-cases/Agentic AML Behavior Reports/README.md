# Agentic AML Behavior Reports – AI-Powered Compliance Automation

## Overview

This folder contains a complete agentic AI solution for automating Anti-Money Laundering (AML) behavior report generation. The solution demonstrates how specialized AI agents can orchestrate the end-to-end process of investigating customer alerts, analyzing behavioral anomalies, mapping to AML typologies, and generating compliance-ready reports.

**Business Impact:**
- **Lead time reduction**: 19 hours → 9 hours (~53% improvement)
- **Manual effort savings**: 6 hours → 2.5 hours per alert (~58% reduction)
- **Annual cost savings**: $588,000 (200 alerts/month at $70/hour analyst rate)
- **Year 1 ROI**: 135% with 5.1 month payback

---

## 📁 Folder Contents

### Files

| File | Purpose |
|------|---------|
| **aml-agents-implementation.ipynb** | Comprehensive Jupyter notebook demonstrating progressive implementation of all 12 agentic AI lab techniques applied to AML alert processing |
| **value-stream-overview.md** | Detailed value stream mapping including current/future-state process analysis, timeline reduction, ROI calculations, and compliance benefits |
| **README.md** | This file – comprehensive guide to the use case and implementation |

---

## 🎯 Problem Statement

**Current Workflow Challenges:**
- Manual alert intake and context loading (30 min/alert)
- Time-consuming behavioral analysis and peer comparison (90 min/alert)
- Labor-intensive typology mapping and risk assessment (60 min/alert)
- Manual narrative drafting and report generation (120 min/alert)
- Human review, decision-making, and archiving (60 min/alert)

**Total Current Lead Time:** 19 hours per alert (2.4 business days)

**Stakeholders:** Risk & AML teams, Internal Audit, Regulators

---

## 🔄 Value Stream Process

### Process Steps (5 Steps)

1. **Alert Intake & Context Load** (PT: 30 min → 10 min)
   - Receive alert from AML models
   - Pull customer master table row and transaction history
   - Look up variable definitions and align with dictionary
   - Build structured case context

2. **Behavioral Analysis** (PT: 90 min → 30 min)
   - Compare recent vs 6/12-month baseline behavior
   - Analyze amount intensity, volatility, frequency
   - Calculate channel and product distributions
   - Compute distance from peer group (K-Means, z-scores)

3. **Typology Mapping** (PT: 60 min → 20 min)
   - Map patterns to known AML typologies
   - Assess risk level for each matched typology
   - List implicated products and channels
   - Draft typology rationale and evidence

4. **Narrative & Recommendation Draft** (PT: 120 min → 60 min)
   - Generate executive summary
   - Document behavioral findings with tables
   - Explain typology matches and risk assessment
   - Provide actionable recommendations

5. **Human Review, Decision & Archiving** (PT: 60 min → 30 min)
   - Review report completeness and quality
   - Adjust findings and recommendations as needed
   - Choose disposition action (SAR, EDD, close, etc.)
   - Sign-off and archive in case management

### Data & System Architecture

```
AML Models (K-Means, Profiles, Rarity)
         ↓
    Alerting / Case System
         ↓
    Agentic AML Report Engine
         ↓
    Data Warehouse (AML Master Table)
         ↓
    AML Analyst (Review & Decision)
         ↓
    Document & Case Repository
         ↓
    Internal Audit / Regulator
    (On-demand access)
```

**Key Systems:**
- **AML Models:** Customer profiles, K-Means clustering, rarity indicators
- **Data Warehouse:** BigQuery with AML master table
- **Typology Library:** Knowledge base of AML patterns
- **Case Management:** Document repository, audit trail

---

## 🤖 Agentic AI Implementation

### Notebook Structure

The `aml-agents-implementation.ipynb` notebook progressively demonstrates all 12 lab techniques from the GAI-3101 course, applied to this use case:

#### Part 1: Environment Setup
- Package installation (OpenAI, AutoGen, LangGraph, LangChain)
- API configuration and client initialization
- Sample AML alert and customer data for testing

#### Part 2: Foundation – Simple Python Agent (Lab 1)
- Base `Agent` class with `_select_action()` and `act()` methods
- 5 specialized AML agents:
  - `ContextAgent`: Alert intake and context extraction
  - `BehavioralAnalysisAgent`: Statistical behavior comparison
  - `TypologyAgent`: AML typology pattern matching
  - `ReportGenerationAgent`: Narrative and recommendation drafting
  - `ReviewAgent`: Quality assurance and completeness checking

#### Part 3: Multi-Agent Communication (Lab 2)
- AutoGen `RoundRobinGroupChat` for sequential agent communication
- Workflow: Coordinator → ContextExtractor → BehavioralAnalyst → TypologyMapper → ReportGenerator → QualityReviewer
- Message passing and state propagation between agents

#### Part 4: Deliberative Agent with LangGraph (Lab 4)
- `StateGraph` workflow orchestration
- Workflow nodes: planner → context_loader → behavioral_analyzer → typology_matcher → report_generator → reviewer
- Conditional routing and structured decision-making

#### Part 5: Observation & Action Tools (Labs 6-7)
Implements real-world tool integrations:

**Observation Tools (Data retrieval):**
- `query_aml_database()`: Fetch customer transaction history from data warehouse
- `get_customer_profile()`: Retrieve KYC profile and risk tier
- `get_peer_statistics()`: Fetch peer group statistics for comparison
- `check_watchlist()`: Screen against sanctions and watchlists

**Action Tools (Execution):**
- `create_sar_filing()`: Submit Suspicious Activity Report
- `update_customer_risk_tier()`: Update customer risk classification
- `store_report()`: Archive report in case management
- `notify_analyst()`: Send notification to assigned analyst

#### Part 6: Rule-Based Reasoning (Lab 9)
- `RuleBasedAMLValidator` with 6 deterministic validation rules:
  - `required_alert_fields`: Check mandatory alert data presence
  - `risk_score_range`: Validate risk score is 0-100
  - `temporal_data_consistency`: Verify recent vs baseline data exists
  - `peer_comparison_sanity`: Check percentiles and z-scores are valid
  - `typology_risk_alignment`: Ensure risk score aligns with rating
  - `report_completeness`: Validate all required report sections exist
- Implements early error detection without LLM calls

#### Part 7: Hierarchical Planning (Lab 8)
- `HierarchicalAMLPlanner` for complex task decomposition
- 16 primitive tasks organized in 4 composite phases:
  - Data Gathering: load_alert, fetch_customer_data, fetch_peer_data, check_watchlists
  - Analysis: behavioral_analysis, peer_comparison, typology_matching
  - Reporting: generate_narrative, create_visualizations, quality_review
  - Decision: assess_risk, determine_action, archive_report
- Task dependency mapping and topological ordering
- Agent assignment strategy (AGENT_ASSIGNMENTS)

#### Part 8: Error Recovery (Lab 12)
- `@with_retry` decorator with exponential backoff
- `CircuitBreaker` pattern for fault tolerance
- `ResilientAMLAgent` class wrapping agents with recovery logic
- Automatic retry on transient failures
- Graceful degradation on permanent failures

#### Part 9: Complete End-to-End System (Lab 11)
- `AMLProcessingSystem` integrating all components
- Orchestrates entire workflow from alert to archived report
- Combines all 12 techniques in unified production-ready system
- Comprehensive error handling and logging

### Lab Technique Mappings

| Lab | Technique | Implementation | Use Case Application |
|-----|-----------|-----------------|----------------------|
| Lab 1 | Simple Python Agent | Base `Agent` class with action selection | Foundation for all AML agents |
| Lab 2 | Round Robin Communication | AutoGen `RoundRobinGroupChat` | Multi-agent alert processing coordination |
| Lab 3 | Reactive Agent | *(Applied in monitoring)* | Real-time alert prioritization |
| Lab 4 | Deliberative Agent | LangGraph `StateGraph` | Complex investigation workflow |
| Lab 5 | Long-Term Memory | *(Applied in state persistence)* | Alert history and case tracking |
| Lab 6 | Observation Tools | AML database, profiles, peers, watchlists | Data retrieval for analysis |
| Lab 7 | Action Tools | SAR filing, risk updates, notifications | Compliance actions and archiving |
| Lab 8 | Hierarchical Planning | `HierarchicalAMLPlanner` with 16 tasks | Investigation decomposition |
| Lab 9 | Rule-Based Reasoning | `RuleBasedAMLValidator` with 6 rules | Data quality and compliance checks |
| Lab 10 | Robustness Evaluation | *(Applied in testing)* | Agent behavior validation |
| Lab 11 | Personal Assistant | `AMLProcessingSystem` | Unified end-to-end orchestration |
| Lab 12 | Error Recovery | `@with_retry`, `CircuitBreaker` | Resilient alert processing |

---

## 📊 Key Metrics & ROI

### Current vs. Future State

**Per Alert Timeline:**

| Metric | Current | Future | Improvement |
|--------|---------|--------|-------------|
| Processing Time | 6 hours | 2.5 hours | -58% |
| Wait/Queue Time | 13 hours | 6.5 hours | -50% |
| Total Lead Time | 19 hours | 9 hours | -53% |
| Manual Effort | 6 hours | 2.5 hours | 3.5 hours saved |

**Annual Impact (200 alerts/month):**

| Metric | Value |
|--------|-------|
| Monthly Hours Saved | 700 hours |
| Monthly Cost Savings | $49,000 |
| Annual Cost Savings | $588,000 |
| Implementation Cost (Year 1) | $250,000 |
| Year 1 Net Benefit | $338,000 |
| Simple ROI (Year 1) | 135% |
| Payback Period | 5.1 months |

**3-Year Cumulative Benefit:**
- Year 1: $338,000 net
- Year 2: $488,000 net ($588K savings - $100K maintenance)
- Year 3: $488,000 net
- **Total 3-Year**: $1,314,000

---

## 🛡️ Compliance & Regulatory Benefits

Beyond direct cost savings, the agentic AML solution delivers significant compliance advantages:

### Audit Trail & Explainability
- Complete digital trail of every analysis step
- Traceable reasoning: data → analysis → typology → recommendation
- Timestamps and version control for all report components
- Reproducible investigations on demand

### Consistency & Standardization
- Uniform application of typology matching rules
- Consistent report structure across all analysts
- Reduced variance in risk assessments
- Standardized recommendation language

### Regulatory Readiness
- On-demand report regeneration with updated parameters
- Rapid response to regulatory inquiries
- Demonstrable due diligence through systematic approach
- Clear escalation paths and decision documentation

### Quality Improvement
- AI-assisted checklists catch missing sections
- Cross-validation of behavioral metrics
- Automated flagging of incomplete analyses
- Peer comparison anomaly detection

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- Jupyter Notebook or JupyterLab
- OpenAI API key
- Google Cloud credentials (for BigQuery integration)
- Optional: AutoGen, LangGraph, LangChain packages

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Digital-Ethos-Academy/GAI-3101-Custom-Agentic-AI-Solutions.git
   cd "use-cases/Agentic AML Behavior Reports"
   ```

2. **Install dependencies:**
   ```bash
   pip install -r ../../requirements.txt
   ```
   Or install packages individually:
   ```bash
   pip install openai autogen langchain langgraph google-cloud-bigquery pandas numpy
   ```

3. **Set up credentials:**
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   export GOOGLE_APPLICATION_CREDENTIALS="path-to-gcp-credentials.json"
   ```

4. **Open the notebook:**
   ```bash
   jupyter notebook aml-agents-implementation.ipynb
   ```

### Running the Notebook

Follow the notebook cells sequentially:

1. **Part 1** – Environment setup and sample data loading
2. **Part 2** – Initialize specialized AML agents
3. **Part 3** – Test multi-agent communication
4. **Part 4** – Run LangGraph workflow
5. **Part 5** – Test observation and action tools
6. **Part 6** – Execute rule-based validation
7. **Part 7** – Run hierarchical planning
8. **Part 8** – Demonstrate error recovery
9. **Part 9** – Run complete end-to-end system

Each section includes:
- Explanation of technique and AML application
- Implementation code with detailed comments
- Example outputs and results
- Key takeaways for production deployment

---

## 📚 Technical Architecture

### Agent Types & Responsibilities

| Agent | Responsible For | Tools Used |
|-------|-----------------|-----------|
| **ContextAgent** | Alert intake, context loading | AML database queries, variable dictionary |
| **BehavioralAnalysisAgent** | Statistical comparison, anomaly detection | Temporal analysis, peer statistics |
| **TypologyAgent** | Pattern matching, risk assessment | Typology knowledge base, rule matching |
| **ReportGenerationAgent** | Narrative generation, recommendations | LLM for text generation, templates |
| **ReviewAgent** | Quality assurance, completeness check | Validation rules, checklist enforcement |

### Workflow Orchestration

```
AML Alert (SNAPSHOT_DATE, CUSTOMER_ID)
        ↓
   ContextAgent (Load context, variable mapping)
        ↓
   BehavioralAnalysisAgent (Temporal + peer comparison)
        ↓
   TypologyAgent (Pattern matching, risk assessment)
        ↓
   ReportGenerationAgent (Narrative, tables, recommendations)
        ↓
   ReviewAgent (Quality review, completeness)
        ↓
   Output: Approved Report + Case Archive
```

### AML Typologies Supported

| Typology | Risk Level | Key Indicators |
|----------|------------|----------------|
| Trade-Based ML | HIGH | High velocity, multiple counterparties, high-risk countries |
| Structuring / Smurfing | MEDIUM | Round amounts, frequent transactions, below-threshold amounts |
| Layering | HIGH | Complex patterns, rapid movement, multiple channels |
| Cash Intensive Business | MEDIUM | Cash-heavy transactions, inconsistent business profile |

### Error Handling & Resilience

- **Retry Logic:** Exponential backoff (2x) for up to 3 attempts
- **Circuit Breaker:** Opens after 3 failures, 60s timeout
- **Graceful Degradation:** Fallback to cached/default data
- **Logging:** Comprehensive audit trail with timestamps

---

## 🔧 Customization & Extension

### Adding New Agents

1. Create a new class inheriting from `Agent`
2. Implement `_select_action()` and `act()` methods
3. Define domain-specific logic and tools
4. Add to `AMLProcessingSystem` orchestration

### Adding New Typologies

Edit the `TypologyAgent` class in Part 2:
1. Add new typology definition to `_load_typology_rules()`
2. Define indicators and risk level
3. Implement matching logic in `match_typologies()`

### Adding New Validation Rules

Edit the `RuleBasedAMLValidator` class in Part 6:
1. Create new rule method following pattern: `rule_<name>(self, alert, customer_data, report)`
2. Add to `self.validation_rules` list in `__init__`
3. Return dict with `rule`, `passed`, `message` keys

### Configuring for Production

- Replace mock observation tools with real BigQuery queries
- Integrate with actual case management system API
- Configure SAR filing integration with regulatory systems
- Set up monitoring and alerting infrastructure
- Implement proper authentication and authorization
- Configure audit logging for compliance requirements

---

## 📖 Additional Resources

### Within This Repository

- **[value-stream-overview.md](./value-stream-overview.md)** – Detailed VSM with current/future timelines, ROI, and compliance benefits
- **[../../support-materials/course-materials/GAI-3101-LabGuide.pdf](../../support-materials/course-materials/GAI-3101-LabGuide.pdf)** – Complete lab guide covering all 12 techniques
- **[../../support-materials/labfiles/](../../support-materials/labfiles/)** – Individual lab solution notebooks

### External References

- [LangGraph Documentation](https://python.langchain.com/docs/langgraph/)
- [AutoGen Documentation](https://microsoft.github.io/autogen/)
- [FATF AML Typologies](https://www.fatf-gafi.org/en/publications.html)
- [FinCEN SAR Filing Requirements](https://www.fincen.gov/resources/filing-information)

---

## 🎓 Learning Outcomes

After working through this implementation, you will understand:

1. ✅ How to design specialized agents for compliance workflows
2. ✅ Multi-agent orchestration for sequential investigation steps
3. ✅ Tool integration for data retrieval and compliance actions
4. ✅ Rule-based reasoning for deterministic validation
5. ✅ Hierarchical planning for complex task decomposition
6. ✅ Error recovery patterns for resilient processing
7. ✅ End-to-end system design for regulatory compliance
8. ✅ ROI quantification and business case development

---

## 📝 Implementation Checklist

For production deployment, ensure:

- [ ] All API credentials are securely configured (not in code)
- [ ] BigQuery queries are optimized for production volumes
- [ ] Case management system integration is complete
- [ ] SAR filing workflow is tested with regulatory requirements
- [ ] Error handling and logging meet audit requirements
- [ ] Monitoring and alerting are configured
- [ ] Load testing with 200+ alerts/month volume
- [ ] User acceptance testing (UAT) with AML analysts
- [ ] Compliance review and sign-off obtained
- [ ] Analyst training materials are prepared
- [ ] Rollback procedures are documented
- [ ] SLA monitoring is in place

---

## ⚠️ Regulatory Considerations

This implementation is designed to **assist** AML analysts, not replace human judgment:

- **Human-in-the-Loop:** All reports require analyst review and sign-off
- **Explainability:** Every recommendation includes traceable reasoning
- **Audit Trail:** Complete digital record of all analysis steps
- **Override Capability:** Analysts can modify any agent-generated content
- **Regulatory Alignment:** Report templates follow SAR/CTR requirements

**Important:** Ensure your organization's legal and compliance teams review the implementation before production deployment.

---

## 🤝 Support & Feedback

For questions, issues, or improvements:

1. Review the [GAI-3101 Course Materials](../../support-materials/course-materials/)
2. Check the individual [Lab Solution Notebooks](../../support-materials/labfiles/)
3. Refer to the [VSM Guide](../../support-materials/guides/vsm-guide.md)
4. Consult framework documentation (LangGraph, AutoGen)

---

## 📄 Document Information

- **Version:** 1.0
- **Last Updated:** November 2025
- **Owner:** AML & Compliance Analytics Team
- **Status:** Production Ready
- **Regulatory Domain:** Anti-Money Laundering (AML), Bank Secrecy Act (BSA)

---

## License

This implementation is part of the GAI-3101 Custom Agentic AI Solutions curriculum. Use and modify according to your organization's needs and regulatory requirements.
