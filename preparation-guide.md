# Workshop Preparation Guide

**Workshop:** Building with AI — AI-Assisted Coding with GitHub Copilot

Please complete these steps **before** the workshop. This should take about 15–20 minutes. If you run into any issues, reply to the workshop email — we're happy to help.

Don't worry if you can't get everything working. We've built time into the morning to help with setup.

---

## Step 1: Unzip the project folder

You received a zip file with this guide. Unzip it and put the folder somewhere you can find it (for example, your Desktop or Documents folder).

The folder should contain:
```
ai-coding-workshop/
  app/
    data/
      stakeholders.json
  step-by-step-guide.md
  preparation-guide.md    ← you're reading this
  pyproject.toml
  README.md
```

---

## Step 2: Install Visual Studio Code

VS Code is the code editor we'll use throughout the day.

1. Go to [https://code.visualstudio.com](https://code.visualstudio.com)
2. Download the version for your operating system (Windows or macOS)
3. Install and open it

**Verify:** You should see the VS Code welcome screen when you open the application.

---

## Step 3: Install Python 3.12

Python is the programming language we'll use to build our application.

### macOS

1. Go to [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Download Python 3.12
3. Run the installer — accept the defaults

### Windows

1. Go to [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Download Python 3.12
3. Run the installer — **check "Add Python to PATH"** before clicking Install

**Verify:** Open a terminal (Terminal on macOS, Command Prompt on Windows) and run:

```
python3 --version
```

You should see `Python 3.12.x` (the last number doesn't matter).

On Windows, you may need to use `python` instead of `python3`.

---

## Step 4: Install uv

uv is a tool that manages Python packages and project environments.

Open a terminal and run:

### macOS

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Windows

```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

After installation, **close and reopen your terminal**.

**Verify:** Run:

```
uv --version
```

You should see a version number.

---

## Step 5: Install GitHub Copilot

GitHub Copilot is the AI assistant we'll use throughout the workshop.

1. If you don't have a GitHub account, create one at [https://github.com](https://github.com)
2. Make sure you have GitHub Copilot access (your organization may provide this, or you can start a free trial)
3. Open VS Code
4. Go to the Extensions panel (click the square icon on the left sidebar, or press `Cmd+Shift+X` on Mac / `Ctrl+Shift+X` on Windows)
5. Search for **"GitHub Copilot"**
6. Install the extension by GitHub (it should be the first result)
7. After installation, click **"Sign in to GitHub"** when prompted and follow the authentication steps

**Verify:** You should see a Copilot icon in the bottom-right status bar of VS Code.

---

## Step 6: Open the project and test it

1. In VS Code, go to **File → Open Folder** and select the `ai-coding-workshop` folder you unzipped
2. Open the built-in terminal: **Terminal → New Terminal** (or press `` Ctrl+` ``)
3. Run these two commands:

```
uv sync
uv run fastapi dev app/main.py
```

4. Open [http://localhost:8000](http://localhost:8000) in your browser

**Verify:** You should see a welcome page that says "Welcome to Your Stakeholder Directory."

Press `Ctrl+C` in the terminal to stop the app. You'll start it again during the workshop.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `uv: command not found` | Close and reopen your terminal, then try again. If it still doesn't work, re-run the install command from Step 4. |
| `python3: command not found` | On Windows, try `python` instead. If that doesn't work, reinstall Python and make sure "Add to PATH" is checked. |
| The app shows an error | Make sure you're in the `ai-coding-workshop` folder when running the commands. Check that `uv sync` completed without errors first. |
| Copilot won't sign in | Make sure you're signed into GitHub in your browser first, then try the VS Code sign-in again. |

If none of this works, don't worry — we'll help you at the start of the workshop.

---

## Checklist

Before the workshop, confirm:

- [ ] VS Code installed and opens correctly
- [ ] Python 3.12 installed (`python3 --version` shows 3.12.x)
- [ ] uv installed (`uv --version` shows a version number)
- [ ] GitHub Copilot extension installed and signed in
- [ ] Python extension installed
- [ ] Workshop repo cloned and the app runs (you see the Welcome page)

If anything doesn't work, don't worry — just let us know and we'll sort it out before the workshop starts.

---

## What to Expect

You'll be building a stakeholder directory web application using AI as your coding partner. No prior programming experience is required — we'll guide you through every step. Bring your curiosity and don't be afraid to experiment!
