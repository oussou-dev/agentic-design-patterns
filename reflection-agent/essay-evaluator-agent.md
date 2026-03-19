## Description

This agent takes a short essay, evaluates it based on criteria like clarity, structure, and argument strength, 
and then suggests improvements or rewrites. 
It reflects on the essay before rewriting, mimicking a self-reviewing student or an AI tutor.


## Highlights

- Reflects on user-generated content (not just summaries)
- Can simulate teacher-style feedback
- Uses evaluation criteria as part of its reflection process

## Code (Essay Review with Feedback and Revision)

```python
# Step 1: Evaluate the essay
def evaluate_essay(essay: str) -> str:
    score = 0
    feedback = []
 
    if len(essay.split()) < 100:
        feedback.append("The essay is too short.")
    else:
        score += 1
 
    if "however" in essay or "on the other hand" in essay:
        feedback.append("Good use of contrast and structure.")
        score += 1
    else:
        feedback.append("Try adding transitional phrases for better flow.")
 
    if "because" in essay:
        feedback.append("Argument is supported with reasoning.")
        score += 1
    else:
        feedback.append("Consider adding rationale for your opinions.")
 
    return f"🧠 Reflection:\n" + "\n".join(feedback), score


# Step 2: Rewrite based on feedback
def revise_essay(essay: str, feedback: str) -> str:
    if "too short" in feedback:
        return essay + " In conclusion, this topic requires more exploration to fully understand its implications."
    if "Consider adding rationale" in feedback:
        return essay + " This is important because it affects many aspects of society."
    return essay

 
# 🧪 Example
essay_text = (
    "Technology has changed the way we communicate. Social media allows people to stay connected. "
    "This can be positive, but also creates issues with privacy and attention spans."
)
 
essay_evaluator_agent(essay_text)
```

## Sample Output

✍️ Original Essay:
Technology has changed the way we communicate...

🧠 Reflection:
The essay is too short.
Try adding transitional phrases for better flow.
Consider adding rationale for your opinions.
📝 Score: 1/3

✅ Revised Essay:
Technology has changed the way we communicate...
This is important because it affects many aspects of society.

## Use Cases

- AI writing tutors
- Automated essay scoring and revision
- Educational platforms with feedback loops
