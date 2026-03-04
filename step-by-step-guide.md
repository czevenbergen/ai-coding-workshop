# Workshop Step-by-Step Guide

# Building with AI: A Hands-On Workshop

Welcome! Today you'll build a personal recipe book web application using AI as your coding partner. This guide walks you through each session. Follow along at your own pace — support staff are here to help if you get stuck.

**Checkpoint branches** are available throughout the day. If you fall behind or want a fresh start at any session, you can run:

```
git checkout checkpoint/01   # After Session 1
git checkout checkpoint/02   # After Session 2
git checkout checkpoint/03   # After Session 3
git checkout checkpoint/04   # After Session 4
git checkout checkpoint/05   # After Session 5
```

---

## Session 1: Ideation (9:30–10:15)

### What you'll learn
- How to use AI as a brainstorming and design partner
- How the way you ask shapes what you get back

### What to do

**1. Open Copilot Chat**

In VS Code, open the Copilot Chat panel (click the chat icon in the left sidebar, or press `Ctrl+Shift+I` / `Cmd+Shift+I`).

**2. Design your recipe app — with AI**

You're going to have a conversation with Copilot about what your recipe app should do. You're not writing code yet — just thinking and planning together.

Start by telling Copilot what you want to build. Here are some ideas to get you going, but use your own words:

- "I want to build a personal recipe book web app. What features would make it useful?"
- "If I only have a few hours, which features should I build first?"
- "What information should a recipe have? Can you suggest a simple data model?"

Spend about 15 minutes exploring. Ask follow-up questions. Push back if the AI suggests something too complex. This is a conversation.

**3. Make your plan**

Based on your conversation, write down (on paper, or in a new file in VS Code) the features you want to build today. Keep it realistic — 3 to 4 features is plenty. For example:

- View a list of all recipes
- Add a new recipe
- View a single recipe's details
- Search or filter recipes

**4. Group discussion**

We'll compare notes as a group. Did the AI suggest the same things to everyone? What was different?

### Lesson learned

> The AI is a useful thinking partner, but different inputs produce different outputs. You shape the conversation.

---

## Session 2: First Feature (10:15–11:15)

### What you'll learn
- The plan → execute → iterate cycle
- Working in small increments, not big leaps
- Reading AI output is as important as writing prompts

### What to do

We're going to build the recipe list page — a page that shows all your recipes. We'll do this step by step, not all at once.

**Step 1: Plan**

Before you write any code, be clear about what you need:
- A Python route in `app/main.py` that handles requests to the homepage
- Some recipe data to display (we'll start with hardcoded data — just a Python list)
- An HTML template that shows the recipes

**Step 2: Create recipe data**

Open `app/main.py` in VS Code. Ask Copilot to help you create some sample recipe data. Be specific:

- Tell it you want a Python list of dictionaries
- Each recipe should have a title, a short description, and a category
- Ask for 4-5 sample recipes

Review what Copilot gives you. Does it make sense? Would you change anything? Edit it if you want.

**Step 3: Create the list route**

Now ask Copilot to create a FastAPI route that passes these recipes to a template. Some things to mention in your prompt:
- You're using Jinja2 templates
- The route should be for the homepage (`/`)
- It should pass the recipes to a template called `recipes.html`

You already have a working route for `/` in `main.py` from the boilerplate. You'll need to modify or replace it.

**Step 4: Create the template**

Ask Copilot to create the HTML template file. Be specific about:
- Where the file should go (`app/templates/recipes.html`)
- That it should extend the base template
- That it should display each recipe's title, description, and category

**Step 5: Run and iterate**

Start your app if it's not already running:

```
uv run fastapi dev app/main.py
```

Open [http://localhost:8000](http://localhost:8000) in your browser. What do you see?

- If it works: great! Look at the code. Does it make sense?
- If there's an error: read the error message. Copy it into Copilot Chat and ask for help. This is normal — iteration is the process.

**Step 6: Read the code**

Your recipe list works. Now spend 5 minutes *reading* the code Copilot generated.

- Open `app/main.py` and read the route function
- Open the template and read the HTML
- Pick one thing you don't fully understand and ask Copilot: "Can you explain what this part does?" (Select the code, then ask in chat.)

### Lesson learned

> Work in small steps, not big leaps. The real skill is evaluating what the AI gives you, not just writing prompts.

---

*Take a break! (11:15–11:30)*

---

## Session 3: Adding Features + Dealing with Problems (11:30–12:45)

### What you'll learn
- How prompting specificity affects results
- Common AI failure modes: hallucination, over-engineering, drift
- What the "context window" is and why it matters

### Part A: Build the "Add Recipe" form (40 min)

Now you'll build something more complex: a form where you can add new recipes.

This requires multiple pieces:
1. A new route that shows the form (`GET /add`)
2. The HTML form template
3. A route that receives the form submission (`POST /add`)
4. Adding the new recipe to your list

**Work incrementally.** Don't ask Copilot to build all four pieces at once. Build one at a time:

1. First, ask for the route and template to *display* the form
2. Run it. Make sure the form appears.
3. Then, ask for the route to *handle* the form submission
4. Run it. Add a recipe. Does it appear in your list?

If something's not working, describe the specific problem to Copilot. "The form submits but the recipe doesn't appear" is much better than "it's not working."

### Part B: The intentional failure exercise (35 min)

Now we're going to see what happens when things go wrong.

**Step 1: Give a bad prompt**

Open a new Copilot Chat conversation and type exactly this:

> "Make the app better and more professional."

Submit it. Let Copilot do its thing.

**Step 2: Observe**

Look at what the AI suggests. You'll likely see some combination of:
- Code restructuring you didn't ask for
- New features you didn't want
- Libraries or frameworks you've never heard of
- Changes that don't match your current code

**Step 3: Try to recover**

Stay in the same conversation. Try to steer the AI back to something useful. Spend about 3 minutes on this.

**Step 4: Start fresh**

Now undo any changes (use `Ctrl+Z` / `Cmd+Z` or `git checkout .`). Open a **new** chat conversation and ask for one specific improvement, like:

> "Add a navigation bar to the base template with links to the recipe list and the add recipe page."

Compare: how much faster and better was the specific prompt?

**Step 5: Group discussion**

We'll talk about what happened and name the patterns.

### Lesson learned

> AI fails in predictable ways. Learning to recognize hallucination, over-engineering, and context drift is more valuable than avoiding them. When a conversation goes off track, a fresh start is often faster than a fix.

---

*Lunch break! (12:45–13:30)*

---

## Session 4: Structure and Patterns (13:30–14:30)

### What you'll learn
- How breaking code into smaller pieces makes everything easier
- How AI follows and amplifies existing patterns in your code

### What to do

**Step 1: Assess the mess**

Look at your `app/main.py`. By now it probably has:
- Sample recipe data
- Multiple route functions
- Maybe some helper logic

All in one file. That's fine for getting started, but it makes things harder as the app grows.

**Step 2: Plan the restructure**

Ask Copilot to help you think about how to organize the code. A good structure might be:

```
app/
  main.py          — FastAPI app setup and configuration
  routes.py        — All route functions
  data.py          — Recipe data and data operations
  templates/
    base.html      — Base template with layout
    recipes.html   — Recipe list page
    add.html       — Add recipe form
```

**Step 3: Refactor**

Ask Copilot to help you move code into the new structure, one file at a time.

- Start with `data.py` — move the recipe list and any functions that modify it
- Then `routes.py` — move the route functions, import data from `data.py`
- Update `main.py` to import routes

**After each move, run the app and verify it still works.** Don't move everything at once — move one piece, test, move the next.

**Step 4: Add a new feature within the structure**

Now add something new — for example, a recipe detail page (clicking a recipe shows its full details). Notice how the AI follows the patterns you've established:

- It puts the new route in `routes.py`
- It creates a new template in the templates folder
- It follows the same coding style

**Step 5: Reflect**

Compare this experience to Session 2. Was it easier to add the new feature now that the code is organized? Did the AI's suggestions fit better into the codebase?

### Lesson learned

> Investing in structure pays off immediately. The AI amplifies whatever patterns exist in your codebase — good or bad.

---

## Session 5: Leveling Up (14:30–15:15)

### What you'll learn
- How to give AI persistent context about your project
- How small configuration investments yield large returns

### What to do

**Step 1: Create a copilot instructions file**

Until now, you've been telling Copilot what your project is every time you start a conversation. What if it just *knew*?

Create a new file at `.github/copilot-instructions.md` in your project:

1. Create the `.github` folder if it doesn't exist
2. Create `copilot-instructions.md` inside it

Ask Copilot to help you write it, or write it yourself. Include things like:

```markdown
# Project: Personal Recipe Book

This is a Python web application built with FastAPI and Jinja2 templates.

- Use Pico CSS for styling (already included in base.html)
- Keep code simple and readable
- Use the existing project structure: routes in routes.py, data in data.py, templates in app/templates/
- Data is stored in memory (Python lists) — no database
- Use type hints for function parameters
```

**Step 2: Test the difference**

Now ask Copilot to add a new small feature — for example:
- A "delete recipe" button
- Better styling for the recipe cards
- A recipe count on the homepage

Notice: does Copilot now follow your project conventions without you having to explain them?

**Step 3 (optional stretch): Create a reusable prompt**

If you have time, create a prompt file at `.github/prompts/add-page.prompt.md`:

```markdown
---
description: "Add a new page to the recipe app"
---

Create a new page for the recipe app. I need:
1. A new route function in app/routes.py
2. A new Jinja2 template in app/templates/
3. A link to the new page in the navigation bar

The page should: {{ input }}
```

Try using it via the Copilot Chat prompt menu.

### Lesson learned

> You can shape AI behavior by giving it persistent context about your project. Small investments in configuration yield large returns.

---

*Take a break! (15:15–15:30)*

---

## Session 6: Free Build (15:30–16:30)

### What you'll learn
- How to apply everything independently
- Your own working rhythm with AI

### What to do

This is your time. Build whatever you want to add to your recipe app. Here are some ideas if you need inspiration:

**Easier:**
- Improve the styling — nicer cards, better layout, colors
- Add a recipe count ("Showing 5 recipes")
- Add a confirmation before deleting a recipe

**Medium:**
- Search recipes by name or ingredient
- Filter recipes by category
- Sort recipes alphabetically or by date added

**Harder:**
- Save recipes to a JSON file so they survive when you restart the server
- Add recipe images (by URL)
- Edit existing recipes
- Mark recipes as favorites

**Remember what you've learned:**
1. Plan before you prompt — know what you want before you ask
2. Work in small steps — one feature at a time
3. Read and evaluate — don't just accept, understand
4. Be specific — vague prompts give vague results
5. Recognize failure modes — if the AI is hallucinating or over-engineering, step back
6. Use structure — put new code where it belongs
7. Use context — your copilot instructions file helps

Support staff are here if you get stuck, but try to work through problems yourself first. That's where the real learning happens.

### Lesson learned (self-discovered)

> Everything from today, applied on your own. Notice how your approach has changed since this morning.

---

## Closing (16:30–17:00)

We'll wrap up together:
- Show-and-tell: volunteers demo what they built (2 minutes each)
- Group reflection: what surprised you? What was harder or easier than expected?
- Principles review: we'll revisit the 9 principles with examples from today
- You'll receive a principles reference card to take home

**Thank you for participating!**

---

## Quick Reference

### Useful commands

| Command | What it does |
|---|---|
| `uv run fastapi dev app/main.py` | Start the app in development mode |
| `Ctrl+C` / `Cmd+C` (in terminal) | Stop the app |
| `Ctrl+Z` / `Cmd+Z` | Undo changes in a file |
| `git checkout .` | Undo ALL file changes (reset to last commit) |
| `git checkout checkpoint/XX` | Switch to a checkpoint branch |

### Copilot shortcuts

| Shortcut | What it does |
|---|---|
| `Ctrl+Shift+I` / `Cmd+Shift+I` | Open Copilot Chat |
| Select code → right-click → Copilot | Ask about selected code |
| `#file` in chat | Reference a specific file |
