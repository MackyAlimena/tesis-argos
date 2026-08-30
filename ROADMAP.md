# Plan de Ejecución — ARGOS

> **Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional.**
> **Trabajo de Grado — Ingeniería en Informática (Orientación Gestión)** · Universidad Austral
> **Alumna:** Macarena Alimena · **Tutor Académico:** Marcos Giagnorio
> **Documento maestro de cronograma operativo** · Actualizado: 28/08/2026

---

## 0. Parámetros congelados

Estos valores se fijan aquí y **no se modifican después de medir**. Congelarlos antes del experimento es la mitigación #1 del sesgo de doble rol (practitioner-researcher, §8.1 de `kb/context.md`).

| Parámetro | Valor | Fuente |
|---|---|---|
| **Carga horaria total** | **320 h** = 8 h/sem × 40 semanas | ADR-006 |
| **Ventana de ejecución** | S01 (31/08/2026) → S40 (06/06/2027) | Este documento |
| **Reserva / colchón** | 30 h (9,4 % del total), sin asignar | Este documento |
| **Receso declarado** | S18–S19 (28/12/2026 – 10/01/2027), 0 h | Este documento |
| **T0 — Instrumentación silenciosa** | **15/02/2027** — telemetría pasiva, sin gates, sin cambio de política | Este documento |
| **T1 — Intervención plena** | **15/03/2027** — matriz A2 activa, gates gobernados, evidencia obligatoria | Este documento |
| **Ventana PRE** | 01/03/2026 → 14/03/2027 | Este documento |
| **Ventana POST** | 15/03/2027 → 16/05/2027 (9 semanas) | Este documento |
| **N mínimo PRs post** | 60 PRs. Trigger de contingencia: si al **25/04/2027** no se alcanza, se extiende la ventana consumiendo reserva. | Este documento |
| **N reconstruction test** | 40 PRs (20 pre / 20 post), muestreo aleatorio, auditor **externo y ciego** | Este documento |
| **N panel Delphi** | 8 expertos (rango aceptable 6–10). Se invitan 12 para asegurar 8. | Este documento |

### 0.1. Criterios de éxito pre-registrados

Cada criterio tiene umbral numérico y veredicto binario. **El claim de la tesis se sostiene o se cae contra C1.**

| # | Criterio | Métrica | Umbral de éxito | Qué prueba |
|---|---|---|---|---|
| **C1** | **Reconstrucción de decisiones** | TRD = % de PRs donde un auditor ciego puede reconstruir las 4 dimensiones: (a) origen del cambio (agente/humano/modelo), (b) nivel de autonomía aplicable, (c) controles ejecutados, (d) firma humana y evidencia que la respalda | **Δ ≥ 40 puntos porcentuales** entre TRD_post y TRD_pre. Expectativa: pre < 25 %, post ≥ 80 % | El claim central |
| **C2** | **Fidelidad de la traza** | GDR = discrepancia entre `trace.json` del orquestador y los eventos reales de Git/CI | **0 %** (tolerancia cero) | Que la evidencia no sea a su vez una ficción |
| **C3** | **Profundidad de revisión** | Proporción de PRs de origen agéntico aprobados sin comentario Y con < 60 s de revisión por cada 100 líneas de diff | **Reducción ≥ 30 %** post vs. pre | Que el sello de goma retroceda |
| **C4** | **No degradación de entrega** *(guardrail)* | DORA lead time for changes + deployment frequency | **Deterioro ≤ 15 %** respecto de la línea de base | Que la gobernanza no mate la productividad que motivó usar agentes |
| **C5** | **Validación externa** | Consenso Delphi (IQR ≤ 1 en escala 1–5) sobre relevancia, completitud y aplicabilidad de A0/A1/A2/A3 | **≥ 75 % de los ítems** alcanzan consenso en ronda 2 | Que la autora no sea jueza de su propio diseño |

> **C4 es deliberadamente un guardrail, no un objetivo.** Un marco de gobernanza que mejora C1 destruyendo el lead time no resuelve el problema: lo cambia de lugar. Declararlo antes de medir es parte de la honestidad del diseño.

### 0.2. Sobre el alcance de las horas del artefacto A3

Las 44 h asignadas a A3 (collector + conformance engine + tablero) **no construyen una plataforma**. Cubren la porción de investigación: diseño del esquema de evidencia, calibración, testbench de ADR-005 y documentación. La implementación operativa se absorbe en el trabajo profesional de la autora sobre el pipeline real — eso *es* investigación-acción (ADR-001), y se declara explícitamente para que no se lea como una subestimación del esfuerzo.

---

## 1. Mapa de hitos

```text
  [ HOY: 28 Ago 2026 ]
         │
         ├── 🔴 01 Sep 2026 ── HITO 1: Plan de Trabajo de Grado          (4 días)
         ├── 🔴 15 Sep 2026 ── HITO 2: Informe Ético y Social            (18 días)
         │
         ├── 📥 Sep–Oct 2026 ── F1: Doble línea de base (BL-01 + IS-01)
         ├── 🗂️ Nov 2026 ───── F2: A1 · Taxonomía de riesgos
         ├── 🕸️ Dic 2026 ───── F3: A0 · Criterios de topologías
         ├── 🧊 28/12 – 10/01 ─ RECESO DECLARADO (0 h)
         ├── 🎚️ Ene 2027 ───── F4: A2 · Matriz Autonomía × Control  + convocatoria Delphi
         ├── ⚙️ Feb–Mar 2027 ─ F5: A3 · Telemetría, motor y tablero
         │        └── 📡 15/02/2027 · T0 — instrumentación silenciosa
         │
         ├── 🔴 23 Feb 2027 ── HITO 3: Pitch de Tesis
         │
         ├── 🚦 15/03/2027 ─── T1 — INTERVENCIÓN PLENA (abre ventana POST)
         ├── 👥 Mar–Abr 2027 ─ F6: Panel Delphi + reconstruction test PRE
         ├── 📊 Abr–May 2027 ─ F7: Reconstruction test POST + análisis pre/post
         ├── ✍️ May–Jun 2027 ─ F8: Consolidación de la memoria
         │
         └── 🏁 Jun–Jul 2027 ── HITO 4: Defensa Final
```

---

## 2. Presupuesto de horas por fase

| Fase | Semanas | Horas | % |
|---|---|---:|---:|
| **F0** · Entregas formales de cátedra | S01–S03 | 24 | 7,5 % |
| **F1** · Diagnóstico y doble línea de base | S04–S09 | 32 | 10,0 % |
| **F2** · A1 — Taxonomía de riesgos | S10–S13 | 28 | 8,8 % |
| **F3** · A0 — Criterios de topologías | S14–S17 | 28 | 8,8 % |
| *Receso declarado* | S18–S19 | 0 | — |
| **F4** · A2 — Matriz Autonomía × Control | S20–S22 | 24 | 7,5 % |
| **F5** · A3 — Telemetría, motor y tablero | S23–S25, S27–S29 | 44 | 13,8 % |
| **H3** · Pitch de Tesis | S26 | 4 | 1,3 % |
| **F6** · Panel Delphi + reconstruction PRE | S30–S33 | 32 | 10,0 % |
| **F7** · Medición post y análisis | S34–S37 | 28 | 8,8 % |
| **F8** · Consolidación de la memoria | S38–S40 | 46 | 14,4 % |
| **Reserva** (sin asignar) | — | 30 | 9,4 % |
| **TOTAL** | **40 semanas** | **320** | **100 %** |

> **Regla de la reserva:** se consume ante un trigger declarado (retraso de datos, N post insuficiente, feedback estructural del tutor). Lo que no se consuma va a F8. No se usa para agregar alcance.

---

## 3. Redacción incremental: artefacto → capítulo

La memoria **no se escribe en mayo**. Cada fase cierra con el borrador del capítulo que le corresponde. F8 consolida; no crea.

| Capítulo | Contenido | Se redacta en |
|---|---|---|
| 1–3 | Introducción, estado del arte, metodología | Reutiliza Plan de Trabajo (S01) + vigilancia continua |
| **4** | Diagnóstico del caso: estado de facto y línea de base | **S09** (F1) |
| **5** | A1 — Taxonomía de riesgos del desarrollo agentizado | **S13** (F2) |
| **6** | A0 — Criterios de gobernabilidad de topologías | **S17** (F3) |
| **7** | A2 — Matriz Autonomía × Control | **S22** (F4) |
| **8** | A3 — Modelo de evidencia, motor y tablero + calibración | **S29** (F5) |
| **9** | Resultados: validación pre/post y Delphi | **S37** (F7) |
| 10 | Discusión, limitaciones, trabajo futuro | S38–S39 (F8) |
| Anexos | Diario de investigación, ADRs, protocolos, código | Continuo |

---

## 4. Cronograma semanal detallado

Leyenda de estado: ⏳ en curso · 📝 pendiente · 🎯 hito · 🧊 receso

### FASE 0 — Entregas formales de cátedra · S01–S03 · 24 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S01** | 28/08–06/09 | 12 | **Plan de Trabajo de Grado.** Instanciar la plantilla oficial: Motivación (gap fábrica vs. producto) · Objetivo + pregunta + SP1–SP5 · Funcionalidades reinterpretadas como capacidades del marco · Tecnologías (collector, trazas, tablero, corpus normativo) · Arquitectura de gobernanza en capas (1 diagrama) · Metodología DSR + caso único + Delphi · **§0 de este documento embebido** (320 h, ventanas, criterios C1–C5) · Bibliografía APA. **Entrega 01/09.** | PDF entregado a la Facultad + fuente en `docs/03-plan-de-trabajo/`. Los 5 criterios pre-registrados figuran con número. |
| **S02** | 07/09–13/09 | 8 | **Informe Ético y Social.** Las 5 preguntas contra la matriz E1–E10. Preguntas 1–2 (objeto, fin, stakeholders, *moral crumple zone*). Preguntas 3–4 (mitigación en 3 horizontes; **E9 vigilancia laboral**: prohibición declarada de usar telemetría para evaluación individual). Pregunta 5 (integridad + **declaración de uso de IA en la propia tesis**). Fundamentación *Magnifica Humanitas*. | Borrador completo enviado a Marcos **el 11/09** (deja 4 días de margen). |
| **S03** | 14/09–20/09 | 4 | Incorporación de feedback y **entrega Informe Ético (15/09)**. Apertura de F1. | 🎯 Entregado. Consistencia cruzada verificada contra el Plan de Trabajo. |

### FASE 1 — Diagnóstico: doble línea de base · S04–S09 · 32 h

> **Esta fase produce DOS líneas de base, no una.** La cuantitativa (BL-01, datos de PRs) y la **estructural** (IS-01, inventario de la superficie agéntica de facto). IS-01 no depende de terceros y es, en sí mismo, un hallazgo: documenta que la autonomía de los agentes hoy no fue decidida sino heredada del modo en que se armó el pipeline.

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S04** | 21–27/09 | 6 | ⚠️ **BLOQUEANTE — Pedido formal del export de PRs.** Enviar la especificación de `data/raw/README.md` por escrito. Acordar anonimización, retención y confidencialidad con la empresa. Declarar la ventana PRE. | Pedido enviado por escrito con **fecha de compromiso de entrega**. Acuerdo de datos por e-mail o firmado. **Trigger: si al 09/10 no hay datos, se activa el Plan B (§6).** |
| **S05** | 28/09–04/10 | 6 | **IS-01 — Inventario de la superficie agéntica de facto.** Relevar todo agente, hook y verificación que hoy corre en el pipeline: quién lo puso, cuándo, qué archivos toca, si exige revisión humana (formal vs. de hecho), qué evidencia deja. | Tabla IS-01 con ≥1 fila por agente/verificación y las 6 columnas completas. Sin celdas vacías: "desconocido" es un dato válido y significativo. |
| **S06** | 05–11/10 | 6 | Cierre de IS-01 + **mapeo contra el Catálogo Giagnorio (2026)**: qué categorías de las 14 están cubiertas, cuáles no, y cuáles se implementaron sin decisión explícita. Redacción de la sección "estado de facto". | IS-01 v1.0 en `kb/`. Sección redactada (insumo directo del **capítulo 4**). |
| **S07** | 12–18/10 | 6 | Ingesta y anonimización del export. Script de carga reproducible a `data/processed/`. | Dataset cargado, **N de PRs declarado**, script versionado y re-ejecutable. |
| **S08** | 19–25/10 | 4 | Análisis exploratorio: tiempo de aprobación vs. tamaño del diff · % aprobado sin comentarios · humano vs. agente · defectos escapados por origen. | 4 gráficos + tabla de estadísticos descriptivos en `evaluation/pre-post-analysis/`. |
| **S09** | 26/10–01/11 | 4 | **BL-01 — Nota de línea de base.** Consolidar hallazgos. **Capítulo 4 (borrador).** Envío a Marcos. | BL-01 escrito. Contiene el número que va al pitch (ej.: "diffs de N líneas de origen agéntico aprobados en T segundos, sin comentarios, en el X % de los casos"). ✅ **Checkpoint con tutor.** |

### FASE 2 — A1 · Taxonomía de riesgos del desarrollo agentizado · S10–S13 · 28 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S10** | 02–08/11 | 8 | Barrido sistemático del corpus: OWASP Top 10 LLM + guías agénticas · NIST AI 600-1 y SP 800-218A · ISO/IEC 23894 · papers 2023–2026 según `kb/literature/estrategia-bibliografica-y-vigilancia.md`. Fichado con la plantilla existente. | **≥ 25 riesgos candidatos** fichados con fuente verificada. |
| **S11** | 09–15/11 | 8 | Estructura de la taxonomía: ejes **fase del SDLC × mecanismo × actor afectado**. Depuración de solapamientos y duplicados. | Estructura de 2 niveles cerrada y justificada. Cada riesgo tiene exactamente un lugar. |
| **S12** | 16–22/11 | 6 | **El aporte (SP1): riesgos propios** derivados de IS-01 y BL-01 que las taxonomías vigentes no cubren. Candidatos: degradación silenciosa de la revisión por volumen; falsa independencia entre agentes homogéneos; pérdida de contexto de seguridad en pases de mano; evidencia emitida pero no reconciliable. | **≥ 4 riesgos** marcados como "no cubiertos por taxonomías vigentes", cada uno con justificación de por qué no está en OWASP/NIST/ISO. |
| **S13** | 23–29/11 | 6 | Mapeo A1 → controles ISO/IEC 42001 Anexo A y 27002. **Capítulo 5 (borrador).** | A1 v1.0 congelado. Capítulo 5 borrador. ✅ **Checkpoint con tutor.** |

### FASE 3 — A0 · Criterios de gobernabilidad de topologías · S14–S17 · 28 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S14** | 30/11–06/12 | 8 | Modelado de topologías de referencia: monolítica · cadena secuencial · supervisor-worker · revisión cruzada entre pares. Ubicación de las **costuras** (puntos donde un humano puede insertarse y donde la evidencia tiene frontera natural). | 4 topologías diagramadas, con costuras marcadas y contadas en cada una. |
| **S15** | 07–13/12 | 8 | **Derivación de los criterios** (criterios, no ranking — ver delimitación §5.2 de `kb/context.md`): observabilidad de la costura · independencia real del revisor · granularidad del pase de mano · reversibilidad · atribuibilidad del cambio. | **≥ 5 criterios**, cada uno con: enunciado, pregunta de test aplicable, y un ejemplo concreto de topología que lo viola. |
| **S16** | 14–20/12 | 8 | **Aplicación de A0 al pipeline real** (sobre IS-01): diagnóstico de gobernabilidad de la topología que existe hoy. | Informe de aplicación. Identifica **al menos una costura que hoy no existe** y qué se perdió por no tenerla. |
| **S17** | 21–27/12 | 4 | Cierre A0 v1.0 + **Capítulo 6 (borrador).** | A0 v1.0. ✅ **Checkpoint con tutor antes del receso.** |

### 🧊 RECESO DECLARADO — S18–S19 · 28/12/2026 – 10/01/2027 · 0 h

> No es un hueco: es planificación. Un cronograma que asume 8 h/semana durante el receso de verano argentino no es un cronograma, es una declaración de intenciones.

### FASE 4 — A2 · Matriz Autonomía × Control · S20–S22 · 24 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S20** | 11–17/01 | 8 | **Definición operacional de A0–A4:** cuál es el observable que distingue un nivel del siguiente (SP2). ➕ **Convocatoria del Panel Delphi:** invitaciones a auditores ISO 27001/42001, tech leads e investigadores. | Reglas de clasificación aplicables sin criterio subjetivo. **≥ 12 invitaciones enviadas** para asegurar 8 confirmaciones. |
| **S21** | 18–24/01 | 8 | Controles obligatorios y **evidencia mínima por nivel** (SP3). Mapeo celda → control de ISO 42001 Anexo A / 27002. | Matriz completa: 5 niveles × (control humano, controles automáticos, evidencia obligatoria, firma indelegable). |
| **S22** | 25–31/01 | 8 | **Clasificación de los agentes de IS-01 en la matriz → la brecha declarado vs. real.** Este es el número que hace visible el problema. **Capítulo 7 (borrador).** | A2 v1.0. Cada agente de IS-01 con nivel asignado, controles exigidos y **brecha calculada** contra los controles que realmente tiene. |

### FASE 5 — A3 · Telemetría, motor de conformidad y tablero · S23–S25, S27–S29 · 44 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S23** | 01–07/02 | 8 | **Esquema de evidencia** (*trace schema*): campos mínimos por nivel A0–A4 — agente, versión de modelo, prompt de sistema, diffs intermedios, nivel asignado, controles ejecutados, firma, retención. | Schema versionado en `src/collector/`. Cada campo justificado contra una celda de A2. |
| **S24** | 08–14/02 | 8 | **Collector:** emisión de trazas desde CI/CD + reconciliación determinística contra Git. | `trace.json` emitido en **≥ 10 ejecuciones reales**. GDR (C2) medido por primera vez. |
| **S25** | 15–21/02 | 6 | 📡 **T0 — Instrumentación silenciosa activa (15/02).** Telemetría pasiva, sin gates, sin cambio de política: no contamina la ventana PRE. ➕ **Preparación del pitch** (deck + demo). | T0 corriendo. Deck de 12 slides + demo ensayada cronometrada. |
| **S26** | 22–28/02 | 4 | 🎯 **HITO 3 — Pitch de Tesis (23/02/2027).** Estructura: problema → claim → **BL-01 en gráficos** → los 4 artefactos → calibración ADR-005 → plan de validación y cronograma a defensa. | 🎯 Pitch defendido. Feedback del tribunal registrado en `kb/` como insumo de F6/F7. |
| **S27** | 01–07/03 | 8 | **Conformance Engine:** evalúa la traza contra la política A2 y bloquea o marca según nivel. | Motor corriendo en el pipeline. **5 casos de prueba** pasan/fallan exactamente como se predijo. |
| **S28** | 08–14/03 | 8 | **Tablero de KRIs** (HIR, CRS, ACI, GDR — ver `evaluation/hive-calibration/README.md`) + **calibración de gates**: curva FP/FN sobre *golden dataset* para evitar *bypass fatigue*. | Tablero operativo. Umbrales de gates **congelados y documentados** con su curva. |
| **S29** | 15–21/03 | 6 | 🚦 **T1 — INTERVENCIÓN PLENA (15/03). Abre la ventana POST.** ➕ **Testbench ADR-005:** role boundary adherence, context drift, reconciliación de traza, fault injection. **Capítulo 8 (borrador).** | 🚦 A2 activa, gates gobernados, evidencia obligatoria. Los **4 ejes de ADR-005** con resultado medido. |

### FASE 6 — Validación externa y reconstruction test PRE · S30–S33 · 32 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S30** | 22–28/03 | 8 | **Diseño del instrumento Delphi** (ronda 1): relevancia, completitud y aplicabilidad de A0/A1/A2/A3 en escala 1–5 + campos abiertos. Envío. | Instrumento revisado por el tutor. **Ronda 1 enviada a 8 expertos**, con fecha de corte **11/04**. |
| **S31** | 29/03–04/04 | 6 | Seguimiento de ronda 1 ➕ **Protocolo RT-01 del reconstruction test:** muestreo aleatorio, cegado, rúbrica de las 4 dimensiones de C1, **reclutamiento del auditor externo**. | RT-01 escrito y congelado. **Auditor externo confirmado** (no la autora — mitigación #2 del doble rol). |
| **S32** | 05–11/04 | 8 | Análisis de ronda 1 + construcción de ronda 2 con feedback controlado. | Ronda 2 enviada, corte **25/04**. |
| **S33** | 12–18/04 | 10 | **Reconstruction test PRE:** 20 PRs aleatorios de la ventana pre, auditoría ciega con rúbrica RT-01. | **TRD_pre medido**, con intervalo de confianza y desacuerdos documentados. |

### FASE 7 — Medición post y análisis pre/post · S34–S37 · 28 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S34** | 19–25/04 | 8 | Cierre de ronda 2 Delphi + análisis de consenso (IQR ≤ 1). ⚠️ **25/04 — Checkpoint del N post:** verificar que la ventana alcanzó **60 PRs**; si no, extender consumiendo reserva. | Informe Delphi v1: % de ítems con consenso → **veredicto de C5**. Decisión sobre el N documentada. |
| **S35** | 26/04–02/05 | 8 | **Reconstruction test POST:** 20 PRs de la ventana post, **mismo auditor, misma rúbrica, mismo cegado**. | **TRD_post medido.** Aquí se resuelve C1 — el claim se sostiene o se cae. |
| **S36** | 03–09/05 | 6 | Análisis pre/post completo: C1 (TRD) · C2 (GDR) · C3 (profundidad de revisión) · C4 (guardrail DORA). Pruebas estadísticas y tamaño del efecto. | Tabla de resultados **contra los umbrales pre-registrados de §0.1**, con **veredicto explícito por criterio**, incluido el negativo si lo hay. |
| **S37** | 10–16/05 | 6 | **Capítulo 9 (resultados)** + incorporación del feedback Delphi a los artefactos → **A0–A3 v2**. | Capítulo 9 borrador. Artefactos v2 con changelog de qué cambió por el panel. |

### FASE 8 — Consolidación de la memoria · S38–S40 · 46 h

| Sem | Fechas | h | Foco y tareas | Definición de HECHO |
|---|---|--:|---|---|
| **S38** | 17–23/05 | 14 | Consolidación de capítulos 1–3 (introducción, estado del arte, metodología) desde el Plan de Trabajo + vigilancia bibliográfica acumulada. **Capítulo 10** (discusión, limitaciones, trabajo futuro). | Capítulos 1–3 y 10 en versión integrada. Limitaciones incluye explícitamente el caso único y el doble rol. |
| **S39** | 24–30/05 | 16 | Integración total del documento: coherencia entre capítulos, unificación terminológica, verificación de **cada referencia contra la fuente original** (APA). Anexos: diario de investigación, ADRs, protocolos RT-01 y Delphi, código. | Documento único compilable. **Cero referencias sin verificar.** |
| **S40** | 31/05–06/06 | 16 | Revisión final, corrección de estilo, envío a Marcos con margen. Preparación de la defensa. | ✅ **Borrador completo de la memoria entregado al tutor.** |

### Junio–Julio 2027 — Defensa

| Período | Actividad | Horas |
|---|---|---|
| S41–S43 (07/06–27/06) | Incorporación de correcciones del tutor · preparación del deck de defensa · ensayos | Reserva |
| Jun–Jul 2027 | 🏁 **HITO 4 — Defensa Final ante el tribunal** | — |

---

## 5. Dependencias críticas

| # | Dependencia | Vence | Impacto si falla |
|---|---|---|---|
| D1 | Export histórico de PRs pedido y recibido | Pedido S04 (27/09) · Recibido 09/10 | Sin BL-01 no hay ventana pre → se cae C1 y C3. Activa Plan B. |
| D2 | IS-01 completo | S06 (11/10) | Sin inventario no hay A2 aplicable ni brecha declarado-vs-real. **No depende de terceros.** |
| D3 | Invitaciones Delphi enviadas | S20 (17/01) | Enviar en marzo es tarde; los expertos no responden con 2 semanas de aviso. |
| D4 | Collector emitiendo trazas | S24 (14/02) | Sin collector no hay T0 ni T1 → no hay ventana post. |
| D5 | Intervención T1 activa | 15/03/2027 | Cada semana de retraso acorta la ventana post 1:1. Piso absoluto: **29/03** (deja 7 semanas). |
| D6 | Auditor externo confirmado | S31 (04/04) | Sin auditor externo, el reconstruction test lo hace la autora → se cae la mitigación del doble rol. |
| D7 | N post ≥ 60 PRs | 25/04/2027 | Bajo poder estadístico. Trigger declarado de extensión de ventana. |

---

## 6. Riesgos y plan B

| Riesgo | Prob. | Impacto | Trigger | Mitigación operativa |
|---|:---:|:---:|---|---|
| **No llegan los datos históricos de PRs** | 🟡 Media | 🔴 Alto | 09/10/2026 sin export | **Plan B:** el eje empírico pasa a IS-01 + reconstruction test solo sobre la ventana post + peso mayor al Delphi. C1 se reformula como TRD absoluto post con auditoría de los PRs pre reconstruibles desde Git crudo. Ya previsto en §15 de `kb/context.md`. |
| **La intervención T1 se corre** | 🟡 Media | 🔴 Alto | 29/03/2027 sin T1 | La autora controla el despliegue (respuesta del 28/08). Mitigación: T1 mínimo viable = matriz A2 + evidencia obligatoria, aunque el tablero quede incompleto. El tablero no es condición de la medición. |
| **N post insuficiente** | 🟡 Media | 🟠 Medio | 25/04/2027 < 60 PRs | Extender ventana hasta el 09/05 consumiendo reserva; comprimir S36–S37. |
| **Panel Delphi con respuesta baja** | 🟡 Media | 🟠 Medio | 11/04 con < 6 respuestas | Se invitan 12 para asegurar 8. Fallback: ronda única + entrevistas semiestructuradas individuales. |
| **Cuestionamiento por doble rol** | 🟢 Alta pero prevista | 🟠 Medio | Permanente | Las 4 mitigaciones de §8.1 operacionalizadas con fecha: criterios pre-registrados (S01) · auditor externo (S31) · triangulación (IS-01 + PRs + entrevistas) · diario de investigación (continuo, anexo). |
| **Deriva hacia desarrollo de producto** | 🟡 Media | 🟠 Medio | Permanente | ADR-004. Techo duro de 44 h en A3. Si A3 excede presupuesto, se recorta funcionalidad del tablero, nunca la calibración. |
| **Deriva hacia benchmark de herramientas** | 🟢 Baja | 🟠 Medio | Permanente | Regla escrita: criterios, no rankings (§5.2). Un ranking vence en 6 meses; la defensa es en 2027. |
| **Redacción comprimida al final** | 🟢 Baja | 🔴 Alto | Cualquier capítulo sin borrador en su semana | Mapeo artefacto→capítulo de §3. Un capítulo sin borrador en su fase es una alarma, no un atraso menor. |

---

## 7. Cadencia de seguimiento

| Ritual | Frecuencia | Salida |
|---|---|---|
| **Checkpoint con tutor** | Fin de cada fase (S09, S13, S17, S22, S29, S34, S37, S40) | Artefacto vN + una página de estado |
| **Registro en el diario de investigación** | Semanal | Entrada fechada separando rol ingeniera / rol investigadora (anexo de la memoria) |
| **Vigilancia bibliográfica** | Mensual, 1 h de la reserva | Fichas nuevas en `kb/literature/` |
| **Revisión del presupuesto de horas** | Fin de cada fase | Horas reales vs. planificadas; consumo de reserva declarado |
| **Compuerta de re-calibración trimestral (ADR-005)** | Trimestral / ante cambio de LLM | Auditoría de detección sobre *golden dataset* y reporte de re-certificación de autonomía |
