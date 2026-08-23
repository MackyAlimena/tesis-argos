# Catálogo de Agentes de IA — Laboratorio IV (2026)

> **Documento de Referencia de Cátedra e Investigación**  
> **Autor:** Marcos Giagnorio (`mgiagnorio@austral.edu.ar`) — Tutor Académico de Tesis ARGOS  
> **Ámbito:** Facultad de Ingeniería, Universidad Austral  
> **Base conceptual:** DORA Report 2025, Thoughtworks Tech Radar Vol. 33, PMBOK 8, Gartner/McKinsey 2026, Surveys arXiv (2024–2026) y ecosistema de herramientas agénticas (Claude Code, GitHub Copilot, Atlassian Rovo, Apache DevLake, Playwright, Semgrep, Snyk, etc.).

---

## 🧭 Principio Rector y Modelo de Responsabilidad

> **La industria convergió en agentes *revisores/verificadores* con humano en el loop, más que en agentes que escriben código autónomamente. El rol humano define especificaciones, políticas, checklists y contexto; el agente verifica y reporta. La responsabilidad nunca se delega (PMBOK 8, modelo asignar vs. delegar de Linear).**

---

## 🏛️ DOMINIO A — GESTIÓN DEL PROYECTO

### 1. Planificación y estimación (PM / PO)

| # | Agente | Qué hace | Referencia del estado del arte |
|---|---|---|---|
| 1.1 | **Sprint Planner** | Propone el contenido del sprint: dependencias entre historias, balance de carga vs. velocity histórica. | Atlassian Rovo "Agents in Jira" (GA 2026) |
| 1.2 | **Estimador por analogía** | Sugiere story points comparando contra historias ya completadas, con justificación (planning poker con agente). | arXiv 2509.14483 (multi-agent effort estimation) |
| 1.3 | **Capacity Planner** | Cruza disponibilidad real (exámenes, ausencias), skills y velocity; simula escenarios what-if. | Epicflow |
| 1.4 | **Detector de scope creep** | Clasifica cada pedido entrante como in/out of scope y acumula el impacto sobre el sprint. | Dart AI, Supernormal |
| 1.5 | **Backlog Groomer** | Detecta duplicados, tickets sin detalle, prioriza con RICE/WSJF/MoSCoW. | Rovo "Issue Organizer" |
| 1.6 | **Descomponedor de épicas** | Convierte una épica en user stories con acceptance criteria listos para refinar. | Rovo "Work Item Planner", ClickUp Brain |

### 2. Riesgos, issues y blockers ★ (PM)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 2.1 | **Identificador proactivo de riesgos ★** | Genera y mantiene el risk register (probabilidad, impacto, mitigación), re-puntúa cada sprint. | programme-risk-ai (GitHub, open source) |
| 2.2 | **Detector temprano de blockers ★** | Analiza señales: tickets "In Progress" sin commits en N días, PRs sin review >48h, ítems que rebotan de estado. | LinearB, Swarmia signals |
| 2.3 | **Early warning de sprint** | Recalcula a diario la probabilidad de completar el sprint y alerta antes de la mitad. | ClickUp "Deadline Guardian" |
| 2.4 | **Detector de sobrecarga del equipo** | Señales de burnout: commits nocturnos, rework creciente, caída de participación (señal, no diagnóstico). | Swarmia, TeamRetro sentiment |

### 3. Monitoreo y métricas ★ (PM / TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 3.1 | **Analista DORA sobre DevLake ★** | Interpreta los dashboards de DevLake (deployment frequency, lead time, CFR, MTTR) y redacta el análisis mensual. | Apache DevLake + Grafana |
| 3.2 | **Burndown/velocity predictivo** | Proyecta la fecha de entrega considerando cambios de composición del equipo. | Agile36, Devoteam |
| 3.3 | **Agente EVM ★** | Calcula PV/EV/AC, CPI/SPI y EAC por entrega de 4 semanas; explica variancias en lenguaje natural (costos con tarifas ficticias por rol). | Galorath SEERai, TrueProject |
| 3.4 | **Sprint Health semáforo** | Consolida diario: burndown, WIP, blockers, PRs viejos, scope changes → resumen a Discord/Slack. | Monday "Project Analyzer" |
| 3.5 | **Benchmarking entre equipos ★** | Compara DORA/velocity/carry-over entre equipos y sugiere prácticas del mejor equipo. | DevLake benchmarks, Jellyfish |

### 4. Comunicación y reporting ★ (PM / PO)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 4.1 | **Status Reporter semanal ★** | Genera el informe (avance, riesgos, RAG status) desde la actividad real en Jira+GitHub+Discord, con tono según audiencia. | Rovo (caso de uso #1 para PMs) |
| 4.2 | **Resumidor de standups ★** | Recolecta respuestas asíncronas en Discord/Slack, extrae blockers y action items. | Troopr, DailyBot, Geekbot |
| 4.3 | **Minutas y action items** | Transcribe reuniones, extrae decisiones/compromisos y los rutea a tickets. | Fireflies, Otter, Fathom |
| 4.4 | **Preparador de Steering ★** | Minutas previas + métricas + status report → borrador del deck mensual (avance, demo, riesgos, decisiones requeridas). | Workflow notes→slides |
| 4.5 | **Escalador con SLA** | Detecta blockers que superan el SLA y redacta el escalamiento con contexto y evidencia. | Asana AI Teammates |
| 4.6 | **Redactor de release notes** | Agrupa los work items del incremento y redacta notas en versión técnica y de negocio. | Rovo "Release Notes Drafter", GitHub |
| 4.7 | **Documentador de progreso semanal ★** | Compila evidencia del sprint (PRs, decisiones, deuda, burndown) en el reporte obligatorio. | Compuesto |

### 5. Proceso y calidad de gestión ★ (PO / QA)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 5.1 | **Definition of Ready checker** | Verifica claridad, criterios, estimación y dependencias antes de que la historia entre al sprint. | Rovo "Readiness Checker" |
| 5.2 | **Definition of Done checker ★** | Antes de cerrar un ticket: PR mergeada, tests verdes, doc actualizada, deploy a staging, AC cumplidos. | ClickUp "Quality Checker" |
| 5.3 | **Facilitador de retros** | Agrupa feedback por temas, detecta patrones recurrentes ("esto salió 3 sprints seguidos"), propone experimentos. | TeamRetro, Parabol |
| 5.4 | **Perseguidor de action items** | Consolida compromisos de retros/steerings, persigue responsables, reporta % de cumplimiento. | Fireflies + Jira |
| 5.5 | **Auditor de higiene de Jira** | Tickets sin estimación, sin épica, descripciones vacías → notifica al responsable. | Rovo Issue Organizer |

---

## 🛠️ DOMINIO B — INGENIERÍA

### 6. Requerimientos y especificación (SDD) ★ (PO / TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 6.1 | **Spec-driven development ★** | Feature → `requirements.md` + `design.md` + `tasks.md` versionados, revisados antes de codificar. | GitHub Spec Kit, Kiro (AWS), OpenSpec |
| 6.2 | **Traductor a EARS** | Reescribe requisitos vagos en sintaxis verificable *"WHEN… THE SYSTEM SHALL…"*. | Kiro specs |
| 6.3 | **Auditor INVEST de historias** | Evalúa cada historia contra criterios INVEST y propone la reescritura. | Caso Austrian Post (XP paper) |
| 6.4 | **Generador de acceptance criteria ★** | User story → escenarios Gherkin (*Given/When/Then*) incluyendo casos borde y de error. | Jira AI, StoriesOnBoard |
| 6.5 | **Detector de ambigüedades** | Informe de ambigüedades, contradicciones entre historias y preguntas de clarificación para el PO. | arXiv 2409.00038 |
| 6.6 | **Matriz de trazabilidad** | Por cada AC: qué PR lo implementa y qué test lo verifica; alerta historias huérfanas. | Promesa central de SDD (Tessl, Kiro) |

### 7. Arquitectura y diseño ★ (TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 7.1 | **Redactor de ADRs ★** | Detecta decisiones que alteran límites del sistema y redacta el ADR (formato MADR); el humano decide. | Práctica documentada Codex/Claude |
| 7.2 | **Diagramador C4/Mermaid ★** | Regenera diagramas de contexto/contenedores/componentes desde el repo en cada cambio. | C4 plugin Claude Code, GitDiagram |
| 7.3 | **Detector de drift arquitectónico** | Compara arquitectura declarada (ADRs/C4) vs. real en cada PR; reporta violaciones de capas. | Archyl, ArchSteer |
| 7.4 | **Design reviewer** | Evalúa el design doc antes de implementar: acoplamiento, SPOF, escalabilidad, alternativas. | Patrón "arquitecto senior" |
| 7.5 | **Guardián de convenciones** | Mantiene `AGENTS.md` / `CLAUDE.md` con estructura, patrones y naming del proyecto como contexto compartido. | Thoughtworks: context engineering |

### 8. Calidad de código — revisión, no escritura (TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 8.1 | **Code reviewer de PRs** | Comenta bugs, estilo y resumen de cada PR. | CodeRabbit, Greptile, Qodo, Copilot review |
| 8.2 | **Detector de regresiones cross-file** | Con contexto del repo completo detecta que un cambio rompe un contrato en otro módulo. | Greptile (~82% detección) |
| 8.3 | **Auditor de deuda técnica** | Escaneo periódico: duplicación, funciones largas, TODOs viejos → backlog de refactoring priorizado. | SonarQube AI CodeFix, CodeScene |
| 8.4 | **Linter semántico del equipo** | Revisa PRs contra convenciones propias que ningún linter estático cubre. | CodeRabbit path instructions, CLAUDE.md |
| 8.5 | **Traductor de PRs a negocio** | Cada PR en lenguaje de negocio: qué historia implementa, riesgo, qué probar. | Especialización de resúmenes de PR |

### 9. Testing y QA ★ (QA / TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 9.1 | **Generador de unit tests ★** | Genera suites con casos borde y las ejecuta hasta que pasen. | Diffblue Cover (81% cobertura en benchmark) |
| 9.2 | **Agentes E2E Playwright ★** | Trío oficial: planner (explora la app y arma plan), generator (plan → código), healer (repara tests rotos). | Playwright v1.56 test agents |
| 9.3 | **Mutation tester** | Introduce mutantes y genera tests para los que sobreviven. | Mutahunter, arXiv 2602.08146 |
| 9.4 | **QA explorador autónomo** | Recorre la app como usuario y detecta roturas de regresión ★. | Harness AI Test Automation, QA Wolf |
| 9.5 | **Generador de guiones UAT ★** | AC → script UAT paso a paso en lenguaje natural + acta de aceptación para el steering. | Nicho sin producto dominante |

### 10. Seguridad y hardening ★ (TL / QA)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 10.1 | **SAST con triage** | Corre Semgrep/CodeQL en el pipeline, filtra falsos positivos, propone el fix. | Semgrep Assistant (vía MCP), Copilot Autofix |
| 10.2 | **Threat modeler STRIDE** | Describe la app → modelo de amenazas, árboles de ataque, scoring y mitigaciones. | STRIDE GPT (open source) |
| 10.3 | **Cazador de secretos** | Detecta credenciales antes del commit (hook en el repo del equipo). | Gitleaks, TruffleHog, GitGuardian |
| 10.4 | **Vigía de dependencias** | Monitorea `package.json`/`pom.xml`, abre PRs de upgrade priorizados por alcanzabilidad. | Snyk, Dependabot, Renovate |
| 10.5 | **Checklist OWASP por feature ★** | Para historias sensibles (login, upload) genera checklist ASVS y verifica el PR contra él. | Patrón `/security-review` |

### 11. Datos y performance ★ (TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 11.1 | **Generador de datos mock ★** | Datasets realistas con consistencia referencial para test y demos. | Tonic Fabricate, NeMo Data Designer, Faker |
| 11.2 | **Optimizador de queries ★** | Query + esquema + EXPLAIN → antipatrones, reescritura y recomendación de índices. | EverSQL, pganalyze |
| 11.3 | **Asesor de índices** | Analiza queries lentas del log y propone índices con costo/beneficio. | pganalyze Index Advisor |
| 11.4 | **Revisor de performance en PRs** | Detecta N+1, queries en loops, payloads grandes en el diff. | CodeRabbit, Greptile |
| 11.5 | **Analista de carga** | Ejecuta smoke test k6, lee resultados y reporta cuellos de botella priorizados. | k6 MCP, Grafana MCP |

### 12. DevOps / CI-CD / Infra ★ (TL)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 12.1 | **Doctor de pipelines ★** | Build roto → lee logs, identifica causa raíz (flaky, timeout, dependencia) y comenta el fix. | Saturnhead AI, patrón "ci-doctor" |
| 12.2 | **Revisor de Terraform ★** | Revisa planes IaC contra políticas de seguridad y costos (~55% de IaC generado por IA es seguro). | Gomboc AI, Terraform MCP oficial |
| 12.3 | **SRE de incidentes** | Ante una falla correlaciona logs, métricas y deploys recientes; propone causa raíz. | Datadog Bits AI, Cleric (read-only) |
| 12.4 | **Checklist pre-deploy** | CI verde, migraciones revisadas, flags configurados, rollback documentado → o bloquea. | Hooks de Claude Code |
| 12.5 | **Verificador post-deploy** | Compara métricas pre/post release y recomienda continuar o revertir. | Harness AI Verification/Rollback |

### 13. Documentación, onboarding y conocimiento ★ (TL / PO)

| # | Agente | Qué hace | Referencia |
|---|---|---|---|
| 13.1 | **Docs vivas acopladas al código** | Si una función o path cambia, el doc "falla" antes del merge y se propone la actualización. | Swimm |
| 13.2 | **API docs desde OpenAPI** | Genera y mantiene la referencia de API navegable. | Mintlify, ReadMe |
| 13.3 | **Onboarding de repo ★** | README + guía del primer día para integrantes nuevos. | `/init` de Claude Code, DeepWiki |
| 13.4 | **Tutor del proyecto ★** | Responde preguntas citando la doc; descarga al TL de mentoring repetitivo. | Rovo, Glean, Notion AI |
| 13.5 | **Generador de runbooks** | Conocimiento tribal → runbook paso a paso. | Skill `operations:runbook` |
| 13.6 | **Lecciones aprendidas inter-equipos ★** | Destila retros/incidentes/decisiones en repositorio consultable por todos los equipos. | Rovo Lessons Learned Agent |

---

## 🎛️ DOMINIO C — META (Agentes sobre agentes: Gobernanza y Supervisión)

> ⭐️ **Vínculo directo con la Tesis ARGOS:** Este dominio formaliza la necesidad de un sistema de control y auditoría automatizado.

| # | Agente | Qué hace | Referencia / Vínculo ARGOS |
|---|---|---|---|
| 14.1 | **Auditor de agentes** | Registra qué acciones tomaron los agentes del equipo, verifica permisos, produce log auditable para el steering. | **ARGOS A3:** Recolector de telemetría y audit trail fidelity (PMBOK 8 / Linear model). |
| 14.2 | **Evaluador de agentes** | Corre la suite de evals de cada agente en CI y bloquea el merge ante regresiones. | **ARGOS A3 + ADR-005:** *Governance Gatekeeper* y banco de calibración. |
| 14.3 | **Curador de contexto** | Mantiene `AGENTS.md`/`CLAUDE.md` del repo actualizado para que todos los agentes trabajen con el mismo contexto. | **ARGOS A0:** Topología, fronteras de rol y prevención de context drift. |

---

## 📚 Fuentes Principales del Estado del Arte

* **DORA 2025 State of AI-assisted Software Development** — [https://dora.dev/dora-report-2025/](https://dora.dev/dora-report-2025/) *(La IA amplifica: mejora equipos maduros, degrada los disfuncionales).*
* **Thoughtworks Technology Radar Vol. 33** — *Spec-Driven Development (SDD), context engineering, MCP.*
* **PMI: AI in PM Global Report 2025 / PMBOK 8 / PMI Infinity** — [https://www.pmi.org/infinity](https://www.pmi.org/infinity)
* **Gartner (2026–2027)** — *40% de apps empresariales con agentes para fin de 2026; >40% de proyectos agénticos cancelados para 2027 por falta de gobernanza.*
* **GitHub Spec Kit & Kiro (AWS)** — [https://github.com/github/spec-kit](https://github.com/github/spec-kit) · [https://kiro.dev](https://kiro.dev/)
* **Apache DevLake** — [https://devlake.apache.org/docs/DORA/](https://devlake.apache.org/docs/DORA/)
* **Playwright test agents** — [https://playwright.dev/docs/test-agents](https://playwright.dev/docs/test-agents)
* **STRIDE GPT** — [https://github.com/mrwadams/stride-gpt](https://github.com/mrwadams/stride-gpt)
* **AGENTS.md (Estándar)** — [https://agents.md](https://agents.md/)
* **Surveys Académicos Clave:**
  - *Multi-agent Software Engineering:* arXiv 2404.04834
  - *Evaluation of LLM-based Agents:* arXiv 2503.16416
  - *Agile Effort Estimation with Multi-Agent Systems:* arXiv 2509.14483
