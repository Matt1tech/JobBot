# JobBot

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white" alt="Python 3">
  <img src="https://img.shields.io/badge/SQLite-local_database-003B57?logo=sqlite&logoColor=white" alt="SQLite">
  <img src="https://img.shields.io/badge/Playwright-browser_automation-2EAD33?logo=playwright&logoColor=white" alt="Playwright">
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="MIT License"></a>
</p>

> **A personal job-search copilot that finds promising roles, prepares a tailored resume, and helps you apply—with you in control.**

Job hunting can mean repeating the same search, rewriting, and form-filling for every role. JobBot brings those steps into one local dashboard: compare openings with your resume, review the match and the tailored version, then explicitly approve the applications you want to send.

**JobBot is a sample project, not a fully autonomous job agent.** It is designed to demonstrate a practical, human-in-the-loop use of AI and browser automation.

## What makes it different?

- **Match before you apply.** Search for roles based on your resume or a position you specify, and see a match score, reasons, and missing qualifications.
- **Tailor without inventing.** JobBot asks the AI to use facts from your original resume only, and flags new employers or numbers for you to check.
- **You approve every application.** Review the job and its tailored resume, select what you want, and only then start applying.
- **Keep track of what happened.** See completed applications, the resume and answers used, and a screenshot; applications that need human attention are separated for follow-up.
- **Run it on your computer.** The dashboard and its saved application history are local, with AI provider choices to suit your setup.

## How it works

```text
Your resume + search preferences
              ↓
  Find and score job openings
              ↓
 Review matches and tailored resumes
              ↓
     You approve selected jobs
              ↓
 Apply where possible, or hand off to you
```

### 1. Set up your profile

Upload a PDF, DOCX, or TXT resume, add contact details and reusable application answers, and select an AI provider.

### 2. Find and compare jobs

Choose **Find jobs that fit my resume** or **Search a position**, then set your location. JobBot can search:

- Greenhouse, Lever, and Ashby company boards you configure
- Public feeds from Remotive and Arbeitnow
- Job links you paste in yourself

For each opening, JobBot shows a score, why it may fit, what may be missing, and—when it meets your configured score threshold—a tailored resume.

### 3. Review, then approve

Check each match and its resume. Select applications individually, or use **Approve all ≥ 75** if that threshold suits you. Approval is required before JobBot starts submitting applications.

### 4. Follow through

JobBot uses a browser to fill and submit supported application forms. Some applications will require you to take over—for example, if a site asks for a CAPTCHA, login, or information JobBot cannot determine. Open the saved application link, finish it yourself, and mark it submitted in the dashboard.

## Get started

### Requirements

- Python 3
- Microsoft Edge for browser-based applications
- An AI provider configured in the dashboard

### Run on Windows

```powershell
cd C:\Users\User\Desktop\claudeEnv
python -m pip install -r requirements.txt
python server.py
```

Open [http://localhost:8765](http://localhost:8765) in your browser. Stop the server with `Ctrl+C`.

If Edge is not installed, you can install Playwright's Chromium browser instead:

```powershell
python -m playwright install chromium
```

In the dashboard, upload your resume, enter your profile and standard answers, choose an AI provider, and click **Save setup**.

## AI providers

| Provider | What you need |
| --- | --- |
| Claude Code | Install Claude Code and sign in by running `claude` once in a terminal. No separate API key is needed. |
| Cloudflare Workers AI | Your Cloudflare Account ID and an API token with Workers AI permission. |
| NVIDIA NIM | An API key from [build.nvidia.com](https://build.nvidia.com/). |

## Your data and AI

- JobBot stores its local database, uploaded resumes, generated resumes, and application screenshots in the `data/` folder. This folder is excluded from Git.
- JobBot sends resume and job information to whichever AI provider you configure so it can assess and tailor applications. Review that provider's data and privacy policies before use.
- Application details are sent to the job sites when you approve and submit an application.
- Review AI-generated content before approving it. The warnings are a prompt to check—not a guarantee that every detail has been verified.

## Important limitations

- JobBot does not search LinkedIn, Indeed, or JobStreet automatically; those sites block automated access. You can paste a job link from any site.
- Application forms vary. Browser automation may not work for every employer, and CAPTCHAs, logins, and unfamiliar questions need your attention.
- JobBot is a personal-use sample. It cannot guarantee that a job is a good fit, that an application will be accepted, or that a website permits automation.

## 🧰 Tools and technologies

| Tool | What it does in JobBot |
| --- | --- |
| 🐍 **Python** | Runs the local server and application workflow. |
| 🗃️ **SQLite** | Stores your local job and application history. |
| 🌐 **HTML, CSS, and JavaScript** | Power the lightweight dashboard in your browser. |
| 🎭 **Playwright** | Automates supported application forms in a browser. |
| 📄 **PyMuPDF and python-docx** | Read resumes and generate tailored PDF/DOCX documents. |
| 🤖 **Claude Code, Cloudflare Workers AI, or NVIDIA NIM** | Provide AI-powered matching and resume tailoring. |

Python package dependencies are listed in [`requirements.txt`](requirements.txt).

## 📜 License

This project is released under the [MIT License](./LICENSE).
