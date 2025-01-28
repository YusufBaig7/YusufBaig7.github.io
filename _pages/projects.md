---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

# [Can LLMs Understand Math? Exploring the Pitfalls in Mathematical Reasoning](https://github.com/can-llms-understand-math/llm-experiments)

---

## Key Points

- **Problem**: LLMs struggle with multi-step mathematical reasoning, often producing logically inconsistent results.  
- **Solution**: Introduces **MAPLE (Mathematical Pitfalls and Logical Evaluation)** score for a holistic assessment, incorporating:
  - Error rates
  - Redundancy
  - Logical validity  

---

## Methodology
- **Multi-stage Evaluation**:
  - **Stage 1**: Compare LLM outputs with correct answers to identify misalignments.  
  - **Stage 2**: Judge LLM analyzes reasoning steps to assign error labels.  
  - **Stage 3**: Compute MAPLE score using error severity, redundancy, and validity metrics.

---

## Experiments
- Tested on the MATH dataset (12,500 problems).  
- Evaluated models: Gemini, GPT-4, Llama, Mixtral.  
- Identified common errors:
  1. Misunderstandings
  2. Incorrect methods
  3. Calculation errors  

- **Findings**:
  - Accuracy declines with problem difficulty; MAPLE score rises, exposing flaws.
  - Topic-wise: Stronger in geometry, weaker in calculus.

---

## Conclusion
The MAPLE score offers a detailed framework for identifying and addressing reasoning pitfalls in LLMs, paving the way for improvements in mathematical problem-solving.
