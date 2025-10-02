# Managing the Team 👉 

## Big Idea

**Great CTOs manage by designing systems**—for structure, roles, autonomy, measurement, learning, and communication—*not* by micromanaging tasks. A team becomes effective only when you give it **tools and rules**; just grouping people doesn’t make them a team. *Your job is to architect the environment where people can do their best work.* 

---

## Team Charter

**What it is:** A short, plain-English document that defines **purpose, scope, customers, resources, required skills, and key metrics** for the team. **Keep it concise.**   

**Why it matters:** **Clarity reduces thrash.** When everyone knows *why* the team exists and *how* success is measured, decision cycles shorten and cross-team alignment improves. *A good charter also protects focus—saying what the team does **not** own is as important as saying what it does.* 

**Practice:**

* **Write the charter** with your PM/lead(s) and publish it in your knowledge base.
* **Include KPIs** the team can influence (e.g., time-to-resolve, ticket volume). 

*Examples (2):*

1. *Support Engineering* adopts a charter: “We own incident triage and data access (read-only for most, elevated for a few), we don’t ship code—dev teams do.” Result: fewer hand-off loops. 
2. *Growth Team* adds “internal customers” to its customer list and adds “activation rate” and “time-to-experiment” as KPIs; experiments accelerate.

---

## Team Structure

**Guiding principle:** **There is no one perfect structure.** Culture, temperament, business criticality, and customer proximity all shape what works. 

**Span of control:** A practical rule of thumb is **≈7 direct reports per manager**; larger groups are exceptions that require special conditions (e.g., homogeneous support/testing). *Plan for growth—assume the team will double.*  

**Common patterns** (choose deliberately):

* **Product-aligned pods:** FE/BE/QA/support per product line; each pod reports up to a line manager. **Great for clarity and accountability.** 
* **Lifecycle-oriented:** Teams by lifecycle stage (acquisition, activation, retention). **Optimizes continuity of experience.** 
* **Customer/Vertical-based:** Teams by customer segment or industry. **Maximizes domain empathy.** 
* **Hybrid:** Mix and evolve as needs change. **Start simple; specialize as you scale.** 

*Examples (2):*

1. *B2B SaaS with two products* moves from a monolithic team to two **product pods**; bug volume per release drops as ownership tightens. 
2. *Marketplace startup* splits into **lifecycle teams** (supply vs. demand vs. trust & safety); cross-team SLAs coordinate hand-offs.

---

## Titles & Levels

**Why titles matter:** Titles shape expectations—internally and externally. They signal **responsibility, experience, pay band, and level in the hierarchy**; people *do* care about them. **Choose titles intentionally.**  

**Reality check:** There’s **no universal standard**—“Senior” in one company can equal “Mid” in another. Build your own clear ladder and definitions. 

**Practice:**

* Define **scope, impact, autonomy, and leadership** expectations per level.
* Review titles during growth/comp cycles to avoid **title inflation**.

*Examples (2):*

1. *Fast-growing startup* formalizes an IC ladder (IC1–IC6) with behavioral anchors; promotions stop being ad hoc and bias-prone.
2. *Platform team* changes “DevOps Engineer” to “Platform Engineer” to better reflect scope and career path; recruiting pipeline quality improves.

---

## Working with the Team: Autonomy, Metrics, Accountability

**Autonomy:** Match **decision rights** to maturity. Early on, provide more guidance; as capabilities grow, **delegate architectural and process decisions** within guardrails. *Autonomy without clarity creates chaos; clarity without autonomy creates stagnation.*

**Metrics:** Pick metrics that reflect the team’s mission (from the charter). Typical examples: **lead time, change failure rate, incident time-to-resolve, backlog health**, etc. *Measure what you’ll act on; vanity metrics erode trust.* 

**Accountability:** Make **outcomes** (not inputs) the unit of accountability—tie retrospectives and reviews to those outcomes. *When quality targets slip, adjust staffing/process, not just pressure.* 

*Examples (2):*

1. *Mobile team* adopts a quality bar (crash-free sessions, P90 cold start). With clearer targets, they negotiate fewer one-off escalations and work the prioritized queue. 
2. *Payments team* links on-call load and incident MTTR to roadmap capacity; when the queue grows, they staff reliability work instead of pushing features.

---

##  1-to-1

**Purpose:** Build trust, surface blockers early, and coach for growth. **Cadence matters**—*weekly or biweekly* is typical for fast-moving teams. Use a consistent agenda: progress, priorities, obstacles, feedback *both ways*, and development goals.

**Practice:**

* Keep a shared, running doc; track commitments.
* Invite hard topics: *psychological safety drives real signal*.
* **Do not** turn 1:1s into status meetings—use project tools for that.

*Examples (2):*

1. *New manager* institutes 30-minute weekly 1:1s with three prompts: “What’s best/worst this week?” “Where do you need me?” “What should we stop doing?”
2. *Senior IC* uses 1:1s to propose a testing revamp; manager helps scope an experiment and aligns stakeholders.

---

## Learning & Development

**Build a portfolio of learning modes**—mix low-cost, high-frequency options with occasional deep dives:

* **Online libraries/resources** and **platform certifications** (role-relevant). 
* **Bootcamps:** short, immersive courses; affordable for companies; great for career pivots.
* **User groups/meetups:** monthly, community-driven, strong for networking and practical tips—*encourage attendance*.
* **Internal training:** brown bags, design reviews, guilds. 
* **Conferences:** budget deliberately; require a brief write-up of takeaways; also valuable for employer branding and future recruiting.  

*Examples (2):*

1. *Platform team* runs a quarterly **Testing Guild**; after three sessions they standardize on e2e + visual regression for critical flows and cut regressions. 
2. *Data team* attends an analytics conference; they return with a doc proposing dbt-based ELT and a BigQuery POC, which later becomes the source of truth. 

---

## Communication

**Default to written, durable channels for broad updates.** **Email** beats chat for information everyone must see and retrieve later. Maintain an **engineering@** mailing list and use it for policy/process changes, org updates, and major launches. *Chats are for real-time coordination; not for canonical announcements.* 

**Meetings:** Use a predictable **operating cadence** (e.g., weekly team standup, biweekly planning, monthly reviews). Keep agendas short; distribute pre-reads.

**Feedback:** Establish **clear feedback loops**—retros, incident reviews, skip-levels—so issues flow *up* as well as *down*.

*Examples (2):*

1. *Org update* goes to the mailing list with TL;DR, context, and links to docs; the announcement is searchable six months later when new hires need context. 
2. *Bug escalations* stop ping-ponging in Slack after you stand up a **triaged queue** and teach managers to be **umbrellas**, not **funnels**. 

---

## Quick Checklist

* **Publish a team charter** with mission, scope, customers, resources, skills, and KPIs.   
* **Right-size structure** (product, lifecycle, vertical, or hybrid) and **respect span limits**.  
* **Define titles/levels** that signal scope and growth paths. 
* **Manage with autonomy + metrics + accountability** (work the queue, not the engineers).  
* **Invest in learning** (bootcamps, user groups, internal training, conferences).   
* **Communicate for durability**—email for broad updates; keep cadences and feedback loops healthy. 

---
