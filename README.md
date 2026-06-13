# Job Application Agent
### Multi-step AI reasoning · Grounded with Microsoft Foundry IQ · Built with GitHub Copilot

A browser-based AI agent that transforms generic CVs into role-specific applications in seconds. Paste a CV and job description — get an ATS-optimized summary, tailored cover letter, skill gap analysis, and certification roadmap.

Built for the **Microsoft Agents League Hackathon — Creative Apps Track, June 2026**.

---

## The problem

87% of junior roles require 2+ years of experience. Most candidates send identical CVs to every application. Recruiters spend 6 seconds scanning each one.

**The real issue:** Candidates often *have* the skills, but they're buried, poorly framed, or invisible to ATS systems.

---

## How it works

1. **Paste** your CV and a job description
2. **Watch** the agent reason through 6 steps in real time:
   - ⚡ **Foundry IQ retrieval** — Semantically matches your CV against the role
   - 📋 **Extract requirements** — Parses all required/preferred skills from the JD
   - 📊 **Score your fit** — Match % + skill badges (matched/gap)
   - ✏️ **Tailor for ATS** — Rewrites summary & skills with role-specific keywords
   - 📝 **Generate cover letter** — Personalized, grounded in your actual profile
   - 🎓 **Suggest certs** — Specific certifications to close gaps
3. **Copy** each section or download as formatted text

---

## Microsoft Foundry IQ — Grounded retrieval layer

This agent uses **Foundry IQ** (Azure AI Search) to retrieve semantically relevant chunks of your CV before reasoning — reducing hallucination and keeping outputs grounded in your real profile.

**How it works:**

```
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
```

**Fallback behavior:** If Azure Search isn't configured, the app uses your pasted CV as context — you still get full functionality. Foundry IQ activates automatically when credentials are provided.

---

## Tech stack

| Component | Technology |
|-----------|-----------|
| Frontend | HTML · CSS · Vanilla JavaScript (no build, no dependencies) |
| Knowledge retrieval | Microsoft Foundry IQ (Azure AI Search semantic search) |
| AI reasoning | Groq Llama 3.1 or Google Gemini 1.5 Flash (both free tier) |
| Development | GitHub Copilot |

---

## Quick start

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

1. Open `job_application_agent.html` in your browser
2. Enter API keys in the config bar (top of page)
3. Paste your CV and a job description
4. Click **Run agent** — watch it reason through 6 steps
5. Copy or download each output section

**No server, no installation required.** Keys never leave your browser or get stored.

---

## Why this matters

- **Real grounding:** Foundry IQ retrieves your actual CV context, not hallucinated skills
- **Visible reasoning:** Watch each step unfold — no black box
- **ATS-ready output:** Keywords tailored to the specific role
- **No fabrication:** Only reframes and surfaces what you already have
- **Fully local:** Runs entirely in-browser, no data stored on servers

---

## Built with GitHub Copilot

Copilot was used throughout development:
- Implementing Foundry IQ semantic retrieval with error handling
- Structuring the multi-step agent orchestration
- Refining prompts for each reasoning step
- Generating retry logic for rate-limited APIs
- Building the architecture diagram

---

## Security

API keys are **never** stored or committed. For production, API calls would move to a secure backend with environment variables and Azure Key Vault — keys never exposed to the client.

---

## Demo

**Live:** [Add your deployed link]  
**Video:** [Add YouTube/Vimeo link]

---

*Submitted to Microsoft Agents League Hackathon — Creative Apps Track — June 2026*