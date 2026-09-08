---
layout: lesson
title: 'Unit 1: Kickoff — From FE I React to Production Architecture'
title_alt: 'Unidad 1: Lanzamiento — De React FE I a Arquitectura de Producción'
slug: feii-unit-1-kickoff
date: 2026-08-08
author: 'Rubén Vega Balbás, PhD'
lang: en
permalink: /lessons/en/feii/unit-1-kickoff/
description: 'FE II orientation: production front-end as a system of interfaces; four-pillar vector; meta-frameworks vs micro-frontends; AI disclosure discipline.'
tags: [feii, orientation, architecture, interface-layer, production, systems-thinking]
status: complete
---

<aside class="lesson-framing" aria-label="Master idea and field lens">
<p><strong>Master idea:</strong> Production front-end is a <strong>system of interfaces</strong> — orchestration across browser, edge/service, backend, and user — not a single SPA bundle.</p>
<p><strong>Field lens:</strong> <strong>Anchor:</strong> decisions per layer (client · API · deploy · user). <strong>Frontier:</strong> edge, device/<abbr title="Progressive Web App">PWA</abbr>, real-time, multi-surface. <strong>Status:</strong> orientation with no technical CONTENIDOS; prepares Units 2–12.</p>
</aside>

> **Studio test:** Draw a product’s surfaces, contracts, and failure boundaries (CDN/edge, cache, auth, offline) — not only UI components.

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
UbD Stage-1: transfer goal = reframe production FE as distributed interface system + distinguish meta-framework vs micro-frontend.
UbD Stage-2: evidence = three B3 answers + verify checklist (one architecture decision per pillar).
Bloom: B1 Understand/Analyze (conceptual systems knowledge); B3 Apply/Evaluate (architecture decisions; AI speed vs understanding). B2 N/A (0 h lab).
5E: not applicable — orientation/compliance framing unit, not inquiry lab.
CLT: high intrinsic load (many new terms); reduce extraneous load by one systems diagram + worked middleware excerpt before exercises (Chandler and Sweller 1996).
Critical moment (lens Epistemological): AI acceleration ≠ durable understanding (Liu, Fan, and Pan 2026) → B1 framing + B3 item 2 no-AI.
Domain grounding: islands vs micro-frontends (Vepsäläinen 2025). Transfer boundary: architecture paper ≠ measured learning outcome for this kickoff sequence.
-->
{% endif %}

<!-- prettier-ignore-start -->

## 📋 Table of Contents
{: .no_toc }
- TOC
{:toc}

<!-- prettier-ignore-end -->

{% include lesson-semantic-graphic.html %}

---

## Before you start

| Requirement | Required? |
| --- | --- |
| FE I semester 2 (React app deployed) | Yes |
| Track index + `exercises.md` | Yes |
| Team repo for Entrega 1 | Not yet (Unit 2) |

**Time:** 2 h magistral · **0 h lab** · 1 h individual exercises (B3). Full calendar: [FE II track index]({{ '/tracks/feii/' | relative_url }}).

---

## Session in 6 steps

| # | Action | Where |
| --- | --- | --- |
| 1 | System of interfaces + four-pillar vector | §1 |
| 2 | Meta-framework vs micro-frontend (+ Astro) | §2 |
| 3 | Middleware excerpt (Unit 2 preview) | §3 |
| 4 | AI disclosure: speed ≠ understanding | §4 |
| 5 | Three individual exercises | B3 |
| 6 | Submit evidence | Submit |

---

## Verify / Failures / Submit

**Verify**

- [ ] One paragraph: single interface vs system of interfaces
- [ ] One architecture decision per pillar of the vector
- [ ] Meta-framework ≠ micro-frontend (and why they often combine)
- [ ] Exercise 2 distinguishes speed from understanding (no AI)

**Common failures**

| Mistake | Avoid by |
| --- | --- |
| Treating U1 as a free week | Submit the 3 exercises — Unit 2 assumes this frame |
| Expecting a team lab | 0 h lab is official; first lab is Unit 2 |
| Using AI on exercise 2 | Marked solvable without AI |

**Submit:** three answers via the professor channel. No team PR.

> _"Before the first line of code, prepare the forge. Before the first query, load the memory. Documentation is not an afterthought — it is the first act of architecture."_
> — Tao of Development, `wis-014`
{: .tao-development-quote }

> **AI Assistance Disclosure:** docs-first methodology; plans, prompts, and reports are documented.  
> **Code:** §3 middleware is an **Excerpt** (does not run in U1). Policy: [FE II conventions]({{ '/lessons/en/feii/' | relative_url }}#-conventions-used-across-these-lessons).

---

## Objectives

By the end of this orientation you will be able to:

1. Bridge FE I (React SPA) to FE II (production architecture).
2. Apply the **four-pillar vector** (browser · service · deploy · user).
3. Distinguish **meta-framework** from **micro-frontend** — and place Astro (U2–3).
4. Defend why AI speed alone is insufficient evidence of understanding.

---

## 1 · System of interfaces

In FE I you built an **SPA** (*Single Page Application*): one project, one deploy. FE II asks what happens when the interface **scales**: multi-framework composition, edge, PWA, CI/CD, IoT, and process defence.

```
                 [ INTERFACE LAYER ]
                          │
        ┌─────────────────┼─────────────────┐
        ▼                 ▼                 ▼
 [ BROWSER ]        [ EDGE / API ]      [ USER ]
 Micro-frontends    Middleware/auth     Multi-surface
 Storage / PWA      Cache / SSR         a11y · network · device
```

The component model (props, state) stays; the **deployment context** changes.

### Four-pillar vector

For each dimension, write **one architecture decision** (not a UI component):

| Dimension | In production | Question |
| --- | --- | --- |
| **Browser / client** | PWA, Service Workers, Storage | What lives offline and what syncs? |
| **Service / API** | REST, GraphQL, **BFF** (*Backend for Frontend*) | How do you decouple domain from view? |
| **Deploy / infra** | Edge, **CDN**, **CI/CD** | What logic runs close to the user? |
| **User** | Device, network, **a11y** | How does the system degrade gracefully? |

This vector returns in Entrega 1 (Astro + middleware), Entrega 2 (WebSocket/IoT), and the capstone.

### Frontier (semester map)

| Vector | What changes | Units |
| --- | --- | --- |
| Edge | Auth/routing/SSR near the user | 2–3, 7 |
| Device / PWA | Offline, WASM, 3D | 4, 8–9 |
| Real-time | WebSocket, distributed state | 10–11 |
| Multi-surface | Tokens, web + embeds + agents | 11–12 |

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
VERIFIED — islands as technical performance pattern; micro-frontends as organizational/development pattern.
Ahmes: scholar/.../68c7da35/extract/extraction.db
nodes: 797a702c-0538-5577-adc4-c3450c511608 (p.3); 1ebbe080-df28-5f9b-ae84-8933f73048d9 (p.11)
evaluator_safe=yes · discovery: profield-frontend-pedagogy field_prospection
transfer: architecture paper supports FE II conceptual framing; does not prove this kickoff sequence's learning outcomes.
-->
{% endif %}

Islands and micro-frontends **look similar but are not the same**: islands are a technical performance pattern (static HTML + selective hydration); micro-frontends are a **development and organizational** pattern for teams (Vepsäläinen 2025, 3, 11). Astro teaches islands first (U2–3); do not confuse “islands in one repo” with “several repos per team.”

---

## 2 · Meta-frameworks vs micro-frontends

| | **Meta-framework** | **Micro-frontends** |
| --- | --- | --- |
| **Boundary** | One project | Several applications |
| **Problem** | SSR/SSG, DX, structure, performance | Team scale, independent deploys |
| **Dependencies** | Centralized | Fragmented / federated |
| **Integration** | Build / unified server | Runtime (federation) or edge proxy |
| **Examples** | Next, Nuxt, SvelteKit — **Astro** (composition + islands) | Module Federation, Web Components, edge routing |

> They are not opposites: in production each micro-frontend is often its own meta-framework internally.

```
   [ EDGE / PROXY ] → Next (checkout) · Nuxt (catalog) · Astro (marketing)
```

---

## 3 · Excerpt: edge middleware (Unit 2 preview)

**Excerpt** — does not run in U1. Pattern: context → boundary decision → render → cache. Docs: [Astro middleware](https://docs.astro.build/en/guides/middleware/)

```ts
// src/middleware.ts — Excerpt (Astro; Unit 2+)
import { defineMiddleware } from 'astro:middleware';

export const onRequest = defineMiddleware(async (context, next) => {
  const { request, locals, redirect } = context;
  const url = new URL(request.url);
  locals.isMobile = /mobile/i.test(request.headers.get('user-agent') ?? '');

  if (url.pathname.startsWith('/dashboard') && !request.headers.get('cookie')?.includes('session=')) {
    return redirect('/login', 302);
  }

  const response = await next();
  response.headers.set('Cache-Control', 'public, max-age=60, s-maxage=3600');
  return response;
});
```

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
CLT justification for excerpt: worked example before B3 problems reduces extraneous load when element interactivity is high (Chandler and Sweller 1996, 4).
Ahmes: .../17c6e9fc/extract/extraction.db · node 639f9980-f9bd-524a-9d85-0ee8018d749c · page_index=3 · evaluator_safe=yes
Platform note (not Chicago): Astro middleware docs — not research evidence.
-->
{% endif %}

---

## 4 · AI: speed is not understanding

This unit does **not** establish a technical CONTENIDOS claim. It does fix FE II discipline: disclose AI assistance and defend decisions.

Research on AI-assisted programming distinguishes **immediate task performance** from **genuine learning** — durable, transferable conceptual understanding and evaluative skill (Liu, Fan, and Pan 2026, 1). This course therefore treats speed as insufficient evidence: you must explain, test, and defend.

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
VERIFIED — performance vs learning tension.
Ahmes: scholar/.../dc2bd27d/extract/extraction.db · node 25fa0a93-6808-5ccd-acc7-54b67523897e · page_index=0 · evaluator_safe=yes
Inline form: (Liu, Fan, and Pan 2026, 1).
transfer: frames disclosure policy; does not claim causal superiority of this teaching sequence.
-->
{% endif %}

In FE II, AI helps with diagrams, audits, and PR review (U5–6); it does **not** replace learning architecture.

---

## B3 · Individual exercises · 1 h

1. **Diagnostic.** FE I-style description (one SPA, one deploy): complete the four-pillar vector — what would change in FE II and what would stay.
2. **No AI (declared).** Two sentences: what an AI tool speeding up *your* task proves, and what it does **not** prove about what you understand.
3. **Self-check.** Without opening U2/U8, predict in one sentence each what they will ask of this unit’s “systems lens” ([track index]({{ '/tracks/feii/' | relative_url }})).

Professor sketches: `exercises.md` (not the public handout).

---

## Platform notes (not research evidence)

- [Why Astro](https://docs.astro.build/en/concepts/why-astro/) · [Islands](https://docs.astro.build/en/concepts/islands/) · [Middleware](https://docs.astro.build/en/guides/middleware/)
- [PWA](https://web.dev/learn/pwa/) · [Core Web Vitals](https://web.dev/articles/vitals)
- Web Atelier Astro sequence: [{{ '/lessons/en/astro/' | relative_url }}]({{ '/lessons/en/astro/' | relative_url }})

---

## Outcome

- System of interfaces + four-pillar vector usable on a real product
- Meta-framework (Astro in U2–3) vs micro-frontend (teams/repos)
- Semester calendar on the [track index]({{ '/tracks/feii/' | relative_url }})
- Ready for Astro scaffolding in Unit 2

> _"A monorepo is not a monolith. A monolith is not modular. A modular system need not be distributed."_
> — Tao of Development, `arch-006`
{: .tao-development-quote }

{% comment %}
outcome-graphic-selection:
  source-section: "Outcome"
  visual-grammar: "production-interface-surfaces — multiple production interface surfaces connected as one durable system"
{% endcomment %}
{% include lesson-outcome-graphic.html %}

---

## References

- Chandler, Paul, and John Sweller. 1996. “Cognitive Load While Learning to Use a Computer Program.” *Applied Cognitive Psychology* 10 (2).
- Liu, Dandan, Guangrui Fan, and Lihu Pan. 2026. “Tool, Tutor, or Crutch?: A Grounded Theory of Cognitive Scaffolding and Offloading in AI-Assisted Programming Education.” *International Journal of STEM Education*. https://doi.org/10.1186/s40594-025-00592-w.
- Vepsäläinen, Juho, Petri Vuorimaa, and Arto Hellas. 2025. “The Potential of Serverless Edge-Powered Islands for Web Development.” *Journal of Web Engineering*. https://doi.org/10.13052/jwe1540-9589.2411.

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
Missing evidence (stated): this kickoff has no CONTENIDOS technical claim to prove as a teaching sequence; domain cites frame architecture vocabulary; CLT cite justifies presentation density; AI cite frames disclosure. No evaluator-safe HE comparison of Astro/islands kickoff sequences — pilot informed by transfer (LESSON-SAUCE U1 row).
-->
{% endif %}
