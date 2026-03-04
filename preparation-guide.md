# Workshop Preparation Guide

**Workshop:** Building with AI — AI-Assisted Coding with GitHub Copilot
**Duration:** Full day (9:00–17:00)

Please complete these steps **before** the workshop. This should take about 15–20 minutes. If you run into any issues, reach out to us — we're happy to help.

---

## Step 1: Install Visual Studio Code

VS Code is the code editor we'll use throughout the day.

1. Go to [https://code.visualstudio.com](https://code.visualstudio.com)
2. Download the version for your operating system (Windows, macOS, or Linux)
3. Install and open it

**Verify:** You should see the VS Code welcome screen when you open the application.

---

## Step 2: Install Python 3.12

Python is the programming language we'll use to build our application.

### macOS

1. Go to [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Download Python 3.12 (not a newer version)
3. Run the installer — accept the defaults

### Windows

1. Go to [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Download Python 3.12 (not a newer version)
3. Run the installer — **check "Add Python to PATH"** before clicking Install

**Verify:** Open a terminal (Terminal on macOS, Command Prompt on Windows) and run:

```
python3 --version
```

You should see `Python 3.12.x` (the last number doesn't matter).

On Windows, you may need to use `python` instead of `python3`.

---

## Step 3: Install uv

uv is a tool that manages Python packages and project environments. It replaces several tools you'd otherwise need to install separately.

Open a terminal and run:

### macOS / Linux

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

You should see a version number (e.g., `uv 0.6.x`).

---

## Step 4: Install GitHub Copilot

GitHub Copilot is the AI assistant we'll use throughout the workshop. You need a GitHub account with Copilot access.

1. If you don't have a GitHub account, create one at [https://github.com](https://github.com)
2. Make sure you have GitHub Copilot access (your organization may provide this, or you can start a free trial)
3. Open VS Code
4. Go to the Extensions panel (click the square icon on the left sidebar, or press `Ctrl+Shift+X` / `Cmd+Shift+X`)
5. Search for **"GitHub Copilot"**
6. Install the extension by GitHub (it should be the first result)
7. After installation, click **"Sign in to GitHub"** when prompted and follow the authentication steps

**Verify:** You should see a Copilot icon (a small sparkle/star) in the bottom-right status bar of VS Code. Clicking it should show "Copilot is ready."

---

## Step 5: Install the Python Extension for VS Code

1. In VS Code, go to the Extensions panel again
2. Search for **"Python"**
3. Install the extension by Microsoft (it should be the first result)

**Verify:** The extension appears in your installed extensions list.

---

## Step 6: Clone the Workshop Repository

We've prepared a starter project for the workshop. You'll need Git installed to clone it.

If you don't have Git installed:
- **macOS:** Open Terminal and run `git --version`. If it's not installed, it will prompt you to install it.
- **Windows:** Download from [https://git-scm.com/downloads](https://git-scm.com/downloads)

Then, in your terminal:

```
git clone <REPO_URL_WILL_BE_PROVIDED>
cd ai-coding-workshop
```

Open the project in VS Code:

```
code .
```

**Verify:** Run the following commands:

```
uv sync
uv run fastapi dev app/main.py
```

Open your browser and go to [http://localhost:8000](http://localhost:8000). You should see a "Welcome" page. Press `Ctrl+C` in the terminal to stop the server.

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

You'll be building a personal recipe book web application from scratch, using AI as your coding partner. No prior programming experience is required — we'll guide you through every step. Bring your curiosity and don't be afraid to experiment!
