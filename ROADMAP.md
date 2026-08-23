# Roadmap Oficial y Plan de Ejecución — ARGOS

> **Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional.**  
> **Trabajo de Grado — Ingeniería en Informática (Orientación Gestión)** · Universidad Austral  
> **Alumna:** Macarena Alimena · **Tutor Académico:** Marcos Giagnorio  
> **Estado:** Documento Maestro de Seguimiento y Cronograma Operativo

---

## 🎯 Resumen Ejecutivo de Hitos

```text
  [ HOY: 22 Ago 2026 ]
         │
         ├── ⚡ 22–25 Ago ── Captura de Línea de Base Histórica (data/raw/)
         │
         ├── 🔴 01 Sep 2026 ── HITO 1: Entrega Plan de Trabajo de Grado (10 días)
         │
         ├── 🔴 15 Sep 2026 ── HITO 2: Entrega Informe Ético y Social (24 días)
         │
         ├── ⚙️ Oct–Dic 2026 ── Diagnóstico, Taxonomía (A1) y Topologías (A0)
         │
         ├── ⚙️ Ene–Feb 2027 ── Matriz (A2), Conformance Engine (A3) y Calibración
         │
         ├── 🔴 23 Feb 2027 ── HITO 3: Pitch de Tesis
         │
         ├── 👥 Mar–Abr 2027 ── Panel de Expertos tipo Delphi
         │
         ├── 📊 Abr–May 2027 ── Reconstruction Tests & Análisis Pre/Post
         │
         └── 🏁 Jun–Jul 2027 ── HITO 4: Memoria Final y Defensa de Tesis
```

---

## 📅 Calendario Detallado de Entregas y Fases

### 🚀 Sprint 1: Hacia el Plan de Trabajo (22/08 al 01/09/2026 — 10 días)

* **Objetivo:** Formalizar y entregar la propuesta metodológica y técnica ante la Dirección de Carrera y Cátedra de Trabajo de Grado utilizando la plantilla oficial ([`docs/templates/Plan-de-trabajo-template.md`](file:///home/macky/Projects/tesis/docs/templates/Plan-de-trabajo-template.md)).
* **Entregable:** `docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md` (y versión en formato formal de envío).

| Período | Tareas Específicas | Estado |
|---|---|:---:|
| **22 – 24 Ago** | **⚡ Tarea Crítica: Extracción de Línea de Base.**<br>• Solicitar y extraer export histórico de PRs (últimos 6–12 meses) de la PyME tecnológica.<br>• Campos: timestamps, autor (humano/agente), tamaño de diff, tiempo de revisión, comentarios, fallas escapadas.<br>• Guardar en `data/raw/` anonimizado. | ⏳ En curso |
| **25 – 26 Ago** | **Redacción del Núcleo del Plan de Trabajo:**<br>• *Motivación & Gap:* La IA en la fábrica de software vs. en el producto.<br>• *Objetivos & Claim:* La supervisión humana solo es real si es verificable.<br>• *Capacidades (Funcionalidades):* Clasificación A0–A4, compuertas dinámicas, telemetría y dashboard.<br>• *Arquitectura de Gobernanza en Capas:* Política $\to$ Topología $\to$ Control $\to$ Evidencia $\to$ Tablero. | 📝 Pendiente |
| **27 – 28 Ago** | **Metodología, Cronograma y Bibliografía:**<br>• Formalizar el marco DSR (Peffers) + Investigación-Acción en Caso Único (Yin).<br>• Integrar banco de pruebas y calibración del orquestador (ADR-005).<br>• Cronograma de 480 horas declaradas (~12 h/sem × 40 semanas).<br>• Referencias bibliográficas en formato APA riguroso. | 📝 Pendiente |
| **29 – 30 Ago** | **Revisión con Tutor Académico:**<br>• Envío de borrador a Marcos Giagnorio.<br>• Incorporación de feedback y ajustes finales. | 📝 Pendiente |
| **31 Ago – 01 Sep** | **🔴 ENTREGA FORMAL DEL PLAN DE TRABAJO (01/09/2026):**<br>• Generación de versión final y presentación formal a la Facultad. | 🎯 Hito 1 |

---

### 🕊️ Sprint 2: Hacia el Informe Ético y Social (02/09 al 15/09/2026 — 14 días)

* **Objetivo:** Responder a los [Lineamientos de Evaluación Ética y Social de la Facultad](file:///home/macky/Projects/tesis/docs/templates/Lineamientos-Informe-Etico.md) con anclaje humanista y el Magisterio de la Iglesia.
* **Entregable:** `docs/02-informe-etico/Informe-Etico-Alimena.md`.

| Período | Tareas Específicas | Estado |
|---|---|:---:|
| **02 – 05 Sep** | **Desarrollo de Preguntas 1 y 2 (Objeto, Fin y Stakeholders):**<br>• *Pregunta 1:* Principios éticos generales. Fin: aumentar y garantizar la responsabilidad humana real. Circunstancias modificatorias: justificación de negligencia o vigilancia.<br>• *Pregunta 2:* Impacto positivo en desarrolladores (evitar la *moral crumple zone*), clientes, usuarios y auditores. | 📝 Pendiente |
| **06 – 09 Sep** | **Desarrollo de Preguntas 3 y 4 (Mitigación y Derechos Humanos):**<br>• *Pregunta 3:* Medidas de mitigación en 3 horizontes (corto: fuga de IP/secretos; mediano: *slopsquatting* y degradación de review; largo: desprofesionalización junior).<br>• *Pregunta 4:* Compatibilidad con DDHH y justicia laboral. **Riesgo E9 (Vigilancia Laboral):** declarar la prohibición de usar la telemetría para evaluación individual de desempeño. | 📝 Pendiente |
| **10 – 12 Sep** | **Pregunta 5, Declaración de IA y Fundamentación Pontificia:**<br>• *Pregunta 5:* Integridad académica y **declaración explícita de uso de IA en la tesis**.<br>• *Fundamentación Humanista:* Integración de la Encíclica *Magnifica Humanitas* (León XIV, 2026), distinción entre *elección algorítmica y decisión moral*, y *Algor-ética*. | 📝 Pendiente |
| **13 – 14 Sep** | **Revisión y Control de Calidad:**<br>• Control cruzado de consistencia entre Plan de Trabajo e Informe Ético.<br>• Visto bueno del tutor. | 📝 Pendiente |
| **15 Sep** | **🔴 ENTREGA FORMAL DEL INFORME ÉTICO (15/09/2026):**<br>• Presentación formal ante la Facultad de Ingeniería. | 🎯 Hito 2 |

---

### ⚙️ Fase 3: Diagnóstico, Modelado y Calibración (Octubre 2026 a Enero 2027)

* **Objetivo:** Desarrollar los artefactos conceptuales y técnicos de ARGOS antes de la defensa intermedia (Pitch).

| Período | Foco de Trabajo y Entregables Intermedios | Artefactos |
|---|---|:---:|
| **Octubre 2026** | • Procesamiento y análisis estadístico de la línea de base (`data/processed/`).<br>• Primer borrador de **A1 (Taxonomía de Riesgos del Desarrollo Agentizado)**. | **A1** |
| **Noviembre 2026** | • Formalización de **A0 (Criterios de Gobernabilidad de Topologías)**.<br>• Análisis de pases de mano inter-agente y costuras de inspección humana. | **A0** |
| **Diciembre 2026** | • Construcción de **A2 (Matriz Autonomía × Control A0–A4)** mapeada a ISO 42001 e ISO 27001.<br>• Definición de compuertas y evidencias obligatorias por nivel. | **A2** |
| **Enero 2027** | • Implementación del prototipo técnico **A3 (Collector + Conformance Engine + Tablero)**.<br>• Ejecución del banco de pruebas y calibración del orquestador ([`ADR-005`](file:///home/macky/Projects/tesis/kb/adrs/ADR-005-calibracion-y-verificacion-del-orquestador.md)).<br>• **Convocatoria del Panel Delphi:** Envío de invitaciones formales a 6–10 expertos. | **A3** + Testbench |

---

### 🎤 Fase 4: Pitch de Tesis (Febrero 2027)

* **Fecha del Hito:** **23 de Febrero de 2027**
* **Objetivo:** Defender con solvencia el estado de avance, los hallazgos empíricos preliminares y la arquitectura del marco ante el tribunal evaluador.

**Estructura del Pitch (Deck de 10–12 slides):**
1. **El Problema (1 slide):** La IA entró a la fábrica de software; la supervisión humana se rompe por volumen.
2. **El Claim (1 slide):** La supervisión humana solo es real si es verificable; evidencia proporcional.
3. **Evidencia Empírica de la Línea de Base (2 slides):** Gráficos reales de PRs (diffs de 500 líneas aprobados en segundos sin comentarios = ficción de cumplimiento).
4. **Los 4 Artefactos ARGOS (3 slides):** Topología (A0), Riesgos (A1), Matriz A0–A4 (A2), Motor y Tablero (A3).
5. **Calibración y Testbench (1 slide):** Protocolo de verificación del orquestador (ADR-005).
6. **Plan de Validación Final y Cronograma a Defensa (2 slides):** Panel Delphi + Pruebas de Reconstrucción + Horizonte Junio 2027.

---

### 🔬 Fase 5: Validación Empírica, Delphi y Redacción Final (Marzo a Julio 2027)

| Período | Actividades y Metodología | Entregables |
|---|---|:---:|
| **Marzo – Abril 2027** | **Panel de Expertos (Delphi ligero):**<br>• Rondas de evaluación cualitativa con 6–10 auditores ISO y tech leads.<br>• Ajustes y calibración final del framework (v2). | Informe de Validación Delphi |
| **Abril – Mayo 2027** | **Validación Cuantitativa en PyME:**<br>• *Reconstruction Tests:* Auditoría ciega sobre PRs antes vs. después de ARGOS.<br>• Medición de métricas DORA extendidas, HIR y tasa de defectos escapados. | Resultados Cuantitativos |
| **Mayo – Junio 2027** | **Redacción Integral de la Memoria:**<br>• Consolidación de capítulos, anexos metodológicos, diario de investigación y código fuente. | Borrador Completo de Tesis |
| **Junio – Julio 2027** | 🏁 **DEFENSA FINAL DE TRABAJO DE GRADO** | **Tesis Aprobada** |

---

## ⚠️ Matriz de Riesgos y Puntos de Control Inmediatos

| Riesgo | Impacto | Fecha Límite | Mitigación Operativa |
|---|:---:|:---:|---|
| **Pérdida de la línea de base histórica** | 🔴 Crítico | 25/08/2026 | Extraer el dataset de Git/PRs de la PyME ahora mismo; si se espera, el "antes" se contamina. |
| **Desvío hacia desarrollo de producto generalista** | 🟡 Medio | Permanente | Mantener el enfoque de gestión/DSR: el código es solo el recolector y evaluador de políticas (ADR-004). |
| **Demora en convocatoria del panel Delphi** | 🟡 Medio | 31/01/2027 | Invitar a los expertos en enero para sesionar en marzo; no esperar a último momento. |
