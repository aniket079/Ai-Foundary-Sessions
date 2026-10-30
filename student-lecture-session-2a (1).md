import os

content = """# Module 2 Lecture Document: Advanced Reasoning with Chain-of-Thought (CoT) & Structured Search
## Course: Applied AI and Prompt Engineering (2nd Module)
### Session Duration: 2 Hours (120 Minutes) | Target Audience: Undergraduate Students & AI Practitioners

---

## Executive Overview & Learning Objectives
Welcome to Module 2! In previous sessions, we explored foundational prompt architectures (R.C.T.C.), vector spaces, and Retrieval-Augmented Generation (RAG). However, when asking Large Language Models (LLMs) to perform multi-step mathematical reasoning, formal logic, or complex software architecture, standard prompting often fails. 

Because LLMs are autoregressive token predictors, asking them for an immediate answer forces the model to calculate the final result in a single forward pass without intermediate computation space.

In this 2-hour intensive session, you will learn how to bypass these cognitive limitations using **Chain-of-Thought (CoT)**, **Tree-of-Thought (ToT)**, **Self-Consistency Sampling**, and **Forced Logical Derivation**.

### Key Learning Outcomes:
1. **Understand Autoregressive Mechanics**: Recognize why LLMs struggle with immediate complex logic and how intermediate tokens function as "working memory."
2. **Master Zero-Shot & Few-Shot CoT**: Implement the "Let's think step by step" trigger and design few-shot reasoning trajectories.
3. **Deploy Advanced Structural Frameworks**: Implement Tree-of-Thought (ToT) exploration and Self-Consistency sampling to eliminate single-path reasoning errors.
4. **Enforce Derivation-Before-Code Architectures**: Construct strict guardrail templates that force systemic pseudocode and edge-case analysis prior to code block emission.

---

## 2-Hour Session Timeline & Structure

* **00:00 - 00:25 (25 mins):** Section 1 — Autoregressive Limitations & Chain-of-Thought (CoT) Mechanics
* **00:25 - 00:50 (25 mins):** Section 2 — Tree-of-Thought (ToT) & Self-Consistency Frameworks
* **00:50 - 01:25 (35 mins):** Section 3 — Forcing Logical Derivation Before Final Code Output
* **01:25 - 01:50 (25 mins):** Section 4 — Interactive Classroom Lab ("The Algorithmic Thinking Challenge")
* **01:50 - 02:00 (10 mins):** Section 5 — Socratic Wrap-Up & Prompt Portfolio Entry 4

---

## Section 1: Autoregressive Limitations & Chain-of-Thought (CoT) Mechanics (25 Mins)

### 1.1 The "Immediate Answer" Problem
When you ask an LLM a complex question like:
> *"If A is father of B, but B is not the son of A, what is the relationship between B and A?"*

If the prompt demands an immediate 1-word answer, the neural network must compute the relational transformation within its internal transformer layers before emitting the first token. For multi-step problems, this frequently leads to **hallucination or logical collapse**.

```
[Standard Prompting]
Input: Question -> [Transformer Network] -> Output: Answer (High risk of error)

[Chain-of-Thought Prompting]
Input: Question -> [Step 1 Tokens] -> [Step 2 Tokens] -> [Step 3 Tokens] -> Output: Final Answer
```

### 1.2 Intermediate Tokens as "Working Memory"
LLMs do not have an offline scratchpad unless we give them one in the context window. Every token emitted by the model becomes part of the prompt for subsequent tokens.
By forcing the model to generate step-by-step reasoning tokens, we allow the self-attention mechanism to attend to previous intermediate deductions, effectively creating a **dynamic working memory**.

### 1.3 Zero-Shot CoT: The Magic Trigger
In 2022, researchers (Kojima et al.) discovered that simply appending a single phrase to a complex prompt dramatically improved reasoning accuracy on benchmark datasets (GSM8K, SVAMP):

> **Zero-Shot CoT Trigger:** `"Let's think step by step."`

#### Comparison Table: Standard vs. Zero-Shot CoT
| Feature | Standard Prompting | Zero-Shot CoT Prompting |
| :--- | :--- | :--- |
| **Prompt Structure** | `Solve X and output the answer.` | `Solve X. Let's think step by step.` |
| **Reasoning Path** | Hidden / Uncomputable in 1 pass | Explicitly generated in token sequence |
| **Accuracy on Complex Math** | Low (20% - 40%) | High (70% - 85%) |
| **Token Usage** | Minimal (cheaper) | Expanded (higher latency/cost) |

### 1.4 Few-Shot CoT: Guiding the Trajectory
While Zero-Shot CoT works well for general logic, **Few-Shot CoT** provides exemplar reasoning trajectories. This teaches the model *how* to decompose problems specific to your domain.

```text
[FEW-SHOT COT EXAMPLE]

Q: A store has 15 apples. It sells 4 apples in the morning and receives a shipment of 20 apples in the afternoon. How many apples remain?
A: Let's decompose this step by step:
1. Initial apples = 15.
2. Morning sales: 15 - 4 = 11 apples remain.
3. Afternoon shipment: 11 + 20 = 31 apples.
Therefore, the final answer is 31.

Q: A server processes 120 requests per minute. Traffic spikes by 50% for 3 minutes, then drops by 20% below baseline for 2 minutes. How many total requests were processed in those 5 minutes?
A: Let me solve this step by step:
```

---

## Section 2: Tree-of-Thought (ToT) & Self-Consistency Frameworks (25 Mins)

### 2.1 The Limitations of Linear Chain-of-Thought
Linear CoT follows a single path. If the model makes a minor logical error at Step 2, every subsequent step (Step 3, 4, 5) builds upon that false premise, resulting in **error propagation**.

```
Linear CoT:  Step 1 -> Step 2 (Error!) -> Step 3 (Wrong) -> Step 4 (Wrong)
```

### 2.2 Tree-of-Thought (ToT) Architecture
ToT enables models to explore multiple reasoning possibilities, evaluate intermediate decisions, and back-track when a branch reaches a logical dead end.

```
                  [Problem Statement]
                     /     |     \\
            [Branch A]  [Branch B]  [Branch C]
              /    \\        |           |
          [A1]    [A2]    (Dead End)  [C1] (Optimal)
         (Pass)  (Fail)
```

#### How to Implement ToT in Prompt Engineering:
1. **State Generation**: Ask the model to generate 3 distinct initial hypotheses or approaches.
2. **Evaluation**: Instruct the model to critique each branch (assigning a confidence score from 1–5 or Pass/Fail).
3. **Search & Branching**: Continue generating next steps only for the passing branches.
4. **Synthesis**: Combine the best path into the final solution.

#### ToT Prompt Architecture Template:
```text
[ROLE]: You are an Expert System Architect and Algorithmic Strategist.
[TASK]: Solve the following complex optimization problem using a Tree-of-Thought strategy.

[PROBLEM]: We need to migrate a monolithic SQL database (10 TB) to a microservices architecture with minimal downtime.

[INSTRUCTIONS]:
Phase 1 (Branch Generation): Generate 3 distinct migration strategies (Branch A, Branch B, Branch C).
Phase 2 (Evaluation): For each branch, evaluate:
  - Technical Complexity (1-5)
  - Downtime Risk (1-5)
  - Data Loss Risk (1-5)
Phase 3 (Pruning): Eliminate any branch with a Risk score > 3.
Phase 4 (Deep Dive): Take the winning branch and break it down into a detailed execution plan.
```

### 2.3 Self-Consistency Sampling
Self-Consistency is a decoding strategy that replaces greedy decoding (`Temperature = 0.0`) with a diverse sampling approach (`Temperature = 0.7`), running the same CoT prompt $N$ times to take a **majority vote**.

```
            /-> CoT Path 1 -> Answer: 42
[CoT Prompt] --> CoT Path 2 -> Answer: 42  ==> [Majority Vote] ==> Final Answer: 42
            \\-> CoT Path 3 -> Answer: 38
```

---

## Section 3: Forcing Logical Derivation Before Final Code Output (35 Mins)

### 3.1 The "Code First" Anti-Pattern
When developers ask an LLM: `"Write a Python script to find the longest substring without repeating characters"`, the AI immediately begins generating Python code. 

**Why this fails:**
- The model picks a data structure (e.g., nested loops) on token 5 before evaluating time complexity ($O(N^2)$ vs $O(N)$).
- It fails to handle edge cases (empty strings, single characters, spaces).

### 3.2 The Derivation-First Prompt Pattern
To produce production-grade software, we enforce a strict multi-stage pipeline using explicit boundary tags (e.g., XML/Markdown tags).

```text
[INPUT PROMPT]
  |
  +--> 1. <thinking>      (Identify core problem & algorithmic invariants)
  +--> 2. <edge_cases>    (Enumerate boundaries: empty, null, max size, negative)
  +--> 3. <complexity>    (Target Time/Space bounds, e.g., O(N) time, O(min(N, M)) space)
  +--> 4. <pseudocode>    (Step-by-step algorithmic blueprint)
  +--> 5. <code>          (Clean, documented Python/C++ code implementation)
```

### 3.3 Master Derivation-First Prompt Template

```text
[ROLE]: Senior Principal Software Engineer at Google.
[CONTEXT]: You are implementing a core data-processing utility for a high-frequency trading pipeline.

[TASK]: Implement an optimal algorithm to find the maximum sum contiguous subarray (Kadane's Algorithm variation) that supports array updates.

[CONSTRAINTS & EXECUTION ORDER]:
You MUST format your output using exact XML tags in the following order. Do NOT write executable code until the <code> tag.

<thinking>
Break down the problem mathematically. Identify why naive brute-force approaches fail.
</thinking>

<edge_cases>
List at least 4 critical edge cases (e.g., all negative numbers, single element, empty array, large integers).
</edge_cases>

<complexity_analysis>
State the required Time Complexity and Space Complexity with mathematical justification.
</complexity_analysis>

<pseudocode>
Write step-by-step structured pseudocode. Include loop invariants and state variable definitions.
</pseudocode>

<code>
Provide the complete, production-ready Python 3 code with explicit type hints, docstrings, and zero external dependencies.
</code>
```

---

## Section 4: Interactive Classroom Lab — "The Algorithmic Thinking Challenge" (25 Mins)

### Objective:
Students will experience the difference between standard "Code First" prompting and "Derivation First" CoT prompting by solving a difficult dynamic programming / string manipulation problem.

### Lab Exercise Instructions:

1. **Step 1: Test the Lazy Prompt**
   Open your preferred LLM (ChatGPT, Gemini, Claude). Run this prompt:
   > *"Write a Python function that takes a list of integers and returns the length of the longest increasing subsequence."*

2. **Step 2: Observe the Flaws**
   Check if the model explained its choice of $O(N^2)$ DP vs $O(N \\log N)$ Binary Search + DP. Did it miss edge cases like empty lists or equal elements?

3. **Step 3: Execute the Derivation-First CoT Template**
   Paste the following master template into your LLM:

```text
[ROLE]: Algorithmic Specialist & Technical Interview Examiner.
[TASK]: Solve the Longest Increasing Subsequence (LIS) problem in Python.

[EXECUTION PROTOCOL]:
1. First, inside <thinking> tags, analyze both the O(N^2) Dynamic Programming approach and the O(N log N) Patience Sorting / Binary Search approach. Explain why O(N log N) is optimal.
2. Inside <edge_cases> tags, evaluate handling for:
   - Empty list []
   - List with duplicate elements [2, 2, 2, 2]
   - Strictly decreasing list [5, 4, 3, 2, 1]
   - Negative numbers [-10, -5, 0, 5]
3. Inside <pseudocode> tags, map out the Binary Search (bisect_left) algorithm step-by-step.
4. Inside <code> tags, write the complete Python 3 implementation with type annotations and inline comments.
```

4. **Step 4: Lab Analysis**
   Compare the two outputs. Note how the forced intermediate tags guaranteed the optimal $O(N \\log N)$ solution instead of a slow $O(N^2)$ algorithm!

---

## Section 5: Socratic Discussion & Portfolio Assignment (10 Mins)

### Socratic Wrap-Up Questions:
1. *"Chain-of-Thought prompting increases token usage and latency. In what production scenarios is CoT necessary, and where is it wasteful?"*
2. *"How does forced XML tag structure (<thinking>, <code>) make it easier for software backend pipelines to parse AI outputs programmatically?"*

### Homework Assignment (Prompt Portfolio - Entry 4):
**Design a Self-Correcting Code Reviewer Prompt.**
Construct an R.C.T.C. prompt using Few-Shot CoT that:
1. Accepts a code snippet as input.
2. Analyzes it for memory leaks and security vulnerabilities inside `<vulnerability_analysis>` tags.
3. Proposes two alternative fixes inside `<branch_a>` and `<branch_b>` tags (Tree-of-Thought).
4. Outputs the final secure code inside `<code>` tags.

*Submission Requirement: Submit a Markdown report containing your prompt, the test code input, and the structured XML output.*
""", TargetFile="/workspace/scratch/student-lecture-session-2a.md")
