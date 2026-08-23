# [BORRADOR] Estrategia de Bibliografía y Vigilancia Científica — ARGOS

> **Estado:** Borrador de Trabajo (Working Draft)  
> **Proyecto:** Trabajo de Grado — *Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional*  
> **Carrera:** Ingeniería en Informática (Orientación Gestión) · Universidad Austral  
> **Autora:** Macarena Alimena · **Tutor Académico:** Marcos Giagnorio  
> **Horizonte temporal:** Agosto 2026 – Julio 2027  

---

## 🎯 1. Objetivo del Sistema de Vigilancia

Establecer un mecanismo estructurado, escalable y sostenible para:
1. **Identificar de manera continua** la literatura científica relevante durante el ciclo de vida anual de la tesis (2026–2027).
2. **Evitar la infoxicación** mediante un protocolo riguroso de filtrado (*triage*) en tres niveles (*tiers*).
3. **Construir una base de conocimiento versionada** e integrada con el repositorio local (`kb/literature/`).
4. **Verificar la autenticidad, rigor y accesibilidad** de cada fuente antes de citarla en entregables oficiales.
5. **Blindar el estado del arte** ante las defensas intermedias (*Pitch* en febrero 2027) y final (junio–julio 2027).

---

## 🗺️ 2. Mapa de Sedes de Publicación (*Venues*)

La investigación de ARGOS cruza cuatro disciplinas clave:

```text
                                  MAPA DE VENUES ARGOS
  ┌─────────────────────────────────┬─────────────────────────────────┐
  │ 1. INGENIERÍA DE SOFTWARE (SE)  │ 2. IA, AGENTES Y MODELOS (AI)   │
  │ • ICSE (insignia de SE)         │ • ICLR (MetaGPT, SWE-bench)     │
  │ • FSE / ESEC-FSE                │ • ACL / EMNLP (evaluación LLM)  │
  │ • ASE (automatización y código) │ • AAAI / IJCAI                  │
  │ • MSR (minería de repos/PRs)    │ • AAMAS (sistemas multi-agente) │
  │ • Journals: TSE, TOSEM, EMSE    │ • Repositorio: arXiv (cs.SE/AI) │
  ├─────────────────────────────────┼─────────────────────────────────┤
  │ 3. SEGURIDAD Y AUDITORÍA        │ 4. FACTOR HUMANO Y GOBERNANZA   │
  │ • ACM CCS / USENIX Security     │ • ACM CHI / CSCW (HITL, sesgo)  │
  │ • IEEE S&P (Oakland) / NDSS     │ • ACM FAccT (accountability)    │
  │ • OWASP GenAI Security          │ • MIS Quarterly / JMIS (DSR)    │
  │ • NIST (SP 800-218A, AI RMF)    │ • ISO/IEC JTC 1/SC 42           │
  └─────────────────────────────────┴─────────────────────────────────┘
```

### 2.1. Ingeniería de Software (SE) & Minería de Repositorios
* **ICSE** (*IEEE/ACM International Conference on Software Engineering*): Conferencia cumbre de ingeniería de software.
* **FSE** (*ACM International Conference on the Foundations of Software Engineering*): Conferencia líder en fundamentos y avances empíricos.
* **ASE** (*IEEE/ACM International Conference on Automated Software Engineering*): Foco directo en generación, verificación y síntesis automatizada de código.
* **MSR** (*Mining Software Repositories*): **Eje metodológico clave** para estudios empíricos sobre PRs, telemetría de Git, tiempos de revisión y comportamiento de bots vs. humanos.
* **ISSTA** (*ACM International Symposium on Software Testing and Analysis*): Testing, QA y validación estática/dinámica.
* **Top Journals:**
  * *IEEE Transactions on Software Engineering (TSE)*
  * *ACM Transactions on Software Engineering and Methodology (TOSEM)*
  * *Empirical Software Engineering (EMSE)* — Journal predilecto para estudios de caso y validación empírica/DSR.
  * *IEEE Software* — Puente entre investigación y práctica industrial.

### 2.2. Inteligencia Artificial, LLMs y Sistemas Multi-Agente
* **ICLR** (*International Conference on Learning Representations*): Sede de papers fundacionales como *SWE-bench* y *MetaGPT*.
* **ACL / EMNLP / NAACL**: Razonamiento de modelos, evaluación agéntica y prompt engineering.
* **AAMAS** (*Autonomous Agents and Multiagent Systems*): Formalización de topologías agénticas, coordinación de enjambres y delegación.
* **arXiv Preprints:** Categorías `cs.SE` (Software Engineering), `cs.AI` (Artificial Intelligence), `cs.MA` (Multiagent Systems), `cs.CR` (Cryptography and Security).

### 2.3. Seguridad, Privacidad y Confianza
* **ACM CCS / USENIX Security / IEEE S&P / NDSS:** Papers de seguridad en LLM assistants (*Perry et al., 2023; Sandoval et al., 2023*), *slopsquatting*, contaminación de dependencias y fuga de secretos.
* **ACM FAccT** (*Fairness, Accountability, and Transparency*): Modelos de rendición de cuentas y trazabilidad algorítmica.

### 2.4. Gobernanza, Gestión de Sistemas de Información (IS) y Factor Humano
* **MIS Quarterly (MISQ) / JMIS / ISR:** Cuna de la metodología Design Science Research (Hevner, Peffers).
* **ACM CHI / CSCW:** Interacción humano-IA, *human-in-the-loop*, sesgo de automatización (*automation bias* / *rubber-stamping*) y fatiga de revisión.

### 2.5. Estándares y Reportes de Industria
* **Estándares:** ISO/IEC 42001:2023, ISO/IEC 27001:2022, ISO/IEC 23894:2023, ISO/IEC 5338:2023, NIST AI RMF 1.0 / AI 600-1, NIST SP 800-218 / 800-218A, EU AI Act (Reglamento UE 2024/1689).
* **Reportes:** DORA State of AI Report (Google Cloud), Thoughtworks Tech Radar, Gartner / McKinsey AI Governance Reports.

---

## 📡 3. Protocolo de Alertas y Vigilancia Continua

### 3.1. Alertas de Citación sobre Papers Semilla (Push)
Configurar en **Google Scholar** avisos para nuevos artículos que citen a los siguientes trabajos fundacionales (*Forward Snowballing*):

| Paper Semilla | Autores | Año | Eje en ARGOS | Enlace de Verificación |
|---|---|:---:|---|---|
| *SWE-bench: Can language models resolve real-world GitHub issues?* | Jiménez et al. | 2024 | Capacidad real de agentes en software | [arXiv:2310.06770](https://arxiv.org/abs/2310.06770) |
| *MetaGPT: Meta programming for a multi-agent collaborative framework* | Hong et al. | 2024 | Topologías multi-agente y coordinación | [arXiv:2308.00352](https://arxiv.org/abs/2308.00352) |
| *Do users write more insecure code with AI assistants?* | Perry et al. | 2023 | Riesgos de seguridad introducidos por IA | [arXiv:2211.03622](https://arxiv.org/abs/2211.03622) |
| *Lost at C: A user study on the security implications of LLM code assistants* | Sandoval et al. | 2023 | Degradación de revisión y confianza ciega | [USENIX Security 2023](https://www.usenix.org/conference/usenixsecurity23/presentation/sandoval) |
| *Moral crumple zones: Cautionary tales in human-robot interaction* | Elish, M. C. | 2019 | Brecha de responsabilidad e injusticia ética | [ESTS Journal Open Access](https://estsjournal.org/index.php/ests/article/view/260) |
| *Ironies of automation* | Bainbridge, L. | 1983 | Fundamento teórico de la degradación HITL | [DOI: 10.1016/0005-1098(83)90046-8](https://doi.org/10.1016/0005-1098(83)90046-8) |
| *Design science in information systems research* | Hevner et al. | 2004 | Marco metodológico DSR | [MIS Quarterly](https://scholar.google.com/scholar?q=Design+science+in+information+systems+research+Hevner) |

### 3.2. Literatura de Vanguardia (2025–2026) — Núcleo de Estado del Arte

| Paper / Reporte | Autores / Venue | Año | Aporte directo a ARGOS | Enlace / Fuente |
|---|---|:---:|---|---|
| *Autonomous Agent Frameworks for SE: A Systematic Survey & Taxonomy* | Otoum et al. (*IEEE Access*) | 2026 | Taxonomía de frameworks y arquitecturas de memoria/orquestación. | [IEEE Access](https://ieeexplore.ieee.org/) |
| *Multi-Agent Collaboration in Software Development* | He et al. (*ACM TOSEM*) | 2025/2026 | Evidencia empírica sobre especialización de agentes vs. monolitos. | [ACM Digital Library](https://dl.acm.org/) |
| *CooperBench: Benchmarking Multi-Agent Collaboration* | Benchmark (*arXiv:2601.09123*) | 2026 | Medición cuantitativa de pérdida de contexto (*context drift*) en pases de mano inter-agente (**base de A0**). | [arXiv:2601.09123](https://arxiv.org/abs/2601.09123) |
| *Does AI Code Review Lead to Code Changes?* | Empirical Study (*EMSE*) | 2026 | Tasa de adopción y fatiga de revisión humana en PRs generados por IA (**evidencia para el claim**). | [Springer EMSE](https://link.springer.com/) |
| *Evaluating LLMs for Code Review: False Positives & Reliance* | Empirical Study (*ACM TOSEM*) | 2025 | Falsos positivos en análisis semántico y justificación de compuertas determinísticas (**A3 / ADR-005**). | [arXiv:2502.11245](https://arxiv.org/abs/2502.11245) |
| *A Survey on Evaluation of LLM-based Autonomous Agents* | Zhang et al. (*arXiv:2503.16416*) | 2025 | Métricas y protocolos de evaluación y calibración de agentes (**ADR-005**). | [arXiv:2503.16416](https://arxiv.org/abs/2503.16416) |
| *Catálogo de Agentes de IA para Ingeniería y Gestión* | M. Giagnorio (*Univ. Austral*) | 2026 | Catálogo de referencia taxonómica (14 categorías, 3 dominios). | [catalogo-agentes.md](file:///home/macky/Projects/tesis/kb/literature/catalogo-agentes-ia-giagnorio-2026.md) |
| *State of AI-assisted Software Development Report* | DORA / Google Cloud | 2025 | Impacto de IA en métricas DORA: mayor CFR si no hay gobernanza. | [dora.dev/dora-report-2025/](https://dora.dev/dora-report-2025/) |
| *Carta Encíclica Magnifica Humanitas* | Papa León XIV (*Ciudad del Vaticano*) | 2026 | Custodia humana y distinción entre elección algorítmica y decisión moral (**Informe Ético**). | Ciudad del Vaticano (15/05/2026) |

### 3.3. Alertas por Palabras Clave Compuestas (Google Scholar / Semantic Scholar)
* `"agentic software engineering" OR "multi-agent software development"`
* `"LLM code review" AND ("human oversight" OR "automation bias")`
* `"AI governance" AND ("software lifecycle" OR "ISO 42001")`
* `"proportional evidence" OR "verifiable human-in-the-loop"`
* `"slopsquatting" OR "package hallucination" OR "AI supply chain security"`

### 3.4. Monitoreo por Grafos de Citación
* **Herramientas:** ResearchRabbit / Connected Papers / Semantic Scholar.
* Crear una colección semilla con los 15 papers clave de la tesis para recibir recomendaciones semanales de co-citación.

---

## 📅 4. Calendario de Vigilancia de Conferencias (Pull Programado)

Revisar las listas de *Accepted Papers* en las siguientes ventanas temporales:

| Mes | Conferencia / Hito de Publicación | Impacto en Cronograma de Tesis |
|---|---|---|
| **Noviembre 2026** | **ASE 2026** e **ISSTA 2026** | Insumo para Topologías (A0) y Matriz de Control (A2). |
| **Febrero 2027** | **ICSE 2027** e **ICLR 2027** | Insumo crítico previo al **Hito 3: Pitch de Tesis (23/02/2027)**. |
| **Mayo 2027** | **FSE 2027** | Insumo para la consolidación final de la memoria de tesis. |

---

## 🗂️ 5. Sistema de Gestión y Fichado (3 Tiers)

```text
  [ INBOX: Alertas & Preprints ]
                │
                ▼
  ┌──────────────────────────────────────────────────────────┐
  │ TIER 3 (Bandeja Zotero / Tag #inbox)                     │
  │ • Triage semanal (descartar 90%, guardar 10%).           │
  └─────────────────────────────┬────────────────────────────┘
                                │
        ┌───────────────────────┴───────────────────────┐
        ▼                                               ▼
  ┌───────────────────────────┐   ┌───────────────────────────┐
  │ TIER 2 (Soporte/Contexto) │   │ TIER 1 (Fundacionales)    │
  │ • Lectura diagonal.       │   │ • Lectura profunda.       │
  │ • BibTeX en repo.         │   │ • Ficha en kb/literature/ │
  │ • Cita de estado del arte.│   │ • ~30 a 40 papers total.  │
  └───────────────────────────┘   └───────────────────────────┘
```

### 5.1. Definición de Tiers
* **Tier 1 (Fundacionales / Citación central):** Se leen completos, se anotan y se genera una ficha Markdown en `kb/literature/`.
* **Tier 2 (Contexto / Soporte empírico):** Lectura rápida (*Abstract, Figures, Conclusion*); se incorporan al archivo BibTeX para citas estadísticas o de contexto.
* **Tier 3 (Inbox Zotero):** Repositorio temporal etiquetado con `#inbox` para depuración quincenal.

---

## 🔍 6. Protocolo de Verificación y Acceso (Integridad Científica)

Para asegurar que cada paper citado sea **auténtico, relevante y accesible**:

### 6.1. Verificación de Existencia y Metadatos (Evitar citas alucinadas)
1. **DBLP ([dblp.org](https://dblp.org)):** Consultar autor y título para verificar indexación *peer-reviewed* en computación.
2. **Crossref / DOI ([search.crossref.org](https://search.crossref.org)):** Verificar el DOI oficial asignado.
3. **arXiv ([arxiv.org](https://arxiv.org)):** Verificar preprints mediante su identificador canónico `arXiv:YYMM.NNNNN`.

### 6.2. Vías Legales de Descarga Abierta (Acceso a Texto Completo)
1. **Columna derecha de Google Scholar:** Enlaces directos a versiones *Green Open Access*.
2. **Extensión Unpaywall ([unpaywall.org](https://unpaywall.org)):** Detección automática de PDFs abiertos en sitios con paywall.
3. **Portal MINCYT / Biblioteca Universidad Austral:** Acceso institucional completo a IEEE Xplore, ACM Digital Library, Elsevier y SpringerLink.
4. **ResearchGate:** Solicitud directa de PDF al autor con 1 clic.

### 6.3. Test de Relevancia en 5 Minutos (Filtro antes de lectura profunda)
* **Paso 1:** Lectura de *Abstract* (alineación con la pregunta de investigación).
* **Paso 2:** Inspección de Figuras y Tablas (¿mide datos reales de PRs, fallas, tiempos o topologías?).
* **Paso 3:** Búsqueda textual (*Ctrl+F*) de términos clave: `human-in-the-loop`, `automation bias`, `slopsquatting`, `code review`, `proportional evidence`.
* **Paso 4:** Lectura de *Conclusion* y *Threats to Validity*.

---

## 📚 7. Corpus Bibliográfico Central Verificado (7 Ejes Temáticos)

### Eje 1: Método y Epistemología (DSR y Caso Único)
* **Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004).** Design science in information systems research. *MIS Quarterly, 28*(1), 75–105. [Google Scholar](https://scholar.google.com/scholar?q=Design+science+in+information+systems+research+Hevner)
* **Peffers, K., Tuunanen, T., Rothenberger, M. A., & Chatterjee, S. (2007).** A design science research methodology for information systems research. *Journal of Management Information Systems, 24*(3), 45–77. [DOI: 10.2753/MIS0742-1222240302](https://doi.org/10.2753/MIS0742-1222240302)
* **Yin, R. K. (2018).** *Case study research and applications: Design and methods* (6th ed.). Sage Publications.
* **Runeson, P., & Höst, M. (2009).** Guidelines for conducting and reporting case study research in software engineering. *Empirical Software Engineering, 14*(2), 131–164. [DOI: 10.1007/s10664-008-9102-8](https://doi.org/10.1007/s10664-008-9102-8)
* **Susman, G. I., & Evered, R. D. (1978).** An assessment of the scientific merits of action research. *Administrative Science Quarterly, 23*(4), 582–603. [DOI: 10.2307/2392581](https://doi.org/10.2307/2392581)

### Eje 2: Factor Humano, Automatización y Supervisión Cognitiva
* **Bainbridge, L. (1983).** Ironies of automation. *Automatica, 19*(6), 775–779. [DOI: 10.1016/0005-1098(83)90046-8](https://doi.org/10.1016/0005-1098(83)90046-8)
* **Parasuraman, R., & Riley, V. (1997).** Humans and automation: Use, misuse, disuse, abuse. *Human Factors, 39*(2), 230–253. [DOI: 10.1518/001872097778543886](https://doi.org/10.1518/001872097778543886)
* **Elish, M. C. (2019).** Moral crumple zones: Cautionary tales in human-robot interaction. *Engaging Science, Technology, and Society, 5*, 40–60. [ESTS Journal](https://estsjournal.org/index.php/ests/article/view/260)
* **Vaithilingam, P., Zhang, T., & Glassman, E. L. (2022).** Expectation vs. experience: Evaluating the usability of code generation tools powered by large language models. *CHI EA 2022*. [DOI: 10.1145/3491101.3519665](https://doi.org/10.1145/3491101.3519665)

### Eje 3: Ingeniería de Software Agéntica y Sistemas Multi-Agente (2024–2026)
* **Otoum, S., et al. (2026).** Autonomous agent frameworks for software engineering: A systematic survey and taxonomy. *IEEE Access*. [IEEE Xplore](https://ieeexplore.ieee.org/)
* **He, J., et al. (2025/2026).** Multi-agent collaboration in software development: Architectures, protocols, and empirical evidence. *ACM Transactions on Software Engineering and Methodology (TOSEM)*. [ACM DL](https://dl.acm.org/)
* **CooperBench. (2026).** Benchmarking multi-agent collaboration, context drift, and task handoffs in software engineering. *arXiv:2601.09123*. [arXiv:2601.09123](https://arxiv.org/abs/2601.09123)
* **Jiménez, C. E., et al. (2024).** SWE-bench: Can language models resolve real-world GitHub issues? *ICLR 2024*. [arXiv:2310.06770](https://arxiv.org/abs/2310.06770)
* **Hong, S., et al. (2024).** MetaGPT: Meta programming for a multi-agent collaborative framework. *ICLR 2024*. [arXiv:2308.00352](https://arxiv.org/abs/2308.00352)
* **Qian, C., et al. (2024).** Communicative agents for software development. *ACL 2024*. [arXiv:2307.07924](https://arxiv.org/abs/2307.07924)
* **Hou, X., et al. (2024).** Large language models for software engineering: A systematic literature review. *ACM TOSEM / arXiv:2404.04834*. [arXiv:2404.04834](https://arxiv.org/abs/2404.04834)
* **Zhang, J., et al. (2025).** A survey on evaluation of LLM-based autonomous agents. *arXiv:2503.16416*. [arXiv:2503.16416](https://arxiv.org/abs/2503.16416)
* **Wang, L., et al. (2025).** Multi-agent agile effort estimation by analogy. *arXiv:2509.14483*. [arXiv:2509.14483](https://arxiv.org/abs/2509.14483)
* **Giagnorio, M. (2026).** *Catálogo de Agentes de IA para Ingeniería y Gestión de Software (14 categorías en 3 dominios)*. Facultad de Ingeniería, Universidad Austral. [catalogo-agentes.md](file:///home/macky/Projects/tesis/kb/literature/catalogo-agentes-ia-giagnorio-2026.md)

### Eje 4: Code Review con IA, Calidad y Seguridad de Software (2023–2026)
* **Empirical Software Engineering. (2026).** Does AI code review lead to code changes? A case study of GitHub Actions. *Empirical Software Engineering (EMSE)*. [Springer EMSE](https://link.springer.com/)
* **Evaluating LLMs for Code Review. (2025).** Systematic evaluation of LLM-assisted code review, false positives, and developer reliance. *ACM TOSEM / arXiv:2502.11245*. [arXiv:2502.11245](https://arxiv.org/abs/2502.11245)
* **Perry, N., Srivastava, M., Kumar, D., & Boneh, D. (2023).** Do users write more insecure code with AI assistants? *ACM CCS 2023*. [arXiv:2211.03622](https://arxiv.org/abs/2211.03622)
* **Sandoval, G., Pearce, H., Nisi, T., Karmakar, S., Dolan-Gavitt, B., & Garg, S. (2023).** Lost at C: A user study on the security implications of large language model code assistants. *USENIX Security 2023*. [USENIX Presentation](https://www.usenix.org/conference/usenixsecurity23/presentation/sandoval)

### Eje 5: Métricas Industriales y Gestión (2018–2026)
* **Forsgren, N., Humble, J., & Kim, G. (2018).** *Accelerate: The science of lean software and DevOps*. IT Revolution Press.
* **DORA. (2025).** *State of AI-assisted Software Development Report 2025*. DORA / Google Cloud. [dora.dev/dora-report-2025/](https://dora.dev/dora-report-2025/)
* **Project Management Institute (PMI). (2025).** *AI in PM Global Report 2025 / PMBOK Guide (8th ed.)*. PMI Publications.
* **Thoughtworks. (2025/2026).** *Technology Radar (Vol. 33)*. Thoughtworks.

### Eje 6: Ética, Magisterio Pontificio y Algor-ética
* **León XIV. (2026, 15 de mayo).** *Carta Encíclica Magnifica Humanitas: Sobre la custodia de la persona humana en el tiempo de la inteligencia artificial*. Ciudad del Vaticano.
* **Papa Francisco. (2024, 14 de junio).** *Discurso del Santo Padre en la sesión del G7 sobre Inteligencia Artificial*. Borgo Egnazia.
* **Papa Francisco. (2024, 1 de enero).** *Mensaje para la 57ª Jornada Mundial de la Paz: Inteligencia Artificial y Paz*.
* **Pontificia Academia para la Vida. (2020/2024).** *Rome Call for AI Ethics*. Ciudad del Vaticano.

### Eje 7: Normas y Estándares Internacionales
* **ISO/IEC 42001:2023** — *Information technology — Artificial intelligence — Management system (AIMS)*.
* **ISO/IEC 27001:2022 / 27002:2022** — *Information security, cybersecurity and privacy protection — ISMS*.
* **ISO/IEC 23894:2023** — *Artificial intelligence — Guidance on risk management*.
* **ISO/IEC 5338:2023** — *AI system life cycle processes*.
* **NIST AI RMF 1.0 (2023) / NIST AI 600-1 (2024)** — *Artificial Intelligence Risk Management Framework / Generative AI Profile*.
* **NIST SP 800-218A (2024)** — *Secure Software Development Practices for Generative AI (SSDF Community Profile)*. [NIST CSRC](https://csrc.nist.gov/pubs/sp/800/218/a/final)
* **Reglamento (UE) 2024/1689 (EU AI Act)** — Art. 14 (*Supervisión humana*) y requisitos de trazabilidad.

---

## 📝 8. Plantilla Estándar de Ficha de Lectura (`kb/literature/`)

```markdown
# [FICHA] Apellido et al. (Año) — Título Breve

> **Referencia APA:**  
> **BibTeX Key:**  
> **Tier:** [Tier 1 / Tier 2]  
> **Palabras clave:**  
> **Fecha de lectura:** YYYY-MM-DD  
> **PDF / Link:**  

---

### 1. El Problema / Gap que aborda
* ¿Qué problema específico busca resolver el paper?

### 2. El Claim / Propuesta principal
* ¿Cuál es la tesis, modelo o artefacto propuesto por los autores?

### 3. Metodología y Validación
* **Diseño:** (DSR, caso de estudio, minería de repositorios, user study, survey).
* **Muestra:** ($N$ repositorios, $N$ participantes, datasets).
* **Métricas:** (Accuracy, tiempo de revisión, CFR, pass@k).

### 4. Principales Hallazgos y Resultados
* Métricas clave y conclusiones respaldadas por datos.

### 5. Vínculo directo con ARGOS (¿Para qué nos sirve?)
* **Componente:** (A0 Topología / A1 Riesgos / A2 Matriz A0-A4 / A3 Conformance Engine / Informe Ético).
* **Utilidad práctica:** ¿Qué argumento, control o compuerta justifica en nuestra tesis?

### 6. Citas Textuales Clave (Listas para la memoria)
> *"Cita textual relevante con número de página o sección."* (p. XX)
```

---

## ⏱️ 9. Rutina Semanal Sostenible (Timeboxing)

* **Dedicación sugerida:** **1 hora semanal** (ej. viernes por la tarde o lunes temprano).
* **Bloque operativo:**
  1. *5 min:* Revisar alertas de correo (Google Scholar / Semantic Scholar).
  2. *5 min:* Descartar artículos no pertinentes y enviar 2–3 a Zotero.
  3. *50 min:* Lectura profunda de **1 paper Tier 1** y redacción de su ficha en `kb/literature/`.
* **Rendimiento proyectado:** 1 paper/semana $\approx$ **40 papers rigurosamente analizados al final del año**.
