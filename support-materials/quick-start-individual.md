# Individual Developer Quick Start
## Get Your First Agent Running in < 1 Hour

[← Back to Main Guide](./README.md) | [Full Individual Guide →](./1-individual-level.md)

---

## 🎯 Goal

Build your first tool-augmented agent using CrewAI in under 1 hour.

---

## 📦 Step 1: Installation (5 minutes)

```bash
# Create project directory
mkdir my-first-agent
cd my-first-agent

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install CrewAI and tools
pip install crewai crewai-tools python-dotenv

# Create environment file
echo "OPENAI_API_KEY=your-key-here" > .env
```

**Get your API key**: Visit [OpenAI Platform](https://platform.openai.com/api-keys)

---

## 🔧 Step 2: Create Your First Agent (10 minutes)

Create `main.py`:

```python
from crewai import Agent, Task, Crew
from crewai_tools import SerperDevTool

# Initialize search tool
search_tool = SerperDevTool()

# Create researcher agent with tools
researcher = Agent(
    role='Research Analyst',
    goal='Find accurate information about {topic}',
    backstory='''You are an expert researcher who knows how to find 
    reliable sources and verify information.''',
    tools=[search_tool],  # Tools make agents powerful!
    verbose=True,
    allow_delegation=False
)

# Create a task
research_task = Task(
    description='''Research the topic: {topic}
    
    Your research should include:
    1. Current state and key developments
    2. Main players or organizations
    3. Recent news (last 6 months)
    
    Use the search tool to find reliable sources.''',
    expected_output='A concise research report with key findings',
    agent=researcher
)

# Create crew
crew = Crew(
    agents=[researcher],
    tasks=[research_task],
    verbose=True
)

# Run!
if __name__ == "__main__":
    result = crew.kickoff(inputs={'topic': 'Agentic AI in 2025'})
    print("\n\n######## FINAL RESULT ########")
    print(result)
```

---

## 🚀 Step 3: Run Your Agent (2 minutes)

```bash
python main.py
```

You'll see your agent:
1. Think about the task
2. Use the search tool
3. Analyze results
4. Generate a report

---

## 🎨 Step 4: Add More Tools (10 minutes)

Enhance your agent with more capabilities:

```python
from crewai_tools import (
    SerperDevTool,
    ScrapeWebsiteTool,
    FileReadTool
)

# Multiple tools for different capabilities
search_tool = SerperDevTool()
scrape_tool = ScrapeWebsiteTool()
file_tool = FileReadTool()

# Enhanced researcher with more tools
researcher = Agent(
    role='Research Analyst',
    goal='Find and analyze information about {topic}',
    backstory='Expert researcher with web scraping and file analysis skills',
    tools=[search_tool, scrape_tool, file_tool],
    verbose=True
)
```

---

## 👥 Step 5: Create Multi-Agent Crew (15 minutes)

Add a writer agent to create content from research:

```python
from crewai import Agent, Task, Crew, Process

# Researcher agent (from before)
researcher = Agent(
    role='Research Analyst',
    goal='Find information about {topic}',
    backstory='Expert researcher',
    tools=[search_tool],
    verbose=True
)

# Writer agent (no tools needed - pure language)
writer = Agent(
    role='Content Writer',
    goal='Create engaging content about {topic}',
    backstory='Skilled writer who creates clear, engaging articles',
    verbose=True
)

# Research task
research_task = Task(
    description='Research {topic} and find key information',
    expected_output='Research findings with sources',
    agent=researcher
)

# Writing task (depends on research)
writing_task = Task(
    description='''Write a 300-word article about {topic} based on the research.
    
    The article should:
    - Have a catchy introduction
    - Present key findings
    - Include a conclusion''',
    expected_output='A well-written article',
    agent=writer,
    context=[research_task]  # Uses research_task output
)

# Create crew with both agents
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    process=Process.sequential,  # Tasks run in order
    verbose=True
)

# Run the crew
result = crew.kickoff(inputs={'topic': 'Agentic AI in 2025'})
```

---

## 🛠️ Step 6: Create Custom Tool (10 minutes)

Build a simple calculator tool:

```python
from crewai_tools import tool

@tool("Simple Calculator")
def calculator(operation: str) -> str:
    """Performs basic mathematical calculations.
    
    Input should be a math expression like '2 + 2' or '10 * 5'.
    
    Example: calculator("15 + 25")
    """
    try:
        result = eval(operation)
        return f"Result: {result}"
    except Exception as e:
        return f"Error: Could not calculate. {str(e)}"

# Use in agent
math_agent = Agent(
    role='Math Assistant',
    goal='Solve mathematical problems',
    backstory='Expert at mathematics and calculations',
    tools=[calculator],
    verbose=True
)

# Test it
task = Task(
    description='Calculate 127 * 384',
    expected_output='The calculated result',
    agent=math_agent
)

crew = Crew(agents=[math_agent], tasks=[task])
result = crew.kickoff()
```

---

## 🎓 What You've Learned

✅ Installed CrewAI and dependencies  
✅ Created your first agent with tools  
✅ Built a multi-agent crew  
✅ Created a custom tool  
✅ Understood task dependencies

---

## 🚀 Next Steps

### Immediate Next Steps
1. **Experiment**: Try different topics and tool combinations
2. **Add Tools**: Explore other [CrewAI tools](https://docs.crewai.com/tools)
3. **Test Edge Cases**: What happens with unusual inputs?

### When Ready
- Read the [Full Individual Guide](./1-individual-level.md) for deeper understanding
- Check [Common Errors](./reference-common-errors.md) when things go wrong
- Learn [Tool Development Best Practices](./reference-tool-development.md)

### Level Up
- Move to [Team Level](./2-team-level.md) when collaborating
- Explore [Technology Decisions](./reference-technology-decisions.md) for scaling

---

## 💡 Tips for Success

**Do's**
- ✅ Start with 2-3 tools per agent
- ✅ Use verbose=True while learning
- ✅ Test tools independently first
- ✅ Give agents clear, specific roles

**Don'ts**
- ❌ Don't add too many tools (overwhelming)
- ❌ Don't skip tool descriptions
- ❌ Don't use CrewAI for single-prompt tasks
- ❌ Don't ignore errors - they teach you

---

## 📚 Resources

- [CrewAI Documentation](https://docs.crewai.com)
- [CrewAI Tools](https://docs.crewai.com/tools)
- [CrewAI Examples](https://github.com/joaomdmoura/crewAI-examples)
- [CrewAI Discord](https://discord.com/invite/X4JWnZnxPb)

---

[← Back to Main Guide](./README.md) | [Full Individual Guide →](./1-individual-level.md)
