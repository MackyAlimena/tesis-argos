# ADR-007: Sustitución del Panel Delphi por Auditoría Externa de Certificación y Entrevistas a Especialistas

- **Estado:** Aceptado
- **Fecha:** 2026-08-30
- **Autor:** Macarena Alimena
- **Contexto:** Calibración del criterio C5 (validación externa) previa a la entrega del Plan de Trabajo (01/09/2026). Supersede parcialmente el punto 2 de la sección *Mitigación de Sesgo por Doble Rol* de [ADR-001](ADR-001-metodologia-dsr-y-caso-unico.md).

## Contexto y Problema

El diseño original fijaba como instrumento de validación externa un **panel de expertos tipo Delphi de 8 especialistas en dos rondas**, para el cual debían cursarse 12 invitaciones (`ROADMAP.md` §0), con consenso medido por rango intercuartílico (IQR ≤ 1) sobre relevancia, completitud y aplicabilidad de A0–A3.

Al revisar el Plan de Trabajo antes de su entrega se identificaron dos problemas con ese instrumento:

1. **Desproporción respecto de los recursos disponibles.** Convocar y sostener a 8 especialistas a lo largo de dos rondas, con 12 invitaciones cursadas para asegurar esa participación, excede lo razonable para un trabajo de grado individual de 320 horas. El riesgo ya estaba declarado en `ROADMAP.md` §6 ("Panel Delphi con respuesta baja"), y su *fallback* previsto —ronda única más entrevistas semiestructuradas individuales— describía, de hecho, el instrumento realmente ejecutable.
2. **Naturaleza de la evidencia obtenida.** Un panel produce *opinión experta sobre un diseño*. El caso de estudio ofrece, en cambio, acceso a una instancia de verificación externa real: la organización transita procesos de certificación en normas ISO, y el proceso de desarrollo intervenido queda comprendido en el alcance de la auditoría de ISO/IEC 27001.

La función que C5 debe cumplir no cambia: **que la autora no sea jueza de su propio diseño**. Lo que cambia es el instrumento con el que se cumple.

## Decisión

Se sustituye el panel Delphi por un **instrumento de validación externa de dos patas**, y se redefine C5 en consecuencia:

**(a) Auditoría externa de certificación ISO/IEC 27001** sobre el proceso de desarrollo intervenido. Es una revisión practicada por un tercero acreditado, con criterios que la autora no controla, sobre el sistema en operación y con consecuencias reales para la organización.

**(b) Entrevistas semiestructuradas a 4 especialistas externos** (rango aceptable 3–6; se contactan 8 para asegurar 4) —auditores de sistemas de gestión y líderes técnicos ajenos al trabajo— sobre relevancia, completitud y aplicabilidad de cada artefacto. **Ronda única, sin exigencia de consenso estadístico.**

**Nuevo umbral de C5:** ausencia de no conformidades y de observaciones atribuibles al proceso de desarrollo gobernado, **y** acuerdo de al menos 3 de cada 4 especialistas consultados sobre la aplicabilidad de cada artefacto.

## Consecuencias

**A favor**

- La auditoría aporta **evidencia de campo en lugar de opinión sobre un diseño**: el marco se somete a un tercero acreditado, en operación real y con consecuencias para la organización. Como mitigación del doble rol es más fuerte que un panel convocado por la propia autora.
- El instrumento pasa a ser ejecutable con los recursos declarados. Elimina el riesgo de que C5 quede sin veredicto por respuesta insuficiente.
- Aprovecha una condición del caso —la PyME en proceso de certificación— que estaba disponible y no se estaba utilizando.

**En contra, y declarado**

- **La auditoría y el panel no miden el mismo constructo.** Una auditoría de ISO/IEC 27001 certifica conformidad del sistema de gestión de seguridad de la información contra los controles de esa norma; **no evalúa la relevancia ni la completitud de A0–A3 como artefactos de investigación.** Por eso el instrumento conserva la segunda pata: las entrevistas cubren la dimensión que la auditoría no alcanza. Presentar la auditoría sola como validación del marco sería un salto injustificado, y así queda advertido para la redacción del capítulo 9.
- **La fecha de la auditoría no la controla la autora.** Se incorpora como riesgo declarado con plan alternativo (`ROADMAP.md` §6): si se reprograma fuera de la ventana, la validación externa se sostiene sobre el auditor ciego de la prueba de reconstrucción, que es independiente de ambos instrumentos.
- **Se pierde la medida de consenso cuantitativa.** El IQR ≤ 1 daba un veredicto numérico; el acuerdo de 3 de cada 4 especialistas es más grueso. Se acepta la pérdida de precisión a cambio de que el criterio sea alcanzable.
- **C5 deja de ser plenamente pre-registrable en un solo umbral numérico.** La pata de auditoría es binaria y depende de un tercero.

**Neutro**

- El presupuesto de la fase F6 (32 h) no se modifica: las horas de diseño y análisis del instrumento Delphi se reasignan a la preparación de las entrevistas y al seguimiento de la auditoría.
- El artefacto **V** conserva su lugar en el conjunto; cambia su composición, no su función.

## Alcance de la sincronización

Esta decisión se propagó a: `ROADMAP.md` (§0, §0.1, §1, §2, §3, §4 S20/S30/S34/S37, §5 D3, §6), `roadmap.html`, `kb/context.md` (§8, §8.2, §9, §12, §13, §14), `README.md`, `ADR-001` (nota de superseción), `docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md`, `docs/04-pitch-tesis/README.md`, `docs/onboarding/`, `kb/diario/README.md`, las skills de `.claude/` y `.agent/`, y el directorio `evaluation/delphi/`, renombrado a `evaluation/validacion-externa/`.

## Pendiente

- **Confirmar con la organización la fecha de la auditoría de certificación ISO/IEC 27001** y verificar que el proceso de desarrollo intervenido quede efectivamente comprendido en su alcance. Es la nueva dependencia D3.
- **Revisar la decisión con el Director** antes de la entrega del 01/09/2026. Los criterios de éxito se pre-registran en el Plan y no se modifican después de medir: la calibración de C5 debe estar acordada antes de firmar.
