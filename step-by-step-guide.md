# Building with AI: A Hands-On Workshop

Welcome! Today you'll build a stakeholder directory — a web application to track contacts, organizations, and categories — using AI as your coding partner.

This guide walks you through each session. Follow along at your own pace — support staff are here to help if you get stuck.

---

## Your First Prompt (during the Opening)

Let's see what Copilot can do. You're going to ask it to change the welcome page you saw during setup — and watch it edit your code in real time.

**Step 1: Open Copilot Chat**

Press `Cmd+Shift+I` (Mac) or `Ctrl+Shift+I` (Windows) to open the Chat panel. Make sure **Agent** is selected at the top.

**Step 2: Send your first message**

Type this into the chat:

> "Change the welcome page so it says 'Welcome, [your name]!' and add a short description of what this app will do."

Watch what happens. Copilot reads your files, figures out what to change, and edits the code directly. You'll see the changes highlighted in your editor.

**Step 3: Review the change**

Look at the highlighted code in your editor. You'll see what was there before and what Copilot changed. This is called a **diff** — it shows you exactly what's different.

- Click **Keep** to accept the change
- Click **Undo** to reject it

**Read it first. Always.** Don't click Keep until you understand what changed.

**Step 4: See it in the browser**

Your app should reload automatically. Check your browser — do you see your name?

**Step 5: Undo everything with a checkpoint**

Every message you send creates a **checkpoint** — a snapshot of your files at that moment. Let's use one now.

In the Chat panel, hover over the message you just sent. You'll see a **Restore Checkpoint** button. Click it.

The change disappears. Your welcome page is back to the original. That's your safety net — if anything goes wrong today, you can always restore a checkpoint.

**What you just learned:**
- **Agent mode edits your files directly.** You type what you want; it makes the changes.
- **Review before you accept.** Always read the diff before clicking Keep.
- **Checkpoints are your safety net.** Every message creates one. Use Restore Checkpoint to undo.
- **New conversation = fresh start.** When you want to try a different approach, start a new conversation. The AI won't carry over mistakes from the old one.

---

## Session 1: First Feature (9:45–10:45)

### What you'll learn
- Building with AI one step at a time
- Why reading AI output is as important as writing prompts

### How a web app works (the 30-second version)

The app you're building has three parts:

- **Data** — the stakeholders you want to display, stored in a file (`app/data/stakeholders.json`)
- **Routes** — Python code that decides what happens when someone visits a URL (like the homepage)
- **Templates** — HTML files that define what each page looks like

Your first task: connect these three pieces so that when you open the app, you see a list of stakeholders. The data already exists — you just need to build the route and the page.

### What to do

We're going to build the first page of your stakeholder directory — a page that lists all your contacts. We'll do this step by step, not all at once. Each step builds one piece: first you'll look at the data, then build the route, then the page.

**Step 1: Look at your data**

Open `app/data/stakeholders.json` in VS Code. This is the sample data your app will display. Take a moment to read through it — each stakeholder has a name, organization, role, and category.

This file is your app's data store. Later, when you build a form to add stakeholders, new entries will be saved here too.

**Step 2: Create the list route**

Right now, opening the app shows the welcome page. You want it to show your stakeholders instead. Ask Copilot to make that happen — you can copy this directly or adapt it:

> "Create a route for the homepage that reads the stakeholders from `app/data/stakeholders.json` and displays them on a page called `stakeholders.html`. Replace the existing welcome page route."

A **route** is a rule that tells the app: "When someone visits this URL, show them this page." Your app already has one route (for the welcome page) — you're replacing it with a new one.

Copilot will update `app/main.py` with the new route. Review the highlighted changes, then click **Keep**.

**Step 3: Create the template**

Now ask Copilot to create the HTML page that displays your stakeholders. Be specific about what you want to see on the page:

> "Create a template at `app/templates/stakeholders.html` that shows a heading 'Stakeholder Directory' and displays each stakeholder's name, organization, role, and category. Use a table or cards."

A **template** is an HTML file that defines what a page looks like. Copilot will create the file and automatically use the same styling as your welcome page.

You'll see the new file appear in your file explorer. Open it, read through the HTML, and click **Keep**.

**Step 4: Run and see**

If your app is already running, it should reload automatically. If not, start it:

```
uv run fastapi dev app/main.py
```

Open [http://localhost:8000](http://localhost:8000) in your browser. What do you see?

- **If it works:** Great! Look at the page. Does the data look right?
- **If there's an error:** Read the error message in the terminal. Copy it into Copilot Chat and ask: "I'm getting this error when I run my FastAPI app. Can you help me fix it?" Include the full error message.

Common issues:
- "Template not found" → check the file is in `app/templates/` and the filename matches
- Import errors → Copilot may have added something that needs a different approach. Ask it to fix the error.

**Step 5: Read the code**

Your stakeholder list works. Now spend a few minutes *reading* the code Copilot generated.

- Open `app/main.py` and read the route function
- Open the template and read the HTML
- Pick one thing you don't fully understand and ask Copilot: "Can you explain what this part does?" (Select the code first, then ask in chat.)

Understanding what the AI wrote is just as important as getting it to write it.

### Lesson learned

> One step at a time. Build one piece, review it, then build the next. The AI writes the code; you steer and verify.

---

*Take a break! (10:45–11:00)*

---

## Session 2: Adding Features + Dealing with Failure (11:00–12:15)

### What you'll learn
- What happens when prompts are vague vs. specific
- How to recover when AI goes wrong

### Part A: Build the "Add Stakeholder" form (40 min)

Now you'll build something more complex: a form where you can add new stakeholders to your directory.

This requires multiple pieces:
1. A new route that shows the form
2. The HTML form template
3. A route that receives the form submission and saves the new stakeholder to the data file

**Work incrementally.** Don't ask Copilot to build all three pieces at once. Build one at a time:

1. **First:** Ask Copilot to create a page where you can fill in a form to add a new stakeholder. Here's one way to start:

   > "Create a page at /add with a form to add a new stakeholder. The form should have fields for name, organization, role, and category."

2. **Run it.** Make sure the form appears in your browser at the URL you chose.
3. **Then:** Ask Copilot to make the form actually work — it should save the new stakeholder to the data file and send you back to the main page. This time, write the prompt yourself.
4. **Run it.** Add a stakeholder through the form. Does it appear in your list?

If something's not working, describe the **specific** problem to Copilot:
- "The form submits but the stakeholder doesn't appear in the list" ✓
- "It's not working" ✗

The more context you give Copilot about what's happening vs. what you expected, the better it can help.

### Part B: The failure experiment (35 min)

Now we're going to see the difference between a vague prompt and a specific one — and practice using checkpoints to recover.

**Step 1: Try the vague prompt**

Make sure your app is working after Part A. This is your "known good state."

Open a **new** Copilot Chat conversation and type this:

> "Make my stakeholder app better and more professional. Add all the features it needs."

Submit it and **watch what happens.** Copilot will start editing your files — possibly many of them. You'll likely see:
- Files you didn't ask it to change
- New features you didn't want
- Code restructuring you didn't request
- Maybe the app doesn't even start anymore

Look at the mess. How many files changed? Can you follow what it did? **Don't click Keep.**

**Step 2: Restore your checkpoint**

In the Chat panel, hover over the message you just sent (the vague prompt). You'll see a **Restore Checkpoint** button. Click it and confirm.

All the changes disappear. Your app is back to exactly how it was before the vague prompt. That's what checkpoints are for.

**Step 3: Try the specific prompt**

Open another **new** conversation and type this:

> "Add a navigation bar to base.html with links to the stakeholder list and the add stakeholder page. Use the existing Pico CSS classes."

Watch it run. One file changes. The diff is small and clear. Check your browser — does the nav bar look right? If so, click **Keep**.

**Step 4: Discuss**

You just experienced three common AI failure patterns:

- **Hallucination** — when the AI invents things that don't exist (APIs, libraries, features)
- **Over-engineering** — when it adds complexity you didn't ask for
- **Drift** — when it gradually moves away from what you actually wanted

These aren't bugs. They're predictable patterns you can learn to spot. And the checkpoint saved you from the worst of it.

### Lesson learned

> AI fails in predictable ways. Specific prompts with clear context produce better results. Always review before accepting — and when things go wrong, use a checkpoint to revert and start fresh.

---

*Lunch break! (12:15–13:15)*

---

## Session 3: Context and Configuration (13:15–14:15)

### What you'll learn
- How to give AI persistent context about your project
- How the right context makes the AI dramatically more useful

### What to do

**Step 1: Create a copilot instructions file**

Until now, you've been telling Copilot what your project is every time you start a conversation. What if it just *knew*?

Ask Copilot to create an instructions file for your project:

> "Create a file at `.github/copilot-instructions.md` that describes this project — what it does, what technologies it uses, and how data is stored. Keep it short and practical."

Review the file Copilot creates. It should include things like:

```markdown
This is a Python web application built with FastAPI and Jinja2 templates.
It's a stakeholder directory for tracking contacts, organizations, and categories.

- Use Pico CSS for styling (already included in base.html)
- Keep code simple and readable
- Data is stored in `app/data/stakeholders.json` — no database
```

Edit it if you want — add rules, remove things that don't seem right, make it yours. Then click **Keep**.

Copilot reads this file automatically in every conversation. It's persistent context — you won't have to explain your project again.

**Step 2: Build a new feature**

With your instructions file in place, add a new feature to your app. Choose one that interests you:

- **Stakeholder detail page** — click a stakeholder's name to see their full information
- **Search** — add a search bar to filter stakeholders by name or organization
- **Delete** — add a button to remove a stakeholder from the list
- **Categories** — group stakeholders by their category on the main page

Plan before you prompt. Work incrementally. Read the output.

Notice: does Copilot now follow your project conventions without you having to explain them? Does it put files in the right places? Use the right styling?

**Step 3: Compare**

Think back to Session 1. You had to explain everything. Now the AI knows your project. Less explaining, better results — that's the compound effect of context.

### Lesson learned

> You can shape AI behavior by giving it persistent context about your project. Small investments in configuration yield large returns.

---

*Take a break! (14:15–14:30)*

---

## Session 4: Free Build (14:30–16:15)

### What you'll learn
- How to apply everything independently
- Your own working rhythm with AI

### What to do

This is your time. Build whatever you want to add to your stakeholder directory. You can work solo or pair up with someone — your choice.

Here are some ideas if you need inspiration:

**Simpler:**
- Improve the styling — nicer layout, better cards, category badges
- Add a stakeholder count ("Showing 12 stakeholders")
- Sort stakeholders alphabetically

**Medium:**
- Search or filter by name, organization, or category
- Edit existing stakeholders
- Add notes to a stakeholder's profile

**More ambitious:**
- Interaction history — log when you last contacted someone
- Export the stakeholder list as a viewable text page
- Tags or labels that can be added and filtered
- A dashboard with category counts

**Remember what you've learned:**
1. **AI as Collaborator** — use it for thinking and building, but you make the decisions
2. **Work in Small Steps** — one piece at a time. Build, review, then build the next.
3. **Context Shapes Output** — be specific, and let your copilot instructions file do the heavy lifting
4. **Verify, Don't Trust** — read everything, spot hallucination and over-engineering, start fresh when needed

Support staff are here if you get stuck, but try to work through problems yourself first. That's where the real learning happens.

### Lesson learned (self-discovered)

> Everything from today, applied on your own. Notice how your approach has changed since this morning.

---

## Closing (16:15–16:45)

We'll wrap up together:
- **Show-and-tell:** volunteers demo what they built (2 minutes each)
- **Group reflection:** what surprised you? What was harder or easier than expected?
- **Principles review:** we'll revisit the 4 principles with examples from today
- You'll receive a **principles reference card** to take home

Thank you for participating!

---

## Quick Reference

### Useful commands

| Command | What it does |
|---|---|
| `uv run fastapi dev app/main.py` | Start the app in development mode |
| `Ctrl+C` / `Cmd+C` (in terminal) | Stop the app |
| `Ctrl+Z` / `Cmd+Z` | Undo changes in a file |

### Copilot shortcuts

| Shortcut | What it does |
|---|---|
| `Cmd+Shift+I` (Mac) / `Ctrl+Shift+I` (Win) | Open Copilot Chat |
| Select code → right-click → Copilot | Ask about selected code |
| `#file` in chat | Reference a specific file |
