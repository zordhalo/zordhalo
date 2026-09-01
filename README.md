```
⠀⠀⠀⠀⢀⡠⣾⣳⡀⠀⠀⠀⠀⠀
⠀⠀⡀⠀⠚⢿⣿⣿⡿⠙⠀⠀⠀⠀
⠀⣘⣿⣇⡀⢘⣿⣿⠀⢀⣠⣶⡀⠀
⠺⣿⣷⣝⣾⣿⣿⣿⣿⣿⣹⣷⣿⠆
⠀⠘⠟⠁⠀⠀⣿⣟⠀⠀⠙⠿⠁⠀
⠀⠀⠀⠀⠀⠀⣿⣿⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⢠⣿⣿⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⢸⣿⡿⡄⠀⠀⠀⠀⠀
⠀⠀⠀⠠⣖⣿⣿⣻⡷⡄⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠈⢻⡟⠁⠀⠀⠀⠀⠀
```

# Lucas Krawczak

**Co-founder & Engineer @ [Advance Labs Inc.](https://advancelabs.dev)**, a Canadian software studio I run with my brother [@SpookYlonMuh](https://github.com/SpookYlonMuh)

*We build shit until it works.*

[![Studio](https://img.shields.io/badge/advancelabs.dev-0B0B0B?style=flat-square&logo=vercel&logoColor=white)](https://advancelabs.dev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucaskrawczak/)
[![Reddit](https://img.shields.io/badge/u%2Fxzordhalox-FF4500?style=flat-square&logo=reddit&logoColor=white)](https://www.reddit.com/user/xzordhalox)
[![X](https://img.shields.io/badge/@xzordhalox-000000?style=flat-square&logo=x&logoColor=white)](https://x.com/xzordhalox)

---

## Free subdomains

### [runs-on.dev](https://runs-on.dev) · open source · [registry](https://github.com/zordhalo/runs-on.dev)

Claim `yourname.runs-on.dev` in about twenty seconds with a GitHub account. It's live
immediately over HTTPS, and you point it at your own hosting with a pull request.

A real TLD means an ICANN application, and the 2026 round wanted $227,000 per application
before you've run anything. This gets the same custom-ending feel for about $10 a year.
The public repo is the database, so every claim is a commit anyone can read, and one
wildcard DNS record covers every name at once. Claiming is a git write, not a DNS write.

**MIT · 73 tests · one name per account · not a TLD, and I don't pretend it is**

---

## Autonomous flight

### [urban-drone-autonomy](https://github.com/Advance-Labs/urban-drone-autonomy) · open source · ✈︎ [fly it in your browser](https://drone.advancelabs.dev)

Sim-first autonomy for a small multirotor I built. The stack is pure Python behind a
`VehicleBackend` seam, so the same mission code runs against a kinematic sim, PX4
SITL, and a Pixhawk without changing the autonomy layer.

I built five environments from real OpenStreetMap data and put the simulator on the web,
so you can fly it yourself. Every number below is one the simulator produced, so there's
no marketing copy to drift out of sync.

**275 tests · no runtime dependencies · verified against PX4 SITL · Apache-2.0**

| Environment | Buildings | Tallest | What it exercises |
|---|---|---|---|
| Test grid | 25 | 54 m | Moving traffic, replanning on invalidation |
| Princess Anne Manor | 308 | 48 m | 5 m AGL, threading under distribution wire |
| Scarborough | 115 | 125 m | Car and pedestrian as legal keep-out volumes |
| North York Centre | 182 | 134 m | Surveillance with real occlusion |
| Downtown Toronto | 161 | **292 m** | Towers exceed the ceiling, so it routes around, not over |

<details>
<summary><b>Four findings that changed the hardware design</b></summary>

<br>

**Lidar can't see wires affordably.** A 12 mm conductor sits below the angular
resolution of any lidar in budget, which caps safe speed near powerlines at
3.5–5.5 m/s.

**But a camera can infer them.** Poles are trivially detectable where wires are not.
The system detects poles, works out which are connected, and avoids the inferred
catenary. That gets 100% recall with zero wire detections. Flight geometry matters more than
the sensor: one forward camera suffices if you fly a lateral sweep first.

**People are a regulatory volume, not an obstacle.** A pedestrian's legal keep-out is
~100× their body size and asymmetric, because overflight is separately prohibited.

**An inferred map can't thread a corridor.** It needs 7–10 m of standoff to cover its
own triangulation error, and at 7 m a residential corridor closes entirely. Good enough
to *avoid* a wire run; threading one needs a survey.

</details>

The airframe is a Holybro X500 V2 with a parametric OpenSCAD payload stack (Pi 5
tray, payload deck, battery tray, GNSS mast, nav-light pods), designed around a
low-light STARVIS camera. Transport Canada RPAS rules shape the design more than any
technical preference does: "autonomous" in Canadian airspace means *pilot-supervised*
autonomy, with a human able to take control at all times.

---

## Answer-engine optimization

### [AEO Toolkit](https://github.com/Advance-Labs/aeo-toolkit) · open source

A TypeScript monorepo I built that scores a site the way an AI assistant reads it:
crawl → parse → score, plus MCP servers and content agents.

**16 packages · 794 passing tests · a 54-rule scoring engine**

| Rule family | Count | Measures |
|---|---|---|
| AEO | 11 | Entity identity & consistency, `sameAs`, extractable answers, citable proof, FAQ/HowTo structure |
| E-E-A-T | 14 | Experience, expertise, authoritativeness, trust |
| Technical SEO | 29 | Crawlability, sitemap coverage & freshness, redirect integrity, canonical validity, structured data, internal linking |

Scores are cross-checked against live answers from ChatGPT, Google AI Overviews,
Perplexity, and Claude, so the number is a measurement you can re-run after fixes,
not an opinion. It's also the engine behind the studio's
[AI-visibility audits](https://advancelabs.dev/services/aeo-audit).

---

## Contributing upstream

### [Pane](https://github.com/dcouple/Pane) · open source · [runpane.com](https://runpane.com/)

A terminal-first agent IDE for running several coding agents in parallel. I run it every
day, so the two things I sent upstream are the two that were costing me something.

**[#572](https://github.com/dcouple/Pane/pull/572) — switching panes.** The "Open" launcher
flashed where the terminal had been on the first visit to every pane, because the stage guard
read *layout hasn't loaded yet* and *layout doesn't exist* as the same state. Then the terminal
that arrived sat behind an activation mask held open by two fixed delays that were standing in
for conditions nobody had written down. Replacing the delays with the conditions themselves,
and letting the activation backstop repaint instead of destructively resetting when it has
nothing to repair, took per-pane activation from **675 ms to 332 ms**.

**[#573](https://github.com/dcouple/Pane/pull/573) — renaming panes.** The IPC handler and the
edit-state handlers already existed and were exported; no component ever rendered them. Adding
the inline sidebar UI surfaced a pre-existing store bug: a main-repo session is stored twice,
and `updateSession` returned early after updating the first copy, so the sidebar went stale on
*any* `session:updated` for that pane, not just renames. Both fixed, with a Playwright test
that I confirmed fails without the store fix.

**852 lines across two pull requests · timings measured on the real Electron app, not a benchmark**

---

## Advance Labs

An independent Canadian software studio, federally incorporated under the CBCA.
We build and ship our own products, and take on fixed-scope client work.

**Services**

| | |
|---|---|
| [AI-Visibility (AEO) Audit](https://advancelabs.dev/services/aeo-audit) | 54-rule site check plus live checks of what the answer engines actually say about you, against your competitors. Fixed price, 3-day turnaround. |
| [Fixed-Scope Build Sprint](https://advancelabs.dev/services/build-sprint) | A scoped chunk of engineering for a written scope and a fixed price. AI integrations and automations, or conversion-focused Next.js builds. 1–2 weeks. |

**Products**

| | |
|---|---|
| [Dialed](https://dialed.advancelabs.dev) | Done-for-you AI phone agents for local business. Answers the line 24/7, handles questions, books appointments, transfers to a human. Live demo line on the site. |
| [Cartrix](https://www.cartrix.live) | Checkout at scale: parallel multi-account purchase automation for limited-release products. |
| BuildCode | AI building-code copilot for Ontario trades. Plain-English answers with the exact cited OBC/OESC section, built with [Kuzyn Builds](https://github.com/Kuzyn-Builds). |

**Client work:** [Kuzyn Builds](https://kuzynbuilds.com) (London, ON custom home
builder: site build + local AI-search setup) · [Next Leaf Prints](https://www.nextleaf.co/)
(Toronto printing & embroidery: storefront redesign). Case studies at
[advancelabs.dev/work](https://advancelabs.dev/work).

---

## Research

### [Quantum Hybrid Research](https://github.com/Advance-Labs/quantum-hybrid-research) · open

Three honest feasibility studies on quantum × classical, including *can quantum
accelerate LLM training?*, plus a 228-test emulator. **Every claim is tagged by its
evidence class**, so a proven result and a speculative one never read the same.

Written up at [quantum.advancelabs.dev](https://quantum.advancelabs.dev).

---

## Things I build on my own time

| | |
|---|---|
| [whoopsie-protocol](https://github.com/zordhalo/whoopsie-protocol) | Reverse-engineered the WHOOP 4.0 BLE protocol: documentation and a reference implementation. Paired with a [FastAPI backend](https://github.com/zordhalo/whoopsie-backend) for metrics ingestion, because I wanted my own biometrics out of someone else's app. |
| [agent-handoff-protocol](https://github.com/zordhalo/agent-handoff-protocol) | Durable agent sessions: serialize, transfer, and meter a running agent's state across compute hosts. MCP server + Neon + Next.js. |
| [lontario](https://github.com/zordhalo/lontario) | Open-source AI-powered hiring platform. |
| [athena-weather-mcp](https://github.com/zordhalo/athena-weather-mcp) | An MCP agent that explores weather alerts and forecasts through an embedded interactive widget (NWS + Open-Meteo). |
| [75-day-tracker](https://github.com/zordhalo/75-day-tracker) | 75 Hard tracker with habit logging, progress visualization, and PWA support. I built it because I was doing the challenge. |
| [photo-organizer](https://github.com/zordhalo/photo-organizer) | Sorts very large photo libraries into categories. |
| [linkedln-commits](https://github.com/zordhalo/linkedln-commits) | Tracks LinkedIn activity the way GitHub renders a commit graph. |
| [beacon-ai](https://github.com/zordhalo/beacon-ai) | AI-therapy application, built for the SambaNova Cloud Devpost hackathon. |

---

## ✞

| | |
|---|---|
| [code-cross](https://github.com/zordhalo/code-cross) | ✞ *Jesus Christ is Risen* ✠ |
| [st-PierGiorgioFrassati](https://github.com/zordhalo/st-PierGiorgioFrassati) | On Blessed Pier Giorgio Frassati, made for London's altar servers. |

---

## Stack

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat-square&logo=threedotjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=flat-square&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/Postgres-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PX4](https://img.shields.io/badge/PX4%20%2F%20MAVLink-19A0E0?style=flat-square&logo=drone&logoColor=white)
![OpenSCAD](https://img.shields.io/badge/OpenSCAD-F9D72C?style=flat-square&logo=openscad&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

## Connect

| | |
|---|---|
| **Studio** | [advancelabs.dev](https://advancelabs.dev) |
| **Hire us** | [advancelabs.dev/services](https://advancelabs.dev/services) |
| **GitHub org** | [@Advance-Labs](https://github.com/Advance-Labs) |
| **LinkedIn** | [in/lucaskrawczak](https://www.linkedin.com/in/lucaskrawczak/) |
| **Reddit** | [u/xzordhalox](https://www.reddit.com/user/xzordhalox) |
| **X** | [@xzordhalox](https://x.com/xzordhalox) |
| **Short address** | [zordhalo.is-a.dev](https://zordhalo.is-a.dev) |
