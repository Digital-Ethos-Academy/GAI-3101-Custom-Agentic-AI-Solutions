# Tool Development Best Practices
## Building Effective Tools for Agents

[← Back to Main Guide](./README.md)

---

## The Tool-First Mindset

**Tools are what make agents powerful**. Without tools, agents are just language models. With well-designed tools, agents become autonomous systems that can:
- Access real-time data
- Perform actions in external systems
- Validate and verify information
- Execute computations
- Interact with APIs and databases

---

## Tool Design Principles

### 1. Single Responsibility Principle
Each tool should do **one thing well**.

```python
# ✅ GOOD: Focused tool
@tool("Search Wikipedia")
def search_wikipedia(query: str) -> str:
    """Search Wikipedia for encyclopedic information"""
    return wikipedia_search(query)

# ❌ BAD: Tool does too much
@tool("Universal Search")
def universal_search(query: str, source: str, format: str, filter: str) -> str:
    """Search everywhere, format everything, filter somehow..."""
    # Too complex! Agent won't know when to use this.
```

### 2. Clear, Detailed Documentation

The docstring is **critical** - it's how the agent decides when to use the tool.

```python
@tool("Database Query Tool")
def query_database(sql: str) -> str:
    """Execute READ-ONLY SQL query on customer database.
    
    Use this tool to retrieve customer data, orders, or analytics.
    
    IMPORTANT:
    - Only SELECT queries allowed (no INSERT, UPDATE, DELETE)
    - Queries automatically limited to 1000 rows
    - Always include WHERE clause to filter results
    
    Args:
        sql: Valid SQL SELECT statement
        
    Returns:
        Query results as JSON string
        
    Examples:
        query_database("SELECT name, email FROM customers WHERE country='US' LIMIT 10")
        query_database("SELECT COUNT(*) FROM orders WHERE date > '2025-01-01'")
    
    Security: Tool automatically validates and sanitizes queries
    Rate Limit: 100 queries per minute
    Owner: data-team@company.com
    """
    # Implementation
```

### 3. Robust Error Handling

Tools must **never crash** - always return helpful error messages.

```python
@tool("API Integration Tool")
def call_external_api(endpoint: str, params: dict) -> str:
    """Call external API with comprehensive error handling"""
    
    max_retries = 3
    retry_delay = 1
    
    for attempt in range(max_retries):
        try:
            response = requests.get(
                endpoint, 
                params=params, 
                timeout=10,
                headers={"User-Agent": "AgentBot/1.0"}
            )
            response.raise_for_status()
            return json.dumps(response.json())
            
        except requests.exceptions.Timeout:
            if attempt < max_retries - 1:
                time.sleep(retry_delay * (attempt + 1))
                continue
            return json.dumps({
                "error": "API timeout after multiple retries",
                "suggestion": "Try again later or simplify request"
            })
            
        except requests.exceptions.HTTPError as e:
            status_code = e.response.status_code
            if status_code == 429:
                return json.dumps({
                    "error": "Rate limit exceeded",
                    "suggestion": "Wait 60 seconds before retrying"
                })
            return json.dumps({
                "error": f"API returned error {status_code}",
                "details": str(e)
            })
            
        except Exception as e:
            logging.error(f"Unexpected error in API tool: {e}")
            return json.dumps({
                "error": "Unexpected error occurred",
                "type": type(e).__name__
            })
```

### 4. Consistent Return Format

Always return **strings** (CrewAI requirement). Use JSON for structured data.

```python
@tool("Get Weather")
def get_weather(location: str) -> str:
    """Get current weather for a location"""
    
    weather_data = fetch_weather(location)
    
    # Return as formatted JSON string
    return json.dumps({
        "location": location,
        "temperature": weather_data["temp"],
        "conditions": weather_data["conditions"],
        "humidity": weather_data["humidity"],
        "timestamp": datetime.now().isoformat()
    }, indent=2)
```

---

## Tool Development Patterns

### Pattern 1: Information Retrieval Tools

```python
@tool("Search Company Knowledge Base")
def search_kb(query: str) -> str:
    """Search internal documentation and knowledge base.
    
    Use when answering questions about company policies, procedures, or history.
    """
    # Vector search in knowledge base
    results = vector_db.similarity_search(query, k=3)
    
    # Format results
    formatted = []
    for i, result in enumerate(results, 1):
        formatted.append(f"{i}. {result.content}\nSource: {result.metadata['source']}\n")
    
    return "\n".join(formatted)
```

### Pattern 2: Action/Execution Tools

```python
@tool("Create Support Ticket")
def create_ticket(title: str, description: str, priority: str = "medium") -> str:
    """Create a support ticket in the ticketing system.
    
    Args:
        title: Brief title of the issue
        description: Detailed description
        priority: One of: low, medium, high, urgent
    """
    try:
        ticket = ticketing_api.create({
            "title": title,
            "description": description,
            "priority": priority,
            "created_by": "agent",
            "status": "open"
        })
        
        return json.dumps({
            "success": True,
            "ticket_id": ticket["id"],
            "ticket_url": ticket["url"],
            "message": f"Ticket #{ticket['id']} created successfully"
        })
        
    except Exception as e:
        return json.dumps({
            "success": False,
            "error": str(e)
        })
```

### Pattern 3: Validation/Verification Tools

```python
@tool("Verify Email Address")
def verify_email(email: str) -> str:
    """Validate email address format and check if domain exists.
    
    Use before sending emails or creating accounts.
    """
    # Basic format validation
    email_regex = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    if not re.match(email_regex, email):
        return json.dumps({
            "valid": False,
            "reason": "Invalid email format"
        })
    
    # Check domain exists
    domain = email.split('@')[1]
    try:
        dns.resolver.resolve(domain, 'MX')
        return json.dumps({
            "valid": True,
            "email": email,
            "domain": domain
        })
    except:
        return json.dumps({
            "valid": False,
            "reason": "Domain does not exist or has no mail server"
        })
```

### Pattern 4: Computation Tools

```python
@tool("Calculate Metrics")
def calculate_metrics(data: str) -> str:
    """Calculate statistical metrics from numerical data.
    
    Input: Comma-separated numbers
    Example: calculate_metrics("10,20,30,40,50")
    """
    try:
        # Parse input
        numbers = [float(x.strip()) for x in data.split(',')]
        
        # Calculate metrics
        metrics = {
            "count": len(numbers),
            "sum": sum(numbers),
            "mean": statistics.mean(numbers),
            "median": statistics.median(numbers),
            "std_dev": statistics.stdev(numbers) if len(numbers) > 1 else 0,
            "min": min(numbers),
            "max": max(numbers)
        }
        
        return json.dumps(metrics, indent=2)
        
    except Exception as e:
        return json.dumps({
            "error": "Could not calculate metrics",
            "details": str(e),
            "example": "Use format: calculate_metrics('10,20,30')"
        })
```

---

## Tool Testing Framework

### Unit Tests for Tools

```python
# tests/test_tools.py
import pytest
from tools import search_kb, verify_email, create_ticket

class TestSearchTool:
    """Test knowledge base search tool"""
    
    def test_search_returns_results(self):
        """Tool should return formatted results"""
        result = search_kb("deployment process")
        assert len(result) > 0
        assert "deployment" in result.lower()
    
    def test_search_handles_empty_query(self):
        """Tool should handle empty queries gracefully"""
        result = search_kb("")
        assert "error" in result.lower() or len(result) == 0
    
    def test_search_returns_string(self):
        """Tool must return string (CrewAI requirement)"""
        result = search_kb("test query")
        assert isinstance(result, str)

class TestEmailVerification:
    """Test email verification tool"""
    
    def test_valid_email(self):
        """Should validate correct email format"""
        result = verify_email("user@example.com")
        data = json.loads(result)
        assert data["valid"] == True
    
    def test_invalid_email_format(self):
        """Should reject invalid format"""
        result = verify_email("not-an-email")
        data = json.loads(result)
        assert data["valid"] == False
    
    def test_returns_json_string(self):
        """Should return parseable JSON string"""
        result = verify_email("test@test.com")
        data = json.loads(result)  # Should not raise exception
        assert "valid" in data

class TestPerformance:
    """Test tool performance"""
    
    @pytest.mark.slow
    def test_tool_completes_quickly(self):
        """Tool should complete in < 5 seconds"""
        import time
        start = time.time()
        result = search_kb("query")
        duration = time.time() - start
        assert duration < 5.0
```

---

## Tool Catalog Template

Document your tools for team/organization use:

```markdown
# Tool Catalog

## Search Tools

### Company Knowledge Base Search
- **Function**: `search_kb(query: str)`
- **Purpose**: Search internal documentation
- **Use Cases**: Policy questions, procedure lookup, historical info
- **Rate Limit**: None
- **Response Time**: < 2s typically
- **Owner**: @platform-team
- **Status**: Production ✅

### Web Search
- **Function**: `web_search(query: str)`
- **Purpose**: Search internet for current information
- **Use Cases**: Recent news, current events, latest developments
- **Rate Limit**: 100/hour per API key
- **Cost**: $0.001 per search
- **Owner**: @platform-team
- **Status**: Production ✅

## Action Tools

### Create Support Ticket
- **Function**: `create_ticket(title: str, description: str, priority: str)`
- **Purpose**: Create tickets in Zendesk
- **Use Cases**: Customer issues, bug reports, feature requests
- **Permissions**: Requires agent with "ticket_create" permission
- **Owner**: @support-team
- **Status**: Production ✅

[Add more tools...]
```

---

## Common Pitfalls to Avoid

### ❌ Don't: Vague Tool Names
```python
@tool("Tool")  # What does this do?
def tool(input: str) -> str:
    ...
```

### ✅ Do: Descriptive Names
```python
@tool("Search Financial Reports Database")
def search_financial_reports(query: str) -> str:
    ...
```

---

### ❌ Don't: Swallow Errors Silently
```python
def risky_tool(input: str) -> str:
    try:
        return dangerous_operation()
    except:
        return ""  # Agent has no idea what went wrong!
```

### ✅ Do: Return Helpful Error Messages
```python
def safe_tool(input: str) -> str:
    try:
        return operation()
    except SpecificError as e:
        return f"Error: {e}. Try using format: example_format"
    except Exception as e:
        logging.error(f"Unexpected error: {e}")
        return "Tool encountered an error. Please try again or contact support."
```

---

### ❌ Don't: Too Many Parameters
```python
@tool("Complex Tool")
def complex(p1: str, p2: str, p3: str, p4: str, p5: str) -> str:
    # Agent will struggle to use this correctly
    ...
```

### ✅ Do: Simple Interface
```python
@tool("Simple Tool")
def simple(query: str, options: str = "default") -> str:
    # Easy for agent to understand and use
    ...
```

---

## Tool Security Checklist

### For All Tools
- [ ] Input validation implemented
- [ ] Output sanitization for PII/secrets
- [ ] Error messages don't reveal sensitive info
- [ ] Rate limiting considered
- [ ] Audit logging in place

### For Data Access Tools
- [ ] Read-only access enforced
- [ ] Query sanitization implemented
- [ ] Row limits in place
- [ ] Restricted to necessary data only

### For Action Tools
- [ ] Confirmation required for destructive actions
- [ ] Permissions checked before execution
- [ ] Changes are logged/auditable
- [ ] Rollback capability exists

---

## Tool Development Workflow

1. **Design**
   - Define clear purpose
   - Specify inputs/outputs
   - Document use cases

2. **Implement**
   - Write tool function
   - Add comprehensive docstring
   - Implement error handling

3. **Test**
   - Unit tests for functionality
   - Error case testing
   - Performance testing

4. **Document**
   - Add to tool catalog
   - Provide examples
   - Note limitations

5. **Deploy**
   - Code review
   - Integration testing with agents
   - Monitor usage

6. **Maintain**
   - Track performance
   - Update based on feedback
   - Deprecate when no longer needed

---

[← Back to Main Guide](./README.md) | [Common Errors ←](./reference-common-errors.md) | [Tech Decisions →](./reference-technology-decisions.md)
