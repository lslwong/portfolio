# AI & Automation Portfolio

---

## 1. Employer Onboarding Conversational Agent
### ElevenLabs TTS + STT → Conversational AI Employer Onboarding and Job Opening Creation Workflow

**GitHub:** https://github.com/lslwong/employerconvoagent

**What it is:** A voice-based conversational agent that replaces Glints' employer onboarding form flow. New employer leads conduct a structured intake conversation via voice — the agent collects company details, hiring needs, candidate profile, and urgency — and outputs a completed sample job posting for the employer to preview plus a CTA to download the app and complete the posting action. Secondly, a structured JSON summary for the sales team is generated and can be patched directly into the CRM for further follow-up.

**Why ElevenLabs:** ElevenLabs TTS handles the agent's voice output; STT captures employer responses in real-time. Voice quality was the deciding factor — a robotic voice in a sales-adjacent context creates friction and drives drop-off. A human-sounding voice creates trust and keeps employers on the call. The STT loop makes the interaction genuinely conversational rather than form-filling with a voice UI.

**Architecture:**
- **Input:** Employer speaks responses during onboarding call
- **STT:** ElevenLabs STT transcribes in real-time and allows employer to confirm the input via text. In future versions, I'd design it so that the employer doesn't need to see the transcription and approve it so it feels like a normal call.
-  **LLM layer:** Processes inputs, handles follow-ups and clarifications. Currently, the LLM layer struggles a bit with speed due to the lower-tier reasoning model that we've hooked it up to. 
- **TTS:** ElevenLabs TTS delivers questions and confirmations in a natural, conversational Indonesian female [voice](https://elevenlabs.io/app/voice-library?voiceId=JaUVfDrFcfwGIsv8X2kN). I've deliberately avoided overly corporate / professional sounding voices and opted for a friendlier, everyday voice as it tested well for local SME owners who'd like to speak to a "real person"; overly coroporate personas intimidate them. 
- **Output:** Job listing sample created according to employer-provided information for employer review > app download flow to complete posting. Additionally, a structured employer profile JSON can be sent to our CRM / sales workflow directly after the conversation ends. 

**Demo video** [here](https://drive.google.com/file/d/1IqXgyIZfvzobh8gvraMpj5Gs6qJg4wIU/view?usp=drive_link)

---

## 2. Performance Marketing Analytics Automation
### Claude + Windsor.ai + Airbridge → Real-time campaign reporting & creative performance analysis

> **Status:** In production at Glints. Two of three planned automations live; third in development. 

**The problem:** The performance marketing team was spending 2–4 hours daily on manual reporting — pulling and reconciling data from Google Ads, Meta Ads, TikTok Ads, and Airbridge (MMP) and calculating CPAs and budget absorption for day-on-day / week-on-week analyses to make budget adjustment decisions. Additionally, creative assets' performance analysis took up significant bandwidth due to the clunky design of the ad platforms' dashboards 

**The solution:** A Claude-based reporting and analysis system connected to all data sources via Windsor.ai (unified API layer) and Airbridge, executing structured analytical workflows via SKILL.md-based instructions.

**Architecture:**
- **Data sources:** Google Ads, Meta, TikTok → Windsor.ai; Airbridge for final install/conversion attribution
- **LLM:** Claude (Sonnet) as the reasoning and reporting layer
- **Interface:** Claude Project with SKILL.md instructions defining each workflow

---

### Automation 1: Claude Hourly & Daily Performance Tracker Skill

**What it does:** On demand or scheduled — pulls the full campaign table for the current day up to the current hour: spend by platform, installs, sign-ups, and other key user acquisition quality metrics. Compares against the same time window last week and yesterday. Calculates budget absorption and flags any metric deviating markedly from guardrails or WoW trends.

**Data logic:**
- Spend: Windsor.ai (to access ad platform APIs)
- Installs/Sign-ups/FTA1D: Airbridge (higher attribution confidence than ads platform native reporting)
- CPI = Windsor spend / Airbridge installs
- DoD and WoW comparisons filtered to same-hour window, with automated campaign strategy adjustment recommendations that can be referenced by performance marketer 

**Status:** Live. Github link [here](https://github.com/lslwong/performancemarketingdailydashboard/).

---

### Automation 2: Creative Asset Performance Analysis, hosted on as a web app on Vercel

**What it does:** Weekly pull of all active ad assets across Meta and Google — headline, copy, creative type, CTR, CPI, cost. Performance is benchmarked against the median for each asset type. Flags underperformers and surfaces top performers for replication briefs.

**Why this matters:** At scale (30+ active creatives across 3 platforms refreshed biweekly), manual asset review takes a full afternoon per week. This reduces it to a 15-minute review of flagged items.

**Status:** Live for Meta and Google. Link [here](https://asset-analysis-glints.vercel.app/).

---

## 3. ElevenLabs Studio: Content Creation Experiments

### 3a. KOL Content Dubbing — Indonesian to Singaporean English

**What it is:** Mega KOL content originally produced in Bahasa Indonesia, dubbed into Indonesianpaccented English using ElevenLabs Studio that has high fidelity to the original KOL's voice. 

**Why:** Glints has strong KOL production capabilities in Indonesia but limited localised content for Singapore and Malaysia. Dubbing with voice cloning is significantly faster and cheaper than reshooting with local talent.

Vina Muliana viral video dubbed in her own voice in English, using the latest Elevenlabs v2 Dubbing Model, link [here](https://drive.google.com/file/d/1svKFVwOzheGcQsLzKPIpYhQb6m_obCYm/view?usp=drive_link). I found that with the new v2 UI, it was more difficult to fine tune the quality directly, and there were some inconsistencies with regards to background audio treatment at the start vs. the end of the video when dubbing quality significantly improved. I'm still investigating what's driving this. 

---

### 3b. Voice Clone — Aterra Social Media Marketing Voiceover

**What it is:** A voiceover for Aterra's social media marketing content produced using a voice clone of my own voice built in ElevenLabs Studio. Aterra is my friend's luxury travel agency. 

**Why this matters:** A marketer using their own voice as a replicable content asset — consistent voice identity across high-volume social content without recording every piece individually.

Namibia fly-in safari marketing video link [here](https://drive.google.com/file/d/1xYttCCbragJntypcw-hrzrO5417TIhFV/view?usp=sharing).

---

## Technical stack

- **LLMs:** Claude (Sonnet/Haiku), GPT-4
- **Data:** Windsor.ai, Airbridge (MMP), Google Ads API, Meta Ads API, TikTok Ads API
- **Voice AI:** ElevenLabs TTS + STT (production), ElevenLabs Studio (content)
- **Workflow:** Claude SKILL.md-based agentic workflows, MCP connectors
- **Code:** Python (data processing, API calls), JSON/CSV pipeline work

---

*laurice.wong@gmail.com · github.com/lslwong · May 2026*
