# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** AI copilot for industrial/PLC programming — generates, debugs, and documents PLC code (ladder logic, structured text, function blocks) as a plugin inside Siemens TIA Portal, Rockwell Studio 5000, and CODESYS.
**Your Role:**

---

## Scores

### Contextual Moat — 2/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** Revised down from 4/5 after reviewing the live prototype. The current workflow is describe → generate → Copy Code — no IDE integration, no persistence, nothing that survives a switch. The "deep, sticky integration" the bet assumes is the plan, not something demonstrated yet. With native copilots already inside the IDEs engineers use daily, the switching-cost argument is weaker than assumed, not stronger.

**Named attacker (from partner challenge):** Siemens Industrial Copilot / Rockwell FactoryTalk Design Studio Copilot — both live inside the target IDEs already, so there's no copy-paste friction to switch back to them.

---

### Data Advantage — 2/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** Revised down from 3/5. The prototype's own upload feature is explicitly mocked ("nothing is sent"), so no proprietary plant/telemetry data is being captured today. The bigger threat isn't an open-source project catching up — it's that Siemens and Rockwell already have more real customer project/usage data flowing through their own copilots than this product can access from a cold start.

**Named attacker (from partner challenge):** Siemens Industrial Copilot / Rockwell FactoryTalk Copilot (built on real customer telemetry via private Azure OpenAI instances / a Rockwell-trained domain SLM), not OpenPLC.

---

### Platform Exposure — 1/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what? (Scored 1 = very exposed, 5 = well protected.)*

**Score rationale:** Revised down sharply from 4/5. This isn't a future risk to hedge against — it already happened. Siemens shipped "Industrial Copilot" / "Engineering Copilot" natively into TIA Portal in 2024 (in-IDE SCL generation, no copy-paste). Rockwell shipped FactoryTalk Design Studio Copilot, a domain-specific model for natural-language-to-ladder-logic generation, explanation, and debugging. A third-party competitor, PLC Copilot, already does the same thing for Studio 5000 via `.L5X` files. Two of three target platforms have native AI copilots live, plus a direct third-party competitor — "well protected" does not hold.

**Named attacker (from partner challenge):** Siemens Industrial Copilot (TIA Portal), Rockwell FactoryTalk Design Studio Copilot (Studio 5000), PLC Copilot (third-party, Studio 5000).

---

## Composite
<!-- Sum of the three axis scores out of 15, and the resulting band. -->

**Sum:** 5/15 *(revised from 11/15)*
**Band:** Weak — high exposure across multiple axes, not a single isolated crack.
**Crack (lowest axis):** Platform Exposure (tied with Data Advantage, but Platform Exposure is the sharper and more immediate risk — see Top Vulnerability)

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->

Platform Exposure, not Data Advantage: Siemens and Rockwell have already shipped native AI code-generation copilots into 2 of the 3 target platforms, and a direct third-party competitor (PLC Copilot) already exists — the core "generate PLC code" feature is being commoditized by the platform vendors themselves, not just threatened by them.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
