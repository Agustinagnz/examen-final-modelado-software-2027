# Parte 2 del Examen: Diseno Practico

**Tiempo:** 60 minutos  
**Puntaje:** 50% del examen final

---

## Objetivo

Disenar una nueva funcionalidad para tu proyecto utilizando la documentacion UML trabajada en la materia.

---

## Entregables

Debes crear:

1. **Caso de Uso Completo**
2. **Diagrama de Clases**
3. **Diagrama de Secuencia**

---

## Opciones Disponibles

### Opcion A: Busqueda de Articulos (Nivel Basico)

**Requisito:**
"Agregar funcionalidad de 'Buscar articulos por titulo o palabra clave' para todos los visitantes"

**Descripcion:**
Los visitantes y usuarios pueden buscar articulos ingresando terminos en una barra de busqueda. El sistema devuelve los articulos cuyo titulo o contenido coincida parcial o totalmente con el termino buscado, ordenados por relevancia o fecha de publicacion.

---

### Opcion B: Valoracion de Articulos (Nivel Intermedio)

**Requisito:**
"Implementar sistema de 'Valorar articulo con puntuacion de 1 a 5 estrellas' para usuarios registrados"

**Descripcion:**
Los usuarios registrados pueden calificar articulos con una puntuacion de 1 a 5 estrellas. El sistema debe calcular y mostrar el promedio de valoraciones de cada articulo. Un mismo usuario no puede valorar dos veces el mismo articulo, pero si puede cambiar su valoracion anterior.

---

### Opcion C: Reporte de Contenido (Nivel Avanzado)

**Requisito:**
"Agregar sistema de reporte de contenido inapropiado con revision de moderador"

**Descripcion:**
Los usuarios registrados pueden reportar un articulo o comentario que consideren inapropiado, seleccionando un motivo (spam, ofensivo, derechos de autor, otro). El sistema notifica al moderador, quien revisa el contenido reportado y puede aprobarlo o rechazarlo. El usuario que reporto recibe una notificacion con la resolucion final.

---

## Requisitos Minimos del Caso de Uso

Incluye:
- ID y nombre
- Actor principal
- Actores secundarios si aplica
- Descripcion
- Precondiciones
- Flujo principal numerado
- Al menos 2 flujos alternativos
- Postcondiciones

---

## Requisitos Minimos del Diagrama de Clases

Incluye:
- Clases nuevas necesarias
- Atributos principales
- Metodos principales
- Relaciones con clases existentes
- Cardinalidad

---

## Requisitos Minimos del Diagrama de Secuencia

Incluye:
- Flujo principal del caso de uso
- Minimo 4 participantes
- Mensajes claros entre objetos
- Orden temporal correcto

---

## Entrega

Completa los archivos en parte2-diseno-practico/.
