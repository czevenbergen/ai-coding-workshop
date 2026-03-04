# Building with AI — Principles Reference Card

**9 principles for effective AI-assisted coding**

---

### 1. AI as Collaborator
AI is a thinking partner from ideation through execution. Use it to brainstorm, design, and build — but you stay in the driver's seat. Review, decide, and test. The AI suggests; you choose.

### 2. Plan → Execute → Iterate
Break work into small, clear steps. Give one instruction, review the result, then move to the next. Don't try to build everything in a single prompt. The cycle is: plan what you need → ask the AI → review and adjust → repeat.

### 3. Context is Everything
The AI only knows what's in its current conversation and the files it can see. It doesn't magically know your full project or your intent. When the AI gives a strange answer, the first question is: "Does it have enough context?"

### 4. Prompting as a Skill
Specific, constrained prompts with clear intent produce better results than vague requests. "Add a delete button to each recipe card in recipes.html" beats "improve the app." State what you want, where you want it, and any constraints.

### 5. Common Failure Modes
AI fails in predictable patterns. Learn to spot them:
- **Hallucination** — invents APIs, libraries, or patterns that don't exist
- **Over-engineering** — adds unnecessary complexity you didn't ask for
- **Drift** — gradually deviates from your intent over long conversations
- **Stale context** — gets confused by earlier parts of the conversation

### 6. Decomposition
Large features should be broken into small, independently completable pieces. "Build a recipe app" is too big. "Add a route that returns the recipe list" is the right size. Small scope = better AI output = easier to verify.

### 7. Existing Code & Patterns
AI follows and amplifies existing patterns in your codebase. If your first file is well-organized, the AI will match that style. If it's messy, the AI will match that too. Consistency compounds — invest in good patterns early.

### 8. Incremental over Ambitious
Ask for small changes, not complete rewrites. The instinct is to ask for everything at once. Resist it. Small requests are easier to verify, easier to fix, and produce better results. Build up, don't tear down and rebuild.

### 9. Reading > Writing
You'll spend more time reading and evaluating AI output than writing prompts. That's normal — it's the job. Don't just check if the code runs. Read it. Understand the structure. Ask the AI to explain parts you don't follow. The goal is comprehension, not just completion.

---

*Workshop: Building with AI — AI-Assisted Coding with GitHub Copilot*
