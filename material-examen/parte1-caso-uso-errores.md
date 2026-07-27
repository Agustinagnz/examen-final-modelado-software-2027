# Parte 1 del Examen: Analisis Critico

**Tiempo:** 20 minutos  
**Puntaje:** 20% del examen final

---

## Consigna

A continuacion se presenta un caso de uso con **7 errores intencionales**. Tu tarea es:

1. Identificar minimo 5 errores
2. Explicar por que es un error
3. Proponer la correccion apropiada

Usa este formato:

```text
ERROR #1:
Ubicacion: [Seccion donde esta el error]
Descripcion: [Que esta mal]
Correccion: [Como deberia ser]
```

---

## Caso de Uso con Errores

### CU-10: Registrar Usuario

**Actor Principal:** Base de Datos, Visitante

**Descripcion:**  
La base de datos permite que un visitante se registre en la plataforma creando una cuenta de usuario.

**Precondiciones:**
- El visitante debe tener una invitacion de otro usuario registrado
- El visitante debe haber visitado al menos 5 articulos en los ultimos 30 dias

**Flujo Principal:**
1. El Visitante accede a la pagina de registro
2. El sistema muestra el formulario con campos: nombre, email, contraseña y biografia
3. El Visitante completa todos los campos del formulario
4. El Visitante hace clic en "Crear cuenta"
5. El sistema guarda la informacion inmediatamente
6. El sistema muestra mensaje "Cuenta creada con exito"
7. Fin del caso de uso

**Flujos Alternativos:**
- Ninguno

**Postcondiciones:**
- La cuenta queda registrada en la base de datos
- Se envia un email de notificacion a todos los usuarios de la plataforma
- Se crea automaticamente un articulo de bienvenida en nombre del nuevo usuario
- El sistema inicia sesion automaticamente con la nueva cuenta

**Excepciones:**
- Si el email ya existe en el sistema, el registro se ignora sin mostrar ningun mensaje

---

## Recordatorio

Busca errores en:
- Actores
- Precondiciones
- Flujo principal
- Flujos alternativos
- Postcondiciones
- Excepciones
