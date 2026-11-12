# Requisitos de MediGest

**Instituto i3 · SQA · Sesión 6**

Especificación propuesta, no implementada ni validada. Prioridad **Alta**: esencial; **Media**: objetivo de calidad relevante. Las sesiones autenticadas son precondiciones del sistema futuro, no funcionalidades desarrolladas en este repositorio.

## Requisitos funcionales

| ID | Actor | Descripción | Prioridad | Criterios de aceptación | Caso asociado |
|---|---|---|---|---|---|
| RF-01 | Paciente | Consultar disponibilidad por médico y fecha. | Alta | Mostrar únicamente horarios disponibles del médico y fecha seleccionados; si no existen, mostrar «Sin disponibilidad». | CP-01 |
| RF-02 | Paciente | Reservar una cita en un horario disponible. | Alta | Asociar la cita al paciente autenticado y al horario elegido; mostrar confirmación y retirar ese horario de la disponibilidad. Rechazar un horario ocupado sin generar otra cita. | CP-02 |
| RF-03 | Paciente | Reprogramar una cita propia activa. | Alta | Cambiarla a un horario disponible, liberar el anterior y confirmar el cambio. Si el destino está ocupado, conservar la cita original. Rechazar citas ajenas. | CP-03 |
| RF-04 | Paciente | Cancelar una cita propia activa. | Alta | Marcarla como cancelada, liberar el horario y confirmar la operación. Rechazar una nueva cancelación de esa cita y cualquier intento sobre citas ajenas. | CP-04 |
| RF-05 | Administrador | Crear, modificar y eliminar horarios médicos. | Alta | Permitirlo solo al administrador; rechazar intervalos solapados para un mismo médico y bloquear modificación o eliminación de horarios con citas activas. | CP-05 |
| RF-06 | Paciente | Consultar y actualizar sus datos personales. | Media | El paciente autenticado puede consultar y modificar únicamente sus propios datos. Se deben validar los campos obligatorios y rechazar accesos a información de otros pacientes. | CP-06 |
## Requisitos no funcionales

| ID | Descripción | Prioridad | Criterios de aceptación propuestos | Validación |
|---|---|---|---|---|
| RNF-01 | Restringir operaciones según identidad y rol. | Alta | Denegar operaciones protegidas sin sesión, gestión de horarios a pacientes y acceso de pacientes a citas ajenas; no revelar datos de dichas citas. | Pendiente; los CP incluyen variantes parciales de autorización, no una evaluación de seguridad completa. |
| RNF-02 | Responder con rapidez a consultas de disponibilidad. | Media | En un futuro entorno de ensayo documentado, con 20 usuarios concurrentes y 1.000 horarios cargados, al menos el 95 % de 100 consultas debe mostrar resultados en ≤2 segundos desde el envío. Registrar configuración del entorno y condiciones de red antes de medir. | Pendiente; requiere sistema, datos y ensayo de rendimiento. |
| RNF-03 | Facilitar el uso mediante teclado. | Alta | En los cinco flujos RF, permitir completar acciones sin ratón, con foco visible, orden lógico y sin trampas de teclado. WCAG 2.1 AA será referencia objetivo; estos criterios no acreditan conformidad completa. | Pendiente; requiere interfaz y evaluación de accesibilidad. |

## Reglas y límites

- Una cita activa es una reserva confirmada y no cancelada; reprogramarla conserva su identidad y estado activo.
- Un horario pertenece a un médico, tiene inicio anterior al fin y admite una única cita activa. Intervalos adyacentes no se consideran solapados.
- No se especifican historias clínicas, pagos, notificaciones ni atención de urgencias.
- Los cinco CP aportan cobertura funcional básica, no exhaustiva. Los RNF requieren verificaciones adicionales futuras.
- Todo cambio de requisito debe mantener su ID, actualizar el CP relacionado y registrarse en [auditoría](auditoria.md) con evidencia real cuando exista.
