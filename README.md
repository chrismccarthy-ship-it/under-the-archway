# Under the Archway

**Interactive architecture intelligence for financial services.** Drag systems onto a layered canvas, wire typed connections (REST, MCP, events, zero-copy), and score paths against NIST, OWASP LLM Top 10, PCI DSS, FFIEC. Describe an architecture in English — Archway builds and explains it. 11 FS reference templates. One HTML file, zero dependencies.

> Lucidchart draws the boxes. Archway reasons about them.

---

## Quick start

No build, no install, no server.

```bash
git clone https://github.com/chrismccarthy-ship-it/under-the-archway.git
open under-the-archway/archway.html      # macOS
# or just double-click archway.html
```

Everything runs client-side in a single self-contained HTML file. The only network calls are the two **optional** integrations (Noun Project icons, brand-from-URL) — everything else works fully offline. Works on desktop and mobile (pinch-zoom, tap-to-add, slide-over panels).

---

## What it does

### 🎨 Design
- **Two layout modes** — **Layer Cake** (horizontal layers stacked top-to-bottom for technical dependencies and system-of-record relationships) and **Swimlane** (vertical lanes left-to-right for ownership, domains, and handoffs), with topology-aware **Auto Layout** (flow rank + barycenter sweeps to minimize edge crossings)
- **~90-component library** — Salesforce, Agentforce, Data 360, MuleSoft, Platform Events / CDC, Oracle HCM, Workday, ServiceNow, FIS, Temenos, core banking, payments, SWIFT, credit bureaus, LLMs, MCP, A2A, vector DBs, Kafka, AWS/Azure/GCP, and more
- **Typed connections** — sync, async, event-stream (animated), batch, human, and **zero-copy/virtual** (double line), each with protocol, auth (incl. Named Credential), encryption, latency, volume, and PII/financial data classification
- **React Flow-style handles**, per-node solid/gradient fills, custom edge labels, an editable + draggable legend, light/dark theme, and brand-from-URL (logo + palette extraction)

### 🔍 Analyze
- **Risk engine** — AI-direct-to-core access, PII into models, missing auth, unencrypted sensitive data, point-to-point sprawl, SPOF concentration, vector-store ingestion risk (OWASP LLM08), and un-modeled consent for PII landing in a CDP
- **Framework-cited findings** — every recommendation traces to published control frameworks: NIST SP 800-53 r5 / 800-207 / AI RMF / Privacy Framework, OWASP Top 10 for LLM Applications (2025), PCI DSS v4.0.1, FFIEC IT Handbook, GDPR, GLBA, EU DORA, ISO/IEC 27001 — **independently audited against primary sources (Oct 2026): zero fabricated citations**
- **Architecture health score** (labeled as the illustrative heuristic it is) with one-click highlight-on-canvas

### ⚖️ Compare
- **Path analysis** — pick any two systems; Archway finds every route, classifies each (Direct / Governed integration / Event-driven / Agent-governed MCP / Zero-copy), and scores them across nine dimensions
- **Optimize-for presets** — calibrated so each goal can surface its canonical pattern: *scale* and *reliable* favor event-driven, *fast/cost/simple* favor direct, *security/long-term* favor the governed layer. The balanced default reflects a governed-FS-enterprise stance — disclosed in-product.

### ✨ Optimize
One-click architecture critique with **✅ Accept / ❌ Reject** per suggestion: remove edge crossings (Sugiyama relayout), reroute point-to-point links behind the integration boundary (system-API pattern), insert PII masking before the model (Salesforce-aware: models the Einstein Trust Layer when the stack is on canvas), enforce mTLS on regulated core paths, add an audit event path, switch layout when the flow reads better the other way, and split over-dense diagrams.

### 🤖 Build with English
> *"build: connect Salesforce to FIS with an AI agent, but don't expose PII to the LLM"*

The reasoning engine parses systems and constraints, assembles the governed pattern (Customer → Salesforce → Agent → **LLM Gateway (masking)** → LLM, alongside MCP → Integration Layer → FIS), generates a walkthrough, runs the risk analysis, and explains why. The assistant also answers *why* questions grounded in the live canvas: outage options, MCP vs REST, 10× scale, maintainability, layout choice.

### ▶️ Play
Every template ships a **story mode** — an animated step-by-step walkthrough with a toggleable 💬 talk track, built for executive presentations and architecture reviews.

### ⎙ Export
**PDF** (print-ready: diagram, legend, findings, health score), **JSON** (lossless round-trip — nodes, positions, colors, connections, protocols, layout, story: *this repo can hold your architecture definitions as code*), plus in-session version snapshots.

---

## Reference templates

| Template | Inspired by |
|---|---|
| AI Banking Assistant | Agentforce + MCP + MuleSoft governed-access pattern |
| Real-Time Fraud Detection | AWS streaming Feature Store fraud architecture |
| AI Claims Assistant | Insurance FNOL with legacy SOAP wrapping |
| Open Banking API Platform | AWS FSI Lens open banking (FAPI: mTLS-bound tokens) |
| Modern Core Banking | AWS core-banking guidance (strangler + CDC) |
| Digital / QR Payments | AWS FS payments; ISO 20022 pacs.008 on RTP rails |
| Real-Time Credit Decisioning | AWS credit decisioning + SageMaker Feature Store |
| SWIFT Connectivity on Cloud | Microsoft SWIFT-on-Azure (SWIFTNet PKI signing, HSM) |
| System of Engagement + HCM | Salesforce/MuleSoft SoE-over-SoR pattern |
| Enterprise Data + Agents | Salesforce Data 360 zero-copy reference |
| Data Platform + Loan Agent | Data 360 + Einstein Trust Layer loan-agent example |

Template fidelity was audited against the vendors' published references (Oct 2026): 6 faithful, 5 simplified-but-fair, 0 misrepresentations.

---

## Tech notes

- Vanilla JavaScript, hand-rolled SVG rendering — no frameworks, no build step, no external JS
- Fonts (Space Grotesk, IBM Plex Mono) from Google Fonts with system fallback
- No localStorage/cookies; state is in-memory + JSON export
- Mobile-friendly: pinch-zoom, touch targets, drawer library, slide-over inspector
- Optional integrations (both degrade gracefully offline): Noun Project icons (OAuth 1.0a signed in-browser; keys stay in memory) and brand-from-URL (Clearbit/favicon + palette extraction)

## Disclaimer

Archway's analysis maps findings to published control frameworks for traceability, and its scoring presets encode a governed-enterprise editorial stance (disclosed in-product). It is a design and communication aid — not a compliance assessment, audit, or substitute for your security and architecture review processes.

## License

MIT — see [LICENSE](LICENSE).
