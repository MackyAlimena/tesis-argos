# ADR-001: Adopción de Design Science Research (DSR) e Investigación-Acción en Caso Único

- **Estado:** Aceptado
- **Fecha:** 2026-08-14
- **Autor:** Macarena Alimena
- **Contexto:** Trabajo de Grado individual en Ingeniería en Informática (Orientación Gestión), Universidad Austral.

## Contexto y Problema
El trabajo propone un marco de gobernanza (artefacto socio-técnico) para supervisar la delegación de tareas a agentes de IA en el desarrollo de software. Tradicionalmente, los tribunales evalúan proyectos de grado como "desarrollo de un producto de software" o "estudio teórico". Se requería un marco metodológico formal que valide la construcción y evaluación de artefactos de gestión e ingeniería.

## Decisión
Se adopta **Design Science Research (DSR)** (Hevner et al., 2004; Peffers et al., 2007) como paradigma principal de investigación, complementado con **Investigación-Acción sobre Caso Único** (Yin, 2018; Runeson & Höst, 2009) en una PyME tecnológica real (Garage Deep Analytics).

## Mitigación de Sesgo por Doble Rol (Practitioner-Researcher)
1. Pre-registro de criterios de éxito en el Plan de Trabajo.
2. ~~Validación externa mediante Panel de Expertos tipo Delphi (auditores 27001/42001, tech leads).~~ **Superseded por [ADR-007](ADR-007-validacion-externa-auditoria-en-lugar-de-delphi.md) (2026-08-30):** la validación externa se practica mediante auditoría externa de certificación ISO/IEC 27001 sobre el proceso de desarrollo intervenido más entrevistas semiestructuradas a 4 especialistas externos. La función de la mitigación no cambia; cambia el instrumento.
3. Triangulación de fuentes (métricas de repositorio + entrevistas + auditoría documental).
4. Bitácora / diario de investigación separando intervenciones de ingeniería de las de investigación.
