---
layout: lesson
title: 'Unidad 1: Lanzamiento — De React FE I a arquitectura de producción'
title_alt: 'Unit 1: Kickoff — From FE I React to Production Architecture'
slug: feii-unit-1-kickoff
date: 2026-08-08
author: 'Rubén Vega Balbás, PhD'
lang: es
permalink: /lessons/es/feii/unit-1-kickoff/
description: 'Orientación FE II: el front-end de producción como sistema de interfaces; vector cuatripartito; meta-frameworks frente a micro-frontends; disciplina de declaración IA.'
tags: [feii, orientacion, arquitectura, capa-interfaz, produccion, pensamiento-sistemico]
status: complete
---

<aside class="lesson-framing" aria-label="Idea maestra y lente de campo">
<p><strong>Idea maestra:</strong> El front-end de producción es un <strong>sistema de interfaces</strong> — orquestación entre navegador, edge/servicio, backend y persona usuaria —, no un único bundle SPA.</p>
<p><strong>Lente de campo:</strong> <strong>Ancla:</strong> decisiones por capa (cliente · API · despliegue · usuario). <strong>Frontera:</strong> edge, dispositivo/<abbr title="Progressive Web App">PWA</abbr>, tiempo real, multi-superficie. <strong>Estado:</strong> orientación sin CONTENIDOS técnicos; prepara Unidades 2–12.</p>
</aside>

> **Prueba de estudio:** Dibuja superficies, contratos y límites de fallo de un producto (CDN/edge, caché, auth, offline) — no solo componentes UI.

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
UbD Stage-1: transfer goal = reframe production FE as distributed interface system + distinguish meta-framework vs micro-frontend.
UbD Stage-2: evidence = three B3 answers + verify checklist (one architecture decision per pillar).
Bloom: B1 Understand/Analyze (conceptual systems knowledge); B3 Apply/Evaluate (architecture decisions; AI speed vs understanding). B2 N/A (0 h lab).
5E: not applicable — orientation/compliance framing unit, not inquiry lab.
CLT: high intrinsic load (many new terms); reduce extraneous load by one systems diagram, acronym table, worked middleware excerpt before exercises (Chandler and Sweller 1996).
Critical moment (lens Epistemological): AI acceleration ≠ durable understanding (Liu, Fan, and Pan 2026) → B1 framing + B3 item 2 no-AI.
Domain grounding: islands vs micro-frontends (Vepsäläinen 2025). Transfer boundary: domain architecture paper ≠ measured learning outcome for this kickoff sequence — pilot informed by transfer.
-->
{% endif %}

<!-- prettier-ignore-start -->

## 📋 Tabla de contenidos
{: .no_toc }
- TOC
{:toc}

<!-- prettier-ignore-end -->

{% include lesson-semantic-graphic.html %}

---

## Antes de empezar

| Requisito | ¿Obligatorio? |
| --- | --- |
| FE I semestre 2 (app React desplegada) | Sí |
| Índice del track + `exercises.md` | Sí |
| Repo de equipo Entrega 1 | Aún no (Unidad 2) |

**Tiempo:** 2 h magistral · **0 h lab** · 1 h ejercicios individuales (B3). Calendario completo: [índice FE II]({{ '/tracks/feii/' | relative_url }}).

---

## Sesión en 6 pasos

| # | Acción | Dónde |
| --- | --- | --- |
| 1 | Sistema de interfaces + vector cuatripartito | §1 |
| 2 | Meta-framework vs micro-frontend (+ Astro) | §2 |
| 3 | Excerpt middleware (vista previa U2) | §3 |
| 4 | Declaración IA: velocidad ≠ comprensión | §4 |
| 5 | Tres ejercicios individuales | B3 |
| 6 | Entregar evidencia | Entrega |

---

## Comprueba / Fallos / Entrega

**Comprueba**

- [ ] Un párrafo: interfaz única vs sistema de interfaces
- [ ] Una decisión de arquitectura por pilar del vector
- [ ] Meta-framework ≠ micro-frontend (y por qué suelen combinarse)
- [ ] Ejercicio 2 distingue velocidad de comprensión (sin IA)

**Fallos frecuentes**

| Error | Evítalo |
| --- | --- |
| Tratar U1 como «semana libre» | Entrega los 3 ejercicios — U2 asume este marco |
| Esperar lab en equipo | 0 h lab es oficial; el primer lab es U2 |
| Usar IA en el ejercicio 2 | Marcado resoluble sin IA |

**Entrega:** tres respuestas por el canal del profesor. Sin PR de equipo.

> _"Antes de la primera línea de código, prepara la forja. Antes de la primera consulta, carga la memoria. La documentación no es un epílogo — es el primer acto de arquitectura."_
> — Tao of Development, `wis-014`
{: .tao-development-quote }

> **Declaración de asistencia IA:** metodología docs-first; planes, prompts e informes se documentan.  
> **Código:** el middleware de §3 es **Excerpt** (no ejecuta en U1). Política: [convenciones FE II]({{ '/lessons/en/feii/' | relative_url }}#-conventions-used-across-these-lessons).

---

## Objetivos

Al salir de esta orientación podrás:

1. Enlazar FE I (SPA React) con FE II (arquitectura de producción).
2. Aplicar el **vector cuatripartito** (navegador · servicio · despliegue · persona usuaria).
3. Distinguir **meta-framework** y **micro-frontend** — y situar Astro (U2–3).
4. Defender por qué la velocidad con IA no basta como evidencia de comprensión.

---

## 1 · Sistema de interfaces

En FE I construiste una **SPA** (*Single Page Application*): un proyecto, un despliegue. FE II pregunta qué ocurre cuando la interfaz **escala**: composición multi-framework, edge, PWA, CI/CD, IoT y defensa de proceso.

```
                 [ CAPA DE INTERFAZ ]
                          │
        ┌─────────────────┼─────────────────┐
        ▼                 ▼                 ▼
 [ NAVEGADOR ]      [ EDGE / API ]    [ PERSONA USUARIA ]
 Micro-frontends    Middleware/auth   Multi-superficie
 Storage / PWA      Caché / SSR       a11y · red · dispositivo
```

El modelo de componentes (props, estado) se mantiene; cambia el **contexto de despliegue**.

### Vector cuatripartito

Para cada dimensión, escribe **una decisión de arquitectura** (no un componente UI):

| Dimensión | En producción | Pregunta |
| --- | --- | --- |
| **Navegador / cliente** | PWA, Service Workers, Storage | ¿Qué vive offline y qué se sincroniza? |
| **Servicio / API** | REST, GraphQL, **BFF** (*Backend for Frontend*) | ¿Cómo se desacopla el dominio de la vista? |
| **Despliegue / infra** | Edge, **CDN**, **CI/CD** | ¿Qué lógica corre cerca del usuario? |
| **Persona usuaria** | Dispositivo, red, **a11y** | ¿Cómo degrada el sistema con elegancia? |

Este vector reaparece en Entrega 1 (Astro + middleware), Entrega 2 (WebSocket/IoT) y el capstone.

### Frontera (mapa hacia el semestre)

| Vector | Qué cambia | Unidades |
| --- | --- | --- |
| Edge | Auth/routing/SSR cerca del usuario | 2–3, 7 |
| Dispositivo / PWA | Offline, WASM, 3D | 4, 8–9 |
| Tiempo real | WebSocket, estado distribuido | 10–11 |
| Multi-superficie | Tokens, web + embebidos + agentes | 11–12 |

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
VERIFIED — islands as technical performance pattern; micro-frontends as organizational/development pattern.
Ahmes: scholar/.../68c7da35/extract/extraction.db
nodes: 797a702c-0538-5577-adc4-c3450c511608 (p.3); 1ebbe080-df28-5f9b-ae84-8933f73048d9 (p.11)
evaluator_safe=yes · discovery: profield-frontend-pedagogy field_prospection
transfer: architecture paper supports FE II conceptual framing; does not prove this kickoff sequence's learning outcomes.
-->
{% endif %}

Islas y micro-frontends **se parecen pero no son lo mismo**: las islas son un patrón técnico de rendimiento (HTML estático + hidratación selectiva); los micro-frontends son un patrón de **desarrollo y organización** de equipos (Vepsäläinen 2025, 3, 11). Astro enseña primero las islas (U2–3); no confundas «islas en un repo» con «varios repos por equipo».

---

## 2 · Meta-frameworks frente a micro-frontends

| | **Meta-framework** | **Micro-frontends** |
| --- | --- | --- |
| **Límite** | Un proyecto | Varias aplicaciones |
| **Problema** | SSR/SSG, DX, estructura, rendimiento | Escala de equipos, deploys independientes |
| **Dependencias** | Centralizadas | Fragmentadas / federadas |
| **Integración** | Build / servidor unificado | Runtime (federation) o proxy en edge |
| **Ejemplos** | Next, Nuxt, SvelteKit — **Astro** (composición + islas) | Module Federation, Web Components, routing en edge |

> No son opuestos: en producción cada micro-frontend suele ser, por dentro, su propio meta-framework.

```
   [ EDGE / PROXY ] → Next (checkout) · Nuxt (catálogo) · Astro (marketing)
```

---

## 3 · Excerpt: middleware en el borde (vista previa U2)

**Excerpt** — no ejecuta en U1. Patrón: contexto → decisión en frontera → render → caché. Docs: [Middleware Astro](https://docs.astro.build/es/guides/middleware/)

```ts
// src/middleware.ts — Excerpt (Astro; Unidad 2+)
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

## 4 · IA: velocidad no es comprensión

Esta unidad **no** demuestra un CONTENIDO técnico. Sí fija la disciplina FE II: declarar asistencia IA y defender decisiones.

La investigación en programación asistida por IA distingue **rendimiento inmediato de la tarea** de **aprendizaje genuino** — comprensión conceptual durable, transferible y capacidad evaluativa (Liu, Fan, and Pan 2026, 1). Por eso el curso trata la velocidad como evidencia insuficiente: debes explicar, probar y defender.

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
VERIFIED — performance vs learning tension.
Ahmes: scholar/.../dc2bd27d/extract/extraction.db · node 25fa0a93-6808-5ccd-acc7-54b67523897e · page_index=0 · evaluator_safe=yes
Inline form: (Liu, Fan, and Pan 2026, 1) — resolver preview may show first author only; References lists all three.
transfer: frames disclosure policy; does not claim causal superiority of this teaching sequence.
Related educator-risk theme (over-reliance / bypassing reasoning) in arXiv scaffold paper remains [BIBLIO-GAP] for public cite — not used as student citation.
-->
{% endif %}

En FE II la IA colabora en diagramas, auditorías y revisión de PRs (U5–6); **no** sustituye aprender arquitectura.

---

## B3 · Ejercicios individuales · 1 h

1. **Diagnóstico.** Descripción estilo FE I (una SPA, un deploy): completa el vector cuatripartito — qué cambiaría en FE II y qué permanecería.
2. **Sin IA (declarado).** Dos frases: qué demuestra que una herramienta acelere *tu* tarea, y qué **no** demuestra sobre lo que comprendes.
3. **Autocomprobación.** Sin abrir U2/U8, predice en una frase qué pedirán a la «lente de sistemas» de esta unidad ([índice]({{ '/tracks/feii/' | relative_url }})).

Esquemas del profesor: `exercises.md` (no público en clase).

---

## Notas de plataforma (no son evidencia de investigación)

- [Por qué Astro](https://docs.astro.build/es/concepts/why-astro/) · [Islas](https://docs.astro.build/es/concepts/islands/) · [Middleware](https://docs.astro.build/es/guides/middleware/)
- [PWA](https://web.dev/learn/pwa/) · [Core Web Vitals](https://web.dev/articles/vitals)
- Secuencia Astro en Web Atelier: [{{ '/lessons/en/astro/' | relative_url }}]({{ '/lessons/en/astro/' | relative_url }})

---

## Resultado

- Sistema de interfaces + vector cuatripartito aplicables a un producto real
- Meta-framework (Astro en U2–3) vs micro-frontend (equipos/repos)
- Calendario del semestre en el [índice del track]({{ '/tracks/feii/' | relative_url }})
- Listo/a para scaffolding Astro en Unidad 2

> _"Un monorepo no es un monolito. Un monolito no es modular. Un sistema modular no tiene por qué ser distribuido."_
> — Tao of Development, `arch-006`
{: .tao-development-quote }

{% comment %}
outcome-graphic-selection:
  source-section: "Resultado"
  visual-grammar: "production-interface-surfaces — multiple production interface surfaces connected as one durable system"
{% endcomment %}
{% include lesson-outcome-graphic.html %}

---

## Referencias

- Chandler, Paul, and John Sweller. 1996. “Cognitive Load While Learning to Use a Computer Program.” *Applied Cognitive Psychology* 10 (2).
- Liu, Dandan, Guangrui Fan, and Lihu Pan. 2026. “Tool, Tutor, or Crutch?: A Grounded Theory of Cognitive Scaffolding and Offloading in AI-Assisted Programming Education.” *International Journal of STEM Education*. https://doi.org/10.1186/s40594-025-00592-w.
- Vepsäläinen, Juho, Petri Vuorimaa, and Arto Hellas. 2025. “The Potential of Serverless Edge-Powered Islands for Web Development.” *Journal of Web Engineering*. https://doi.org/10.13052/jwe1540-9589.2411.

{% if site.publication.publish_internal_metadata %}
<!-- curriculum-internal:
Missing evidence (stated): this kickoff has no CONTENIDOS technical claim to prove as a teaching sequence; domain cites frame architecture vocabulary; CLT cite justifies presentation density; AI cite frames disclosure. No evaluator-safe HE comparison of Astro/islands kickoff sequences was used — pilot informed by transfer (LESSON-SAUCE U1 row).
-->
{% endif %}
