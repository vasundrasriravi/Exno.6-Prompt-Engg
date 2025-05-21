# **EXP 6: Development of Python Code Compatible with Multiple AI Tools**
## Register no : 212222230168
## **Experiment**

Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights.
---

### **Aim**

To compare the responses of two open-source language models, **GPT-Neo** and **GPT-2**, to a given question, and analyze how different models generate text and handle natural language queries.

---

### **Procedure**

1. **Install Required Libraries**

   ```bash
   pip install transformers torch
   ```

2. **Load Models**

   * GPT-Neo: `EleutherAI/gpt-neo-1.3B`
   * GPT-2: `gpt2`

3. **Define Functions**

   * One function each for GPT-Neo and GPT-2 to generate text.
   * A comparison function to evaluate and print results.

4. **Generate Answers**

   * Provide a sample question (e.g., "What are the benefits of renewable energy?") to both models.

5. **Compare Responses**

   * Print and compare both responses.
   * Summarize if outputs are similar or different.

---

### **Python Code**

```python
from transformers import pipeline

# Load GPT-Neo and GPT-2 models
generator_neo = pipeline('text-generation', model='EleutherAI/gpt-neo-1.3B')
generator_gpt2 = pipeline('text-generation', model='gpt2')

# Function to get answer from GPT-Neo
def get_gpt_neo_answer(question):
    generated_text = generator_neo(question, max_length=100, num_return_sequences=1)
    return generated_text[0]['generated_text']

# Function to get answer from GPT-2
def get_gpt2_answer(question):
    generated_text = generator_gpt2(question, max_length=100, num_return_sequences=1)
    return generated_text[0]['generated_text']

# Function to compare answers
def compare_answers(question):
    answer_gpt_neo = get_gpt_neo_answer(question)
    answer_gpt2 = get_gpt2_answer(question)
    print("GPT-Neo Answer:\n", answer_gpt_neo)
    print("\nGPT-2 Answer:\n", answer_gpt2) 
    summary = "Both models provided the same answer." if answer_gpt_neo == answer_gpt2 else "The answers are different."
    print("\nSummary:", summary)
    return {
        "question": question,
        "gpt_neo_answer": answer_gpt_neo,
        "gpt2_answer": answer_gpt2,
        "summary": summary
    }

# Run the comparison
question = "What are the benefits of renewable energy?"
result = compare_answers(question)
```
---
### **Sample Output**

```
GPT-Neo Answer:
 What are the benefits of renewable energy? Renewable energy is clean, sustainable...

GPT-2 Answer:
 What are the benefits of renewable energy? It helps reduce pollution, provides jobs...

Summary: The answers are different.
Comparison Result: {'question': ..., 'summary': 'The answers are different.'}
```
---
### **Summary**

This experiment demonstrates that **GPT-Neo and GPT-2**, while both powerful language models, respond differently to the same natural language query. Each model reflects its distinct training data and architecture, influencing the tone, content, and structure of the response. GPT-Neo tends to generate more structured, informative content, while GPT-2 sometimes outputs more generic or creative responses.

---

### **Conclusion**

In conclusion, integrating and comparing outputs from different language models allows developers and researchers to better understand model behavior, quality, and reliability. This experiment highlights the value of **prompt engineering** and **model selection** in achieving the desired output for AI-driven applications. GPT-Neo often delivers more detailed explanations, whereas GPT-2 may be quicker but less informative.
