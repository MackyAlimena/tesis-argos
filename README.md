# ARGOS: Autonomous Risk & Governance Oversight for Software

> **Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional.**

**Trabajo de Grado — Ingeniería en Informática (Orientación Gestión)**  
**Universidad Austral** · Facultad de Ingeniería  
**Alumna:** Macarena Alimena  
**Tutor Académico:** Marcos Giagnorio  
**Entrega Final:** Junio–Julio 2027  

---

## El Problema y la Apuesta (Claim)

### El Gap
Los marcos vigentes de gobernanza de IA (*ISO/IEC 42001, NIST AI RMF, EU AI Act*) fueron diseñados para gobernar la IA **como producto**. Cuando la IA agéntica entra al **proceso de desarrollo de software**, se desplaza el objeto gobernado y el riesgo se propaga a todo el software entregado por la organización, incluso a sistemas que no contienen IA.

Hoy, la supervisión humana (*Human-in-the-Loop*) en los pipelines de desarrollo se degrada en silencio: el volumen y velocidad de cambios generados por agentes satura la capacidad humana de revisión, convirtiendo la aprobación en un simple sello de goma administrativo (*rubber stamping*).

### El Claim
> **La supervisión humana solo es real si es verificable. Todo nivel de autonomía delegado a un agente de software debe contar con un nivel de evidencia proporcional que permita reconstruir *ex post* quién decidió qué. Sin evidencia proporcional, el HITL opera como una ficción de cumplimiento.**

---

## Por dónde empezar

### Onboarding asistido (recomendado)

Si acabás de clonar el repo y usás un agente de IA (Claude Code, Antigravity, Cursor, Codex), no hace falta que
leas todo a mano: hay dos onboardings guiados que te llevan por el argumento, las decisiones ya tomadas y lo que
está abierto, en ~15 minutos.

| Si sos… | En Claude Code | En cualquier otro agente | A mano |
|---|---|---|---|
| **Tutor académico / director** | `/onboarding-tutor` | *"seguí `docs/onboarding/tutor.md`"* | [`docs/onboarding/tutor.md`](docs/onboarding/tutor.md) |
| **Colaborador externo, revisor o auditor** | `/onboarding-externo` | *"seguí `docs/onboarding/externo.md`"* | [`docs/onboarding/externo.md`](docs/onboarding/externo.md) |

Las reglas del repo que cualquier agente debe respetar están en [`AGENTS.md`](AGENTS.md).

### A mano

Si es tu primera vez en este repo, leé en este orden. Todo lo demás cuelga de estos cuatro documentos.

| # | Documento | Qué vas a encontrar |
|---|---|---|
| 1 | **Este README** | El gap, el claim y los cuatro artefactos. La versión corta del argumento. |
| 2 | [`kb/context.md`](kb/context.md) | **El documento maestro.** Título, problema, objetivos, alcance, metodología, riesgos y bibliografía preliminar. Es un *working doc*: se actualiza, no se archiva. |
| 3 | [`ROADMAP.md`](ROADMAP.md) | Cronograma operativo semana por semana (S01→S40), parámetros congelados, criterios de éxito pre-registrados (C1–C5) y checkpoints con tutor. Versión navegable: [`roadmap.html`](roadmap.html). |
| 4 | [`kb/adrs/`](kb/adrs/) | Las seis decisiones estructurales ya tomadas y **por qué**. Si algo del diseño te resulta raro, la explicación está acá antes de que preguntes. |

**Entregables formales, si querés ver el estado real:**
- [`docs/01-definicion-tema/`](docs/01-definicion-tema/) — Definición de tema (nombre, director, participantes).
- [`docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md`](docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md) — Plan de Trabajo formal. **Entrega 01/09/2026.**

---

## Research abierto: PENDIENTE DEFINICIÓN

Cuatro frentes donde el aporte externo mueve la aguja. Ordenados por urgencia.

| Prioridad | Frente | Qué hace falta | Dónde |
|---|---|---|---|
| 🔴 **Bloqueante** | **Verificación bibliográfica** | 10 referencias (B1–B10) entraron a la bibliografía preliminar sin verificar contra la fuente. Hay que confirmar autoría, año, sede y DOI — o **eliminarlas**, no reformularlas. B3, B6 y B7 son las más frágiles (falta autoría por completo). | [`docs/03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md`](docs/03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md) |
| 🟠 **Alta** | **Estado del arte / vigilancia** | Cubrir los venues del mapa (ICSE, FSE, ASE, MSR, CHI, FAccT, USENIX) buscando trabajo previo que ya resuelva el claim — o que lo contradiga. Toda ficha nueva usa la plantilla. | [`kb/literature/estrategia-bibliografica-y-vigilancia.md`](kb/literature/estrategia-bibliografica-y-vigilancia.md) · [`TEMPLATE-ficha-lectura.md`](kb/literature/TEMPLATE-ficha-lectura.md) |
| 🟠 **Alta** | **Mapeo normativo** | `kb/standards/` está vacío. Falta el mapeo de la taxonomía A1 y la matriz A2 contra ISO/IEC 42001 Anexo A, ISO/IEC 27002 y NIST SP 800-218A. Es lo que convierte a ARGOS en un perfil de implementación y no en un marco inventado. | [`kb/standards/`](kb/standards/) |
| 🟡 **Media** | **Cobertura del Catálogo Giagnorio (2026)** | Cruzar las 14 categorías del catálogo contra lo que ARGOS efectivamente gobierna: qué está cubierto, qué no, y qué se implementó sin decisión explícita. Insumo directo del capítulo 4. | [`kb/literature/catalogo-agentes-ia-giagnorio-2026.md`](kb/literature/catalogo-agentes-ia-giagnorio-2026.md) |

### Dónde el diseño es más atacable
Si vas a romper algo, empezá por acá — es donde más sirve el golpe:
- **Sesgo de doble rol.** La autora diseña el marco, lo implementa en su propia empresa y mide el resultado. Las mitigaciones están declaradas (parámetros congelados antes de medir, auditor externo y ciego, panel Delphi). ¿Alcanzan?
- **Caso único (n=1).** Una PyME. Los límites de generalización están en [`ADR-001`](kb/adrs/ADR-001-metodologia-dsr-y-caso-unico.md).
- **C1 como apuesta binaria.** El claim entero se sostiene o se cae contra un solo umbral: Δ ≥ 40 puntos de TRD. Ver [`ROADMAP.md`](ROADMAP.md) §0.1.
- **C2 con tolerancia cero.** Exigir 0 % de discrepancia entre `trace.json` y los eventos reales de Git/CI puede ser inalcanzable en la práctica.

### Cómo trabajamos el repo
- **Working docs** (`kb/`) se actualizan en su lugar; no se archivan versiones.
- **Toda decisión estructural va a un ADR** en `kb/adrs/`, numerado y con contexto, decisión y consecuencias.
- **Nada entra a la bibliografía sin verificar.** La tesis argumenta sobre evidencia verificable: una cita falsa acá no es un error de estilo, es una contradicción con el propio claim.
- **Checkpoints con tutor** al cierre de cada fase: S09, S13, S17, S22, S29, S34, S37 y S40. Ver [`ROADMAP.md`](ROADMAP.md) §7.

---

## Los Cuatro Artefactos de ARGOS

| # | Artefacto | Propósito |
|---|---|---|
| **A0** | **Criterios de Gobernabilidad de Topologías Agénticas** | Criterios arquitectónicos para estructurar enjambres de agentes de modo que existan costuras naturales de inspección humana. |
| **A1** | **Taxonomía de Riesgos del Desarrollo Agentizado** | Clasificación sistemática de amenazas específicas (alucinaciones de paquetes *slopsquatting*, fuga de contexto, degradación de revisión). |
| **A2** | **Matriz Autonomía × Control (Niveles A0–A4)** | Parametrización de compuertas y controles obligatorios según la libertad delegada al agente. |
| **A3** | **Modelo de Telemetría + Motor Evaluador de Conformidad + Tablero** | Recolector de trazas en CI/CD, *Governance Gatekeeper* automatizado y tablero de visualización de KRIs para la dirección. |
| **V** | **Validación Empírica (Pre/Post) + Panel Delphi** | Medición sobre caso de estudio real en PyME (*reconstruction tests* de PRs) y validación cualitativa externa. Nota: Me gustaría también armar un método de validación a nivel código (ej: mutación de código para ver si se detectan cada X tiempo) |

---

## 📂 Estructura del Repositorio

```text
.
├── README.md                      # Este documento (visión general, pitch y navegación)
├── ROADMAP.md                     # Cronograma operativo S01–S40, parámetros congelados y criterios C1–C5
├── roadmap.html                   # Misma información, versión navegable en el browser
├── AGENTS.md                      # Reglas del repo para agentes de IA (Claude, Antigravity, Cursor, Codex)
│
├── docs/                          # Entregables formales de la Universidad Austral
│   ├── onboarding/                # Onboardings guiados: tutor.md y externo.md
│   ├── templates/                 # Plantillas oficiales (Plan de Trabajo, Informe Ético)
│   ├── 01-definicion-tema/        # Definición formal de tema (nombre, director, participantes)
│   ├── 02-informe-etico/          # Informe Ético y Social (anclado en Magnifica Humanitas)
│   ├── 03-plan-de-trabajo/        # Plan de Trabajo formal + bibliografía pendiente de verificación
│   ├── 04-pitch-tesis/            # Pitch de Tesis — Hito 3 (23/02/2027): deck, demo, feedback
│   └── 05-tesis-final/            # Capítulos de la memoria de tesis (2027)
│
├── kb/                            # Base de Conocimiento y Gobernanza (Working Docs)
│   ├── context.md                 # Contexto maestro consolidado y decisiones
│   ├── literature/                # Fichas de lectura de literatura científica (2023–2026)
│   ├── standards/                 # Mapeo a normas (ISO 42001, ISO 27001, NIST AI)
│   └── adrs/                      # Architectural & Governance Decision Records
│
├── data/                          # Experimento y Línea de Base
│   ├── raw/                       # Dataset histórico anonimizado de PRs (Pre-intervención)
│   └── processed/                 # Métricas calculadas (tiempo de review, diffs, comentarios)
│
├── src/                           # Implementación Técnica de ARGOS (Artefacto A3)
│   ├── collector/                 # Recolector de trazas y eventos agénticos en CI/CD
│   ├── engine/                    # Motor de Evaluación de Conformidad (Governance Gatekeeper)
│   └── dashboard/                 # Tablero de control de gobernanza y KRIs
│
└── evaluation/                    # Validación del Método (DSR)
    ├── delphi/                    # Protocolo y resultados del Panel de Expertos
    ├── hive-calibration/          # Banco de pruebas y calibración del orquestador (ADR-005)
    ├── reconstruction-test/       # Pruebas de reconstrucción de decisiones sobre PRs
    └── pre-post-analysis/         # Scripts de análisis estadístico comparativo
```

---

## Marco Metodológico y Normativo

- **Método Científico:** Design Science Research (DSR — Peffers et al., Hevner et al.) + Investigación-Acción en Caso Único (Yin, Runeson & Höst).
- **Normas de Referencia:** ISO/IEC 42001:2023, ISO/IEC 27001:2022, NIST SP 800-218A (SSDF for GenAI), NIST AI 600-1.
- **Marco Ético Humanista:** Encíclica *Magnifica Humanitas* (León XIV, 2026) sobre la custodia de la persona humana frente al paradigma tecnocrático y la distinción entre elección algorítmica y decisión moral.

---

## Próximos Pasos Inmediatos

- [ ] Mail de aceptación de Director de Trabajo de Grado de parte de Marcos
- [ ] Presentación formal del Plan de Trabajo (**01/09/2026**) — ver [ROADMAP.md](ROADMAP.md) S01. Nota: ya cuento con un Borrador del Plan, el entregable debe ser leído y Firmado por Marcos.
- [ ] Redacción del Informe Ético y Social alineado a las 5 preguntas de la Facultad (entrega el 15/09/2026).
- [ ] Formalización de los Criterios de Gobernabilidad de Topologías (A0).
