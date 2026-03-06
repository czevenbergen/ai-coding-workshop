# Workshop: Building with AI

**Duration:** Full day (9:00–16:45)
**Audience:** Non-technical to slightly technical (employees at a legal/public affairs consultancy)
**Group size:** 10 participants, 3 support staff
**Stack:** Python 3.12, FastAPI, Jinja2 templates, Pico CSS, uv
**Tools:** VS Code + GitHub Copilot
**Application:** Stakeholder Directory

## Principles Taught

| # | Principle | Core Idea |
|---|---|---|
| 1 | AI as Collaborator | AI is a thinking partner from ideation through execution. You stay in the driver's seat — reviewing, deciding, testing. |
| 2 | Work in Small Steps | One instruction at a time. Plan what you need, execute it, review the result, move on. Resist the urge to ask for everything at once. |
| 3 | Context Shapes Output | The AI only knows what you tell it and what it can see. Specific prompts beat vague ones. Good project structure and persistent instructions multiply the effect. |
| 4 | Verify, Don't Trust | Read everything the AI gives you. It fails in predictable ways — hallucination, over-engineering, drift. Your job is to catch these, not avoid them. |

## Distribution

Participants receive a zip file by email before the workshop containing:
- The boilerplate app (ready to run with `uv sync && uv run fastapi dev app/main.py`)
- The step-by-step guide
- The preparation guide

If a participant arrives without the zip, support staff have USB drives with the folder ready to copy.

## Materials

| Material | Purpose |
|---|---|
| Preparation guide | Pre-workshop: install Python 3.12, VS Code, Copilot extension, uv. Sent by email with the zip. |
| Boilerplate app | Hello-world FastAPI app + one template + Pico CSS. Single `uv sync && uv run fastapi dev` to start. |
| Step-by-step guide | Primary participant document — one section per session, with exercises and prompts to try |
| Principles reference card | One-pager takeaway summarizing the 4 core principles. Handed out at the end. |
| Backup folders | Pre-built app states after Sessions 1 and 2. Support staff hand these out if someone's app is broken beyond repair. |

---

## The Day

### Opening — 45 min (9:00–9:45)

**Goal:** Set expectations, verify setup, orient participants to Copilot.

**What happens:**

**Intro (10 min):**
- Welcome, agenda overview, what we're building today (a stakeholder directory — a tool to track contacts, organizations, and categories)
- Framing: "You will build a working web application today. You don't need to understand every line of code. But you will understand what it does and how to change it."
- Introduce the 4 principles briefly — just names and one-liners. "We'll come back to these throughout the day."

**Setup verification (15 min):**
- Everyone opens their project folder in VS Code
- Run `uv sync && uv run fastapi dev app/main.py`
- See the welcome page in the browser
- Support staff help anyone who didn't complete the preparation guide. This is why we budgeted 15 minutes — expect 2-3 people to need help.

**Copilot orientation — first prompt (20 min):**
- Experiential walkthrough. Everyone follows along by sending their first prompt:
  - Open Copilot Chat panel (`Ctrl+Cmd+I`)
  - Confirm that **Agent** is selected in the agent picker at the top of the Chat view. Explain briefly: "Agent mode means Copilot will edit your files directly when you ask it to build something. You'll see changes appear in the editor in real time."
  - **First prompt:** Everyone types: "Change the welcome page so it says 'Welcome, [your name]!' and add a short description of what this app will do." Submit it and watch Copilot edit the file in real time. This is the "wow" moment — let it land.
  - **Teach Keep/Undo through the change they just made:** Walk through the inline diff. Show the editor overlay controls (Up/Down to navigate edits). Point out the Keep and Undo buttons. Key message: **"Always read the changes before you click Keep. Once you Keep, it's final."** Have everyone click Keep.
  - **Teach checkpoints through undoing that change:** In the Chat view, have everyone hover over the message they just sent and point out the Restore Checkpoint option. Click it — watch the personalized welcome disappear and the original return. "If something goes wrong today, you can always come back to a checkpoint."
  - Show how to start a new conversation (and why you'd want to — fresh context, no baggage)
- Key messages:
  - "Agent mode edits your files directly. You type what you want; it makes the changes."
  - "Review before you accept. Always read the diff before clicking Keep."
  - "Checkpoints are your safety net. Every message creates one."

**Instructor note:** Don't rush the orientation. This is the foundation for everything. Every participant must have successfully sent a prompt, seen a change, clicked Keep, and restored a checkpoint before Session 1 begins. If someone can't find the chat panel or doesn't understand Keep vs. Undo, they'll struggle all day.

---

### Session 1: First Feature — 60 min (9:45–10:45)

**Goal:** Build the stakeholder list page. First real experience building with AI.

**Principles taught:** AI as Collaborator, Work in Small Steps.

**What happens:**
- The guide opens with a short "How a web app works" orientation — three concepts (data, routes, templates) in plain language. This gives non-technical participants a mental model before they start building.
- Pre-generated sample data already exists in `app/data/stakeholders.json`. Participants open this file and read through it to understand the data shape before writing any code.
- The guide then walks participants through building the page. Step by step, one piece at a time:
  1. **Look at the data:** Participants open `app/data/stakeholders.json` and read the pre-generated sample data. This orients them to the data structure before building anything.
  2. **Create a route:** Ask Copilot to make the homepage show stakeholders instead of the welcome page. The guide provides an example prompt in plain language (no jargon like "FastAPI" or "Jinja2") with a note that it's fine to copy it directly. It explains what a "route" is in one sentence. Review the changes, then Keep.
  3. **Create a template:** Ask Copilot to create the HTML page. The guide provides an example prompt focused on what they want to *see* (heading, table/cards, stakeholder fields) rather than technical details. Copilot will create the file automatically and use the existing styling. Review, then Keep.
  4. **Run and see:** The app should reload automatically. Open the browser. If there's an error, copy it into Copilot Chat.
  5. **Read the code:** Spend 5 minutes reading what Copilot generated. Pick one thing you don't understand and ask Copilot to explain it.
- The guide provides example prompts for the route and template steps that are deliberately less technical than before — they describe what the participant *wants* rather than how to implement it. A note says "you can copy this directly or adapt it" — giving non-technical participants explicit permission to copy.
- After each step, participants review the inline diff before clicking Keep. This builds the review habit early.
- Support staff focus on people who are stuck at any step. Common issues: template not found errors, the app not reloading, accidentally clicking Keep before reviewing.

**Instructor moment (at the end):** "You just built a working web page with AI as your partner. Notice how we did it: one piece at a time. First the data, then the route, then the page. You didn't ask for everything at once — you built one piece, checked it, then moved on. That's *working in small steps*. Also notice — you spent more time reading what the AI gave you than writing prompts. That ratio is normal. The real skill is evaluation."

**Lesson learned:** One step at a time. Build one piece, review it, then build the next. The AI writes the code; you steer and verify.

---

*Break — 15 min (10:45–11:00)*

---

### Session 2: Adding Features + Dealing with Failure — 75 min (11:00–12:15)

**Goal:** Build a second feature with less scaffolding, then experience and recover from AI failure.

**Principles taught:** Context Shapes Output, Verify, Don't Trust.

**Part A — Add stakeholder form (40 min):**
- Build a form to add new stakeholders. This is more complex: a second route, form handling, writing to the JSON data file.
- The guide provides a graduated scaffold: an example prompt for the first piece (displaying the form) but no example prompt for the second piece (handling submission). This lets participants practice writing their own prompts while still having a safety net for the first unfamiliar task.
- The guide tells participants *what* to build (a form with fields for name, organization, role, category) and the incremental approach (display the form first, then handle submission).
- Key teaching moment: when things don't work, describe the *specific* problem. "The form submits but the stakeholder doesn't appear in the list" beats "it's not working."

**Part B — The failure experiment (35 min):**
- The guide presents two prompts. Participants try both in Agent mode:

  **Prompt A (vague):**
  > "Make my stakeholder app better and more professional. Add all the features it needs."

  **Prompt B (specific):**
  > "Add a navigation bar to base.html with links to the stakeholder list and the add stakeholder page. Use the existing Pico CSS classes."

- **Prompt A flow:** Participants open a new conversation and submit the vague prompt. Agent mode runs — it will edit multiple files, possibly add routes, restructure code, maybe run terminal commands. The chaos is visible and real: diffs everywhere, files they didn't ask to change, maybe the app breaks. Participants observe the damage but **do not click Keep**.
- **Revert:** In the Chat view, participants hover over the Prompt A message and click **Restore Checkpoint**. All changes revert. Their app is back to its working state.
- **Prompt B flow:** Participants open another new conversation and submit the specific prompt. Agent mode runs — it edits one file, adds a clean nav bar. Participants review the diff, verify it in the browser, then click Keep.
- **Group discussion:** "What did the AI do differently? Why? What made Prompt B work better? What would have happened if you had clicked Keep on Prompt A?"
- Instructor names the failure modes they just saw: hallucination, over-engineering, drift. These aren't bugs — they're predictable patterns. The checkpoint saved them.

**Instructor moment:** "What you just saw is why *context shapes output* and *verify, don't trust* matter. The vague prompt gave the AI no constraints, so it invented its own. The specific prompt told it exactly what you wanted — and it delivered. And notice: you didn't click Keep on the bad result. You reviewed, saw the mess, and used a checkpoint to go back. That's the workflow — review first, accept only what you understand."

**Lesson learned:** AI fails predictably. Specific prompts with clear context produce better results. Always review before accepting. When things go wrong, use a checkpoint to revert and start fresh with a better prompt.

---

*Lunch — 60 min (12:15–13:15)*

---

### Session 3: Context and Configuration — 60 min (13:15–14:15)

**Goal:** Teach persistent context. Build another feature with less guidance and better results.

**Principles taught:** Context Shapes Output (deepened).

**What happens:**

**Part A — Create a copilot instructions file (20 min):**
- The guide introduces `.github/copilot-instructions.md`: "Until now, you've been telling the AI what your project is every time. What if it just *knew*?"
- Participants ask Copilot to create the file: "Create a file at `.github/copilot-instructions.md` that describes this project — what it does, what technologies it uses, and how data is stored. Keep it short and practical." This is more consistent with the workshop's own principle (AI as Collaborator) and avoids the awkwardness of manually creating dotfile folders.
- Participants review and edit the generated file — adding rules, removing things that don't seem right, making it theirs. Then Keep.
- The guide explains: Copilot reads this file automatically for every conversation. It's persistent context.

**Part B — Build a new feature (40 min):**
- With copilot instructions in place, participants add a new feature. The guide offers options but doesn't dictate:
  - Stakeholder detail page (click a name → see full info)
  - Search/filter stakeholders by name or organization
  - Delete a stakeholder
  - Group stakeholders by category
- This is the first time participants choose what to build. The guide gives general advice ("plan before you prompt, work incrementally") but no step-by-step instructions.
- Participants should notice: Copilot now respects the project conventions without being reminded. It follows the existing code patterns. The results are better because the context is richer.

**Instructor moment:** "Compare this to Session 1. Less explaining, better results. That's the compound effect of context — your instructions file, your existing code patterns, your prompt specificity. All of it adds up."

**Lesson learned:** Persistent context reduces friction. Small configuration investments yield outsized returns.

---

*Break — 15 min (14:15–14:30)*

---

### Session 4: Free Build — 105 min (14:30–16:15)

**Goal:** Independent application of all principles. Extended building time.

**Principles taught:** All — applied without guidance.

**What happens:**
- Open-ended building time. Participants choose what to add to their stakeholder directory.
- They can work solo or in pairs — their choice. Encourage pairing if someone is less confident.
- Suggestions for those who need direction:
  - Search/filter by name, organization, or category
  - Edit existing stakeholders
  - Stakeholder notes or interaction history
  - Export stakeholder list (as a simple text/CSV page)
  - Tags or labels for stakeholders
  - Sort by name, organization, or date added
  - Visual improvements — better cards, category badges
- Support staff circulate but let people work independently. Intervene if someone is stuck for more than 5 minutes.
- At the 60-minute mark, give a time check: "45 minutes left. If you want to demo, start wrapping up your current feature."

**Instructor note:** This session is long on purpose. The afternoon is where participants internalize the principles through repetition. Don't cut it short. The difference between their Session 1 prompts and their Session 4 prompts is the most visible evidence of learning.

**Lesson learned (self-discovered):** All principles, applied independently. Participants feel the difference between their early experience and now.

---

### Closing — 30 min (16:15–16:45)

**Goal:** Reflect, consolidate, celebrate.

**What happens:**
- Show-and-tell: volunteers show what they built (quick screen shares, 2 minutes each, max 4-5 demos)
- Group reflection (guided questions):
  - "What surprised you today?"
  - "What was harder than expected? Easier?"
  - "How would you describe working with AI to a colleague who wasn't here?"
- Instructor revisits the 4 principles using real examples from the day:
  - "In the opening, you sent your first prompt and watched AI edit your code — *AI as Collaborator*"
  - "In Session 1, you built one piece at a time, reviewed, then moved on — *Work in Small Steps*"
  - "The vague prompt failed; the specific prompt worked — *Context Shapes Output*"
  - "You read the code, spotted problems, used checkpoints to go back when needed — *Verify, Don't Trust*"
- Hand out the principles reference card
- Close: "You built a working web application today using AI as your partner. The principles you practiced apply to any tool, any project, any domain."

---

## Session-Principle Matrix

| Session | Principles | Lesson Learned |
|---|---|---|
| Opening | AI as Collaborator (first taste) | You type what you want; AI makes changes. Review before accepting; checkpoints are your safety net. |
| 1. First Feature | AI as Collaborator, Work in Small Steps | One step at a time. Build one piece, review it, then build the next. |
| 2. Features + Failure | Context Shapes Output, Verify, Don't Trust | AI fails predictably. Specific context produces better results. Review before accepting; use checkpoints to revert and start fresh. |
| 3. Context & Config | Context Shapes Output (deepened) | Persistent context reduces friction. Small configuration investments yield outsized returns. |
| 4. Free Build | All | Self-directed application and consolidation. |

## Support Staff Guide

**Role:** Help participants who are stuck. Don't solve for them — guide them toward asking Copilot the right question.

**Common issues by session:**

| Session | Likely problems | How to help |
|---|---|---|
| Opening | Setup failures, Copilot not signed in, first prompt doesn't produce a visible change | Walk through prep guide steps individually. If the first prompt doesn't edit the welcome page, check that Agent mode is selected and the app is running. |
| 1 | JSON file not loading, template not found, app won't start | Check file paths, check the error message, help them ask Copilot to fix it |
| 2A | Form doesn't submit, data doesn't save to JSON, POST route not working | Help them describe the problem specifically to Copilot — not "it's broken" but "the form submits but nothing appears" |
| 2B | Accidentally clicked Keep on Prompt A, or can't find Restore Checkpoint | Help them find the checkpoint: hover over the message in the Chat view → Restore Checkpoint. If they already clicked Keep, hand them the Session 2 backup folder. |
| 3 | Copilot instructions not being picked up, Copilot creates the file in the wrong location | Check file path (must be `.github/copilot-instructions.md`), restart the chat |
| 4 | Ambitious scope, stuck on complex features | Help them decompose. "What's the smallest version of this that would work?" |

**When to intervene:** If someone has been stuck for more than 5 minutes without making progress. During Session 4, give more space — 10 minutes before stepping in.

**Backup folders:** Have pre-built app states ready for after Session 1 and after Session 2. If someone's app is irreparably broken, hand them the backup and let them continue from a clean state. Don't make a big deal of it — "Here's a fresh copy, you're all caught up."
