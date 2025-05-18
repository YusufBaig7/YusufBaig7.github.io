---
layout: page
title: Projects
permalink: /projects/
description:  
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


# [CogniLLM: Infusing Cognitive Priors for ARC Problem Solving](https://github.com/YusufBaig7/ARC-Challenge)

---

## Key Points

- **Problem**: State-of-the-art LLMs solve fewer than 13% of Abstraction and Reasoning Corpus (ARC) tasks due to limited exemplars and the combinatorial complexity of visual patterns.  
- **Solution**: **CogniLLM** augments a 14B-parameter vision-language transformer with human-like cognitive priors, separates local vs. global structures, unifies transduction and induction objectives, and applies test-time training with a voting mechanism.  

---

## Methodology

- **Knowledge-Prior Pre-training**  
  Attach LoRA adapters to a DeepSeek-R1 base checkpoint and train on 5K synthetic grid examples with captions enumerating discrete vision operations (e.g., flood-fill, shape extraction) to imbue the model with structured priors.

- **Dual-Stage Solver**  
  - **Local vs. Global**: Classify tasks as object-level (local) or pattern-level (global).  
  - **Transduction**: Directly predict the output grid from the input grid.  
  - **Induction**: Generate a Python function that encodes the transformation, then apply it to the input.

- **Test-Time Training & Voting**  
  For each test task, fine-tune the LoRA layers on 400 augmented support examples (one gradient step), discard afterward, and produce four candidate solutions (local/global × transduction/induction). Normalize log-likelihoods and select the final output via majority voting with a diversity penalty.  

---

## Experiments

- **Dataset**: 100 held-out tasks from the public ARC evaluation split.  
- **Baselines**: GPT-4o, DeepSeek-V3, Gemini 2.0 Flash, JudgeLLM.  
- **Pipeline Results (accuracy on 100 tasks)**:  
  1. Knowledge Priors only: 8.0%  
  2. + Global Transduction: 16.0%  
  3. + Local Transduction: 18.0%  
  4. + Global Test-Time Training: 22.0%  
  5. + Local Test-Time Training: 26.0%  
  6. + Voting with Test-Time Training: **29.0%**

- **Findings**:  
  - Test-time training yields the largest single improvement.  
  - Local transduction excels on color-relational tasks; program induction better handles spatial symmetry.  

---

## Conclusion

CogniLLM shows that embedding discrete cognitive priors, combining transduction and induction strategies, and leveraging lightweight test-time adaptation with a voting mechanism can more than double ARC task performance compared to leading LLMs, pointing toward a path for more human-like abstract reasoning.
