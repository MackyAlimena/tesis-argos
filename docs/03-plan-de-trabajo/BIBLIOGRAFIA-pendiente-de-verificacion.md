# Referencias pendientes de verificación

> **Estado:** bloqueante para la entrega del 01/09/2026.
> **Por qué existe este archivo:** el Plan de Trabajo incluye únicamente referencias cuya existencia y datos bibliográficos pueden darse por sólidos. Las que figuran abajo estaban en la bibliografía preliminar (`kb/context.md` §19) pero **no se incorporaron al Plan** porque no fueron verificadas contra la fuente original.
>
> Esto no es formalismo. La tesis sostiene un argumento sobre integridad, trazabilidad y evidencia verificable, y dedica la pregunta 5 del Informe Ético a la citación correcta. Una referencia inexistente o mal atribuida en este trabajo en particular no es un error de estilo: es una contradicción con su propio claim.

---

## 1. Verificar antes de incorporar

Para cada una: confirmar autoría completa, año, título exacto, sede de publicación, y DOI o identificador. Si no se localiza la fuente, **eliminar la referencia**, no reformularla.

| # | Referencia preliminar | Qué falta confirmar |
|---|---|---|
| B1 | Otoum, S., et al. (2026). *Autonomous agent frameworks for software engineering: A systematic survey and taxonomy*. IEEE Access. | Autoría completa (no «et al.»), volumen, número de página o artículo, DOI. |
| B2 | He, J., et al. (2025/2026). *Multi-agent collaboration in software development: Architectures, protocols, and empirical evidence*. ACM TOSEM. | Año definitivo (figura como 2025/2026), autoría completa, volumen y número. |
| B3 | CooperBench. (2026). *Benchmarking multi-agent collaboration, context drift, and task handoffs in software engineering*. arXiv:2601.09123. | **Prioridad alta.** Falta autoría (un benchmark no es autor corporativo de sí mismo) y el identificador arXiv debe confirmarse. |
| B4 | Zhang, J., et al. (2025). *A survey on evaluation of LLM-based autonomous agents*. arXiv:2503.16416. | Autoría completa y correspondencia del identificador con el título. |
| B5 | Wang, L., et al. (2025). *Multi-agent agile effort estimation by analogy*. arXiv:2509.14483. | Autoría completa y correspondencia del identificador. Citado en el catálogo de Giagnorio (ítem 1.2). |
| B6 | Empirical Software Engineering. (2026). *Does AI code review lead to code changes? A case study of GitHub Actions*. EMSE. | **Falta autoría por completo.** El journal no es el autor. |
| B7 | *Evaluating LLMs for Code Review* (2025). ACM TOSEM / arXiv:2502.11245. | **Falta autoría por completo** y el título parece descriptivo, no el título real. |
| B8 | Project Management Institute. (2025). *AI in PM Global Report 2025 / PMBOK Guide* (8.ª ed.). | Son dos obras distintas: separarlas. Confirmar que la 8.ª edición del PMBOK está publicada y su año. |
| B9 | Thoughtworks. (2025/2026). *Technology Radar* (Vol. 33). | Confirmar número de volumen y fecha de publicación. |
| B10 | Hou, X., et al. (2024). *Large language models for software engineering: A systematic literature review*. | El identificador arXiv anotado en `kb/context.md` (2404.04834) **no coincide** con el habitualmente asociado a este SLR. Verificar cuál corresponde antes de citar el preprint; en el Plan se cita la versión de journal, sin identificador. |

## 2. Referencias que salieron del Plan al recortarlo

Al calibrar la extensión del Plan contra el plan de referencia de Ballesteros y Alcázar, la bibliografía pasó de 30 a 27 entradas. Estas quedaron fuera **por no estar citadas en el cuerpo del texto**, no por dudas sobre su validez. Todas son sólidas y vuelven a la memoria final:

| Referencia | Dónde vuelve |
|---|---|
| Susman, G. I., & Evered, R. D. (1978). An assessment of the scientific merits of action research. *ASQ, 23*(4), 582–603. | Capítulo de metodología: fundamenta la investigación-acción. |
| Vaithilingam, P., Zhang, T., & Glassman, E. L. (2022). Expectation vs. experience. *CHI EA 2022*. | Capítulo de estado del arte: percepción de utilidad frente a corrección real. |
| Qian, C., et al. (2024). Communicative agents for software development. *ACL 2024*. | Capítulo de estado del arte: topologías multiagente (artefacto A0). |
| ISO/IEC 27701 — gestión de privacidad | Capítulo normativo, junto al tratamiento del riesgo E8. |
| ISO/IEC/IEEE 12207 — procesos del ciclo de vida del software | Capítulo normativo, si se decide anclar el modelo de proceso. |
| Francisco. (2024). Discurso del G7 sobre IA / Mensaje 57.ª Jornada Mundial de la Paz. | **Informe Ético y Social** (entrega del 15/09), no el Plan. |
| Pontificia Academia para la Vida. (2020). *Rome call for AI ethics*. | **Informe Ético y Social**. |

## 3. Normas: decisión de alcance pendiente

| # | Norma | Situación |
|---|---|---|
| B13 | ISO/IEC 42005 — evaluación de impacto de sistemas de IA | `kb/context.md` ya la marca como «verificar estado de publicación». **Confirmar si está publicada** antes de citarla como norma vigente. No entró al Plan. |

## 4. Verificación recomendada aunque el riesgo sea bajo

Están en el Plan porque son razonablemente sólidas, pero conviene confirmar título y año exactos antes de la entrega.

| # | Referencia | Qué confirmar |
|---|---|---|
| B14 | DORA. (2025). *State of AI-assisted software development report*. | Título exacto y si el autor corporativo correcto es DORA, Google Cloud o ambos. |
| B15 | OWASP Foundation. (2025). *OWASP Top 10 for Large Language Model Applications*. | Año de la versión que efectivamente se usa y si el título vigente incorpora «Agentic». |
| B16 | León XIV. (2026). *Magnifica Humanitas*. | Confirmar título completo, subtítulo y fecha exacta contra el texto oficial del Vaticano. Es la referencia central del Informe Ético: conviene que esté impecable. |
| B17 | Pontificia Academia para la Vida. (2020). *Rome call for AI ethics*. | `kb/context.md` anota «2020/2024». Decidir qué versión se cita y consignar solo esa. |

---

## Cómo cerrar esto

1. Verificar B1–B10 contra la fuente original. Lo que se localice, incorporar a la bibliografía del Plan. Lo que no se localice, **descartar**.
2. Resolver B13 (decisión de alcance, no de verificación).
3. Confirmar B14–B17 y corregir en el Plan si hiciera falta.
4. Registrar en `kb/literature/` una ficha por cada referencia incorporada, según la plantilla existente.

> La bibliografía del Plan queda sólida aun sin B1–B10: cubre método (Hevner, Peffers, Yin, Runeson y Höst, Susman y Evered), factor humano (Bainbridge, Parasuraman y Riley, Elish, Vaithilingam et al.), ingeniería agéntica (SWE-bench, MetaGPT, ChatDev, el SLR de Hou et al.), seguridad del código asistido (Perry et al., Sandoval et al.), métricas (Forsgren et al., DORA) y el corpus normativo completo. **Lo que falta es profundidad en 2025–2026, que es justamente lo que la cátedra pidió** — de ahí que cerrar esta lista sea prioridad y no trámite.
