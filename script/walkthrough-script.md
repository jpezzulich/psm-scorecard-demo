# PSM Program Scorecard — Walkthrough Script

**Format:** Screen recording with voiceover
**Estimated length:** 6–8 minutes
**Recommended tool:** [Loom](https://www.loom.com) (free, records screen + voiceover, one-click share)
**Screen to show:** Claude Code desktop app throughout

---

## Before You Record

- Open Claude Code desktop app
- Have a session open and ready (no prior conversation on screen)
- The skill does NOT need to be re-run live — you can narrate over the existing conversation from the scorecard you already built, or start a fresh run
- Keep this script open in a separate window to read from

---

## INTRO (0:00–0:45)

**[Show: Claude Code desktop app, empty session]**

> "Hi, I'm Jessica Pezzulich, Program Manager on the Salesforce Enablement team. I'm going to show you the PSM Program Scorecard skill — a Claude Code skill I built to automate our quarterly enablement reporting.

> Before this skill existed, building a program scorecard meant manually pulling data from Tableau, exporting survey comments, scoring programs against our framework, writing up themes, and formatting everything into a doc — a process that took several hours per program, per quarter.

> Now it takes a single conversation. Let me show you how it works."

---

## STEP 1: INVOKING THE SKILL (0:45–1:30)

**[Show: Type `/psm-scorecard` in Claude Code and press Enter]**

> "I start by invoking the skill with a simple slash command — `/psm-scorecard`.

> Claude immediately runs a pre-flight check in the background — verifying that Slack is connected, that it can authenticate to the Tableau API, and that it has access to the Readiness Salesforce org where our survey data lives. This all happens silently before it asks me anything."

**[Show: Pre-flight result and intake questions]**

> "Once the checks pass, it asks me four things: my name, the program names I want to score, the OPM+ impact data for the relevant role, and where to send the finished scorecard.

> It determines the current quarter automatically based on today's date and the Salesforce fiscal calendar — I don't have to tell it what quarter we're in."

---

## STEP 2: DATA PULL (1:30–2:30)

**[Show: The conversation where Claude pulls data and confirms program names]**

> "After I answer the intake questions, Claude pulls all the delivery metrics directly from the Tableau Live Delivery Dashboard via REST API — CSAT, attendance, reach, enrollment, class counts — for the current quarter and the three prior quarters.

> It fuzzy-matches my program names against the dashboard to confirm exact matches, so there's no ambiguity about which data it's pulling."

**[Show: Where it pulls survey comments]**

> "For survey comments, it goes directly to the source — the Readiness Salesforce org — using SOQL queries filtered by program name and quarter. This gives us the full, untruncated comment text. In this run it pulled 246 comments for Foundations and 156 for On-the-Job."

---

## STEP 3: DATA SANITY CHECKS (2:30–3:30)

**[Show: The sanity check flags message]**

> "Before scoring anything, the skill surfaces all data anomalies in a single message and waits for my response.

> In this run it flagged six things: attendance drops in both programs that are likely data artifacts from a quarter still in progress, reach below the 50% goal for both programs, the fact that trend data only goes back two quarters, and a marginal content effectiveness score just below the threshold for On-the-Job.

> It also asked me to confirm the HIGH impact call based on the OPM+ data I provided.

> I respond to all flags at once — confirmed as caution, confirmed, confirmed — and then it proceeds."

> "This step is important. The skill never silently overrides a data anomaly. It brings me into the decision so my professional judgment is part of the output."

---

## STEP 4: SCORING & ANALYSIS (3:30–5:00)

**[Show: The scoring output appearing]**

> "Now Claude scores each program using the Combined Enablement Menu Health Framework.

> It calculates Reach — unique learners divided by total enrolled. It calculates the Adoption Score — a weighted average of reach and attendance. It assigns a Quality Flag: green, yellow, or red, based on CSAT, attendance, and reach against our goals.

> And it assigns a Quadrant — Core Driver, Crowd Pleaser, Hidden Gem, or Sunset — based on the combination of reach and business impact."

**[Show: The survey themes appearing]**

> "It then analyzes all the survey comments and surfaces five to seven themes for what's going well — with representative learner quotes — and five to seven improvement themes, each with a specific, actionable opportunity. Finally it distills the top three recommended actions.

> This is the part that used to take the most time. Reading through hundreds of comments, identifying patterns, writing it up. The skill does it in seconds."

---

## STEP 5: REVIEW & PUBLISH (5:00–6:30)

**[Show: The full draft in the conversation]**

> "Before publishing anything, the skill shows me the complete scorecard draft and asks for my approval. It never posts to Slack without explicit confirmation — that's a hard rule built into the skill.

> I review it, confirm the destination — in this case my own DM — and say go ahead."

**[Show: The Slack canvas being created / the DM with the canvas link]**

> "Claude creates a Slack Canvas with the full scorecard and sends it directly to my DM with a link.

> The canvas is fully formatted — tables, emoji flags, quotes, trend data, all of it — ready to share with stakeholders or copy into a review deck."

**[Optional: Show the actual Slack canvas if you can screen-share Slack]**

---

## WRAP-UP (6:30–7:30)

**[Show: The finished canvas or the README]**

> "To recap what just happened: in a single guided conversation, the skill authenticated to three separate systems, pulled and parsed hundreds of rows of delivery data and survey comments, applied our scoring framework with data sanity checks, analyzed learner feedback for themes, and published a formatted Slack Canvas — for two programs simultaneously.

> The whole conversation took about fifteen minutes, most of which was me reviewing outputs and confirming decisions. The alternative was a half-day of manual work.

> This is the PSM Program Scorecard skill. You can find the sample output and full documentation in this GitHub repo.

> If you're interested in how it works under the hood, the skill is built as a Claude Code slash command — a structured markdown file that gives Claude detailed instructions, data sources, scoring logic, and conversational guardrails. No code deployment required."

---

## POST-RECORDING

1. Upload your recording to Loom (or YouTube/Drive)
2. Copy the share link
3. Replace the `[Watch the walkthrough](#)` placeholder in `README.md` with the actual link
4. Commit and push

---

*Script by Jessica Pezzulich · PSM Program Scorecard · October 2026*
