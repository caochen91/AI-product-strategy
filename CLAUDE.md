# CLAUDE.md — AI Product Strategy Sandbox

This file is the single place to pick the project back up. It holds the context, the decisions made so far, what's still open, and a changelog. **Read this first at the start of every session, and update it (especially the Changelog) whenever anything in the repo changes.**

---

## ⚠️ Validation reminders — Claude: raise these at the start of the next session

At the start of the next session, before doing anything else, remind the user that the items below are **AI-generated drafts the user has not validated**, and ask whether they want to validate them now or keep going. Remove an item only after the user confirms they have reviewed it.

- [ ] **`02-the-moat/data-flywheel.md`**: drafted by Claude on 2026-10-16. Loop scores (4/20), encroachment attackers, timelines and % at risk, and the 90-day attack plan are Claude's assumptions. No partner exercise was run.
- [ ] **`02-the-moat/kill-switch.md`**: drafted by Claude on 2026-10-16. The LLM provider the Lovable prototype uses is **unverified**, and the whole audit depends on it.
- [ ] **`README.md` M2 section**: summarizes the two drafts above, so it should be re-checked once they're validated.

---

## 1. What this project is

A 6-module AI product strategy course workbook, kept as a git repo. Each module adds one component; by Module 6 the repo *is* the strategy (board-ready, version-controlled).

| Module | Folder | Theme | Status |
|--------|--------|-------|--------|
| M1 | `01-the-bet/` | What we're building, for whom, why now | **Mostly done** (see open items) |
| M2 | `02-the-moat/` | Data flywheel + encroachment + vendor kill-switch | **Draft by Claude — unvalidated** |
| M3 | `03-the-margin/` | Cost curve, cascading, pricing, stress tests | Template only |
| M4 | `04-the-contract/` | Golden dataset, confidence UX, reliability contract, HITL | Template only |
| M5 | `05-the-guardrails/` | Feedback loops, governance, agent topology, shadow AI | Template only |
| M6 | `06-the-pitch/` | Three-horizon roadmap + board pitch | Template only |

Other files:
- `README.md` — the "strategy at a glance" summary. Keep it in sync with module files.
- `working/idea.md` — brainstorm of 7 candidate product ideas (2026 market trends) used to pick the bet.

---

## 2. The product (the bet)

**Industrial Logic Agent** — an AI copilot for industrial/PLC programming. Generates, debugs, and documents PLC code (ladder logic, structured text, function blocks) for Siemens TIA Portal, Rockwell Studio 5000, and CODESYS. Initial market: discrete manufacturing and packaging lines.

- **Archetype:** Copilot
- **Prototype:** https://industrial-ai-wizard.lovable.app (built with Lovable). Single-page app: describe task → pick platform + language → get code + explanation + categorized debug suggestions (safety / edge cases / improvements) + commissioning-ready functional description.
- **Success target (from idea.md):** 50%+ cut in time-to-working-program; adoption at 3+ design-partner plants in year one.
- **Note:** This is a *hypothetical venture*, not a real product at a company. The diagnostic template asks for a real product — this hasn't been flagged in `diagnostic.md` yet.

---

## 3. Key discussions & decisions

### Why PLC copilot was chosen (2026-09-12)
Picked idea #7 from `working/idea.md` out of 7 candidates (healthcare docs, mid-market banking compliance, agent governance layer, SMB ops coworker, PM prototyping tool, shadow-AI monitor, PLC copilot). Rationale: factory-floor programming is still manual, relies on a shrinking pool of tribal-knowledge engineers, and was largely untouched by the AI coding-assistant wave.

### Vulnerability diagnostic — first pass vs. revised (2026-09-13)
The first scoring was optimistic; after reviewing the live prototype and a partner challenge, all three axes were revised down.

| Axis | First pass | Revised | Why |
|------|-----------|---------|-----|
| Contextual Moat | 4/5 | **2/5** | Prototype workflow is describe → generate → copy code. No IDE integration, no persistence. "Sticky integration" is a plan, not a fact. |
| Data Advantage | 3/5 | **2/5** | Prototype upload is mocked ("nothing is sent") — no proprietary data captured. Siemens/Rockwell already have far more customer data flowing through their own copilots. |
| Platform Exposure | 4/5 | **1/5** | Already happened, not a future risk: Siemens Industrial/Engineering Copilot in TIA Portal (2024), Rockwell FactoryTalk Design Studio Copilot, and third-party PLC Copilot (Studio 5000 via `.L5X`). |
| **Composite** | 11/15 | **5/15 — Weak** | |

**Top vulnerability:** Platform Exposure — the core "generate PLC code" feature is being commoditized by the platform vendors themselves.

**Named attackers:** Siemens Industrial Copilot, Rockwell FactoryTalk Design Studio Copilot, PLC Copilot (third-party).

### Draft kill criteria (in `01-the-bet/prototype.md`, to finalize after user testing)
1. Generated logic needs as much rework as writing from scratch.
2. Engineers won't trust AI logic near safety-critical circuits → capped at "draft only".
3. Free/open alternatives (OpenPLC + generic LLM) replicate most of the value.
4. No real plugin/API path on the target platforms → copy-paste-only workflow gets abandoned.

### Implication to carry into M2+
With a 5/15 score, the strategy can't rest on "generate code". M2 (moat) needs to answer what's defensible *despite* native vendor copilots — e.g. cross-vendor coverage (CODESYS + multi-vendor plants), safety review/commissioning documentation, or correction-loop data the vendors don't capture.

### M2 draft — the moat (2026-10-16, Claude-generated, unvalidated)
The user asked Claude to draft M2 so work could move on to M3. Key draft positions:
- **Flywheel 4/20.** All four loops score 1/5 because the prototype is stateless and ends at "Copy Code". **Correction** is the loop to fix first: import the final code from the IDE, diff it against the generated output, and log accept/reject on debug suggestions.
- **Encroachment:** platform (Siemens/Rockwell native copilots, now, ~60–70% at risk); vertical (PLC Copilot, now, ~20–30%); adjacent (general coding assistants writing Structured Text, CODESYS native AI, 6–12 months, ~15–25%).
- **Defense / positioning:** the vendor-neutral layer for multi-vendor plants and system integrators. Lead with review/verification, safety checks, commissioning docs and cross-vendor translation, not raw generation.
- **Kill switch: Portability = Partial.** There's a single unverified LLM provider (via Lovable), no abstraction, no routing and no eval. The 48-hour actions are: confirm the provider, put the model behind an adapter, mark low-risk tasks for a cheaper model, and build a 10–20 task PLC smoke-test eval.
- **Carry into M3:** model routing (cheap model for explanation/docs, frontier model for code/safety) and the "provider doubles price" scenario feed the cascading strategy and the stress tests.

---

## 4. Open items / next steps

**M1 leftovers**
- [ ] `diagnostic.md`: fill in **Your Role** and **Confidence Level** (H/M/L).
- [ ] `diagnostic.md`: flag the product as a hypothetical venture.
- [ ] `README.md` M1 section: replace `Prototype: [link]` with the Lovable URL, set Confidence, fill Kill Criteria summary, tick the M1 status box.
- [ ] Finalize kill criteria after real user testing.

**M2–M6**
- [x] M2: first draft written by Claude (2026-10-16). **Still needs validation by the user** (see Validation reminders at the top). Verify which LLM provider the Lovable prototype actually uses.
- [ ] M3: cost model, cascade strategy, pricing, stress tests. **← next up**
- [ ] M4: golden dataset (with adversarial rows), confidence UX, reliability contract, HITL.
- [ ] M5: feedback loops, governance (note: safety-critical industrial context → regulatory exposure matters), shadow AI audit.
- [ ] M6: three-horizon roadmap, board pitch, M1-vs-now comparison.

---

## 5. Working conventions

- Fill module templates in place; don't delete template prompts' structure.
- When a score or decision changes, keep the old value visible (e.g. *"revised from 11/15"*) so the reasoning trail survives.
- After any change to a module, update `README.md` at-a-glance and this file's Changelog.
- Commit messages describe the strategy change, e.g. "Revise vulnerability scores after prototype review".

---

## 6. Changelog

Newest first. Add an entry for every session that changes anything.

### 2026-10-16
- **M2 drafted by Claude, NOT validated by the user.** Filled in `02-the-moat/data-flywheel.md` (flywheel 4/20, weakest loop Correction, three encroachment threats, hypothetical Siemens 90-day attack plan) and `02-the-moat/kill-switch.md` (Portability: Partial; provider unverified). Each file has a draft banner at the top. Updated the `README.md` M2 section with a draft flag. Purpose: unblock M3 (the margin). Validation reminder added at the top of this file.
- Audited M1/M2 completeness: `prototype.md` is complete; `diagnostic.md` still lacks Your Role and Confidence Level; both M2 files were untouched templates before this draft.
- Created `CLAUDE.md` as the project sandbox: context, decisions, open items, conventions, and this changelog (backfilled from git history).

### 2026-09-13
- **Revised vulnerability scores after prototype review** (`c7ed713`): Moat 4→2, Data 3→2, Platform 4→1; composite 11/15 → 5/15 (Weak). Top vulnerability changed to Platform Exposure. Updated `README.md` to match.
- **Filled in Module 1** (`a8dd187`): first-pass vulnerability scorecard (11/15) in `diagnostic.md`; `prototype.md` filled with product description, Lovable prototype link, Copilot archetype, one-sentence bet, and draft kill criteria. README M1 section updated.

### 2026-09-12
- **Added `working/idea.md`** (`0e70cec`): 7 candidate product ideas with archetype, why-now, and vulnerability tension, plus sources and a note on the "real product" requirement.
- **Initialisation** (`b2b0b64`): minor edit to `diagnostic.md`.
- **Initial commit** (`a18b11b`): course template — README plus empty templates for all six modules.
