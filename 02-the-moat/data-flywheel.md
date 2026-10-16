# Data Flywheel Map

> ⚠️ **DRAFT — AI-generated, NOT validated.** Filled in by Claude on 2026-10-16 from the prototype (`01-the-bet/prototype.md`) and the diagnostic (`01-the-bet/diagnostic.md`) so work could move on to M3. Scores, attackers, timelines and percentages are reasoned assumptions, not the owner's own input, and no partner exercise was run. Review and validate before relying on any of it. See `CLAUDE.md` → Validation reminders.

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 1/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 1/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 1/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 1/5 |

### Correction Loop - 1/5
**What you capture today:** Nothing. The prototype flow ends at "Copy Code". Engineers fix the logic inside TIA Portal / Studio 5000 / CODESYS, out of the product's sight. The debug panel suggests fixes but doesn't record which ones were accepted.
**How it compounds:** It would be the most valuable loop. Engineer edits to generated logic are labelled examples of "what correct PLC code looks like on a real line", and generic LLMs and most competitors don't have that. To capture it: let engineers paste or import the final code (or `.L5X` / TIA exports), diff it against the generated version, and log accept/reject on each debug suggestion. Use the diffs first as few-shot examples, then as an eval and fine-tuning set.

### Preference Loop - 1/5
**What you capture today:** Nothing. The prototype is stateless, with no accounts and no saved projects. Platform and language are picked again on every request.
**How it compounds:** Every plant and integrator has its own conventions: tag naming, rung structure, alarm handling, comment style, safety interlock patterns. Saving these as a per-team "house style" profile would make each new output need fewer edits, and that gives the product a switching cost that is real rather than assumed.

### Domain Context Loop - 1/5
**What you capture today:** Nothing. Each request is handled on its own, and the three platforms and three languages don't share learnings.
**How it compounds:** A pattern learned on one line type, such as conveyor sequencing on a packaging line, could improve outputs on other line types and across vendors. For example, a validated Studio 5000 interlock pattern could be translated into TIA Portal SCL. This cross-vendor transfer is something a single-vendor copilot (Siemens or Rockwell) structurally can't do.

### Network Loop - 1/5
**What you capture today:** Nothing. Users are isolated.
**How it compounds:** It's weak by nature: plant code is guarded IP, and customers won't share it with each other. The realistic version is a curated library of anonymized function blocks and patterns, built from opted-in corrections, that gets better with each design-partner plant. It should be treated as a later-stage loop, not a launch moat.

**Total Flywheel Score: 4/20**
**Weakest Loop:** All four loops tie at 1. **Correction** is the one to fix first. It's the cheapest to switch on, it produces the most defensible signal, and it feeds the Preference and Domain Context loops.
**Fix for weakest loop:** Close the loop back from the IDE. (1) Add an "import final code" step (paste, or `.L5X` / TIA export) and store the diff against the generated output. (2) Log accept/reject on every debug suggestion. (3) Turn accepted corrections into a golden dataset (this feeds into M4) and team style profiles (Preference loop).

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** Siemens Industrial Copilot / Engineering Copilot (TIA Portal) and Rockwell FactoryTalk Design Studio Copilot (Studio 5000).
**Vector:** Native in-IDE generation, explanation and debugging with full project context, no copy-paste, bundled with licenses customers already pay for.
**Time-to-threat:** Now. Both are already shipped.
**% of value at risk:** ~60–70%. All single-vendor Siemens or Rockwell shops are exposed; what's left is CODESYS and multi-vendor environments.

### 2. Vertical Competitor
**Attacker:** PLC Copilot (third-party, Studio 5000 via `.L5X`) and similar industrial-AI startups.
**Vector:** The same generate/debug/document pitch, already integrated through file import/export, with a head start on design partners.
**Time-to-threat:** Now.
**% of value at risk:** ~20–30%. It competes directly for the same early adopters and system integrators.

### 3. Adjacent Expansion
**Attacker:** General coding assistants (GitHub Copilot, Cursor, ChatGPT/Claude) and CODESYS Group adding native AI.
**Vector:** Structured Text is plain text, so general assistants already write passable IEC 61131-3 ST. Adding IEC 61131-3 awareness is a small step for them. CODESYS could ship its own assistant the way Siemens and Rockwell did.
**Time-to-threat:** 6–12 months.
**% of value at risk:** ~15–25%, mostly the Structured Text use case. Ladder logic and vendor-specific function blocks are less exposed.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*
*(No partner exercise was run. This is a hypothetical attack drafted by Claude.)*

**Attacker:** Siemens (Industrial Copilot in TIA Portal, built with Microsoft / Azure OpenAI).
**Attack vector (target the weakest loop):** The Correction loop. Siemens sees every edit inside TIA Portal and this product sees none, so their model improves from real corrections while this product's doesn't.
**Weeks 1-4 - what they ship:** Bundle Copilot generation, explanation and auto-documentation (functional descriptions, commissioning docs) into the next TIA Portal update at no extra cost for existing license holders.
**Weeks 5-8 - how they poach users:** Push it through distributors and system-integrator partner programmes, and position it as "the safe, vendor-certified choice for safety-relevant code".
**Weeks 9-12 - why users don't come back:** It lives in the IDE with project context and history, it's certified by the vendor that also supplies the hardware, and it learns from their own edits. Going back to a copy-paste web tool is pure friction.
**Your defense:** Don't compete head-on with the "generate code inside TIA Portal" feature. Position as the **vendor-neutral layer** for multi-vendor plants and system integrators who work across Siemens, Rockwell and CODESYS. Lead with **review and verification** (safety checks, commissioning documentation, cross-vendor translation) rather than raw generation, and switch on the Correction loop so the product learns from the work done in its scope.
