# Archway — Team Enablement Guide

*For a new FS Solution Engineer picking up Archway for the first time. 30 minutes to competent, one demo to convinced.*

---

## 1. What this is, in two minutes

Archway is a single HTML file that answers the three questions every architecture conversation comes down to:

1. **What connects to what?** — the canvas
2. **How does it connect?** — typed connections: protocol, auth, encryption, sync/async/event/zero-copy, PII/financial classification
3. **Why should it connect that way?** — the part no diagramming tool does: risk analysis cited to published control frameworks, scored path comparison, an Optimize engine, and discovery questions

Lucidchart draws the boxes. Archway argues about them. That third question is the whole product — if you only ever draw with it, you're using 20% of it.

It runs from a double-click. No install, no server, no login, works offline, works on an iPad in a customer's conference room. The file **is** the app, and the JSON it exports **is** the architecture — which is why it lives in a Git repo.

## 2. The honesty model — what you're allowed to claim

Archway has three layers, and your credibility depends on never confusing them:

| Layer | What it is | What you say |
|---|---|---|
| **Cited facts** | 27 framework citations (NIST, OWASP LLM Top 10 2025, PCI DSS v4.0.1, FFIEC, GDPR, DORA, MCP spec), vendor claims, template fidelity — all independently audited against primary sources, zero fabrications | "Every finding traces to a published control — click the source chips." |
| **Deterministic detection** | Risk rules fire on actual graph facts. "PII passes into a model" means a PII-flagged edge literally terminates at an LLM node | "The engine isn't guessing — it's reading the diagram." |
| **Disclosed heuristics** | The 1–5 pattern scores, health score, preset weights, template latencies. Directionally grounded in literature, labeled "illustrative" in-product | "The scores are calibrated judgment to structure a conversation — not measurements." |

One more precision point: the in-app assistant is **authored answers computed over the live canvas** — fact-checked, canvas-aware, but a finite script. Only ✨ AI-extract makes a real model call. Say it that way and no one can catch you overselling.

## 3. Your first 30 minutes (do this before demoing to anyone)

1. Open `archway.html`. The AI Banking Assistant template loads — click **▶ Play** and read the talk track once through.
2. Click a node, then a connection. Change a protocol. Toggle PII on an edge and watch **◎ Analyze** react.
3. Click **✨ Optimize** — accept one suggestion, reject one.
4. **⇄ Compare Paths**: Salesforce → Core Banking, flip the "Optimize for" presets, watch the winner change (scale/reliable → event-driven; fast/cost/simple → direct; security/long-term → governed layer).
5. Paste this into **⇪ Import**:
   ```
   flowchart TD
     Cust[Customer] --> Mob[Mobile App] --> SF[Salesforce]
     SF --> Agent[AI Agent] --> LLM[LLM]
     SF --> Core[Core Banking]
   ```
   Run Analyze. Notice it flags the AI path *and* the point-to-point link — that's the import→critique loop you'll run on customer diagrams.
6. **⎙ PDF** — untick two sections, generate, see what the customer leave-behind looks like.
7. Break something. Delete the MCP server from the bank template and re-run Analyze — understanding what makes findings appear is understanding the tool.

---

## 4. The 15-minute first demo

### Opening setup *(before you share your screen)*

> "Every architecture review at [Customer] starts the same way: someone opens a diagram that was accurate eight months ago, three people disagree about what the arrows mean, and the real question — *should it be built this way?* — never gets asked, because the diagram can't answer it. I want to show you a different way to have that conversation. Fifteen minutes, one screen, and at the end you'll have something your architects can argue with productively."

### Scene 1 — The diagram that knows what it's drawing *(3 min)*
*Pain: diagrams are dumb pictures; metadata lives in people's heads.*

**What to show:**
- Load the **AI Banking Assistant** template
- Click the MuleSoft → Core Banking edge: protocol, mTLS + OAuth, latency, financial-data flag
- Toggle the **PII** highlight chip — the sensitive paths light up alone

**Talk track:**
> "This looks like a diagram, but every line is typed. This connection isn't 'an arrow' — it's REST over mTLS with OAuth, about 140 milliseconds, carrying financial data. Here's every path PII takes through [Customer]'s estate — one click. When your risk team asks 'where does customer data actually go?', this is the difference between an afternoon of archaeology and pressing a button."

> *"Pause point: when someone at [Customer] asks that question today, who answers it — and how long does it take?"*

### Scene 2 — The architecture that explains itself *(4 min)*
*Pain: reviews depend on who's in the room; findings are opinions.*

**What to show:**
- Hit **◎ Analyze** — health score, findings stacked by severity
- Open "PII passes into a model" — read the recommendation, point at the **source chips** (OWASP LLM02, GDPR Art. 32, GLBA)
- Point at the **"Ask the customer"** questions under a finding
- Hit **✨ Optimize**, accept "PII leaves the trust boundary" — watch the Trust Layer node appear and the finding flip to passing

**Talk track:**
> "Now the part a drawing tool can't do. The engine read the graph and found this: raw customer context reaching the language model. That's not my opinion — it's OWASP's 2025 LLM Top 10 and GDPR Article 32, cited right there. And watch: I accept the suggestion, it inserts the masking layer — on our platform that's the Einstein Trust Layer, which is enforced inline, you don't build it — and the finding goes green. Your architects don't have to trust me. They can check the sources."

> *"Pause point: who plays the challenger role in [Customer]'s design reviews today — and what happens when they're not in the room?"*

### Scene 3 — The argument, settled with evidence *(4 min)*
*Pain: 'how should A talk to B' decisions are fought with slideware.*

**What to show:**
- **⇄ Compare Paths**: Salesforce → Core Banking
- The ranked path cards; the recommended card's benefits/tradeoffs
- Flip "Optimize for" from **Balanced** → **Fastest implementation** → **Highest scalability**; the winner changes each time

**Talk track:**
> "Here's the meeting that usually takes three weeks: should Salesforce hit the core directly, go through the integration layer, or ride events? Archway scores every real path on the canvas across nine dimensions. And here's the honest part — change what you're optimizing for, and the recommendation changes. Optimize for speed-to-market, direct wins. Optimize for scale, event-driven wins. The scores are calibrated judgment, labeled as such — the point isn't that the tool decides. It's that [Customer]'s teams finally argue about the *criteria* instead of the conclusion."

> *"Pause point: what is this architecture actually optimized for today — and did anyone choose that on purpose?"*

### Scene 4 — Their diagram, not mine *(3 min)*
*Pain: demos show the vendor's world; the customer's mess stays unexamined.*

**What to show:**
- **⇪ Import** → drop in a draw.io file or screenshot (underlay appears; AI-extract if keys are set up)
- **Analyze** on the imported estate — the **Fundamental Approach** panel ("partially governed… early AI… 40% custom")
- **⎙ PDF** — tick/untick sections, add the customer name, generate

**Talk track:**
> "Everything so far was my reference architecture. This is yours. I drop in the diagram [Customer]'s team already has — draw.io, Mermaid, even a screenshot I trace or extract — and the same engine reads it. This panel is the honest mirror: how much is point-to-point, where AI has no governance yet, how much is custom-built. Every finding comes with the questions worth asking your own team. And when we're done, I print exactly the sections you want your steering committee to see — and nothing you don't."

> *"Pause point: if I ran this on your current-state diagram today, what do you think it would flag first?"*

### Pause points, compiled

| Scene | Discovery question |
|---|---|
| 1 | Who answers "where does PII go?" today, and how long does it take? |
| 2 | Who challenges designs when the senior architect isn't in the room? |
| 3 | What is this architecture optimized for — and was that chosen on purpose? |
| 4 | What would this flag first on your current-state diagram? |

### Close — the cascade

> "Notice these weren't four features — they were one loop. Typed diagrams make analysis possible. Analysis makes the review objective. Objective reviews make the A-to-B argument finite. And running it on *your* diagram turns a demo into a working session. The deliverable isn't a picture — it's a review your risk team can check the sources on, and a conversation your architects actually want to have. That's the promise: not a prettier diagram — a diagram that argues back."

---

## 5. The customer workshop variant (45–60 min, their diagram)

The demo sells the idea; the workshop creates the deal. Sequence: **Import their diagram (get it in advance)** → verify the extraction *with them* (5 min of "did I draw your world right?" — this builds more trust than any slide) → **Fundamental Approach** panel as the agenda → walk 3–4 findings max, leading with the **Ask-the-customer questions, not the findings** → Compare Paths on one integration they're actively debating → build the PDF live, letting *them* choose the sections → leave the JSON with their architect. You ran a discovery session disguised as a tool demo; their answers to the question bank are your MEDDIC evidence.

## 6. Objections you will hit

| They say | You say |
|---|---|
| "Is this AI making things up?" | "The analysis engine isn't generative — rules over the graph, findings cited to NIST/OWASP/PCI/FFIEC/GDPR/DORA, independently audited. The only generative step is image extraction, which is labeled and verified against the original." |
| "The scores favor the integration layer — of course, you're Salesforce." | "Fair — and it's disclosed in the product. The balanced default reflects a governed-enterprise stance; flip the presets and direct or event-driven win on their home turf. The criteria are on the table, which is more than most slideware offers." |
| "Our architecture is confidential." | "It runs from a local file, offline, no telemetry, nothing leaves the machine — except AI-extract, which calls the Anthropic API and is optional. Trace the diagram manually and nothing is transmitted anywhere." |
| "We use [other tool]." | "Keep it. Archway imports draw.io and Mermaid, and the JSON export means this becomes the review layer, not a replacement canvas." |
| "Is the health score benchmarked?" | "No — and it says so on screen. It's an illustrative heuristic to rank findings, not a certification. The findings underneath it are the substantiated part." |

## 7. Running this as a scalable team asset

**The repo is the product.** `github.com/chrismccarthy-ship-it/under-the-archway` holds the tool, this guide, and the version history. Pull before every customer session; never demo from a months-old download. (Enable GitHub Pages and the repo doubles as a live demo link.)

**Architecture-as-code per account.** After every workshop, export the JSON. That file is the account's architecture record — findings reproduce exactly when you reload it, which means your week-2 review and your month-6 review are diffable. Store account JSONs in your **account folders / Quip / internal systems — never in this repo** (it's the tool's home, and anything customer-identifiable stays off GitHub entirely).

**Three guardrails, non-negotiable:**
1. **AI-extract sends the image to the Anthropic API** under whoever's key is entered. For customer-confidential diagrams, clear it against data-handling policy first — or use the underlay-and-trace path, which transmits nothing.
2. **Verify every import before presenting.** Imported edges are flagged "verify against source" for a reason; an analysis of a wrong diagram is confidently wrong.
3. **Never present layer-3 heuristics as findings.** The table in §2 is the line. The in-product disclaimers back you up — don't talk past them.

**Contribution loop.** New reference template for a pattern you keep demoing? New risk rule? New discovery questions that landed well? PR to the repo with a source for any factual claim — the zero-fabrications bar is the asset's moat, and one uncited "fact" spends it. Template additions follow the existing pattern: nodes, edges, story, all metadata illustrative-but-realistic.

**Onboarding cadence that works:** Day 1 — §3 hands-on. Day 2 — shadow a demo, follow along in your own copy. Week 1 — give the §4 demo internally, get torn apart. Week 2 — run §5 on a real account's diagram with a senior SE in the room. After that, you're the one teaching it.

## 8. Quick reference

| Button | What it does |
|---|---|
| **⇪ Import** | JSON / draw.io / Mermaid / image (underlay + optional AI-extract) |
| **◎ Analyze** | Framework-cited findings + Fundamental Approach + Ask-the-customer questions |
| **✨ Optimize** | Accept/reject improvement suggestions that update the diagram |
| **⇄ Compare Paths** | Score every route A→B; presets change the recommendation |
| **▶ Play** | Animated walkthrough; 💬 toggles the talk track |
| **⎙ PDF** | Report builder — include/exclude sections, customer + author fields |
| **⤓ JSON** | Lossless export — the architecture as code |
| **◈ Brand** | Customer logo/palette + Noun Project icons (BYO keys, memory-only) |
