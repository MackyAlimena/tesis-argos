# ADR-005: Marco de Evaluación, Calibración y Verificación del Orquestador y Enjambre de Agentes (Hive)

- **Estado:** Aceptado
- **Fecha:** 2026-08-22
- **Autor:** Macarena Alimena

## Contexto
En el desarrollo de software tradicional, la evaluación se enfoca en el *producto* final (compilación, unit tests, linters). En el desarrollo asistido por enjambres de agentes de IA (*hives* u orquestadores multi-agente como MetaGPT, CrewAI, LangGraph o motores propietarios), el objeto gobernado es el **proceso de producción**. 

Un sistema agéntico puede producir código que pase los tests funcionales, pero haber violado fronteras de rol, perdido contexto de seguridad, sufrido alucinaciones de dependencias o emitido trazas falsas/incompletas. Se requiere un marco sistemático para calibrar y evaluar el comportamiento del orquestador y la fidelidad de su telemetría antes y durante su operación.

## Decisión
Se establece un protocolo de **Evaluación y Calibración del Hive/Orquestador** estructurado en cuatro ejes:

1. **Calibración de Topología y Pases de Mano (A0):**
   - *Fidelidad de frontera de rol (Role Boundary Adherence):* Asegurar que ningún agente invada competencias asignadas a otro (ej. agente de testing alterando lógica sin delegación).
   - *Deriva y retención de contexto (Context Drift & Loss):* Medir la degradación semántica de restricciones y requerimientos de seguridad en los pases de mano inter-agente.
   - *Segregación real de funciones:* Prohibir la asunción de que un agente revisor provee independencia si comparte arquitectura/pesos con el agente emisor sin supervisión humana.

2. **Calibración de Quality Gates Gobernados y Guardrails (A2 / A3):**
   - *Curva de Falsos Positivos vs. Falsos Negativos:* Calibración de umbrales en detectores de alucinaciones (*slopsquatting*), SCA y linters sobre un conjunto de prueba (*golden dataset*) para evitar *bypass fatigue*.
   - *Mecanismos de contención (Circuit Breakers / Kill-switches):* Corte automático ante bucles infinitos, exceso de consumo de tokens o intentos de acceso a archivos restringidos.

3. **Verificación de la Fidelidad de Telemetría (A3):**
   - *Audit Trail Fidelity:* Verificación determinística de correspondencia 1:1 entre los eventos reportados en las trazas del orquestador (`trace.json`) y las acciones reales en el control de versiones (Git commits) y pipelines de CI/CD.
   - *Completitud de procedencia:* Garantizar la inclusión de metadatos indispensables (agente, modelo, prompt, diff, nivel de autonomía asignado, tiempo de retención).

4. **Protocolo de Validación Experimental (Testbench de Gobernanza):**
   - *Blind Reconstruction Tests:* Auditoría ciega de decisiones sobre PRs generados por el hive.
   - *Inyección de Fallos (Fault Injection / Red Teaming):* Pruebas de estrés inyectando paquetes falsos y directivas ambiguas para evaluar la capacidad de contención y escalamiento al humano.
   - *KRIs del Orquestador:* Incorporación al tablero de indicadores de *Human Intervention Rate (HIR)*, *Context Retention Score* y *Agent Churn Index*.

## Consecuencias
- El orquestador deja de ser una "caja negra" y pasa a ser un componente calibrado y auditable bajo el ciclo PDCA (ISO 9001 / ISO 42001).
- Se formaliza el banco de pruebas de gobernanza en la carpeta `evaluation/hive-calibration/`.
