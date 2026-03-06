# Copilot Instructions

**Before non-trivial changes:** Explain approach, highlight assumptions, describe expected impact.
**After acting:** Summarize what was done, note any deviations.
**When uncertain:** Ask. Accuracy over momentum.

## What This Project Is

A **full-day AI coding workshop** (9:00–16:45) for non-technical to slightly technical participants at a legal/public affairs consultancy. 10 participants, 3 support staff. Participants build a stakeholder directory web app using GitHub Copilot as their coding partner.

**Stack:** Python 3.12, FastAPI, Jinja2 templates, Pico CSS, uv.

**Goal:** Teach participants how to work effectively with AI coding assistants. The app is the vehicle; the principles are the product.

## Directory Structure

**`workshop-plan.md`** — Facilitator-facing master plan. Session structure, timing, teaching moments, instructor notes, support staff guide. This is the source of truth for what happens during the day.

**`step-by-step-guide.md`** — Participant-facing guide. What participants follow during the workshop. Exercises, prompts to try, reflection questions. Must align with the workshop plan but written for a different audience.

**`preparation-guide.md`** — Pre-workshop setup instructions. Install Python, VS Code, Copilot, uv. Sent to participants by email with the project zip file.

**`principles-reference-card.md`** — One-page takeaway summarizing the 4 core principles. Handed out at the end.

**`app/`** — The boilerplate starting point participants get. Minimal FastAPI hello-world. This is what's in the zip file.

**`README.md`** — Participant-facing readme. Quick start instructions.

**`.github/`** — Copilot configuration for workshop development (this file, agents, prompts). Not participant-facing.

## Workshop Design Principles

- **Principles over features.** Every session exists to teach specific principles. The app features are chosen to create teaching moments, not because the app needs them.
- **Guided morning, free afternoon.** Morning sessions build skills with structured guidance. The afternoon is extended free building time.
- **Learn by doing, then by failing.** Participants build something that works, then experience failure modes to learn verification.
- **Consistent document alignment.** `workshop-plan.md` (facilitator view) and `step-by-step-guide.md` (participant view) must tell the same story from different angles. Changes to one may require changes to the other.
- **The boilerplate is minimal.** `app/` should be the simplest possible starting point — just enough that participants can run it and see something.
- **Backup folders** replace checkpoint branches. Support staff hand out pre-built app states if someone's app is broken beyond repair.

## Distribution

Participants receive the project as a **zip file by email** (no git). Support staff carry USB drives with the zip as backup.

## What We're Doing Now

We are **designing and refining the workshop** — not building the app. The documents are the product. The current focus is iterating on:

- Session structure, timing, and flow
- Exercises and teaching moments
- How principles map to activities
- Participant-facing content (step-by-step guide, reference card)
- Facilitator-facing content (workshop plan, instructor moments)

The app code and backup folders come later, after the workshop design is solid.

## Content Standards

- **Audience-aware.** Participant-facing content must be approachable for people who have never coded. Facilitator-facing content can assume teaching experience.
- **Concise.** Every sentence earns its place. No filler, no hedging, no "in this section we will..."
- **Actionable.** Instructions tell people what to do, not what they could do. "Ask Copilot to..." not "You might want to consider asking..."
- **Consistent voice.** Participant guide: warm, direct, encouraging. Workshop plan: structured, precise, practical.

## Cross-Cutting Concerns

When changing the workshop design, evaluate:

- **Session-principle alignment** — does every session still teach its intended principles?
- **Timing** — do the sessions still fit within the day (9:00–16:45)?
- **Document consistency** — do workshop-plan.md and step-by-step-guide.md still align?
- **Progressive difficulty** — does the complexity still build gradually?
