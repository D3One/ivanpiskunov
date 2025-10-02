# 1.2 — Hiring & Interviewing

**Core idea (what the author argues):** Hiring is inherently uncertain—even “a world-class interview process is successful only about 70 percent of the time.” The antidote is a **structured, scalable system** that reduces bias, measures outcomes, and makes it possible for others to hire with the same quality you would. *Hire deliberately, track your success, and correct fast when it’s wrong.*  

**What to design for:**

* **Candidate experience:** Be intentional about how candidates feel during and after the process; your reputation compounds online and affects close rates. 
* **Equitable opportunities:** Replace “gut feel” with **rubric-based scoring** tied to the JD to minimize unconscious bias. 
* **Scalability:** Build a repeatable system so others can run the same interviews and reach consistent conclusions. 

**Practical playbook:**

* **Use structured interviews (e.g., Topgrading-style)** that step through 2–5 prior roles and ask the same evidence-seeking questions, with a **scorecard** anchored to core values (e.g., “respectful challenge”). *Keep a dedicated notetaker.*  
* **Assess real coding, but balance for drop-off.** You must see candidates write code, yet heavy take-homes increase funnel attrition. Balance **predictive ability**, **drop-off**, and **candidate experience**; consider live pair-programming or right-sized tasks.   
* **Add explicit early checks.** A **90-day probationary/introductory period** with 15–30-day check-ins—or **contract-to-hire**—improves transparency and speeds correction. *“Hire slow, fire fast.”*  
* **Make and present offers with context.** Decide level from your rubric, map to compensation bands, and supply an **equity context spreadsheet** (shares outstanding, strike, latest valuation). Then **sell the offer** via **call → email → dinner**.   

*Examples (2 case-style scenarios):*

1. **Scaling beyond the founder:** *A seed-stage CTO* documents a role rubric, switches to **panel + scorecard** interviews, adds a 90-day intro period, and reduces “bad-hire time to correction” from 8 months to 6 weeks.
2. **Fixing a leaky funnel:** *A growth startup* replaces a 12-hour take-home with a **90-minute pair session** on a repo mirroring the stack; completion rate jumps from 35% to 78% while on-the-job signal stays high.

---

# 1.3 — Onboarding

**Core idea (what the author argues):** Good onboarding serves three goals: **respect the employee**, **evaluate the hire**, and **build culture**. It accelerates time-to-impact and gives managers clear signals about fit and performance.  

**Philosophy & scope:**

* **Shared responsibility (“Boy Scout Rule”).** Onboarding content goes stale; *expect* newcomers to improve docs as they go. **Everyone owns the polish.** 
* **Company-wide consistency + team-level customization.** Keep the *experience* and cultural introduction consistent across teams, but tailor the **milestones and materials** for each team/role. 

**Practical playbook (documents & milestones):**

* **Two artifacts:**

  * **“Engineering Guidebook”** as the **single source of truth** for opinions, best practices, and operations expected to be uniform across engineering. 
  * **“Welcome to [Company] Engineering: Day-1 Guide”** with step-by-step setup, access, tools, *first tickets*, and success criteria. 
* **Milestone design:** Define **first-week/first-30/first-90-day goals** that are observable and map to your rubric; pair each new hire with a **buddy** and schedule **15–30-day check-ins** (aligns with the intro period in 1.2). 
* **Measurement:** Use onboarding to **evaluate hiring quality**—did the hire meet the milestones? If not, escalate coaching or consider parting ways (see 1.4/termination guidance for mechanics).  

*Examples (2 case-style scenarios):*

1. **Day-1 to Day-5 sprint:** *A new backend engineer* completes access, builds the dev environment, ships a small bugfix behind a flag, and writes a **PR checklist** update to the Guidebook. Result: PR merged by Day 3; docs improved immediately.  
2. **Cross-team consistency:** *Frontend vs. Platform teams* share an identical **cultural intro + milestones format**, but each has specific “first tickets” and stack primers. Feedback surveys show higher perceived fairness and faster confidence ramp. 

*Italic note:* *Don’t bury newcomers in unprioritized tickets; one curated starter task + a visible quick win beats a week of “reading”.*

---

# 1.5 — Team Makeup

**Core idea (what the author argues):** Composition should reflect your **problem mix**. Senior engineers produce **more durable, lower-defect solutions** across larger surfaces, but **not every project requires senior depth**. Choose seniority and specialization intentionally, then evolve it as scale increases.  

**When to bias for senior talent:**

* New greenfield architecture; legacy/brownfield rescue; rapidly changing requirements; new/untested tools & patterns; need to establish **new ways of working** without strong external guardrails. 

**Specialization over time:**

* **Day-1 reality:** tiny teams must wear many hats. As headcount grows, increase specialization based on persistent bottlenecks. 
* **Guidelines by team size:**

  * **1–5:** mostly **generalists**, light split across front-end/back-end/mobile. 
  * **5–15:** start **specializing** by product/skill area (backend, FE architecture/design, DevOps, testing); around **15+**, consider dedicated **Testing** and **DevOps**. 
  * **15–30:** hire **subfield experts**; inefficiencies in “how work gets done” get expensive—invest in DX and tooling. 
  * **30+:** organize into **pods** or by product line; make cross-functional units capable of independent delivery. 

**How to choose what to hire next (signal sources):**

* **Listen to the team** for persistent pain, not transient spikes.
* **Seek productivity hurts** (e.g., FE-heavy team with BE reliability gaps ⇒ hire BE/DevOps; same logic for testing and DX).
* **Specialize with scale:** try to stay generalist-heavy until you pass ~12 engineers. 

*Examples (2 case-style scenarios):*

1. **Brownfield rewrite:** *A startup with an 8-year monolith* prioritizes senior hires (BE lead, Staff DX) for 2 quarters, establishing patterns and CI/CD guardrails; follows with mid-level generalists to scale delivery. Outcome: defect rate down 40%, lead time down 30%. 
2. **Post-Series A specialization:** *Team grows from 7→18.* They add **QA lead** and **DevOps** at 15 engineers, then split into **product-aligned pods** at 30, each cross-functional (PM, FE, BE, QA, partial DevOps). Incident MTTR halves after pod formation.  

*Italic note:* *Revisit composition quarterly; hiring momentum can lock in the wrong mix if you don’t course-correct.*

---

## Pull-quotes (short, compliant)

* “Even a world-class interview process is successful only about 70 percent of the time.” 
* “How can you hire a software engineer without having had them write code for you?” 

---
