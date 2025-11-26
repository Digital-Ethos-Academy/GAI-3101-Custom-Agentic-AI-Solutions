# Installation & IDE Setup Guide

This guide will help you set up your development environment for **GAI-3101: Crafting Custom Agentic AI Solutions**. You will need a Python environment and an Integrated Development Environment (IDE) to run the lab notebooks.

## 1. Python Environment Setup

Regardless of which IDE you choose, you first need to set up your Python environment and install the required libraries.

### Prerequisites
*   **Python 3.10+**: Ensure you have a modern version of Python installed. You can download it from [python.org](https://www.python.org/downloads/).
*   **Git**: Required to clone the repository.

### Step-by-Step Setup

1.  **Clone the Repository** (if you haven't already)
    ```bash
    git clone https://github.com/Digital-Ethos-Academy/GAI-3101-Custom-Agentic-AI-Solutions.git
    cd GAI-3101-Custom-Agentic-AI-Solutions
    ```

2.  **Create a Virtual Environment**
    It is best practice to use a virtual environment to isolate project dependencies.
    
    *   **macOS/Linux**:
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```
    *   **Windows**:
        ```powershell
        python -m venv venv
        .\venv\Scripts\activate
        ```

3.  **Install Dependencies**
    Install all required packages using the `requirements.txt` file provided in this repository.
    ```bash
    pip install -r requirements.txt
    ```

---

## 2. IDE Setup

We recommend using **Visual Studio Code (VS Code)** or **Cursor** for this course. Both offer excellent support for Python and Jupyter Notebooks.

### Option A: Visual Studio Code (Recommended)

VS Code is a robust, extensible code editor.

1.  **Install VS Code**: Download from [code.visualstudio.com](https://code.visualstudio.com/).
2.  **Install Extensions**:
    Open VS Code and go to the Extensions view (Ctrl+Shift+X / Cmd+Shift+X). Search for and install:
    *   **Python** (by Microsoft)
    *   **Jupyter** (by Microsoft)
3.  **Open the Project**:
    *   File > Open Folder... > Select the `GAI-3101-Custom-Agentic-AI-Solutions` folder.
4.  **Select Interpreter**:
    *   Open any `.ipynb` file from `LabFiles/`.
    *   Click on the "Select Kernel" button in the top-right corner.
    *   Select **Python Environments...** > **venv (Python 3.x.x)**.
    *   *Note: If you don't see your venv, ensure you created it in the root of the project.*

### Option B: Cursor

Cursor is an AI-powered code editor built on top of VS Code. It provides the same interface but with deeply integrated AI capabilities.

1.  **Install Cursor**: Download from [cursor.sh](https://cursor.sh/).
2.  **Setup**:
    *   Since Cursor is a fork of VS Code, it supports the same extensions.
    *   Install the **Python** and **Jupyter** extensions if they aren't pre-installed.
3.  **Configuration**:
    *   Follow the same steps as VS Code to open the project and select the `venv` kernel for your notebooks.
    *   You can use `Cmd+K` (macOS) or `Ctrl+K` (Windows) to ask AI questions about the code directly in the editor.

### Option C: Antigravity (Google)

Antigravity is a powerful, AI-first IDE from Google.

1.  **Access Antigravity**: Navigate to [antigravity.google/product](https://antigravity.google/product).
2.  **Open the Project**:
    *   Import the repository from GitHub or open your local folder.
3.  **Setup**:
    *   Ensure the environment is configured to use the project's dependencies.
    *   Open any `.ipynb` file from `LabFiles/`.
    *   Select the active Python kernel that corresponds to your environment.

## 3. API Keys

Most labs in this course require access to Large Language Models (LLMs).
1.  Create a `.env` file in the root of the project.
2.  Add your API keys:
    ```env
    OPENAI_API_KEY=sk-...
    ANTHROPIC_API_KEY=sk-...
    ```
    *(Refer to specific labs for which keys are required).*

## 4. Troubleshooting

*   **Kernel issues**: If Jupyter cannot find your kernel, try running `python -m ipykernel install --user --name=gai-3101` while your venv is active.
*   **Missing packages**: Run `pip install -r requirements.txt` again to ensure everything installed correctly.
