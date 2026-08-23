# [BORRADOR] Estrategia de Bibliografía y Vigilancia Científica — ARGOS

> **Estado:** Borrador de Trabajo (Working Draft)  
> **Proyecto:** Trabajo de Grado — *Gobernanza de agentes de IA en el desarrollo de software* (Univ. Austral)  
> **Autora:** Macarena Alimena · **Tutor Académico:** Marcos Giagnorio  
> **Horizonte temporal:** Agosto 2026 – Julio 2027  

---

## 🎯 1. Objetivo del Sistema de Vigilancia

Establecer un mecanismo estructurado, escalable y sostenible para:
1. Identificar de manera continua la literatura científica relevante durante el ciclo de vida anual de la tesis.
2. Evitar la infoxicación mediante un protocolo de filtrado (*triage*) en tres niveles (*tiers*).
3. Construir una base de conocimiento bibliográfica versionada e integrada con el repositorio de investigación (`kb/literature/`).
4. Blindar el estado del arte y la justificación teórica/empírica ante las instancias de evaluación (Pitch en Feb 2027 y Defensa Final en Jun-Jul 2027).

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
* **Estándares:** ISO/IEC 42001:2023, ISO/IEC 27001:2022, ISO/IEC 23894, ISO/IEC 5338, NIST AI RMF 1.0 / AI 600-1, NIST SP 800-218 / 800-218A, EU AI Act.
* **Reportes:** DORA State of AI Report (Google Cloud), Thoughtworks Tech Radar, Gartner / McKinsey AI Governance Reports.

---

## 📡 3. Protocolo de Alertas y Vigilancia Continua

### 3.1. Alertas de Citación sobre Papers Semilla (Push)
Configurar en **Google Scholar** avisos para nuevos artículos que citen a los siguientes trabajos fundacionales:

| Paper Semilla | Autores | Año | Eje en ARGOS |
|---|---|:---:|---|
| *SWE-bench: Can language models resolve real-world GitHub issues?* | Jiménez et al. | 2024 | Capacidad real de agentes en software |
| *MetaGPT: Meta programming for a multi-agent collaborative framework* | Hong et al. | 2024 | Topologías multi-agente y coordinación |
| *Do users write more insecure code with AI assistants?* | Perry et al. | 2023 | Riesgos de seguridad introducidos por IA |
| *Lost at C: A user study on the security implications of LLM code assistants* | Sandoval et al. | 2023 | Degradación de revisión y confianza ciega |
| *Moral crumple zones: Cautionary tales in human-robot interaction* | Elish, M. C. | 2019 | Brecha de responsabilidad e injusticia ética |
| *Ironies of automation* | Bainbridge, L. | 1983 | Fundamento teórico de la degradación HITL |
| *Design science in information systems research* | Hevner et al. | 2004 | Marco metodológico DSR |

### 3.2. Alertas por Palabras Clave Compuestas
* `"agentic software engineering" OR "multi-agent software development"`
* `"LLM code review" AND ("human oversight" OR "automation bias")`
* `"AI governance" AND ("software lifecycle" OR "ISO 42001")`
* `"proportional evidence" OR "verifiable human-in-the-loop"`
* `"slopsquatting" OR "package hallucination" OR "AI supply chain security"`

### 3.3. Monitoreo por Grafos de Citación
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

## 📝 6. Plantilla Estándar de Ficha de Lectura (`kb/literature/`)

```markdown
# [FICHA] Apellido et al. (Año) — Título Breve

> **Referencia APA:**  
> **BibTeX Key:**  
> **Tier:** [Tier 1 / Tier 2]  
> **Palabras clave:**  
> **Fecha de lectura:** YYYY-MM-DD  

---

### 1. El Problema / Gap que aborda
* ¿Qué problema específico busca resolver el paper?

### 2. El Claim / Propuesta principal
* ¿Cuál es la tesis, modelo o artefacto propuesto por los autores?

### 3. Metodología y Validación
* ¿Qué diseño metodológico utilizaron? (Dataset, tamaño muestral $N$, herramientas evaluadas, métricas).

### 4. Principales Hallazgos y Resultados
* Métricas clave y conclusiones respaldadas por datos.

### 5. Vínculo directo con ARGOS (¿Para qué nos sirve?)
* ¿A qué componente aporta? (A0 Topología / A1 Riesgos / A2 Matriz / A3 Evidencia / Ética).
* ¿Qué argumento o control justifica?

### 6. Citas Textuales Clave (Listas para la memoria)
> *"Cita textual relevante con número de página."* (p. XX)
```

---

## ⏱️ 7. Rutina Semanal Sostenible (Timeboxing)

* **Dedicación sugerida:** **1 hora semanal** (ej. viernes por la tarde o lunes temprano).
* **Bloque operativo:**
  1. *5 min:* Revisar alertas de correo (Scholar / Semantic Scholar).
  2. *5 min:* Descartar artículos no pertinentes y enviar 2–3 a Zotero.
  3. *50 min:* Lectura profunda de **1 paper Tier 1** y redacción de su ficha en `kb/literature/`.
* **Rendimiento proyectado:** 1 paper/semana $\approx$ **40 papers rigurosamente analizados al final del año**.
