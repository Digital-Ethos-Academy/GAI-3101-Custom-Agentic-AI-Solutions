# GenAI Use-Case Evaluation & Recommendation Engine

An intelligent multi-agent system that automates the evaluation of whether a business use case should leverage Generative AI, deterministic logic, or a hybrid approach. This solution demonstrates comprehensive agentic AI implementation using all 12 lab techniques from the GAI-3101 course.

## 📋 Overview

When teams propose new AI projects, architecture and governance teams must evaluate whether GenAI is the right fit or if traditional deterministic approaches would be more appropriate. This evaluation process is currently manual, time-consuming, and inconsistent.

This agentic solution automates the evaluation workflow, applying a structured decision tree and generating comprehensive recommendation reports with trade-off analysis.

## 🎯 Problem Statement

**Current State:**
- AI architects spend ~2.75 hours per use case manually evaluating GenAI appropriateness
- ~40 use case evaluations per month
- Inconsistent evaluation criteria across reviewers
- Long lead times (13.75 hours including wait times)

**Target State:**
- Automated data collection and structuring
- Decision tree-based evaluation with explainable rationale
- Comprehensive recommendation reports with trade-offs
- Knowledge base of past decisions for consistency

## 🏗️ Architecture

### Agents

| Agent | Role | Key Functions |
|-------|------|---------------|
| **InfoCollectionAgent** | Data Gatherer | Extract use case info, answer decision-tree questions, identify data characteristics |
| **EvaluationAgent** | Decision Maker | Apply decision tree logic, calculate confidence, generate rationale |
| **ReportGenerationAgent** | Documentation | Create trade-off analysis, warnings, implementation guidance |

### Decision Tree Logic

```
Q1: Can problem be solved with CLEAR DETERMINISTIC RULES?
├── YES → Recommend: DETERMINISTIC
└── NO → Continue to Q2

Q2: Does output require NATURAL LANGUAGE generation?
├── YES → Recommend: GENAI
└── NO → Continue to Q3

Q3: Must UNSTRUCTURED DATA be analyzed?
├── YES → Recommend: GENAI
└── NO → Recommend: DETERMINISTIC

Q4: Are there MIXED requirements?
├── YES → Override to: HYBRID
└── NO → Use previous recommendation
```

### Tools

**Observation Tools (Lab 6):**
- `search_similar_cases()` - Query knowledge base for precedents
- `get_evaluation_criteria()` - Retrieve current decision tree configuration
- `get_compliance_requirements()` - Look up compliance details

**Action Tools (Lab 7):**
- `save_evaluation_to_kb()` - Persist evaluation to knowledge base
- `notify_stakeholders()` - Alert requesters and governance team
- `export_report()` - Generate downloadable report

## 📊 Value Stream Analysis

### Workflow Steps

| Step | Current Time | Future Time | Improvement |
|------|--------------|-------------|-------------|
| Collect Evaluation Data | 45 min | 15 min | 67% ↓ |
| Apply Decision Tree & Draft | 60 min | 15 min | 75% ↓ |
| Generate Recommendation | 60 min | 30 min | 50% ↓ |
| **Total Manual Effort** | **2.75 hr** | **1 hr** | **64% ↓** |

### Lead Time Impact

| Metric | Current | Future | Improvement |
|--------|---------|--------|-------------|
| Lead Time | 13.75 hr | 4 hr | 71% ↓ |
| Manual Effort | 2.75 hr | 1 hr | 64% ↓ |

### Financial Impact

**Annual Volume:** 480 evaluations (40/month)

| Metric | Value |
|--------|-------|
| Hours Saved per Evaluation | 1.75 hr |
| Total Hours Saved Annually | 840 hr |
| Cost per Hour (AI Architect) | $80 |
| **Annual Cost Savings** | **$67,200** |
| Implementation Cost (Year 1) | $60,000 |
| **Year 1 ROI** | **12%** |
| **Year 2+ Net Benefit** | **$47,200/year** |

## 🔬 Lab Techniques Applied

This implementation demonstrates all 12 GAI-3101 lab techniques:

1. **Lab 1: Simple Python Agent** - Base `Agent` class with action selection
2. **Lab 2: Round Robin Communication** - AutoGen GroupChat orchestration
3. **Lab 4: Deliberative Agent** - LangGraph StateGraph workflow
4. **Lab 6: Observation Tools** - KB search, criteria retrieval
5. **Lab 7: Action Tools** - KB persistence, notifications
6. **Lab 8: Hierarchical Planning** - Task decomposition with dependencies
7. **Lab 9: Rule-Based Reasoning** - Deterministic validation rules
8. **Lab 12: Error Recovery** - Circuit breaker, retry with backoff
9. **Lab 11: End-to-End System** - Complete `GenAIEvaluationSystem` integration

## 📁 Repository Structure

```
use-cases/GenAI Use-Case Evaluation and Recommendation Engine/
├── README.md                                    # This file
├── value-stream-overview.md                    # Detailed VSM analysis
└── genai-evaluation-agents-implementation.ipynb # Complete implementation
```

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- OpenAI API key
- Required packages: `openai`, `pyautogen`, `langchain`, `langchain-openai`, `langgraph`

### Installation

```bash
pip install openai pyautogen langchain langchain-openai langgraph python-dotenv
```

### Quick Start

```python
from genai_evaluation_system import GenAIEvaluationSystem

# Initialize system
system = GenAIEvaluationSystem()

# Submit use case for evaluation
use_case = {
    "use_case_id": "UC-2025-001",
    "title": "Customer Email Response Generator",
    "description": "Generate personalized email responses to customer inquiries",
    "input_data_types": ["customer_email_text", "account_data"],
    "expected_output": "Natural language email response",
    "volume": "500 emails/day",
    "compliance_requirements": ["GDPR", "brand_guidelines"]
}

# Get recommendation
result = system.evaluate_use_case(use_case)

print(f"Recommendation: {result['report']['recommendation']['approach']}")
print(f"Confidence: {result['report']['recommendation']['confidence']}%")
```

## 📝 Sample Output

```
=== EVALUATION RESULT ===

Use Case: Customer Email Response Generator
Recommendation: GENAI (90% confidence)

Decision Path:
  - Q1: NO - Cannot be fully solved with deterministic rules
  - Q2: YES - Requires natural language generation

Rationale:
GenAI is recommended because natural language output is required.
These capabilities are not achievable with traditional deterministic approaches.

Warnings:
  ⚠️ GenAI outputs are non-deterministic; implement output validation
  ⚠️ GDPR compliance: Ensure no PII is sent to external LLM APIs

Next Steps:
  1. Review recommendation with requesting team
  2. Conduct prompt engineering proof-of-concept
  3. Evaluate LLM provider options and costs
```

## 🔒 Validation Rules

The system includes 6 deterministic validation rules:

1. **Required Fields** - All mandatory use case fields present
2. **Decision Tree Completeness** - All 4 questions answered
3. **Recommendation Consistency** - Recommendation aligns with criteria
4. **Confidence Threshold** - Minimum 60% confidence required
5. **Trade-offs Present** - Pros/cons analysis included
6. **Compliance Addressed** - Relevant warnings generated

## 🛡️ Error Recovery

- **Retry with Exponential Backoff** - 3 attempts with 2x backoff
- **Circuit Breaker** - Opens after 3 failures, 60s timeout
- **Graceful Degradation** - Falls back to HYBRID recommendation if service fails

## 📈 Future Enhancements

1. **Vector Database Integration** - Replace simulated KB with Pinecone/Weaviate
2. **Web UI** - Self-service submission portal
3. **Feedback Loop** - Track recommendation accuracy
4. **Integration** - Connect to JIRA/ServiceNow for governance tracking
5. **Fine-tuning** - Train custom model on historical decisions

## 📚 Related Resources

- [Value Stream Overview](./value-stream-overview.md) - Detailed business case
- [Implementation Notebook](./genai-evaluation-agents-implementation.ipynb) - Full code walkthrough

---

**Course:** GAI-3101 Custom Agentic AI Solutions  
**Version:** 1.0  
**Last Updated:** November 2025
