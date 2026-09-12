# Candidate Product Ideas (for The Bet)

Brainstormed against 2026 AI market trends and adoption gaps, to help pick a product for the Module 1 diagnostic. None of these are real products yet — see note at bottom.

---

## 1. Healthcare documentation / care-planning copilot
- **Archetype:** Copilot
- **Why now:** Healthcare is one of the most underserved sectors for AI agents in production (18% vs. 47% in banking/insurance), and documentation burden is a top driver of clinician burnout.
- **Vulnerability tension:** Low data advantage (EHR data is siloed/regulated), high platform exposure (Epic/Oracle Health could ship this natively).

## 2. Vertical AI for mid-market banking/insurance compliance
- **Archetype:** Oracle
- **Why now:** Banking/insurance leads production adoption (47%) and hyper-personalization is driving 10–25% revenue lift — but that's concentrated in large institutions, leaving mid-market underserved.
- **Vulnerability tension:** Strong contextual moat (workflow depth, compliance data) but real platform risk from core banking vendors.

## 3. AI agent governance/observability layer
*("who approved this agent, what did it do")*
- **Archetype:** Orchestrator
- **Why now:** 55% of execs describe internal AI use as a "chaotic free-for-all," 36% have no formal supervision plan, and 88% of agents never reach production — governance is the actual bottleneck, not model capability.
- **Vulnerability tension:** Genuine data advantage (audit trails compound), but crowded incumbent risk (every cloud vendor wants this natively).

## 4. Small-team "digital coworker" for a specific ops function
*(e.g., SMB finance/ops agent)*
- **Archetype:** Automator
- **Why now:** Agentic AI letting small teams "punch above their weight" is called out as the defining 2026 shift; SMBs are underserved relative to enterprise tooling.
- **Vulnerability tension:** Weak moat (workflow is generic, low switching cost) — good axis to stress-test in the diagnostic.

## 5. Rapid-prototyping/validation tool for non-technical PMs
*(spec-to-clickable-prototype)*
- **Archetype:** Creator
- **Why now:** Multiple 2026 sources call speed-to-learn "your moat" — tools that compress idea-to-testable-prototype time ride that trend directly.
- **Vulnerability tension:** Very high platform exposure — exactly the kind of feature a v0/Lovable/Cursor could absorb.

## 6. AI security posture monitor for shadow-AI tool sprawl
- **Archetype:** Oracle
- **Why now:** 67% of execs believe they've already had a data leak from unapproved AI tools; security is explicitly named as shifting from checkbox to differentiator in 2026.
- **Vulnerability tension:** Strong, defensible data advantage (proprietary detection signal) if real usage telemetry is available — worth scoring high on that axis.

## 7. AI copilot for industrial/PLC programming
- **Archetype:** Copilot
- **Why now:** Factory-floor programming (ladder logic, structured text, function blocks) is still manual and dependent on a shrinking pool of tribal-knowledge controls engineers — largely untouched by the AI coding-assistant wave that's transformed general software dev.
- **Where it deploys:** As a plugin inside the tools engineers already use — Siemens TIA Portal, Rockwell Studio 5000, CODESYS — starting with discrete manufacturing and packaging lines.
- **Success looks like:** 50%+ cut in time-to-working-program, adoption by controls engineers at 3+ design-partner plants within the first year.
- **Vulnerability tension:** High contextual moat potential (deep, sticky integration into engineers' daily tools) but real platform exposure if Siemens/Rockwell/CODESYS ship native AI assist themselves; data advantage depends on access to proprietary plant code/telemetry, which is scarce and guarded.

---

## Note on "real product" requirement
`diagnostic.md` asks for a real product at your company, not a hypothetical. None of the above are real yet. Options:
- Pick one and run the exercise as a hypothetical venture (flag it as such in `diagnostic.md`).
- Substitute a real product you actually work on, and re-ground the diagnostic in that instead.

## Sources
- [Top AI Trends in 2026: How Ready Are You? | FPT Software](https://fptsoftware.com/resource-center/blogs/top-ai-trends-in-2026)
- [Product Management Trends: 11 Shifts Shaping 2026](https://productschool.com/blog/product-fundamentals/product-management-trends)
- [What's next in AI: 7 trends to watch in 2026 | Microsoft](https://news.microsoft.com/source/features/ai/whats-next-in-ai-7-trends-to-watch-in-2026/)
- [Enterprise AI adoption in 2026: Why 79% face challenges despite high investment | WRITER](https://writer.com/blog/enterprise-ai-adoption-2026/)
- [AI Agent Adoption 2026: 120+ Enterprise Data Points](https://www.digitalapplied.com/blog/ai-agent-adoption-2026-enterprise-data-points)
- [Enterprise AI agents in 2026: adoption surges while projects get cut | PATech Labs](https://www.patechlabs.com/news/enterprise-ai-agents-2026-adoption-vs-cancellation)
