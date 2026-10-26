# Strategic Brand Naming

Find distinctive names through research, creative exploration, and disciplined elimination.

An agent skill for naming companies, products, services, and brands. It starts with a detailed business and industry intake, asks which types of names you want, explores language, history, behavior, culture, and metaphor, then checks the strongest candidates before recommending them.

## Install

For agents supported by the [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add schleksy/strategic-brand-naming
```

You can also copy this repository into your agent's skills directory as `strategic-brand-naming/`. Keep `SKILL.md` and the `references/` directory together. Follow your agent's installation instructions and verify that the skill loads.

The skill uses the open [Agent Skills format](https://agentskills.io/specification). It requires no executable scripts or API keys. Current availability and conflict screening require suitable live research tools; without them, it can complete discovery and explain unfinished checks. It presents unchecked names only when you explicitly request exploratory ideas.

## Use

Ask your agent to use **Strategic Brand Naming**, then describe what you are naming:

> Name a tool that helps freelance designers get overdue invoices paid. It should feel confident and human, work in the US and UK, and leave room for future products. Explore different research territories before recommending a shortlist.

You can also use it to improve an existing round:

> These names all sound like generic software. Diagnose why the direction is weak and pivot into genuinely different territories.

Or evaluate a candidate:

> Evaluate this name for strategic fit, pronunciation, spelling, meaning, and expansion. Recheck current domains and potential brand conflicts, and distinguish findings from unresolved questions.

## How it works

| Stage | Work |
|---|---|
| Understand | Ask about the business, industry, differentiation, business model, audience, markets, growth, and constraints. Reuse known answers and resolve missing core information. |
| Choose types | Ask which types to prioritize or avoid: descriptive, suggestive, metaphorical, arbitrary/abstract, coined, founder, geographic/cultural, or acronym. |
| Investigate | Read relevant industry, dictionary, archive, scholarly, and cultural sources. Develop verified roots across distinct territories and follow promising references. |
| Generate and pivot | Develop a broad pool. Change territories when a direction becomes generic, crowded, unreadable, or strategically weak. |
| Eliminate | Remove intrinsically weak names before spending time on detailed external screening. |
| Screen | Complete live company/product, exact-domain, preliminary trademark, language/culture, and required handle checks for each finalist. Reject hard failures and research replacements. |
| Recommend | Test the strongest names in speech and real use, evaluate their stories, and present a small shortlist with clear tradeoffs. |

For a new project, expect questions before names. You can choose one type, a ranked mix, or ask the agent to recommend a mix. Known project details do not need to be repeated.

## What you get

- A business and industry brief with an explicit choice of name types.
- Distinct research territories and the reason for each pivot.
- A curated shortlist with pronunciation, origin or construction, strategic fit, and material risks.
- Dated evidence for external checks, with unfinished work clearly marked.
- A project record that preserves decisions, rejected directions, and next steps.

The skill avoids mechanical vowel removal, invented etymologies, repetitive category compounds, and domain-first naming. A good story supports a strong name; it does not rescue a weak one.

## Screening limits

Domain availability, company conflicts, social handles, and trademarks are separate checks. An absent search result or missing website does not prove availability. Old findings must be rechecked.

Trademark screening is a preliminary knockout, not legal clearance. Serious launch decisions should receive appropriate professional trademark review. Required incomplete checks block a screened shortlist. If no candidate passes the hard requirements, the agent reports that outcome and continues with a meaningful pivot instead of filling the list with failures.

## Files

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Agent instructions and workflow. |
| [references/methodology.md](references/methodology.md) | Full research territories, naming types, phases, screening, and evaluation criteria. |
| [references/intake.md](references/intake.md) | Business discovery, name-type menu, and intake completion rules. |
| [references/research-sources.md](references/research-sources.md) | Concrete source routes, root discovery, and live screening procedure. |
| [references/records.md](references/records.md) | Reusable project record fields and shortlist format. |
| [agents/openai.yaml](agents/openai.yaml) | Display metadata for compatible OpenAI agents. |
| [evals/evals.json](evals/evals.json) | Example tasks and acceptance criteria for checking behavior. |

## Contributing

Keep changes focused. Preserve the research, pivot, elimination, and freshness rules. When changing behavior, try the relevant prompts in `evals/evals.json` and include the observed results with your change. Never commit private briefs, credentials, or client research.
