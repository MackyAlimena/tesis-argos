# ADR-003: Quality Gates Gobernados por Autonomía vs. Quality Gates Tradicionales

- **Estado:** Aceptado
- **Fecha:** 2026-08-22
- **Autor:** Macarena Alimena

## Contexto
En revisiones técnicas surge la observación de que el control en pipelines equivale a "Quality Gates de CI/CD".

## Decisión
Se clarifica la distinción conceptual:
- **Punto de inyección técnico:** Quality Gate en CI/CD.
- **Aporte de Gobernanza (ARGOS):** Parametrización dinámica del gate según el nivel de autonomía (A0–A4), inspección de trazas y contexto del LLM, detección de riesgos específicos (alucinaciones de dependencias, *slopsquatting*) y emisión de evidencia estructurada auditable *ex post*.
