# ADR-004: Descarte de Agente Auditor de Compliance y Reencuadre en Conformance Engine

- **Estado:** Aceptado
- **Fecha:** 2026-08-22
- **Autor:** Macarena Alimena

## Contexto
Surgió la sugerencia de construir un "agente orquestador que audite normas ISO 27001/42001 en una empresa".

## Decisión
Se descarta construir un bot generalista de auditoría documental (evitando el desvío hacia un proyecto de producto RAG). Se reencuadra la idea dentro del artefacto **A3** como un **Motor Evaluador de Conformidad en CI/CD (Governance Gatekeeper)**, que audita automáticamente si las trazas del agente que escribe código cumplen con la matriz A2.
