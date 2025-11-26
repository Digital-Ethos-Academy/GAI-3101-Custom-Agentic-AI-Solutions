# GAI-3101: Crafting Custom Agentic AI Solutions

## Overview
This repository contains the course materials and lab exercises for **GAI-3101: Crafting Custom Agentic AI Solutions**. Developed by Ascendient, LLC, this course guides you through the process of building sophisticated, autonomous AI agents using modern frameworks and techniques.

## Course Materials
The repository includes comprehensive guides to support your learning, located in the `support-materials/` directory:
- **Lab Guide**: Step-by-step instructions for the hands-on exercises.
  - [HTML Version](support-materials/GAI-3101-LabGuide.html)
  - [PDF Version](support-materials/GAI-3101-LabGuide.pdf)
- **Student Lesson Guide**: [GAI-3101-StudentLessonGuide.pdf](support-materials/GAI-3101-StudentLessonGuide.pdf) - Detailed conceptual lessons and reference material.

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
1.  **Clone the repository**:
    ```bash
    git clone https://github.com/Digital-Ethos-Academy/GAI-3101-Custom-Agentic-AI-Solutions.git
    cd GAI-3101-Custom-Agentic-AI-Solutions
    ```

2.  **Set up your environment**:
    It is recommended to use a virtual environment (venv or conda) to manage dependencies.
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    # Install dependencies (refer to notebooks for specific packages)
    pip install jupyterlab
    ```

3.  **Launch the Labs**:
    ```bash
    jupyter lab
    ```
    Navigate to the `LabFiles` directory and open the notebook for the module you wish to work on.

## License
Copyright © 2025 Ascendient Learning, LLC. All rights reserved.
This material is proprietary. Unauthorized copying, modification, distribution, or use is strictly prohibited.
