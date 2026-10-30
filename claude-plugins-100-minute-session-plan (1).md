# Claude Plugins: 100-Minute Session Plan

A full step-by-step lesson plan for first-semester B.Tech students: they build and use one plugin, **Study Buddy**, in Claude chat. No code, no terminal. Every block has what to say, what to click, what students do, and what to check. Checked against Anthropic's plugin docs on 16 Oct 2026.

---

## Overview

| Time | Block | Format |
| :--- | :--- | :--- |
| **0–10** | 1. Hook and what a plugin is | Talk + live comparison |
| **10–25** | 2. Tour of the Plugins page | Live demo, students follow |
| **25–35** | 3. Design Study Buddy on paper | Worksheet |
| **35–40** | Break | — |
| **40–70** | 4. Build Study Buddy | Step-by-step build-along |
| **70–90** | 5. Lab: make it yours | Pairs |
| **90–100** | 6. Wrap-up, safety, quiz | Discussion |

---

## Learning Outcomes
By the end, every student can:
1. Say in one sentence what a plugin is and name its three main parts.
2. Find, open, switch off, and remove a plugin in Claude.
3. Build a working plugin by describing it in plain English.
4. Test it with three fixed prompts and improve it.
5. Decide whether a plugin is safe to add.

---

## What Students Need
* A laptop (phones work for watching, not for building) with internet.
* A Claude account signed in at `claude.ai` or the Claude desktop app.
* A notebook and pen for the worksheet.
* Access to **Customize > Plugins**. Plugin availability depends on the plan, so verify this before class.

---

## Instructor Checklist

### Two Days Before
* Open **Customize > Plugins** on your own account and confirm **Discover** and **Add** are visible.
* Send students a short message: bring a laptop, sign in to Claude before class, and open **Customize > Plugins** to confirm it loads. Ask anyone who cannot see it to tell you in advance.
* Print the worksheet from Block 3, one per student.

### One Day Before
* Run the whole build (Block 4) once on your account. Note any menu label that differs from this plan and fix the doc.
* Keep your finished Study Buddy installed as the fallback.
* Save the three test prompts and the build prompt in a note you can copy from.

### Fifteen Minutes Before
* Projector tested, browser zoom at 125% so the back row can read.
* Claude signed in, one clean chat open, Study Buddy temporarily switched off so the hook demo shows the difference.
* Worksheets on desks.

---

## Words Students Must Know

| Word | Plain Meaning |
| :--- | :--- |
| **Claude** | The AI assistant you chat with |
| **Prompt** | The message you type to Claude |
| **Instructions** | Rules that tell Claude how to behave |
| **Plugin** | A saved package of instructions and tools you can add to Claude |
| **Skill** | The part of a plugin that holds the instructions |
| **Command** | A named action you pick from the `/` menu |
| **Connector** | A link that lets Claude reach another app, like email or a calendar |
| **Directory** | Anthropic's reviewed list of plugins in the Discover tab |
| **Enable / disable** | Switch a plugin on or off without deleting it |
| **Test prompt** | A message you reuse to check whether your plugin behaves well |

*Write these on the board in the first 10 minutes. Point back to them all session.*

---

## Block 1 (0–10 min) | Hook and What a Plugin Is
**Goal:** Students see the difference a plugin makes before hearing any definition.

### Minute 0–1: Welcome
* **Say:** *"Today you will build your own add-on for Claude, without writing any code. By the end you will have a study helper you built yourself."*

### Minute 1–5: Live Comparison
1. In a clean chat with Study Buddy switched off, type: `Teach me recursion.`
2. Let Claude answer. Scroll so the class sees the long, general explanation.
3. Switch Study Buddy on, open a new chat, and type the same prompt.
4. Point out the differences: shorter, one everyday example, then one quiz question that waits for the student.
5. Ask the class: *"What changed between the two answers?"* Take three answers. Write them on the board.

### Minute 5–9: What a Plugin Is
* **Say:** *"A plugin is a saved way of helping that Claude follows. You can add it, switch it off, or remove it in one click."*
* Walk through the three parts from the word list: **skill**, **command**, **connector**.
* **Analogy:** The skill is the rulebook, the command is the button you press, the connector is a link to another app. Today we only use the rulebook.

### Minute 9–10: Check Understanding
* **Ask:** *"Which part of the plugin made Claude quiz us?"* (**Answer:** The skill.)
* If fewer than half answer, repeat the analogy once.

---

## Block 2 (10–25 min) | Tour of the Plugins Page
**Goal:** Every student can find the Plugins page and explain what they see. Students follow on their own laptops.

### Minute 10–12: Open the Page
1. In `claude.ai` or the desktop app, find **Customize** on the left side.
2. Select **Plugins**. The page lists the plugins on your account and has a **Discover** tab and an **Add** button.
3. **Say:** *"Everything we do today starts on this page."*
4. Walk the room and confirm every student has it open. Help anyone stuck now, not later.

### Minute 12–17: Discover
1. Select **Discover**. These are plugins you can add: Anthropic's directory and any your organization provides.
2. Select any one plugin. Do not press Add.
3. Read its description aloud. Ask: who is this for, and what would it do for you?
4. Open its tabs. Show **Skills** (the rulebook) and **Connectors** (links to other apps).
5. Find the Connectors tab states: *Connected*, *Not connected*, *Not added*.
6. **Say:** *"Adding a plugin does not sign you in to anything. You choose separately whether to connect."*

### Minute 17–20: Where Plugins Appear
1. Open a new chat and type `/` in the message box.
2. Show the menu. Skills from your plugins are listed, with the plugin name beside each.
3. **Say:** *"You can pick a skill from here, or just describe the task and Claude will use the matching skill."*

### Minute 20–22: Switch Off and Remove
1. Open any plugin you have added.
2. Show the **Disable plugin** toggle. Turn it off, then on.
3. Show the plugin's menu and the **Remove** option. Do not remove anything.
4. **Say:** *"Nothing here is permanent, so you can experiment safely."*

### Minute 22–25: Safety Talk
Say these four points slowly, and ask students to write them down:
1. A plugin's skill is a set of instructions Claude will follow, so a bad one can mislead you.
2. A connector can reach outside services using your account.
3. Plugins in the directory are scanned and reviewed by Anthropic. Plugins from a random link or uploaded file are not.
4. Read what is inside before you add it, and only add plugins from sources you trust.

* **Ask:** *"A senior sends you a plugin file and says it will do your assignments. It wants to connect to your email. What do you do?"*
* Take two answers. Good answers: read it first, ask why it needs email, do not add it if unsure.

---

## Block 3 (25–35 min) | Design Study Buddy on Paper
**Goal:** Students turn an idea into clear instructions before they touch Claude. Clear instructions are what make a plugin good.

### Minute 25–27: Explain Why
* **Say:** *"Claude can only follow what you tell it clearly. If you say 'help me study', you get random help. If you say 'explain in simple words, give one example, then ask three questions one by one', you get a study buddy."*

### Minute 27–33: Fill the Worksheet
Hand out the worksheet below. Students fill the right column on paper, alone, for 4 minutes. Then 2 minutes comparing with the person next to them.

| Question | Your Answer | Example Answer |
| :--- | :--- | :--- |
| **Who is it for?** | First-year B.Tech students | First-year B.Tech students |
| **What do I give it?** | A topic, like pointers in C | A topic, like pointers in C |
| **What should it do first?** | Explain in simple words with one everyday example | Explain in simple words with one everyday example |
| **What next?** | Ask 3 quiz questions, one at a time, and wait for my answer | Ask 3 quiz questions, one at a time, and wait for my answer |
| **What if I am stuck?** | Give a small hint when I say hint, never the full answer | Give a small hint when I say hint, never the full answer |
| **How should it sound?** | Short, friendly, no jargon without explanation | Short, friendly, no jargon without explanation |
| **What must it never do?** | Give a long lecture or give answers before I try | Give a long lecture or give answers before I try |

### Minute 33–35: Share
Ask two students to read one answer each. Praise specifics (e.g., *"Wait for my answer is exactly the kind of clear rule that works"*). Say: *"Keep your worksheet, we use it in the next block."*

---

## Break (35–40 min)
Leave the build prompt from Block 4 on the projector. Walk around and help anyone who still cannot see the Plugins page.

---

## Block 4 (40–70 min) | Build Study Buddy
**Goal:** Every student builds, saves, and tests a working plugin. Move at the pace of the slowest pair, but cap each step at its time.

### Step 1 (40–43 min): Start Building
1. Open **Customize > Plugins**.
2. Select **Add**.
3. Choose **Create with Claude**. A new conversation opens with a request to create a plugin already filled in.
4. Do not press send yet.
* **Check:** Every screen shows the new conversation with text already in the message box. If a student sees a form instead, they chose *Create a plugin* by mistake. Ask them to go back and pick *Create with Claude*.

### Step 2 (43–50 min): Describe Your Plugin
1. Select the text in the message box and replace it with the prompt below. Students copy it from the projector or from your shared note.
2. Ask students to compare it with their worksheet, line by line, and change anything that differs from their own answers.
3. Send the message.

```text
Create a plugin called Study Buddy for first-year B.Tech students.
When I give a topic, it should:
1. Explain it in simple words with one everyday example.
2. Ask me 3 quiz questions, one at a time, and wait for my answer.
3. Give feedback after each answer.
If I say hint, give a small hint, never the full answer.
Keep replies short and friendly. Ask me anything you need to know.
```

* **Say:** *"Notice that this is just our worksheet written as a message. Nothing more."*

### Step 3 (50–55 min): Answer Claude's Questions
1. Claude will ask follow-up questions. Read each one aloud.
2. Students answer in their own words, in short sentences.
3. Ask the class after: which questions did our worksheet already answer? Which ones surprised us?
* **Check:** No student should skip questions or reply with "ok" only. Vague answers lead to a vague plugin.

### Step 4 (55–58 min): Save the Plugin
1. When Claude finishes, it assembles the plugin and offers it as a file.
2. Select the option to save it to your account.
3. Wait for the confirmation before moving on.
* **Check:** Every student sees a saved confirmation. Anyone without it waits with a neighbour who has it.

### Step 5 (58–63 min): Review What Claude Made
1. Open **Customize > Plugins**.
2. Find **Study Buddy** in your list and select it.
3. Open the **Skills** tab and read the instructions.
4. **Ask:** *"Does this match what we asked for? Is anything missing? Is anything surprising?"*
5. Take two answers. Point out that reading a plugin's contents is exactly the safety habit from Block 2.

### Step 6 (63–68 min): Test with Three Prompts
1. Open a new chat. (*This matters: plugins load into new chats.*)
2. Run the three test prompts below in order, in the same chat.
3. For each, compare the reply with the right column. Tick or cross on paper.

| Test | Type This | What Good Looks Like |
| :--- | :--- | :--- |
| **1** | `Teach me pointers in C` | Short explanation, one everyday example, then quiz question 1 only |
| **2** | A wrong answer on purpose | Kind correction, explains why, then moves to question 2 |
| **3** | `hint` | A small nudge, not the full answer |

* **Say:** *"These three prompts are our test set. After every change we run the same three, so we know whether the change helped."*

### Step 7 (68–70 min): Improve One Thing
1. Each student picks one flaw from their tests (e.g., replies too long, or showed the answer too early).
2. Open the plugin and adjust its instructions if your account offers editing. If not, repeat steps 1 to 4 with the fix added to the prompt (e.g., *"Keep each reply under 150 words"*).
3. Run the same three tests again and note whether it improved.
*(If time is short, do this as homework.)*

---

## Block 5 (70–90 min) | Lab: Make It Yours
**Goal:** Students adapt Study Buddy for a real subject and test a classmate's version.

### Minute 70–72: Form Pairs and Pick a Subject
1. Pair students. Each pair picks one subject they study this semester.
2. Give each pair one twist from the table below, or let them invent one.

| Subject | Add This Line to the Plugin Prompt |
| :--- | :--- |
| **Programming in C** | Quiz me with short code snippets and ask: what does this print? |
| **Physics** | Always include units and one real-life example |
| **Mathematics** | Show one worked example, then give me a similar problem |
| **Engineering Graphics** | Explain with a step-by-step drawing procedure |
| **Communication Skills** | Give me a short passage and ask me to rewrite it better |

### Minute 72–82: Build Version 2
1. Repeat Block 4 steps 1 to 4 with the twist added, and name the plugin **Study Buddy Physics**, **Study Buddy C**, and so on.
2. Both partners build their own version.
3. Circulate. Check three things: the instructions are specific, the quiz waits for an answer, and the hint rule exists.

### Minute 82–88: Swap and Test
1. Swap laptops with your partner.
2. Run three test prompts on their plugin. Write one thing that worked and one thing to improve.
3. Tell your partner kindly, in one sentence each.

### Minute 88–90: Share
Two or three pairs show one test and say what they would improve next.

---

## Block 6 (90–100 min) | Wrap-Up, Safety, and Quiz

### Minute 90–92: Recap
* **Say:** *"A plugin packages skills, commands, and connectors. We built one by writing clear instructions, saving it, testing it with three prompts, and improving it."*

### Minute 92–94: Safety Checklist
Students copy this into their notebooks:
1. Do I know who made this plugin?
2. Have I read its skills?
3. What connectors does it want, and why?
4. Did it come from the directory or a random link?
5. Can I switch it off or remove it if it misbehaves? (*Yes, always.*)

### Minute 94–99: Quiz
Ask aloud. Students answer on paper, then reveal:

| Question | Answer |
| :--- | :--- |
| What are the three main parts of a plugin? | Skills, commands, connectors |
| Where do you add, disable, or remove a plugin? | Customize > Plugins |
| Does adding a plugin sign you in to its connectors? | No, you connect each one separately |
| Why run the same three tests after each change? | To see whether the change actually helped |
| Which plugins has Anthropic reviewed? | The ones in the directory, not random links or uploads |

### Minute 99–100: Exit Ticket
Each student writes one sentence: *"One thing I will use my plugin for is..."* Collect them as they leave.

---

## Homework
Build a new plugin for one problem in your own life, such as a revision planner or a lab-report helper. Submit a half-page note with five items: what it does, your three test prompts, one thing you improved, one safety check you made, and the answers on your safety checklist.

| Criterion | Weight |
| :--- | :--- |
| **Clear, specific instructions** | 40% |
| **Testing and improvement** | 30% |
| **Safety note** | 20% |
| **Creativity** | 10% |

---

## Troubleshooting (If Something Goes Wrong)

| Problem | Fix |
| :--- | :--- |
| Student cannot see Customize or Plugins | Check the plan and app version. Pair them with a neighbour for the session |
| Plugin does not show in the `/` menu | Check it is enabled, then open a new chat |
| Claude ignores the quiz | Make the instruction firmer (e.g., *"Always ask question 1 before anything else"*) |
| Replies too long | Add: *"Maximum 150 words per reply"* |
| Claude gives the answer instead of a hint | Add: *"Never reveal the answer when I say hint"* |
| Saved plugin cannot be found | Open **Customize > Plugins** and check the full list, including disabled plugins |
| Student is far behind | Let them use your finished Study Buddy and rejoin at Step 6 |

---

## Questions Students Often Ask

* **Can I share my plugin with friends?** A plugin created this way is for you. Sharing with others needs an organization plan or another route, so do not promise this.
* **Is this coding?** No. You describe what you want in plain English, and Claude assembles the plugin.
* **Will it work in every chat?** It works in new chats on the account you saved it to. Open a new chat after saving.
* **Can it break my account?** Switching a plugin off or removing it undoes it. Be careful with connectors, which reach outside services.
* **Do I need to pay?** Check your plan. Plugin availability depends on it.

---

## If Time Runs Short
1. Cut Step 7 and the pair demo first.
2. Then shorten Block 2 by skipping the Discover demo.
3. **Never cut the worksheet or the three-prompt test.** Those carry the learning.

---

## References
* `claude.com/docs/plugins/overview`: Using plugins in chat
* `claude.com/docs/plugins/create-with-claude`: Building one without code
