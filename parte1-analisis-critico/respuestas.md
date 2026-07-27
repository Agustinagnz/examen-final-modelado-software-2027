# Parte 1: Analisis Critico - Respuestas

**Nombre del estudiante:**  Agustina González
**Fecha:** 27/07/2026

---

## Error 1

**Ubicacion:** Actores

**Descripcion:** La base de datos no es un actor, los actores son externos al sistema. Una base de datos es un componente interno del sistema, no una entidad externa que interactúe con él. 

**Correccion:** El actor principal debe ser únicamente Visitante.

---

## Error 2

**Ubicacion:** Precondiones

**Descripcion:** La precondición "El visitante debe tener una invitacion de otro usuario registrado" no es coherente con el caso de uso de registro de usuario, ya que introduce una restricción funcional que no forma parte del objetivo del caso de uso ni resulta necesaria para poder iniciarlo.

**Correccion:** Eliminar esa precondición o reemplazarla por una condición realmente necesaria para iniciar el registro (por ejemplo, que el visitante no tenga una sesión iniciada, si aplica al sistema).

---

## Error 3

**Ubicacion:** Precondiciones

**Descripcion:** La precondición "El visitante debe haber visitado al menos 5 artículos en los últimos 30 días" no constituye una condición previa necesaria para ejecutar el caso de uso de registro de usuario. Es una restricción ajena al proceso de creación de una cuenta.

**Correccion:** Eliminar esa precondición y mantener únicamente condiciones indispensables para comenzar el caso de uso.

---

## Error 4

**Ubicacion:** Flujo principal

**Descripcion:** En el paso 5, el sistema guarda la información inmediatamente después de que el usuario envía el formulario, sin realizar previamente ninguna validación (por ejemplo, verificar que el email no exista o que los datos sean válidos). 

**Correccion:** Incorporar un paso de validación antes de almacenar la información y continuar con el registro únicamente si las validaciones son satisfactorias.

---

## Error 5

**Ubicacion:** Flujos alternativos

**Descripcion:** No se indican flujos alternativos, aunque existen escenarios alternativos previsibles, como el ingreso de datos inválidos o un email ya registrado. Estos comportamientos deben contemplarse mediante flujos alternativos.

**Correccion:** Agregar los flujos alternativos correspondientes para los casos de validación fallida, permitiendo al visitante corregir la información y continuar con el registro.

---

##Error 6

**Ubicación:** Excepciones

**Descripción:** La oración "Si el email ya existe en el sistema, el registro se ignora sin mostrar ningún mensaje" no constituye una excepción, sino un resultado esperado de una validación de negocio. Debe tratarse como un flujo alternativo que informe el error al usuario y le permita corregir el dato.

**Correcion:**  Una opción sería considerar este caso a la sección como un Flujo alternativo, indicando que el sistema informa que el email ya está registrado y solicita ingresar uno diferente.

