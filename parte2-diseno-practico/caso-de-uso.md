# Parte 2: Caso de Uso

**ID:**  CU-01
**Nombre:** Reportar Contenido

**Actor Principal:**  Usuario registrado
**Actores Secundarios:** Moderador

## Descripcion

Permite que un usuario registrado informe un artículo o comentario que considere inapropiado, seleccionando un motivo (spam, ofensivo, derechos de autor, otro). El sistema registra el reporte, notifica al moderador para su revisión, quien revisa el contenido reportado y puede aprobarlo o rechazarlo. Y posteriormente informa al usuario que realizó el reporte sobre la resolución adoptada. 
Para que la funcionalidad se incorpore de forma más limpia se considerará que un usuario puede reportar varias veces contenidos diferentes, pero no puede registrar dos reportes activos sobre el mismo contenido.


## Precondiciones

1. El usuario debe haber iniciado sesión.
2. El artículo o comentario debe existir.
3. El contenido debe encontrarse disponible.
4. El usuario no debe tener un reporte activo sobre ese mismo contenido.

## Flujo Principal

1. El Usuario registrado visualiza un artículo o comentario.
2. El Usuario registrado selecciona la opción "Reportar contenido".
3. El sistema muestra el formulario de reporte.
4. El Usuario registrado selecciona el motivo del reporte.
5. El Usuario registrado confirma el envío.
6. El sistema valida la información ingresada.
7. El sistema verifica que el usuario no haya reportado previamente el mismo contenido.
8. El sistema registra el reporte con estado "Pendiente".
9. El sistema asocia el reporte al usuario y al contenido correspondiente.
10. El sistema genera una notificación dirigida al Moderador.
11. El Moderador accede al listado de reportes pendientes.
12. El Moderador selecciona un reporte para revisarlo.
13. El sistema muestra toda la información del reporte y del contenido denunciado.
14. El Moderador decide aprobar o rechazar el reporte.
15. El sistema actualiza el estado del reporte con la resolución correspondiente.
16. El sistema registra la fecha y el moderador responsable de la revisión.
17. El sistema genera una notificación para el Usuario registrado con el resultado del proceso.
18. El caso de uso finaliza.

## Flujos Alternativos

### FA1
### 7a. Al realizar la verificación, el sistema detecta un reporte duplicado

7a.1. El sistema detecta un reporte activo del mismo usuario sobre el mismo contenido.

7a.2. El sistema informa que ya existe un reporte pendiente.

7a.3. El caso de uso finaliza.

### FA2

### 14a. El moderador aprueba el reporte

14a.1. El sistema marca el reporte como "Aprobado".

14a.2. El sistema registra la resolución.

14a.3. Continúa en el paso 16.


### 14b. El moderador rechaza el reporte

14b.1. El sistema marca el reporte como "Rechazado".

14b.2. El sistema registra la resolución.

14b.3. Continúa en el paso 16.


## Postcondiciones

1. El reporte queda registrado en el sistema.
2. El estado del reporte refleja la decisión del moderador.
3. Se conserva el historial de la revisión.
4. El usuario recibe una notificación con la resolución.
5. El moderador responsable queda asociado al reporte revisado.
