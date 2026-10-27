# Exact-domain checks and access fallbacks

Read this before checking candidate domains. Use the exact spelling and extension from the brief. A skill cannot supply network access, but an agent with a suitable connector, HTTP client, terminal, or browser has several practical lookup routes. Discovery here is read-only; do not buy, reserve, transfer, or configure a domain.

## Contents

- [Public Vercel discovery](#public-vercel-discovery)
- [Interpret the response](#interpret-the-response)
- [Other access routes](#other-access-routes)
- [When a check fails](#when-a-check-fails)
- [Evidence and user disclosure](#evidence-and-user-disclosure)

## Public Vercel discovery

Vercel documents domain availability and pricing discovery without an account, access token, project, or installation. Use an available read-only domain-search connector if sufficient. Otherwise call the public endpoint through an HTTP-capable tool or terminal:

```bash
curl --fail-with-body --silent --show-error --max-time 30 \
  --request POST \
  --url https://api.vercel.com/v1/registrar/domains/search \
  --header 'Content-Type: application/json' \
  --data '{"domains":["example.com","example.dev"]}'
```

Replace the example names with actual surviving candidates. The equivalent HTTP request is `POST https://api.vercel.com/v1/registrar/domains/search`, content type `application/json`, body `{"domains":["exact-name.com"]}`. Do not send an Authorization header or ask for a token for this public lookup. Generic REST/SDK examples may show authentication; consult the current public-discovery documentation rather than assuming login is necessary.

- Supply 1 to 200 exact domain names per request. Batch larger pools. The API checks these names; it does not invent suggestions.
- Prefer an existing suitable connector or HTTP tool; a Vercel plugin and CLI are optional. A tool limited to opening GET URLs cannot necessarily make this POST request.
- Parse the returned `results` entries by exact domain, retaining the provider's observed fields and the response time. Missing, malformed, or omitted entries remain unknown.
- Check current [Registrar API documentation](https://vercel.com/docs/domains/registrar-api) and the [endpoint reference](https://vercel.com/docs/rest-api/domains-registrar/get-domain-availability-and-pricing) if the service or schema changes. Never hardcode today's observed availability into this skill.

## Interpret the response

- `available: true` means Vercel reports it can be registered at the check time. Record any returned `years`, `price`, `renewalPrice`, and `premium`; quote USD and the actual term. Do not assume the initial quote covers renewal or invent missing prices.
- `available: false` means unavailable through this result or not confirmed. It does not by itself prove another party registered the name. Use registrar details or registry/RDAP evidence to distinguish registered, unsupported, reserved, and unknown when possible.
- Missing fields, timeouts, denied requests, and service errors are unknown. Do not convert them to false/taken or true/available. A missing price is not zero.
- Keep standard registration, premium registration, aftermarket resale, auction, brokerage, and an active existing brand separate. A parked page does not mean a domain can be bought at ordinary registration cost.
- Respect hard requirements: an alternate extension, modifier, or over-budget resale domain does not pass an exact `.com` requirement. Exclude confirmed hard failures; keep an unverified requirement visibly pending on a provisional candidate.

## Other access routes

- **Vercel CLI, when already available:** inspect `vercel domains --help` and the chosen subcommand's help. Current commands include `vercel domains check example.com example.dev --format=json` and `vercel domains price example.com --format=json`. For keyword suggestions use `vercel domains search example --tld com --available --format=json`. API search accepts exact names; CLI search accepts a keyword. If a CLI version lacks these commands or requests login for discovery, use the public HTTP endpoint instead of treating credentials as a prerequisite. See [CLI documentation](https://vercel.com/docs/cli/domains).
- **Public registrar website:** an agent with permitted browser access can inspect [Vercel Domains](https://vercel.com/domains) or another reputable registrar's exact-name search. Capture the actual availability, registration/resale classification, quoted term, price, renewal if shown, and date. Search-engine snippets about the registrar are not a current quote.
- **Registry/RDAP:** use [ICANN Lookup](https://lookup.icann.org/) or the relevant registry's documented RDAP service to corroborate registration status. Find the responsible service through [IANA's RDAP bootstrap](https://data.iana.org/rdap/dns.json), rather than guessing a registry endpoint. A domain record supports registered status. A valid no-object response does not establish registrar purchasability: a name can be reserved or unsupported. RDAP alone does not quote a price. See [ICANN's explanation](https://lookup.icann.org/en/faq).
- **Another supported connector or registrar:** use documented read-only availability/price operations already accessible to the agent. Do not invent anonymous endpoints or sign up for paid services as a workaround.

Cross-check contradictory results before making a positive claim. An exact-domain registrar quote is useful evidence of current purchasability; registry data answers the separate registration question. Recheck before a final selection or purchase if time has passed. No result reserves the domain, establishes trademark rights, or authorizes a purchase.

## When a check fails

1. Identify the actual failure: no HTTP-capable tool, outbound network restriction, invalid request, unsupported extension, stale CLI, authentication wall, rate limit, timeout, provider failure, or ambiguous response.
2. Correct a malformed request when possible. For a rate limit, respect the service's retry guidance; use a bounded retry or another permitted source rather than repeated requests. Do not bypass access controls.
3. Try a genuinely accessible alternative from the routes above. A missing Vercel account is not by itself a blocker for public discovery. A missing terminal is not a blocker if an available connector can perform the lookup.
4. If the available routes cannot complete it, record `domain: unknown / not verified`, the route actually attempted, its actual failure, and any successful partial findings. Continue independent naming work and other checks.
5. In the answer, prominently label any offered candidates **provisional, screening incomplete**. Say exactly which domains or checks remain unknown and why. Do not silently omit the check, blame an unspecified model limitation, or imply the method was completed.

Do not label an unattempted check as a technical limitation. Say `not performed` when it was not performed. If current access cannot execute a route at all, state that capability gap without pretending a request was sent.

## Evidence and user disclosure

For each exact domain record:

- Candidate spelling and full domain.
- Provider/endpoint or result URL, actual check time, and returned status.
- Actual term, currency, registration price, renewal price, and premium/resale classification where observed.
- Registry corroboration if available, contradictions, and remaining uncertainty.
- Pass/fail/unknown against the brief; the next unresolved action.

If a POST result has no shareable URL, retain the endpoint, exact request domains, dated response, and observed fields in the project record. Never manufacture a clickable result page. Keep research requests free of credentials and private client details beyond the candidate domain strings needed for the check.

Use the limitation disclosure format in [records.md](records.md). The user should see what was checked, what was blocked or not performed, and what that means for each provisional name before treating it as a usable choice.

## Sources

- [Vercel: unauthenticated search announcement](https://vercel.com/changelog/search-domains-without-authentication)
- [Vercel: public discovery and authenticated management](https://vercel.com/docs/domains/registrar-api)
- [Vercel CLI domain commands](https://vercel.com/docs/cli/domains)
- [ICANN RDAP lookup FAQ](https://lookup.icann.org/en/faq)

Check the current provider documentation when access or response behavior differs. This reference describes lookup procedures, not permanent availability findings.
