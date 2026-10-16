# Kill Switch Audit

> ⚠️ **DRAFT — AI-generated, NOT validated.** Filled in by Claude on 2026-10-16 so work could move on to M3. Claude has **not** confirmed which LLM provider the Lovable prototype actually calls. The "Current State" column describes the likely setup of a Lovable-built prototype and must be checked. Review and validate before relying on any of it. See `CLAUDE.md` → Validation reminders.

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | A single LLM provider, assumed to be reached through Lovable's built-in AI integration (provider and model **unverified**). There is no fallback provider. | H | Confirm the exact provider and model the prototype calls. Get API access to a second frontier provider and run the same prompts against it. |
| **Abstraction** | None. Prompts and the call to the model are embedded in the app, and the code / explanation / debug / docs outputs are one prompt chain tied to one model. | H | Move prompts into versioned templates behind a thin "generate / explain / debug / document" interface, so the model sits behind one swappable adapter. |
| **Routing** | One model handles everything. The explanation and documentation panels likely use the same (expensive) model as code generation. | M | Mark which tasks are low-risk (explanation, docs formatting) and could go to a cheaper model. This feeds the cascading strategy in M3. |
| **Eval** | No eval set. There's no way to tell whether a model swap makes PLC output better or worse, and that matters most for safety-relevant logic. | H | Write 10–20 reference PLC tasks with expected behaviour, including safety interlocks, as a smoke test to run before any model change. This seeds the golden dataset in M4. |

## Portability Score
<!-- Ready / Partial / Locked -->

**Partial.** Little has been built, so a switch is cheap in absolute effort. But there's no abstraction and no eval, so a swap can't be done *safely*: there's no way to confirm the new model's PLC code is still correct.

## If the LLM provider doubles pricing tomorrow:
<!-- What's your 48-hour response? -->

Short-term impact is low because the product is pre-revenue with no paying users. The 48-hour response: (1) route explanation and documentation to a cheaper model and keep the frontier model only for code generation and safety debug; (2) cache repeated or identical requests; (3) add per-user usage caps on the free prototype. Over the longer term, this scenario is why the abstraction layer and eval set above are needed before any customer pilot. The detailed numbers belong in M3's stress tests.

## If the LLM provider ships a competing product:
<!-- What's defensible that they can't replicate? -->

The bigger danger is the IDE vendors, not the model vendor: Siemens' Industrial Copilot is built with Microsoft on Azure OpenAI, so a competitor may already run on the same model family. Raw generation isn't defensible. What is:
- **Vendor neutrality:** one tool across Siemens, Rockwell and CODESYS. Neither an IDE vendor nor a model vendor will build for their rivals' platforms.
- **Correction data:** accepted edits and safety fixes from real lines, if the Correction loop gets switched on (see `data-flywheel.md`).
- **Domain workflow:** safety review, commissioning documentation and cross-vendor translation, tuned to how integrators actually hand projects over.
