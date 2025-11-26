# GAI-3101: Crafting Custom Agentic AI Solutions

## Overview
This repository contains the course materials and lab exercises for **GAI-3101: Crafting Custom Agentic AI Solutions**. Developed by Ascendient, LLC, this course guides you through the process of building sophisticated, autonomous AI agents using modern frameworks and techniques.

## Repository Structure

```
GAI-3101-Custom-Agentic-AI-Solutions/
├── README.md                    # This file
├── INSTALL.md                   # Installation and setup instructions
├── requirements.txt             # Python dependencies
├── LabFiles/                    # Hands-on lab exercises (12 modules)
│   ├── simple-python-agent/
│   ├── introducing-single-agents/
│   ├── using-observation-tools/
│   ├── using-action-tools/
│   ├── rule-based-reasoning/
│   ├── building-personal-assistant/
│   ├── autogen-reactive-agent/
│   ├── round-robin-chat/
│   ├── langgraph-deliberative-agent/
│   ├── hierarchical-planning/
│   ├── long-term-memory/
│   └── implementing-error-recovery/
├── use-cases/                   # Real-world implementations of course techniques
│   ├── Agentic AML Behavior Reports/
│   │   └── value-stream-overview.md              # AML workflow VSM with ROI analysis
│   └── Campaign Execution & Committee Presentation/
│       ├── README.md                             # Complete implementation guide
│       ├── value-stream-overview.md              # Campaign workflow VSM
│       └── campaign-agents-implementation.ipynb  # Full notebook with all 12 techniques
└── support-materials/           # Comprehensive guides and resources
    ├── README.md               # Support materials index and navigation
    ├── course-materials/       # Official course documents
    │   ├── GAI-3101-LabGuide.html
    │   ├── GAI-3101-LabGuide.pdf
    │   └── GAI-3101-StudentLessonGuide.pdf
    ├── guides/                 # Best practices and decision guides
    │   ├── vsm-guide.md       # Value Stream Mapping for use case identification
    │   └── when-not-to-use-agentic-ai.md
    ├── templates/              # Practical templates for planning and ROI
    │   ├── template-use-case-card.md
    │   ├── template-roi-estimation.md
    │   └── template-opportunity-checklist.md
    ├── quick-starts/           # Framework-specific quick start guides
    │   └── quick-start-individual.md
    └── references/             # Technical references and best practices
        ├── checklists.md
        ├── reference-common-errors.md
        ├── reference-technology-decisions.md
        └── reference-tool-development.md
```

## Course Materials

### Official Course Documents
Located in `support-materials/course-materials/`:
- **[Lab Guide (HTML)](support-materials/course-materials/GAI-3101-LabGuide.html)** - Interactive step-by-step lab instructions
- **[Lab Guide (PDF)](support-materials/course-materials/GAI-3101-LabGuide.pdf)** - Downloadable lab instructions
- **[Student Lesson Guide (PDF)](support-materials/course-materials/GAI-3101-StudentLessonGuide.pdf)** - Comprehensive conceptual lessons

### Support Materials
Comprehensive best practices and resources - **[Start Here](support-materials/README.md)**:
- **Guides**: VSM methodology, decision frameworks, when to use alternatives
- **Templates**: Use case cards, ROI estimation, opportunity assessment
- **Quick Starts**: Get started quickly with different frameworks
- **References**: Common errors, tool development, technology decisions

## Real-World Use Cases
The `use-cases/` directory contains complete, production-ready implementations of agentic AI solutions for real business problems. Each use case demonstrates how to apply all 12 course techniques to solve specific business challenges.

### Case 1: Agentic AML Behavior Reports
**Business Context**: Automated Anti-Money Laundering (AML) compliance reporting

**Key Files**:
- `value-stream-overview.md` - Value stream mapping with VSM metrics, current/future state analysis, and ROI calculations

**Business Impact**:
- **Lead time reduction**: 19 hours → 9 hours (~53% improvement)
- **Manual effort savings**: 3.5 hours per alert
- **Annual value**: $588,000 in cost savings (200 alerts/month at $70/hour)
- **Year 1 ROI**: 135% with $338,000 net benefit

**Workflow**: Alert intake → Behavioral analysis → Typology mapping → Narrative drafting → Review & archiving

### Case 2: Campaign Execution & Committee Presentation
**Business Context**: Automating end-to-end marketing campaign analysis and presentation generation

**Key Files**:
- `README.md` - Comprehensive implementation guide with architecture details
- `value-stream-overview.md` - Detailed VSM with current/future timelines
- `campaign-agents-implementation.ipynb` - Full Jupyter notebook demonstrating all 12 course techniques applied to the campaign workflow

**Business Impact**:
- **Lead time reduction**: 40 hours → 16.5 hours (~59% improvement)
- **Manual effort savings**: 12 hours → 4.5 hours per campaign (~62.5% reduction)
- **Annual savings**: $108,000 (20 campaigns/month at $60/hour analyst rate)
- **5-year ROI**: $340,000 cumulative

**Workflow**: Input validation → Data preparation → Monitoring setup → Analytical review → Scheduling → PPT assembly

**Techniques Applied**:
- Lab 1: Simple Python Agent foundation
- Lab 2: Multi-agent communication with AutoGen
- Lab 4: Deliberative planning with LangGraph
- Lab 6-7: Observation & action tools
- Lab 8: Hierarchical task planning with dependencies
- Lab 9: Rule-based validation logic
- Lab 12: Error recovery with retry & circuit breaker patterns

## Lab Exercises
All hands-on exercises are located in the `LabFiles/` directory. Each module is structured with a main starter notebook (e.g., `<topic>.ipynb`) and a corresponding `solutions/` folder containing the completed version.

### Modules
The labs are organized to take you from basic agent concepts to advanced multi-agent architectures:

1.  **Simple Python Agent** (`LabFiles/simple-python-agent/`)
    *   *Focus*: Introduction to the fundamental structure of an AI agent using pure Python.
2.  **Introducing Single Agents** (`LabFiles/introducing-single-agents/`)
    *   *Focus*: Building your first functional single-agent system.
3.  **Using Observation Tools** (`LabFiles/using-observation-tools/`)
    *   *Focus*: Equipping agents with capabilities to read and understand their environment.
4.  **Using Action Tools** (`LabFiles/using-action-tools/`)
    *   *Focus*: Enabling agents to execute tasks, manipulate files, and interact with external systems.
5.  **Rule-Based Reasoning** (`LabFiles/rule-based-reasoning/`)
    *   *Focus*: Hybridizing LLM intelligence with deterministic rules for predictable behavior.
6.  **Building a Personal Assistant** (`LabFiles/building-personal-assistant/`)
    *   *Focus*: Integrating skills to create a helpful personal assistant agent.
7.  **AutoGen Reactive Agent** (`LabFiles/autogen-reactive-agent/`)
    *   *Focus*: Leveraging the AutoGen framework to create agents that react to dynamic inputs.
8.  **Round Robin Chat** (`LabFiles/round-robin-chat/`)
    *   *Focus*: Orchestrating multi-agent conversations using a round-robin pattern.
9.  **LangGraph Deliberative Agent** (`LabFiles/langgraph-deliberative-agent/`)
    *   *Focus*: Building agents that can plan and deliberate using LangGraph.
10. **Hierarchical Planning** (`LabFiles/hierarchical-planning/`)
    *   *Focus*: Structuring agents to handle complex tasks through hierarchical decomposition.
11. **Long-Term Memory** (`LabFiles/long-term-memory/`)
    *   *Focus*: Implementing vector stores or databases to give agents persistent memory.
12. **Implementing Error Recovery** (`LabFiles/implementing-error-recovery/`)
    *   *Focus*: Designing robust agents that can detect and recover from failures.

## Getting Started

### Prerequisites
*   **Python 3.8+**
*   **Jupyter Notebook** or **JupyterLab**
*   **API Keys**: You will likely need API keys for LLM providers (e.g., OpenAI, Anthropic) as specified in the individual notebooks.

### Setup
For detailed installation instructions, see **[INSTALL.md](INSTALL.md)**.

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/Digital-Ethos-Academy/GAI-3101-Custom-Agentic-AI-Solutions.git
    cd GAI-3101-Custom-Agentic-AI-Solutions
    ```

2.  **Set up your environment**:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    pip install -r requirements.txt
    pip install jupyterlab
    ```

3.  **Launch the Labs**:
    ```bash
    jupyter lab
    ```
    Navigate to the `LabFiles` directory and open the notebook for the module you wish to work on.

### Additional Resources
- **[Support Materials](support-materials/README.md)** - Best practices, templates, and guides
- **[VSM Guide](support-materials/guides/vsm-guide.md)** - Identify agentic AI opportunities
- **[Quick Start Guide](support-materials/quick-starts/quick-start-individual.md)** - Get your first agent running

## License
Copyright © 2025 Ascendient Learning, LLC. All rights reserved.
This material is proprietary. Unauthorized copying, modification, distribution, or use is strictly prohibited.
