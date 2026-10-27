# Strategic Brand Naming

Distinctive names, backed by research and checked for real-world use.

An agent skill for naming and renaming brands, companies, products, and services, evaluating candidates, and improving weak naming rounds. It starts with one question at a time, distinguishes companies from products and tools, and calibrates naming taste before a long research pass. It then explores source-backed territories and checks the strongest names before presenting 5–10 distinct options. Its scope is commercial naming; naming people, files, or code identifiers falls outside that scope.

## Install and verify loading

For agents supported by the [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add schleksy/strategic-brand-naming
```

Choose the intended agent and installation scope in the installer. A fork, download, or clone outside an agent's discovery locations does not make the skill available automatically.

For manual local installation, copy the complete repository into the appropriate skill directory, keeping `SKILL.md`, `references/`, and `agents/` together:

| Host and scope | Skill directory | Explicit invocation |
|---|---|---|
| Claude Code, this project | `.claude/skills/strategic-brand-naming/` | `/strategic-brand-naming` |
| Claude Code, your local projects | `~/.claude/skills/strategic-brand-naming/` | `/strategic-brand-naming` |
| Codex, this project | `.agents/skills/strategic-brand-naming/` | `$strategic-brand-naming` |
| Other supported hosts | Follow that host's skill installation instructions. | Use its skill selector or explicit invocation. |

Claude's local folders do not automatically carry into every Cowork or cloud session; follow the host's account-level skill setup there. For a tool without native skills, explicitly provide the full `SKILL.md` and its referenced files as instructions. A link alone only helps if that tool can actually fetch those files.

After installation:

- Confirm the skill appears in the host's available-skills list or selector.
- Invoke it explicitly once and ask it to identify its starting stage. For an underspecified business, expect one focused discovery question at a time, followed by early direction calibration before lengthy research.
- Confirm the agent loaded the actual `SKILL.md` and references, rather than relying on a README summary. If loading is unclear, inspect the host's tool trace or skill invocation indicator; an agent's claim alone is not proof.
- Update installed copies when this repository changes. Check for stale or duplicate installations if behavior differs.

The skill uses the open [Agent Skills format](https://agentskills.io/specification). It needs no proprietary API key or executable script. A screened recommendation requires live source access, exact-domain lookup, and relevant conflict databases. When access prevents checks, it can still offer useful provisional names from a usable brief, with a prominent account of what was completed, what could not be verified, why, and the remaining checks.

## Discovery versus execution

- **Description:** the concise `SKILL.md` frontmatter explains what the skill does and when to load it. It includes naming, renaming, candidate evaluation, and weak-round pivots. Automatic selection is a host/model decision, not a guarantee. Explicit invocation is the most direct loading test.
- **Instructions:** the body of `SKILL.md` defines the workflow, stage requirements, supporting files, and completion audit after loading. Detailed procedures belong here rather than in the description.
- **README:** this page helps people install, invoke, and assess the skill. Reading it alone is not executing the method.
- **Domain access:** [the domain-checking guide](references/domain-checks.md) gives a public Vercel API request that needs no login or token, plus connector, CLI, registrar website, and registry/RDAP routes. No Vercel plugin is required.
- **Checkout guidance:** `AGENTS.md` and `CLAUDE.md` route compatible agents working inside this checkout to the full skill. They do not activate it globally or replace installation in another workspace.

OpenAI's invocation policy is explicitly enabled in `agents/openai.yaml`. The portable frontmatter keeps only the standard `name` and `description`; it does not disable model invocation in Claude Code.

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
| Understand | Establish company, product, tool, feature, or service scope. Ask one adaptive question per message; cover the full brief without repeating known answers. |
| Calibrate direction | Learn liked/disliked names and why. When needed, show 5–7 varied exploratory names before lengthy research or bulk domain checks. Explain styles progressively. |
| Investigate | Read relevant industry, dictionary, archive, scholarly, and cultural sources. Develop verified roots across distinct territories and follow promising references. |
| Generate and pivot | Vary roots, vocabulary, sounds, and constructions. Compare contrasting styles internally while respecting presentation exclusions. Pivot when a direction becomes weak. |
| Eliminate | Remove intrinsically weak names before spending time on detailed external screening. |
| Screen | Complete live company/product, exact-domain, preliminary trademark, language/culture, and required handle checks for each finalist. Reject hard failures and research replacements. |
| Recommend | Present the best 5–10 distinct qualified options, strongest first, with exact domain status and observed prices/terms. Offer ranked reserves grouped by style. |

For a new project, expect a conversation, not a questionnaire dump. Each answer informs the next question. Names you like and your reasons can establish direction; otherwise a small varied exploratory pitch helps test taste. Those early names are clearly unchecked, and feedback comes before the long research pass. Known project details and resolved direction do not need to be repeated.

## What you get

- A business and industry brief with an explicit choice of name types.
- Distinct research territories and the reason for each pivot.
- A ranked shortlist of 5–10 distinct options with pronunciation, origin or construction, strategic fit, and material risks.
- Exact domain status and observed price, currency, term, renewal when quoted, provider, and check date for every final option.
- An offer to see the next-best research candidates grouped by style, strongest first, with incomplete screening and rejection reasons preserved.
- Dated evidence for external checks, with unfinished work clearly marked.
- A project record that preserves decisions, rejected directions, and next steps.

The skill avoids mechanical vowel removal, invented etymologies, repetitive category compounds, and domain-first naming. A good story supports a strong name; it does not rescue a weak one.

## What a completed run must demonstrate

- A resolved brief for the actual naming object, plus taste calibration and hard constraints, using information already supplied.
- Actual findings from distinct research territories, with inspected source entries and roots that informed the names.
- Specific elimination reasons and meaningful pivots where needed, rather than a long list of spelling variants.
- Separate dated evidence for every recommended name's exact domain, commercial use, preliminary marks, language/culture, and required handles.
- A short completion audit stating what was done and what remains unresolved.

A word with an attractive story, a plan to browse later, or an unrelated list of source homepages does not demonstrate a completed method. The workflow should continue through accessible research and checks instead of returning an unsupported word as the finished result.

## Reliability and screening limits

These are portable agent instructions, not a runtime enforcement system. They improve clarity and make skipped work inspectable, but cannot force every model to obey, prove a source was read, or supply missing tools. Hard enforcement would require the consuming application to validate structured evidence and reject incomplete outputs; no such host-level enforcement is installed by this repository.

When a tool or source is genuinely inaccessible, the answer must say so before presenting a **provisional shortlist, screening incomplete**. Each name keeps unknown domain, conflict, origin, or handle fields visible. The agent must distinguish work completed, access blocked, and work not performed; it must not hide limitations or claim the full method ran. A usable brief does not require another permission round to receive those provisional ideas. Confirmed hard failures remain excluded.

If an agent ignores the workflow, distinguish a loading failure from an execution failure: verify invocation and file access first, then inspect the stage record and candidate-specific evidence. Report a minimal reproducible prompt, host/model, loaded revision, tool access, and observed output when filing an issue. Do not include private client research.

Domain availability, company conflicts, social handles, and trademarks are separate checks. An absent search result or missing website does not prove availability. Old findings must be rechecked.

Trademark screening is a preliminary knockout, not legal clearance. Serious launch decisions should receive appropriate professional trademark review. Required incomplete checks block a screened shortlist. If no candidate passes the hard requirements, the agent reports that outcome and continues with a meaningful pivot instead of filling the list with failures.

## Files

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Agent instructions and workflow. |
| [references/methodology.md](references/methodology.md) | Full research territories, naming types, phases, screening, and evaluation criteria. |
| [references/intake.md](references/intake.md) | Business discovery, name-type menu, and intake completion rules. |
| [references/research-sources.md](references/research-sources.md) | Concrete source routes, root discovery, and live screening procedure. |
| [references/domain-checks.md](references/domain-checks.md) | Public unauthenticated availability/pricing, fallback routes, and exact-domain evidence. |
| [references/records.md](references/records.md) | Stage status, evidence registers, and completion audit. |
| [AGENTS.md](AGENTS.md) / [CLAUDE.md](CLAUDE.md) | Small entry points for agents working in this checkout. |
| [agents/openai.yaml](agents/openai.yaml) | Display metadata for compatible OpenAI agents. |
| [evals/evals.json](evals/evals.json) | Example tasks and acceptance criteria for checking behavior. |
| [evals/triggers.json](evals/triggers.json) | Positive and negative routing cases for the description. |

## Contributing

Keep changes focused. Preserve the research, pivot, elimination, and freshness rules. When changing behavior, try the relevant prompts in `evals/evals.json` and include the observed results with your change. Never commit private briefs, credentials, or client research.

## Host documentation

- [Vercel: domain discovery without authentication](https://vercel.com/docs/domains/registrar-api)
- [Claude Code skills: descriptions, installation locations, and invocation](https://code.claude.com/docs/en/skills)
- [Claude Code project instructions and their enforcement limits](https://code.claude.com/docs/en/memory)
- [OpenAI: building skills and writing trigger descriptions](https://developers.openai.com/plugins/build/skills)
- [ChatGPT and Codex: skill discovery and explicit invocation](https://learn.chatgpt.com/docs/build-skills)

Host discovery rules can change. Follow the current host documentation when an installation route differs from this guide.
