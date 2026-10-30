# Claude Plugins: 100-Minute Session Plan

A full step-by-step lesson plan for first-semester B.Tech students: they build and use one plugin, Study Buddy, in Claude chat. No code, no terminal. Every block has what to say, what to click, what students do, and what to check. Checked against Anthropic's plugin docs.

---

## Overview

| Time | Block | Format |
| :--- | :--- | :--- |
| **0-10** | 1. Hook and what a plugin is | Talk + live comparison |
| **10-25** | 2. Tour of the Plugins page | Live demo, students follow |
| **25-35** | 3. Design Study Buddy on paper | Worksheet |
| **35-40** | Break | — |
| **40-70** | 4. Build Study Buddy | Step-by-step build-along |
| **70-90** | 5. Lab: make it yours | Pairs |
| **90-100** | 6. Wrap-up, safety, quiz | Discussion |

---

## Learning Outcomes
By the end of this session, every student can:
1. Say in one sentence what a plugin is and name its three main parts.
2. Find, open, switch off and remove a plugin in Claude.
3. Build a working plugin by describing it in plain English.
4. Test it with three fixed prompts and improve it.
5. Decide whether a plugin is safe to add.

---

## Prerequisites & Requirements
- **Hardware:** Laptop (phones work for watching, not for building) with internet.
- **Account:** A Claude account signed in at `claude.ai` or the Claude desktop app.
- **Supplies:** Notebook and pen for the worksheet.
- **Access:** Access to `Customize > Plugins`. (Verify plugin availability on student accounts prior to class).

---

## Instructor Checklist

### Two Days Before:
- Open `Customize > Plugins` on your own account and confirm **Discover** and **Add** are visible.
- Send students a short message: bring a laptop, sign in to Claude before class, and open `Customize > Plugins` to confirm it loads. Ask anyone who cannot see it to notify you in advance.
- Print the worksheet from Block 3 (one per student).

### One Day Before:
- Run the full build (Block 4) once on your account. Note any menu label that differs from this plan and update notes.
- Keep your finished Study Buddy installed as a fallback.
- Save the three test prompts and the build prompt in a copyable note.

### Fifteen Minutes Before:
- Projector tested; browser zoom set to 125%.
- Claude signed in, one clean chat open, Study Buddy temporarily switched off for the hook demo.
- Worksheets distributed on desks.

---

## Key Vocabulary (Write on Board)

| Term | Plain Meaning |
| :--- | :--- |
| **Claude** | The AI assistant you chat with |
| **Prompt** | The message you type to Claude |
| **Instructions** | Rules that tell Claude how to behave |
| **Plugin** | A saved package of instructions and tools you can add to Claude |
| **Skill** | The part of a plugin that holds the instructions |
| **Command** | A named action you pick from the `/` menu |
| **Connector** | A link that lets Claude reach another app (e.g., email, calendar) |
| **Directory** | Anthropic's reviewed list of plugins in the Discover tab |
| **Enable / Disable** | Switch a plugin on or off without deleting it |
| **Test Prompt** | A message you reuse to check whether your plugin behaves well |

---

## Block 1 (0-10 min) | Hook & What a Plugin Is
**Goal:** Students observe the operational difference a plugin makes before hearing formal definitions.

* **Minute 0-1 (Welcome):** *"Today you will build your own add-on for Claude without writing any code. By the end, you will have a study helper you built yourself."*
* **Minute 1-5 (Live Comparison):**
  1. In a clean chat with Study Buddy switched off, type: `Teach me recursion.`
  2. Let Claude answer. Scroll so the class sees the long, general explanation.
  3. Switch Study Buddy on, open a new chat, and type the same prompt.
  4. Point out the contrast: shorter explanation, one everyday example, and one quiz question that waits for the student.
  5. Ask the class: *"What changed between the two answers?"* Write responses on the board.
* **Minute 5-9 (Deconstructing a Plugin):** Explain that a plugin is a saved set of instructions. Walk through the 3 components: **Skill** (rulebook), **Command** (trigger button), **Connector** (link to external apps).
* **Minute 9-10 (Check Understanding):** *"Which part of the plugin made Claude quiz us?"* (Answer: The Skill).

---

## Block 2 (10-25 min) | Tour of the Plugins Page
**Goal:** Every student locates `Customize > Plugins` and understands its interface.

* **Minute 10-12 (Navigation):** Direct students to `Customize > Plugins`. Walk the room to verify every screen has it open.
* **Minute 12-17 (Discover Tab):** Explore official directory plugins. Review descriptions, skills, and connector permissions (*Connected*, *Not connected*, *Not added*).
* **Minute 17-20 (Command Integration):** Open a new chat, type `/`, and show how skills appear in the command menu.
* **Minute 20-22 (Plugin Lifecycle):** Demonstrate toggling *Disable Plugin* and inspecting the *Remove* option.
* **Minute 22-25 (Safety Foundations):**
  1. A plugin's skill is an executable set of instructions; flawed skills produce misleading outputs.
  2. Connectors grant access to external service accounts.
  3. Directory plugins undergo security scanning; external file uploads do not.
  4. Inspect skill definitions before adding plugins from unverified sources.

---

## Block 3 (25-35 min) | Design Study Buddy on Paper
**Goal:** Translate pedagogical intent into precise operational prompts using a structured worksheet.

### Design Worksheet Matrix

| Design Parameter | Student Specification | Baseline Reference |
| :--- | :--- | :--- |
| **Target Audience** | First-year B.Tech undergraduates | First-year B.Tech students |
| **Input Topic** | Topic name (e.g., Pointers in C) | Any technical concept |
| **Primary Action** | Simple explanation + 1 everyday analogy | Clear conceptual breakdown |
| **Interactive Step** | Ask 3 sequential quiz questions (one by one) | Interactive evaluation |
| **Hint Protocol** | Small hints on request; never reveal answer | Scaffolded learning |
| **Tone & Style** | Concise, encouraging, jargon-free | Accessible & supportive |
| **Negative Constraints** | No lectures, no immediate answer reveals | Avoid text walls |

---

## Block 4 (40-70 min) | Build Study Buddy

### Step-by-Step Implementation:
1. **Start Building (40-43 min):** Navigate to `Customize > Plugins > Add > Create with Claude`.
2. **Input Master Prompt (43-50 min):**
   ```text
   Create a plugin called Study Buddy for first-year B.Tech students.
   When I give a topic, it should:
   1. Explain it in simple words with one everyday example.
   2. Ask me 3 quiz questions, one at a time, and wait for my answer.
   3. Give feedback after each answer.
   If I say hint, give a small hint, never the full answer.
   Keep replies short and friendly. Ask me anything you need to know.
   ```
3. **Refine via Claude Q&A (50-55 min):** Answer Claude's clarifying questions with specific rules.
4. **Save Plugin (55-58 min):** Save the assembled plugin to account.
5. **Inspect Skills (58-63 min):** Open `Customize > Plugins > Study Buddy > Skills` to review generated system instructions.
6. **Execution Testing (63-68 min):** Run 3 verification test cases:
   - *Test 1:* `Teach me pointers in C` $ightarrow$ Expect short explanation + 1 analogy + Question 1.
   - *Test 2:* Submit wrong answer $ightarrow$ Expect kind correction + Question 2.
   - *Test 3:* Type `hint` $ightarrow$ Expect subtle nudge without giving away full solution.
7. **Iterative Refinement (68-70 min):** Adjust word counts or strictness constraints based on test results.

---

## Block 5 (70-90 min) | Lab: Customization & Peer Testing

Students pair up, select a subject domain, and append domain-specific rules:

| Subject Domain | Specialized Prompt Constraint |
| :--- | :--- |
| **Programming in C** | Quiz using short code snippets; ask "What does this print?" |
| **Physics** | Include metric units and one physical real-world scenario |
| **Mathematics** | Show one worked example, then present a similar problem |
| **Engineering Graphics** | Explain using a step-by-step drafting procedure |
| **Communication Skills** | Provide a rough passage and ask student to rewrite professionally |

---

## Block 6 (90-100 min) | Safety Review, Quiz & Exit Ticket

### Safety Audit Checklist:
1. Is the plugin author known and trusted?
2. Have all skill instructions been read and inspected?
3. What connectors does it request, and are they strictly necessary?
4. Was it installed from the official directory or an unverified link?
5. Can it be disabled or removed immediately if required?

### Final Assessment Quiz:
* *Q1: What are the 3 main parts of a plugin?* **(Skills, Commands, Connectors)**
* *Q2: Where do you manage plugins?* **(Customize > Plugins)**
* *Q3: Does adding a plugin auto-connect external accounts?* **(No, connectors require separate authorization)**
* *Q4: Why run fixed test prompts after prompt changes?* **(To systematically verify performance delta)**