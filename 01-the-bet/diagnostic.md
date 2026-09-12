# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** AI copilot for industrial/PLC programming — generates, debugs, and documents PLC code (ladder logic, structured text, function blocks) as a plugin inside Siemens TIA Portal, Rockwell Studio 5000, and CODESYS.
**Your Role:**

---

## Scores

### Contextual Moat — 4/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:**

**Named attacker (from partner challenge):**

---

### Data Advantage — 3/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:**

**Named attacker (from partner challenge):** OpenPLC

---

### Platform Exposure — 4/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what? (Scored 1 = very exposed, 5 = well protected.)*

**Score rationale:**

**Named attacker (from partner challenge):**

---

## Composite
<!-- Sum of the three axis scores out of 15, and the resulting band. -->

**Sum:** 11/15
**Band:** Moderate — some protection, but cracks exist.
**Crack (lowest axis):** Data Advantage

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->

Data Advantage is the crack — without proprietary plant/telemetry data, an open alternative like OpenPLC could close the gap.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
