# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->

Industrial Logic Agent — a working single-page web app where an engineer describes a PLC task in plain language, picks a target platform (TIA Portal / Studio 5000 / CODESYS) and language type (ladder logic / structured text / function blocks), and gets back generated code plus three reviewed panels: a plain-language explanation, categorized debug suggestions (safety / edge cases / improvements), and a commissioning-ready functional description.

## Tool Used
<!-- v0 / Cursor / Lovable / other -->

Lovable

## Prototype Link
<!-- Paste the shareable URL -->

https://industrial-ai-wizard.lovable.app

## AI Value Archetype
<!-- Automator / Copilot / Oracle / Creator / Orchestrator -->

Copilot

## The Bet in One Sentence
<!-- What you're building, for whom, why now -->

An AI copilot that generates, debugs, and documents PLC code for industrial controls engineers, deployed inside the tools they already use (Siemens TIA Portal, Rockwell Studio 5000, CODESYS), starting with discrete manufacturing and packaging lines.

## Kill Criteria
<!-- When would you stop? What evidence would kill this bet? -->

Draft — revisit and finalize after real user testing:
- Real controls engineers find generated logic needs as much rework as writing from scratch (no net time savings).
- Engineers won't trust or deploy AI-generated logic near safety-critical circuits regardless of debug/doc quality, capping the product to a narrow "draft only" use case.
- Free/open alternatives (e.g., OpenPLC + generic LLM prompting) replicate most of the value, so no one will pay.
- None of the three target platforms offer a real plugin/API path, forcing a copy-paste-only workflow engineers abandon after the novelty wears off.
