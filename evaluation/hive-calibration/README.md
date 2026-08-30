# Protocolo de Calibración y Verificación del Orquestador / Hive Agéntico

> **Objetivo:** Establecer el banco de pruebas (*testbench*) de gobernanza para evaluar empíricamente que el enjambre de agentes y su orquestador operan de acuerdo con las restricciones de topología (A0), los límites de autonomía (A2) y la fidelidad de telemetría (A3) antes y durante su integración en el pipeline de desarrollo.

---

## 🎯 ¿Por qué calibrar el Orquestador?

En el marco **ARGOS**, no basta con verificar que el código resultante compile o pase pruebas unitarias. Debe verificarse la **calidad y gobernabilidad del proceso de generación**.

Un orquestador puede producir código funcional pero violar políticas de gobernanza si:
1. Permite que agentes excedan su ámbito de responsabilidad (*role leakage*).
2. Pierde restricciones de seguridad en los pases de mano inter-agente (*context drift*).
3. Emite trazas de auditoría desalineadas con los cambios reales en Git/CI/CD (*audit drift*).
4. Aplica *Quality Gates* con umbrales descalibrados que inducen al *bypass* humano o a la fuga de vulnerabilidades.

---

## 🔬 Ejes de Evaluación y Calibración

### 1. Calibración de Topología y Pases de Mano (A0)
* **Adherencia a Límites de Rol (*Role Boundary Test*):** Evaluar si cada subagente (ej. *Planner*, *Coder*, *Reviewer*, *Tester*) opera estrictamente dentro de sus permisos de lectura/escritura y capacidades de ejecución de herramientas.
* **Preservación y Deriva de Contexto (*Context Retention Score*):** Medición de la pérdida de directivas no funcionales (seguridad, accesibilidad, dependencias permitidas) a lo largo de la cadena de delegación.
* **Independencia Real en Revisiones:** Detección y bloqueo de configuraciones donde un agente valida a otro sin heterogeneidad de modelos o sin costura humana obligatoria según el nivel A2.

### 2. Calibración de Quality Gates Gobernados (A2 / A3)
* **Matriz de Falsos Positivos vs. Falsos Negativos:**
  * Pruebas sobre *Golden Datasets* con código vulnerable conocido y dependencias inexistentes (*slopsquatting*).
  * Calibración de umbrales para maximizar detección de riesgos sin generar fatiga de falsos positivos en el equipo de ingeniería.
* **Pruebas de Contención / Kill-Switch (*Circuit Breaker Evaluation*):**
  * Validación del corte determinístico ante bucles infinitos de razonamiento, superación de presupuestos de tokens o intentos de modificación de archivos restringidos (`.github/workflows`, variables de entorno sensibles).

### 3. Verificación de Fidelidad de Telemetría (A3)
* **Reconciliación Traza vs. Git (*Trace Reconciliation*):**
  * Comparación criptográfica/determinística entre los eventos declarados en el log del orquestador (`trace.json`) y el árbol de commits / acciones ejecutadas en CI/CD.
* **Completitud de Evidencia para Auditoría:**
  * Validación de que la traza contiene todos los campos necesarios para reconstruir *ex post* la cadena de custodia: agente emisor, versión de modelo, prompt del sistema, diffs intermedios, tiempo de ejecución y nivel de autonomía A0–A4.

### 4. Pruebas de Estrés e Inyección de Fallos (*Fault Injection / Red Teaming*)
* Inyección deliberada de requerimientos ambiguos, bibliotecas alucinadas y solicitudes de escalada de privilegios para medir la tasa de escalamiento efectivo al supervisor humano (*Human Escalation Rate*).

### 5. Cadencia de Re-calibración Trimestral y Auditoría de Detección (Ciclo PDCA)
* **Compuerta de Re-calibración Trimestral:** Ejecución programada del banco de pruebas (*golden dataset*) cada 3 meses o ante cambios de versión de LLMs o prompts de sistema.
* **Auditoría de Sensibilidad de Detección:** Verificación experimental de que los agentes especializados no han degradado su tasa de detección de vulnerabilidades, dependencias maliciosas o fallos de conformidad (*prompt drift / model drift*).
* **Informe de Salud y Re-certificación:** El tablero emite el reporte trimestral con el que la dirección técnica re-certifica o revierte los niveles de autonomía A0–A4 delegados.

---

## 📊 KRIs del Orquestador para el Tablero Directivo (A3)

| KRI | Definición | Rango Deseable |
|---|---|---|
| **HIR (*Human Intervention Rate*)** | % de ejecuciones donde el orquestador requirió intervención o desempate humano. | Proporcional al nivel A0–A4 asignado |
| **CRS (*Context Retention Score*)** | Índice semántico de retención de restricciones entre el ticket y el PR final. | $\ge 90\%$ |
| **ACI (*Agent Churn Index*)** | Promedio de iteraciones o auto-correcciones circulares por tarea resuelta. | $< 3$ iteraciones/tarea |
| **GDR (*Gate Discrepancy Rate*)** | Tasa de inconsistencias entre la telemetría del orquestador y los logs de Git/CI. | $0\%$ (tolerancia cero) |
| **FPR / FNR (*False Positive/Negative Rate*)** | Tasa de bloqueos indebidos o riesgos no detectados en los gates gobernados. | Calibrado según apetito de riesgo |
