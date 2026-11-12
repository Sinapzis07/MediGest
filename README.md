# MediGest – Sistema de Gestión de Citas Médicas

**Instituto i3 · Módulo de Calidad del Software (SQA) · Sesión 6**

Proyecto académico exclusivamente documental sobre un sistema propuesto para organizar citas médicas. No contiene aplicación, frontend, backend ni base de datos; tampoco acredita funcionalidades implementadas o pruebas ejecutadas.

## Objetivo general

Demostrar gestión de configuración, requisitos, trazabilidad, planificación de pruebas y auditoría mediante documentos coherentes y un flujo de control de versiones en GitHub.

## Funcionalidades propuestas

1. Consultar disponibilidad de médicos (RF-01).
2. Reservar una cita médica (RF-02).
3. Reprogramar una cita propia (RF-03).
4. Cancelar una cita propia (RF-04).
5. Administrar horarios médicos (RF-05).

## Usuarios del sistema propuesto

- **Pacientes:** consultar disponibilidad y gestionar sus propias citas.
- **Médicos:** consultar su agenda de citas, como contexto del sistema; esta consulta no se detalla en los cinco RF de esta entrega.
- **Administradores:** administrar horarios médicos.

## Equipo y responsabilidades

| Integrante | Nombre editable | Rol | Responsabilidad |
|---|---|---|---|
| 1 | [Nombre del integrante 1] | Líder del proyecto | Coordinar alcance, coherencia y aprobación de entregables. |
| 2 | [Nombre del integrante 2] | Responsable de documentación | Elaborar y mantener los documentos. |
| 3 | [Nombre del integrante 3] | Gestor de cambios y auditor SQA | Controlar versiones, registrar cambios y verificar trazabilidad. |

Los roles del equipo son distintos de los roles de usuario del sistema. Quien revise un cambio debe ser distinto de su autor; si el auditor es autor, otro integrante realizará la revisión.

## Documentos y trazabilidad

- [Requisitos](requisitos.md): RF, RNF, prioridades y criterios de aceptación.
- [Plan de pruebas](plan-pruebas.md): cinco casos propuestos, todos pendientes.
- [Auditoría](auditoria.md): plantilla para registrar cambios y evidencias reales.

Cadena de trazabilidad: **RF → CP → documento modificado → commit real → PR real → revisión**. Los RNF no tienen casos propios en esta entrega y su validación queda pendiente.

## Gestión de configuración propuesta

La línea base documental estará formada únicamente por estos cuatro archivos. GitHub conservará su historial cuando el equipo los publique manualmente. Para cada cambio, indicar documento, sección, motivo e IDs afectados; proponerlo en una rama, solicitar revisión mediante Pull Request y registrar las referencias reales en la auditoría. La línea base se considerará aprobada solo tras una revisión efectiva, no por la creación de estos documentos.
