## Ole Coenraad

Backend engineer in Amsterdam. Three years building and running production software for international live productions — theatre, opera, museums, television, large-scale events — delivered on site in India, Germany and California. Now freelance.

**Available for contract work: 24–32 hours per week, CET with US overlap.**

---

### What I work on

**Backend systems** in Python and TypeScript. Fastify, Prisma, PostgreSQL, Next.js, Supabase. Before that, three years of C#/.NET (ASP.NET MVC) on Azure with Microsoft SQL Server.

**AI agent tooling** — memory and retrieval layers, MCP servers, guardrails, local models. Most of my recent work is here.

**Infrastructure I actually run**, not just configure: a two-node Ubuntu fleet with systemd timers, Tailscale, Ollama for local inference, a self-hosted GitHub Actions runner, Cloudflare Tunnel, and Uptime Kuma + Beszel monitoring. gitleaks and semgrep in pre-commit across every repository.

---

### Most of my code is private — here is what is in it

Roughly **88,000 lines of Python** and **15,000 lines of TypeScript** across my own projects. A few things from it that say more than the line count:

**A test suite that went from 38 to 94 green.** An upstream data source shut down permanently and took a whole pipeline with it. I migrated to a new adapter while keeping the existing on-disk format and every downstream caller untouched, so nothing else had to change. That project runs a **Python 3.11–3.14 CI matrix** — the workflow carries a written justification for a `pandas`/`matplotlib` wheel break across versions, because a matrix without a reason for its entries is just noise.

**Seven vulnerabilities found and fixed across seven of my own repositories** — command injection, zip-slip, DOM-XSS, CSV formula injection, and an unauthenticated `0.0.0.0` dashboard that exposed a paid API key. Every fix was proven with a regression test that **fails against the vulnerable code** before it passes against the fix. A fix you cannot demonstrate failing is not a fix you have verified.

**Three things I got wrong, and what they taught me** — the part I would actually want to talk about:

- An integration was tested end to end against a stub built from the real upstream signatures. Everything passed. On the first live run, four identical calls returned −23.2%, −24.8%, −14.5% and −17.7%: the real implementation *sampled*. A scoreboard would have reported the accuracy of a dice roll as model performance for months. **A stub proves the call, not the behaviour.**
- A numerical function had a finite-difference test that compared the code against its own derivative. It was a tautology that had passed for months. I replaced it with three independent routes, including reference values computed to 40 digits outside the code under test. **A test that compares your code with itself proves nothing.**
- A generated build queue read "0 items remaining", which looks like success. One item had been marked complete while only a preliminary study existed. **An auto-generated list that reads zero is the most dangerous result there is** — check its emptiness, not just that it regenerated.

I write in Dutch and English, and I care more about whether a result is actually true than about whether it looks green.

---

### Contact

olecoenraad@gmail.com · Amsterdam, Netherlands · Dutch KvK registered, VAT invoicing
