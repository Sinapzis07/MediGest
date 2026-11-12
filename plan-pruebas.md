# Plan de pruebas de MediGest

**Instituto i3 · SQA · Sesión 6**

Plan documental para una implementación futura. **No se ejecutaron pruebas del sistema: no existe una aplicación desarrollada en este proyecto.** Todos los casos están en estado **Pendiente**; sus resultados son expectativas, no observaciones.

## Condiciones futuras de ejecución

Será necesario disponer de un entorno de ensayo, sesiones de dos pacientes (P1 y P2), un médico M1, un administrador A1 y datos ficticios. H1 y H2 representan horarios distintos disponibles; H3, uno ocupado. Restaurar los datos antes de cada CP y mantener los cambios entre los pasos del mismo caso; las sesiones independientes no reinician los datos. No utilizar datos personales reales.

Para CP-05, preparar en una misma fecha futura un horario libre de 09:00 a 09:30 y uno persistente con cita activa de 10:00 a 10:30. Crear el nuevo horario de 11:00 a 11:30, modificarlo a 11:30–12:00 y eliminarlo. Intentar después crear 10:15–10:45 para comprobar el solapamiento con el horario persistente.

## Casos propuestos

| ID | Requisito | Precondiciones y datos | Pasos de prueba | Resultado esperado | Estado |
|---|---|---|---|---|---|
| CP-01 | RF-01 | P1 autenticado; M1 con H1 libre y H3 ocupado en una fecha de ensayo; otra fecha sin horarios. | 1. Seleccionar M1 y la fecha de ensayo.<br>2. Consultar disponibilidad.<br>3. Consultar la fecha sin horarios. | Aparece H1, no H3; los resultados corresponden al médico y fecha seleccionados. La segunda consulta muestra «Sin disponibilidad». | Pendiente |
| CP-02 | RF-02 | P1 autenticado; H1 libre y H3 ocupado. | 1. Seleccionar H1 y confirmar reserva.<br>2. Consultar la cita y la disponibilidad.<br>3. Intentar reservar H3. | Se confirma una única cita de P1 en H1 y H1 deja de estar disponible. El intento sobre H3 se rechaza sin crear otra cita. | Pendiente |
| CP-03 | RF-03 | P1 autenticado con cita activa C1 en H1; H2 libre; H3 ocupado; C2 pertenece a P2. | 1. Reprogramar C1 de H1 a H2.<br>2. Verificar cita y disponibilidad.<br>3. Intentar mover C1 a H3.<br>4. Intentar reprogramar C2. | C1 conserva identidad y estado activo en H2; H1 queda libre. El intento sobre H3 conserva C1 en H2. El acceso a C2 se rechaza sin revelar sus datos ni modificarla. | Pendiente |
| CP-04 | RF-04 | P1 autenticado con cita activa C1 en H1; C2 pertenece a P2. | 1. Cancelar C1.<br>2. Consultar su estado y H1.<br>3. Repetir la cancelación.<br>4. Intentar cancelar C2. | C1 queda cancelada y H1 disponible. La repetición se rechaza sin alterar datos. C2 no se revela ni modifica. | Pendiente |
| CP-05 | RF-05 | A1 y P1 con sesiones separadas; M1 con un horario libre y otro con cita activa. | 1. Como A1, crear un horario válido sin solapamiento.<br>2. Modificarlo y eliminarlo mientras está libre.<br>3. Intentar crear un intervalo solapado.<br>4. Intentar modificar y eliminar el horario con cita activa.<br>5. Como P1, intentar crear, modificar y eliminar horarios. | A1 puede realizar las tres operaciones sobre horarios libres válidos. Se rechazan solapamientos, cambios o eliminación de horarios con citas activas y todas las operaciones administrativas intentadas por P1. | Pendiente |
| CP-06 | RF-06 | P1 autenticado; formulario de perfil de P1 disponible; P2 con perfil completo existente. | 1. Intentar guardar el perfil de P1 dejando campos obligatorios vacíos o con formatos inválidos.<br>2. Corregir con datos válidos y guardar.<br>3. Intentar acceder o modificar los datos de P2 (ej. manipulando URL o ID). | El sistema rechaza el paso 1 mostrando alertas de validación de campos. El paso 2 actualiza a P1 exitosamente. El paso 3 es bloqueado por permisos sin exponer datos de P2. | Pendiente |

## Registro futuro de ejecución

Para cada CP, completar cuando realmente se ejecute: **fecha, ejecutor, versión/commit probado, entorno, resultado observado, evidencia e incidencia**. Actualmente todos estos datos están **pendientes**. Solo una ejecución real permitirá cambiar el estado a Aprobado, Fallido o Bloqueado.

Los CP-03, CP-04 y CP-05 cubren parcialmente RNF-01. No verifican todas las condiciones de seguridad. RNF-02 y RNF-03 quedan fuera de estos cinco casos y necesitan ensayos específicos futuros. La revisión de estos documentos no equivale a ejecutar los CP.
