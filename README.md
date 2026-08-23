# ARGOS: Autonomous Risk & Governance Oversight for Software

> **Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional.**

**Trabajo de Grado — Ingeniería en Informática (Orientación Gestión)**  
**Universidad Austral** · Facultad de Ingeniería  
**Alumna:** Macarena Alimena  
**Tutor Académico:** Marcos Giagnorio  
**Entrega Final:** Junio–Julio 2027  

---

## 🎯 El Problema y la Apuesta (Claim)

### El Gap
Los marcos vigentes de gobernanza de IA (*ISO/IEC 42001, NIST AI RMF, EU AI Act*) fueron diseñados para gobernar la IA **como producto**. Cuando la IA agéntica entra al **proceso de desarrollo de software**, se desplaza el objeto gobernado y el riesgo se propaga a todo el software entregado por la organización, incluso a sistemas que no contienen IA.

Hoy, la supervisión humana (*Human-in-the-Loop*) en los pipelines de desarrollo se degrada en silencio: el volumen y velocidad de cambios generados por agentes satura la capacidad humana de revisión, convirtiendo la aprobación en un simple sello de goma administrativo (*rubber stamping*).

### El Claim
> **La supervisión humana solo es real si es verificable. Todo nivel de autonomía delegado a un agente de software debe contar con un nivel de evidencia proporcional que permita reconstruir *ex post* quién decidió qué. Sin evidencia proporcional, el HITL opera como una ficción de cumplimiento.**

---

## 🏛️ Los Cuatro Artefactos de ARGOS

| # | Artefacto | Propósito |
|---|---|---|
| **A0** | **Criterios de Gobernabilidad de Topologías Agénticas** | Criterios arquitectónicos para estructurar enjambres de agentes de modo que existan costuras naturales de inspección humana. |
| **A1** | **Taxonomía de Riesgos del Desarrollo Agentizado** | Clasificación sistemática de amenazas específicas (alucinaciones de paquetes *slopsquatting*, fuga de contexto, degradación de revisión). |
| **A2** | **Matriz Autonomía × Control (Niveles A0–A4)** | Parametrización de compuertas y controles obligatorios según la libertad delegada al agente. |
| **A3** | **Modelo de Telemetría + Motor Evaluador de Conformidad + Tablero** | Recolector de trazas en CI/CD, *Governance Gatekeeper* automatizado y tablero de visualización de KRIs para la dirección. |
| **V** | **Validación Empírica (Pre/Post) + Panel Delphi** | Medición sobre caso de estudio real en PyME (*reconstruction tests* de PRs) y validación cualitativa externa. |

---

## 📂 Estructura del Repositorio

```text
.
├── README.md                      # Este documento (visión general, pitch y navegación)
│
├── docs/                          # Entregables formales de la Universidad Austral
│   ├── templates/                 # Plantillas oficiales (Plan de Trabajo, Informe Ético)
│   ├── 01-definicion-tema/        # Definición formal de tema (Hito 14/08/2026)
│   ├── 02-informe-etico/          # Informe Ético y Social (anclado en Magnifica Humanitas)
│   ├── 03-plan-de-trabajo/        # Plan de Trabajo formal de tesis
│   └── 04-tesis-final/            # Capítulos de la memoria de tesis (2027)
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

## 🧭 Marco Metodológico y Normativo

- **Método Científico:** Design Science Research (DSR — Peffers et al., Hevner et al.) + Investigación-Acción en Caso Único (Yin, Runeson & Höst).
- **Normas de Referencia:** ISO/IEC 42001:2023, ISO/IEC 27001:2022, NIST SP 800-218A (SSDF for GenAI), NIST AI 600-1.
- **Marco Ético Humanista:** Encíclica *Magnifica Humanitas* (León XIV, 2026) sobre la custodia de la persona humana frente al paradigma tecnocrático y la distinción entre elección algorítmica y decisión moral.

---

## 🚀 Próximos Pasos Inmediatos

- [ ] Captura del dataset histórico de PRs en PyME (*Línea de base antes de perder el "antes"*).
- [ ] Presentación formal del Plan de Trabajo (Octubre 2026).
- [ ] Redacción del Informe Ético y Social alineado a las 5 preguntas de la Facultad.
- [ ] Formalización de los Criterios de Gobernabilidad de Topologías (A0).
