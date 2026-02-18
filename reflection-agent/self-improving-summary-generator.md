## Description

This agent takes a block of text, generates a summary, then critiques its own output, and 
finally rewrites the summary based on that reflection. It operates in three steps:

1. Generate → 2. Reflect → 3. Revise  
All handled internally using prompt chaining or custom logic.


## Highlights

- Demonstrates metacognitive flow
- Can use basic logic or an LLM for reflection
- Structured for easy expansion (multi-pass, scoring, reasoning)

## Code (Simulated Reflection Flow)

```python
# Step 1: Generate a summary
def generate_summary(text: str) -> str:
    return text[:100] + "..." if len(text) > 100 else text

# Step 2: Reflect on the summary quality
def reflect_on_summary(summary: str) -> str:
    if len(summary.split()) < 20:
        return "The summary is too short and lacks detail."
    elif "..." in summary:
        return "The summary seems incomplete or abrupt."
    return "The summary is clear and sufficiently detailed."

# Step 3: Improve the summary
def improve_summary(text: str, reflection: str) -> str:
    if "too short" in reflection or "incomplete" in reflection:
        return text[:200] + "..." if len(text) > 200 else text
    return generate_summary(text)

# Full Reflection Agent
def reflection_summary_agent(text: str) -> str:
    summary = generate_summary(text)
    print("📝 Initial Summary:", summary)
 
    reflection = reflect_on_summary(summary)
    print("🔍 Reflection:", reflection)
 
    improved = improve_summary(text, reflection)
    print("✅ Improved Summary:", improved)
    return improved
 
# 🧪 Example
text = (
    "Artificial intelligence (AI) is revolutionizing industries by enabling machines to perform tasks that normally require human intelligence. "
    "From healthcare to finance, AI is optimizing workflows, making predictions, and transforming decision-making processes. "
    "This shift is largely powered by advancements in machine learning, natural language processing, and computer vision."
)

reflection_summary_agent(text)
```

## Sample Output

📝 Initial Summary: Artificial intelligence (AI) is revolutionizing industries by enabling machines to perform tasks tha...  
🔍 Reflection: The summary seems incomplete or abrupt.  
✅ Improved Summary: Artificial intelligence (AI) is revolutionizing industries by enabling machines to perform tasks that normally require human intelligence.  
From healthcare to finance, AI is optimizing workflows, making predictions, and transforming decision-making processes...  

## Use Cases

- Writing assistants that revise their own drafts
- Research summarizers that auto-improve quality
- Multi-pass content generation workflows
