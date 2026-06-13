# Job Application Agent

### Multi-step AI reasoning · Grounded with Microsoft Foundry IQ · Built with GitHub Copilot

A browser-based AI agent that transforms generic CVs into role-specific applications in seconds. Paste a CV and job description — get an ATS-optimized summary, tailored cover letter, skill gap analysis, and certification roadmap.

[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen)](https://vcookie-job-application-agent.netlify.app)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-blue)](https://github.com/Vengefulcookie/job-application-agent)
[![Hackathon](https://img.shields.io/badge/Microsoft-Agents_League-f39c12)](https://github.com/microsoft/agents-league)

Built for the **Microsoft Agents League Hackathon — Creative Apps Track, June 2026**.

---

## The Problem

87% of junior roles require 2+ years of experience. Most candidates send identical CVs to every application. Recruiters spend 6 seconds scanning each one.

**The real issue:** Candidates often *have* the skills, but they're buried, poorly framed, or invisible to ATS systems.

---

## How It Works

1. **Paste** your CV and a job description
2. **Watch** the agent reason through 6 steps in real time
3. **Copy** each section or download as formatted text

### The 6 Reasoning Steps

| Step | What it does |
|------|---------------|
| ⚡ **Foundry IQ retrieval** | Semantically matches your CV against the role |
| 📋 **Extract requirements** | Parses all required/preferred skills from the JD |
| 📊 **Score your fit** | Match % + skill badges (matched/gap) |
| ✏️ **Tailor for ATS** | Rewrites summary & skills with role-specific keywords |
| 📝 **Generate cover letter** | Personalized, grounded in your actual profile |
| 🎓 **Suggest certs** | Specific certifications to close gaps |

---

## Microsoft Foundry IQ — Grounded Retrieval Layer

This agent uses **Foundry IQ** (Azure AI Search) to retrieve semantically relevant chunks of your CV before reasoning — reducing hallucination and keeping outputs grounded in your real profile.

**How it works:**
Input (CV + Job Description)
↓
⚡ Foundry IQ Knowledge Base
(Azure AI Search semantic search)
Retrieves most relevant CV sections
Falls back to pasted CV if unavailable
↓
All 6 steps use this grounded context
↓
Output: ATS Summary · Cover Letter · Gap Analysis · Certs

**Fallback behavior:** If Azure Search isn't configured, the app uses your pasted CV as context — you still get full functionality. Foundry IQ activates automatically when credentials are provided.

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | HTML · CSS · Vanilla JavaScript (no build, no dependencies) |
| Knowledge retrieval | Microsoft Foundry IQ (Azure AI Search semantic search) |
| AI reasoning | Groq Llama 3.1 or Google Gemini 1.5 Flash (both free tier) |
| Development | GitHub Copilot |

---

## Quick Start

### 1. Get a free AI API key

**Groq (recommended — fastest free tier)**
- [console.groq.com](https://console.groq.com) → Sign up → API Keys → Create

**Gemini (alternative)**
- [aistudio.google.com](https://aistudio.google.com) → Get API key → Create

### 2. (Optional) Set up Foundry IQ grounding

- [ai.azure.com](https://ai.azure.com) → New project
- Deploy embedding model: `text-embedding-3-small`
- Upload your CV via Chat playground → Add your data
- Copy Search endpoint + API key from View code

> Skip this step if Azure quota is limited — the app runs fully with pasted CV context

### 3. Run it

1. Open `index.html` in your browser
2. Enter API keys in the config bar (top of page)
3. Paste your CV and a job description
4. Click **Run agent** — watch it reason through 6 steps
5. Copy or download each output section

**No server, no installation required.** Keys never leave your browser or get stored.

---

## Running Locally

```bash
# Clone the repository
git clone https://github.com/Vengefulcookie/job-application-agent.git

# Navigate into the folder
cd job-application-agent

# Open the HTML file in your browser
open index.html
```

That's it — no build step, no dependencies, no server.

## Why This Matters
- Real grounding: Foundry IQ retrieves your actual CV context, not hallucinated skills
- Visible reasoning: Watch each step unfold — no black box
- ATS-ready output: Keywords tailored to the specific role
- No fabrication: Only reframes and surfaces what you already have
- Fully local: Runs entirely in-browser, no data stored on servers

## What I Learned
- Microsoft Foundry IQ (Azure AI Search): This was my first time implementing semantic search for retrieval-augmented generation. I learned about vector embeddings, similarity scoring, and how to structure fallback behavior when Azure credentials aren't available.

- Multi-step agent orchestration: Keeping the UI responsive while running 6 sequential API calls required careful state management. Each step updates the UI in real time so users see the reasoning unfold.

- Prompt engineering for honesty: The biggest challenge was preventing hallucination. The prompts explicitly instruct the AI to only use information from the retrieved CV context. If a skill isn't mentioned, it's marked as a gap — not fabricated.

- Rate limiting & retries: Free tier APIs have limits. I implemented exponential backoff retry logic and clear error messages so users know when to switch between Groq and Gemini.

- No-build frontend: Keeping the entire app in a single HTML file with vanilla JS makes it instantly deployable and auditable. Anyone can view the source and see exactly what it does with their data.

## Hackathon Context
Built for the Microsoft Agents League Hackathon — Creative Apps Track, June 2026.

Why this fits the track: It's a creative application of agentic AI — not just a chatbot wrapper, but a multi-step reasoning system that transforms unstructured data (CV + job description) into structured, actionable outputs.

Built with GitHub Copilot: Used throughout for implementing Foundry IQ retrieval, structuring agent orchestration, refining prompts, and generating retry logic.

## Privacy & Security
API keys never leave your browser or get stored

No data is sent to any server except the AI APIs you configure

For production use, API calls would move to a secure backend with environment variables

## Demo
- Live: vcookie-job-application-agent.netlify.app
- Video: [Add YouTube/Vimeo link]

## Contact
- GitHub: github.com/Vengefulcookie
- LinkedIn: linkedin.com/in/snethemba-shangase-softw-mech-civil0101
- Portfolio: vcookie-portfolio.netlify.app

Built for the Microsoft Agents League Hackathon with ☕, Copilot, and a frustration with generic job applications

⬆ Back to top

⭐ If this tool helps you land a role, consider starring the repo! ⭐
