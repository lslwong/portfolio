# AI & Automation Portfolio
**Laurice Wong** · Head of Strategy & Marketing, Glints TapLoker · Apr 2024 – Present

---

## 1. Employer Onboarding Conversational Agent
### ElevenLabs TTS + STT → Conversational AI workflow

**GitHub:** https://github.com/lslwong/employerconvoagent

**What it is:** A voice-based conversational agent that replaces Glints' employer onboarding form flow. New employer leads conduct a structured intake conversation via voice — the agent collects company details, hiring needs, candidate profile, and urgency — and outputs a structured JSON summary for the sales team.

**Why ElevenLabs:** ElevenLabs TTS handles the agent's voice output; STT captures employer responses in real-time. Voice quality was the deciding factor — a robotic voice in a sales-adjacent context creates friction and drives drop-off. A human-sounding voice creates trust and keeps employers on the call. The STT loop makes the interaction genuinely conversational rather than form-filling with a voice UI.

**Architecture:**
- **Input:** Employer speaks responses during onboarding call
- **STT:** ElevenLabs STT transcribes in real-time
- **LLM layer:** Processes inputs, handles follow-ups and clarifications
- **TTS:** ElevenLabs TTS delivers questions and confirmations in a natural voice
- **Output:** Structured employer profile JSON → CRM / sales workflow

**Demo video:** *(link to be added)*

*(Full technical documentation and setup guide in the GitHub repo above)*

---

## 2. Performance Marketing Analytics Automation
### Claude + Windsor.ai + Airbridge → Real-time reporting & creative analysis

> **Status:** In production at Glints TapLoker (May 2026). Two of three planned automations live; third in development. SKILL.md files to be published to GitHub — link to be added.

**The problem:** The performance marketing team was spending 2–4 hours daily on manual reporting — pulling data from Google Ads, Meta Ads, TikTok Ads, and Airbridge (MMP), calculating CPAs and budget absorption, and flagging underperforming creatives.

**The solution:** A Claude-based reporting and analysis system connected to all data sources via Windsor.ai (unified API layer) and Airbridge, executing structured analytical workflows via SKILL.md-based instructions.

**Architecture:**
- **Data sources:** Google Ads, Meta, TikTok → Windsor.ai; Airbridge for final install/conversion attribution
- **LLM:** Claude (Sonnet) as the reasoning and reporting layer
- **Interface:** Claude Project with SKILL.md instructions defining each workflow

---

### Automation 1: Hourly & Daily Performance Tracker

**What it does:** On demand or scheduled — pulls the full campaign table for the current day up to the current hour: spend by platform, installs, sign-ups, FTA1D. Compares against the same time window last week and yesterday. Calculates budget absorption and flags any metric deviating >10% from guardrails or WoW trend.

**Data logic:**
- Spend: Windsor.ai (platform APIs)
- Installs/Sign-ups/FTA1D: Airbridge (higher attribution confidence than platform-reported)
- CPI = Windsor spend / Airbridge installs
- DoD and WoW comparisons filtered to same-hour window

**Status:** Live. Known issue: Meta spend occasionally mismatches platform dashboard (Windsor schema mismatch — in debug). *[GitHub link — to add]*

---

### Automation 2: Creative Asset Performance Analysis

**What it does:** Weekly pull of all active ad assets across Meta and Google — headline, copy, creative type, CTR, CPI, cost — benchmarked against the median for each asset type. Flags underperformers and surfaces top performers for replication brief.

**Why this matters:** At scale (30+ active creatives across 3 platforms), manual asset review takes a full afternoon per week. This reduces it to a 15-minute review of flagged items.

**Status:** Live for Meta and Google. Google headline extraction limited by API — workaround in testing. *[GitHub link — to add]*

---

### Automation 3: AI-Assisted Copywriting Generation *(In Development)*

Feed Claude brand guidelines + top-performing copy examples + guardrails → generate a batch of alternative copy variants → output as CSV for direct upload to platform ad managers.

---

### Automation 4: Repetitive Creative Asset Processing *(Aspirational)*

AI image models to batch-process repetitive creative tasks — removing QR codes, replacing logos, resizing across aspect ratios. Currently evaluating GPT image editing vs. Canva batch processing.

---

## 3. ElevenLabs Studio: Content Creation Experiments

### 3a. KOL Content Dubbing — Indonesian to Singaporean English

**What it is:** KOL content originally produced in Bahasa Indonesia, dubbed into Singaporean English using ElevenLabs Studio for Glints' Singapore employer marketing.

**Why:** Glints has strong KOL production capabilities in Indonesia but limited localised content for Singapore. Dubbing with voice cloning is significantly faster and cheaper than reshooting with local talent.

*(Asset link — to be added)*

---

### 3b. Voice Clone — Aterra Social Media Marketing Voiceover

**What it is:** A voiceover for Aterra's social media marketing content produced using a voice clone of my own voice built in ElevenLabs Studio.

**Why this matters:** A marketer using their own voice as a replicable content asset — consistent voice identity across high-volume social content without recording every piece individually.

*(Asset link — to be added)*

---

## Technical stack

- **LLMs:** Claude (Sonnet/Haiku), GPT-4
- **Data:** Windsor.ai, Airbridge (MMP), Google Ads API, Meta Ads API, TikTok Ads API
- **Voice AI:** ElevenLabs TTS + STT (production), ElevenLabs Studio (content)
- **Workflow:** Claude SKILL.md-based agentic workflows, MCP connectors
- **Code:** Python (data processing, API calls), JSON/CSV pipeline work

---

*laurice.wong@gmail.com · github.com/lslwong · May 2026*
