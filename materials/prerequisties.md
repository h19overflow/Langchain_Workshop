# Prerequisites for LangChain RAG Agent Workshop

Before starting the workshop, you need to set up three things: **Python**, **uv (package manager)**, and **Google API credentials**. This guide walks you through each step with explanations.

---

## P.1 Install Python

**What is Python?**

Python is the **programming language** that runs everything in this workshop. It's like the engine of a car—without it, nothing works. Every line of code you'll write runs through Python.

**Why Python?**

- **LangChain is built in Python** — we need Python to use it
- **AI/ML ecosystem** — most AI tools (PyTorch, TensorFlow, LangChain) are written in Python
- **Easy to learn** — clean syntax makes it beginner-friendly for this workshop

**How to Install Python:**

#### On Windows:
1. Go to [python.org](https://www.python.org/downloads/)
2. Click the yellow **"Download Python install manager"** button
3. Run the installer
4. **⚠️ IMPORTANT:** Check the box that says **"Add Python to PATH"** — this lets your computer find Python from anywhere
5. Click **Install Now**
6. Verify it worked:
   ```bash
   python --version
   ```
   You should see something like `Python 3.14.x` or similar

#### On macOS:
1. Go to [python.org](https://www.python.org/downloads/)
2. Select your OS version (Intel or Apple Silicon)
3. Download the **macOS installer**
4. Run the `.pkg` file and follow the steps
5. Verify it worked:
   ```bash
   python3 --version
   ```

#### On Linux:
Python usually comes pre-installed. Verify:
```bash
python3 --version
```

If not installed:
```bash
sudo apt install python3 python3-pip  # Ubuntu/Debian
sudo yum install python3 python3-pip  # RedHat/CentOS
```

**What to Check:**
- [ ] Running `python --version` (or `python3 --version` on macOS/Linux) shows version 3.11 or higher
- [ ] No "command not found" error

---

## P.2 You're Ready!

Python comes with **pip** (Python's built-in package manager) already installed. You don't need to install anything else—pip will handle downloading and installing all the libraries you need for this workshop.

**What is pip?**

Pip is like a **librarian for code**. When you want to use LangChain, embeddings, or other tools, you download them with pip. It handles the downloading, installing, and organizing of pre-built code libraries.

**Verify pip is installed:**
```bash
pip --version
```

You should see something like `pip 24.x` or higher. If pip came with Python, you're all set!

---

## P.3 Create a Virtual Environment

**What is a Virtual Environment?**

A virtual environment is an **isolated folder on your computer** where you install project-specific packages. Think of it like a separate workspace for this workshop—it keeps your workshop dependencies separate from other Python projects you might have.

**Why use a virtual environment?**

- **Isolation** — If you have multiple Python projects, they won't interfere with each other
- **Cleanliness** — You can delete the entire folder later without affecting your system Python
- **Easy debugging** — If something breaks, you know it's in this project, not your whole system
- **Best practice** — Professional developers always use virtual environments

**How to Create and Activate:**

1. **Open your terminal/PowerShell** and navigate to your workshop folder:
   ```bash
   cd C:\Users\YourUsername\Projects\Langchain_Workshop
   ```

2. **Create the virtual environment:**
   ```bash
   python -m venv venv
   ```
   This creates a folder called `venv` with everything isolated inside.

3. **Activate the virtual environment:**

   **On Windows (PowerShell):**
   ```bash
   .\venv\Scripts\Activate.ps1
   ```

   **On macOS/Linux:**
   ```bash
   source venv/bin/activate
   ```

   You'll see `(venv)` appear at the start of your terminal line—that means you're inside the virtual environment.

---

## P.4 Install Required Packages

**What are we installing?**

You're installing **libraries** (pre-built code) that this workshop needs:
- `langchain-core` — Core LangChain functionality
- `langchain-google-genai` — Connector for Google's Gemini API
- `langchain-huggingface` — Local embedding models
- `langchain-community` — Additional LangChain tools
- `faiss-cpu` — Fast similarity search for vectors
- `pypdf` & `python-docx` — Read PDF and Word documents
- `sentence-transformers` & `torch` — Power the embeddings
- `python-dotenv` — Load your API key securely from `.env`

**How to Install (Make sure you're inside the virtual environment first):**

Check that you see `(venv)` in your terminal. Then run:

```bash
pip install langchain-core langchain-google-genai langchain-huggingface langchain-community faiss-cpu pypdf python-docx sentence-transformers torch python-dotenv
```

**This will take a few minutes** — pip is downloading and installing everything. You'll see progress lines as it works.

Once it finishes with ✓ success messages, you're done!

---

## P.5 Create a Google Account and Get API Key

**What is an API Key?**

An API key is like a **password for using Google's AI services**. It tells Google's servers "this is me, let me use Gemini." Without it, your code can't talk to Google's LLM.

**What is an API Key?**

An API key is like a **password for using Google's AI services**. It tells Google's servers "this is me, let me use Gemini." Without it, your code can't talk to Google's LLM.

**Why Google Gemini?**

- **Free tier available** — you get free API calls for learning (generous limits)
- **Fast and capable** — `gemini-2.0-flash` is quick enough for RAG tasks
- **Simple setup** — easier than OpenAI for workshops
- **No credit card required** (unless you exceed free tier)

**Step 1: Create a Google Account**

If you don't have a Google account:
1. Go to [accounts.google.com](https://accounts.google.com/signup)
2. Fill in your name, email, and password
3. Follow Google's verification steps
4. Done!

If you already have a Google account, skip this step.

**Step 2: Get Your API Key**

1. Go to [Google AI Studio](https://aistudio.google.com/app/apikeys)
   - (You may need to log in with your Google account)
2. Click **"Create API Key"** button
3. Select **"Create API Key in new project"**
4. Google generates a key for you instantly
5. **Copy the key** (you won't see it again—save it!)

**⚠️ Security Reminder:**
- **Never share your API key publicly** — anyone with it can use your free tier quota
- **Never commit it to GitHub** — use `.env` files instead (we'll cover this)

**What to Check:**
- [ ] You have a Google account
- [ ] You've created an API key in AI Studio
- [ ] You've copied and saved the key somewhere safe (for Step 1.1 of the workshop)

---

## ✅ Verify Everything Works

Once you've completed P.1 through P.5, run this command in your terminal **(with the virtual environment activated)**:

```bash
pip list
```

You should see a list of installed packages including `langchain-core`, `langchain-google-genai`, and others. If you do, **you're ready for the workshop!**

---

## 🆘 Troubleshooting

**"Python command not found"**
- Windows: You skipped checking "Add Python to PATH" during installation. Reinstall and check that box.
- macOS/Linux: Use `python3` instead of `python`

**"pip is not recognized" (Windows)**
- Make sure you've **activated the virtual environment** first: `.\venv\Scripts\Activate.ps1`
- Look for `(venv)` at the start of your terminal line
- If the virtual environment isn't activating, try: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

**"pip install is taking forever"**
- This is normal! Installing `torch` and `sentence-transformers` can take 5-15 minutes
- Let it run. Don't interrupt it.

**"Can't access Google AI Studio"**
- Make sure you're logged into your Google account
- Try a different browser
- Check that you're going to `aistudio.google.com` (not a typo)

**Lost your API key**
- Go back to [Google AI Studio](https://aistudio.google.com/app/apikeys)
- Create a new one (the old one will be disabled)

**"ModuleNotFoundError" when running workshop code**
- Make sure the virtual environment is activated: `(venv)` should show in your terminal
- Reinstall the packages: `pip install -r requirements.txt` (once we provide it)

---

## Next Steps

Once everything is installed and verified, head to **Section 1.1: Environment & Installation** of the main workshop to set up your project and create your `.env` file.