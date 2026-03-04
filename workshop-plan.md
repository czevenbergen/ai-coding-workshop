# Workshop: Building with AI

**Duration:** Full day (9:00–17:00)
**Audience:** Non-technical to slightly technical
**Group size:** 10 participants, 3 support staff
**Stack:** Python 3.12, FastAPI, Jinja2 templates, Pico CSS, uv
**Tools:** VS Code + GitHub Copilot (out-of-the-box, no custom config until Session 5)
**Application:** Personal Recipe Book

## Principles Taught

| # | Principle | Core Idea |
|---|---|---|
| 1 | AI as Collaborator | AI is a thinking partner from ideation through execution. You stay in the driver's seat — reviewing, deciding, testing. |
| 2 | Plan → Execute → Iterate | Break work into small steps. One instruction at a time. Review before moving on. |
| 3 | Context is Everything | The AI only knows what's in its context window. It doesn't know your full codebase or your intent unless you provide it. |
| 4 | Prompting as a Skill | Specific, constrained prompts with clear intent produce dramatically better results than vague requests. |
| 5 | Common Failure Modes | Hallucination, drift, over-engineering, stale context — recognizing these patterns lets you intervene early. |
| 6 | Decomposition | Large features should be broken into small, independently completable pieces. |
| 7 | Existing Code & Patterns | AI works best when it can follow existing patterns. Consistency in your codebase compounds into better AI output. |
| 8 | Incremental over Ambitious | Ask for small changes, not complete rewrites. The urge to ask for everything at once leads to worse results. |
| 9 | Reading > Writing | You'll spend more time reading and evaluating AI output than writing prompts. That's normal — it's the job. |

## Materials to Create

| Material | Purpose |
|---|---|
| Preparation guide | Pre-workshop: install Python 3.12, VS Code, Copilot extension, uv |
| Boilerplate repo | Hello-world FastAPI app + one template + Pico CSS. Single `uv sync && uv run fastapi dev` to start. |
| Step-by-step guide | Primary teaching document — one section per session, with exercises and lesson-learned prompts |
| Checkpoint branches | `checkpoint/01` through `checkpoint/05` — catch-up points between sessions |
| Principles reference card | One-pager takeaway summarizing all 9 principles |

---

## The Day

### Opening — 30 min (9:00–9:30)

**Goal:** Set expectations, verify setup, build excitement.

**What happens:**
- Brief intro: what AI-assisted coding is (and isn't)
- Live demo: instructor builds something small in 2 minutes with Copilot to show the workflow in action
- Setup verification: everyone clones the repo, runs `uv sync && uv run fastapi dev`, sees the hello-world page in their browser
- Framing: "You will build a working web application today. You don't need to understand every line of code. But you will understand what it does and how to change it."

**Lesson learned:** None yet — this is logistics and motivation.

---

### Session 1: Ideation — 45 min (9:30–10:15)

**Goal:** Design the recipe app collaboratively with AI.

**Principles taught:** AI as Collaborator, Prompting as a Skill.

**What happens:**
- Participants open Copilot Chat and design their app through conversation. No coding yet — just thinking together with the AI.
- Suggested prompts to try (but not mandated — they should experiment):
  - "I want to build a personal recipe book web app. What features should it have?"
  - "Which of these should I build first and why?"
  - "Can you describe a simple data model for recipes?"
- After 20 minutes, group discussion: compare what different people got. Different prompts → different designs. Same prompt → sometimes different designs.
- Each participant picks 3-4 features to build during the day and writes them down (on paper or in a notes file).

**Instructor moment:** "Notice how the AI gave you different answers based on how you asked? That's not randomness — it's responding to context and specificity. The more precise you are about what you want, the more useful the response. But also — the AI surfaced ideas you might not have thought of. That's the collaboration."

**Lesson learned:** The AI is a useful thinking partner, but different inputs produce different outputs. You shape the conversation.

---

### Session 2: First Feature — 60 min (10:15–11:15)

**Goal:** Build the recipe list page using the plan-execute-iterate cycle.

**Principles taught:** Plan → Execute → Iterate, Incremental over Ambitious, Reading > Writing.

**What happens:**
- The guide explicitly walks through the cycle:
  1. **Plan:** "We need a route that returns a list of recipes, and a template that displays them."
  2. **Execute:** Ask Copilot to generate the route. Review it. Then ask for the template. Review it. One piece at a time.
  3. **Iterate:** Run the app. See what happens. If something's broken, describe the problem to Copilot and ask for a fix.
- Recipes are hardcoded as a Python list of dicts — no database. Keep it simple.
- The guide intentionally does NOT give exact prompts. Participants must formulate their own. This is where the support staff help people who get stuck.
- After getting it working, the guide prompts: "Your app works. Now spend 5 minutes *reading* the code the AI generated. Can you follow what it does? Pick one thing you don't fully understand and ask Copilot to explain it."

**Instructor moment:** "Who got it working on the first try? Who had to ask Copilot to fix something? That iteration isn't failure — it IS the process. Also notice: you spent more time reading and evaluating what the AI gave you than writing prompts. That ratio is normal and stays that way."

**Lesson learned:** Work in small steps, not big leaps. The real skill is in evaluating AI output, not producing prompts.

---

*Break — 15 min (11:15–11:30)*

---

### Session 3: Adding Features + Dealing with Problems — 75 min (11:30–12:45)

**Goal:** Build a more complex feature, then experience and recover from failure.

**Principles taught:** Prompting as a Skill (reinforced), Common Failure Modes, Context is Everything.

**Part A — Add recipe form (40 min):**
- Build a form to add new recipes. This introduces: a second route, HTML form handling, data mutation (appending to the list).
- More complex than Session 2 — participants need to give Copilot more context about what exists and what they want.
- Incremental approach reinforced: first the route, then the template, then wire them together. Not all at once.

**Part B — Intentional failure exercise (35 min):**
- The guide gives everyone a deliberately bad prompt to use: something like *"Make the app better and more professional."*
- They submit it and observe what happens: the AI may restructure code they don't understand, add features they didn't ask for, introduce libraries they've never heard of, or hallucinate APIs.
- Then the guide walks them through recovery:
  1. First, try to *correct* the AI in the same conversation (3 minutes). See if you can steer it back.
  2. Then, undo everything, start a fresh chat, and redo it with a specific prompt. Compare the effort.
- Group discussion: "What did the AI do? Why? What was the prompt missing?"

**Instructor moment:** "What you just saw has names. When the AI invents things that don't exist — that's *hallucination*. When it adds complexity you didn't ask for — that's *over-engineering*. When it changes things based on the messy earlier conversation — that's *stale context*. These aren't bugs. They're predictable patterns. Now that you can name them, you'll spot them faster. Also: the AI only sees what's in its current window — your conversation, your open files. It doesn't know your whole project. That's why specific prompts matter."

**Lesson learned:** AI fails in predictable ways. Learning to recognize these patterns is more valuable than avoiding them. When the conversation goes off track, sometimes a fresh start is faster than a fix.

---

*Lunch — 45 min (12:45–13:30)*

---

### Session 4: Structure and Patterns — 60 min (13:30–14:30)

**Goal:** Refactor into clean structure, then build within that structure.

**Principles taught:** Decomposition, Existing Code & Patterns.

**What happens:**
- By now, most participants have everything in one or two files. The guide introduces the idea of structure:
  - Routes in one file, templates in a folder, data/models separate.
- They ask Copilot to help split things up. This is a refactoring exercise — the app should work the same before and after.
- After restructuring, they add a new feature: recipe categories or a detail page. The point is to see how building *within* an existing structure is faster and more consistent than building from scratch.
- The guide prompts them to notice: "Did the AI follow the patterns you set up? Are the new files consistent with the existing ones?"

**Instructor moment:** "The AI just followed the conventions that exist in your project. It saw how you organized templates and made the new one the same way. It saw your route style and matched it. This is why structure matters — not just for you, but for your AI collaborator. Good structure is a force multiplier."

**Lesson learned:** Investing in structure pays off immediately — the AI amplifies whatever patterns exist, good or bad.

---

### Session 5: Leveling Up — 45 min (14:30–15:15)

**Goal:** Introduce persistent project context through copilot instructions.

**Principles taught:** Context is Everything (deepened).

**What happens:**
- Introduce `.github/copilot-instructions.md`. Explain: "Until now, you've been telling the AI what your project is every time. What if it just *knew*?"
- Participants create a simple instructions file:
  ```
  This is a Python FastAPI web application using Jinja2 templates and Pico CSS for styling.
  Keep code simple and readable.
  Use hardcoded data — no database.
  ```
- Then they add a new small feature (e.g., a "delete recipe" button, or improved styling) and see how the AI's output changes — it should now respect the project conventions without being reminded.
- Optional stretch: create a `.github/prompts/add-page.prompt.md` that encapsulates the pattern for adding a new page (route + template). Try using it.

**Instructor moment:** "Remember Session 3, when the AI went off the rails partly because it didn't know what kind of project this was? You just fixed that permanently. This file gives the AI persistent context — it reads it every time. Same principle: context shapes output. More context, better output."

**Lesson learned:** You can shape AI behavior by giving it persistent context about your project. Small investments in configuration yield large returns.

---

*Break — 15 min (15:15–15:30)*

---

### Session 6: Free Build — 60 min (15:30–16:30)

**Goal:** Independent application of all principles.

**Principles taught:** All — applied without guidance.

**What happens:**
- Open-ended building time. Participants choose what to add to their recipe app.
- Suggestions for those who need direction:
  - Search/filter recipes by name or ingredient
  - Recipe detail page with nicely formatted ingredients and instructions
  - Favorite/bookmark recipes
  - Simple persistence (save recipes to a JSON file so they survive restart)
  - Recipe categories with navigation
- Support staff circulate but let people work independently. Intervene only when someone is stuck for more than 5 minutes.
- Encourage participants to apply what they learned: plan before prompting, work incrementally, read the output critically, recognize failure modes.

**Lesson learned (self-discovered):** Everything from the day, applied independently. Participants feel the difference between their Session 2 experience and now.

---

### Closing — 30 min (16:30–17:00)

**Goal:** Reflect, consolidate, celebrate.

**What happens:**
- Volunteers show what they built (quick screen shares, 2 minutes each, max 4-5 demos)
- Group reflection (guided questions):
  - "What surprised you today?"
  - "What was harder than expected? Easier?"
  - "What's one thing you'll do differently tomorrow when working with AI?"
- Instructor summarizes the 9 principles using real examples from the day
- Hand out the principles reference card
- Mention: "There's more to learn — custom agents, advanced prompting, working with larger codebases. Today was the foundation."

**Lesson learned:** Explicit articulation of what was learned, cemented through group reflection.

---

## Session-Principle Matrix

| Session | Principles | Lesson Learned |
|---|---|---|
| 1. Ideation | AI as Collaborator, Prompting as a Skill | The AI is a useful thinking partner, but you shape the conversation |
| 2. First Feature | Plan → Execute → Iterate, Incremental over Ambitious, Reading > Writing | Work in small steps; the real skill is evaluating output |
| 3. Features + Problems | Prompting as a Skill, Common Failure Modes, Context is Everything | AI fails predictably; naming the patterns helps you recover faster |
| 4. Structure | Decomposition, Existing Code & Patterns | Good structure is a force multiplier for AI collaboration |
| 5. Leveling Up | Context is Everything | Persistent context configuration yields outsized returns |
| 6. Free Build | All | Self-directed application and consolidation |
