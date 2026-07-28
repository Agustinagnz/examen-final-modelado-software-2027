# Parte 3: Notas para Defensa Oral

## Presentacion del Proyecto

- Nombre del proyecto: Sistema de blog
  
- Feature principal: Se implementó un sistema de "Reporte de Contenido Inapropiado" que permite a los usuarios registrados denunciar artículos o comentarios que consideren inadecuados.
Cada reporte es revisado por un moderador, quien decide si corresponde aprobarlo o rechazarlo. Finalmente, el usuario que realizó la denuncia recibe una notificación con la resolución adoptada.

- Arquitectura general: Arquitectura MVC.

## Decisiones de Diseno

- Estructura de clases: 

Las principales clases del modelo son:

* Usuario
* Moderador
* Articulo
* Comentario
* ReporteContenido
* Notificacion
* MotivoReporte
* EstadoReporte

Estas clases representan la información del dominio y las reglas propias del negocio.

- Uso de MVC: 

Modelo (Model)

Representa las entidades del dominio y las reglas del negocio.

Ejemplos:

* ReporteContenido
* Usuario
* Moderador

Vista (View)

Participan las siguientes vistas:

* VistaReporteContenido
* VistaRevisionReportes
* VistaNotificaciones

Su responsabilidad consiste en presentar información al usuario y capturar sus acciones.

No contienen lógica de negocio.

Controlador (Controller)

Participa el:

* ControladorReportes

Es responsable de coordinar todo el caso de uso.

Entre sus tareas se encuentran:

* validar solicitudes;
* consultar la persistencia;
* crear reportes;
* actualizar estados;
* solicitar notificaciones.
  
- Patrones identificados: El patrón arquitectónico principal es MCV. Permite separar presentación, lógica del negocio y modelo.

## Defensa del Caso de Uso

- Que funcionalidad modele: Reportar Contenido Inapropiado
  
- Que clases agregue:
  
ReporteContenido: Es la entidad principal de la funcionalidad.

Representa cada denuncia realizada por un usuario e incorpora toda la información necesaria para su seguimiento:

* motivo
* descripción
* estado
* fecha de creación
* fecha de revisión

Centraliza el comportamiento asociado al ciclo de vida del reporte mediante operaciones como registrar() y actualizarEstado().

RepositorioReportes: Representa la capa de persistencia responsable de almacenar y recuperar reportes.

Su responsabilidad incluye:

* guardar nuevos reportes;
* verificar reportes activos duplicados;
* actualizar el estado tras la revisión.

Se incorpora para mantener desacoplado el modelo del mecanismo de almacenamiento, siguiendo una arquitectura MVC con acceso a datos mediante repositorios.

GestorNotificaciones: Encapsula toda la lógica relacionada con las notificaciones.

Permite evitar que la clase ReporteContenido conozca cómo se envían los avisos al moderador y al usuario.

Esto favorece el principio de responsabilidad única.

MotivoReporte: Es una enumeración que restringe los valores posibles del motivo del reporte:

* Spam
* Ofensivo
* Derechos de Autor
* Otro

Su utilización evita cadenas de texto arbitrarias y mejora la consistencia del sistema.

EstadoReporte: Define los estados permitidos durante el ciclo de vida del reporte:

* Pendiente
* Aprobado
* Rechazado

Facilita las validaciones y reduce errores.


- Como se relacionan: Las relaciones representan dependencias reales del dominio

* un usuario puede crear varios reportes;
* un moderador puede revisar múltiples reportes;
* un reporte está asociado a un único contenido denunciado;
* un usuario puede recibir múltiples notificaciones.

Estas cardinalidades reflejan correctamente las reglas del negocio.

## Conceptos a Repasar

- Actor primario y secundario:
  Actor primario: Es quien inicia un caso de uso para alcanzar un objetivo. En este diseño, el actor primario es el "Usuario Registrado", ya que comienza el proceso al reportar un contenido.
  Actor secundario: Es un actor que participa en el caso de uso brindando un servicio o completando una actividad iniciada por otro actor. En este diseño, el "Moderador" interviene revisando los reportes registrados.

- Precondicion y postcondicion
  Las precondiciones son los requisitos que deben cumplirse antes de ejecutar un caso de uso. Por ejemplo, el usuario debe haber iniciado sesión.
  Las postcondiciones describen el estado del sistema una vez finalizado el caso de uso. Por ejemplo, el reporte queda registrado y el usuario recibe una notificación con la resolución.

- Diferencia entre diagrama de clases y secuencia:
  
El diagrama de clases modela la estructura estática de un sistema orientado a objetos. Define qué elementos existen, sus características (atributos), sus responsabilidades (métodos) y cómo se relacionan entre sí. 

El diagrama de secuencia modela el comportamiento dinámico del sistema a través del tiempo. Muestra cómo los objetos interactúan entre sí mediante el intercambio de mensajes en un escenario o caso de uso específico.

- Principios SOLID basicos:
  
Single Responsibility Principle (SRP)

Definición: Cada clase debe tener una única responsabilidad y un único motivo para cambiar.

Aplicación

* ReporteContenido administra únicamente la información del reporte.
* RepositorioReportes administra únicamente la persistencia.
* GestorNotificaciones administra únicamente las notificaciones.

Ejemplo: Si cambia la forma de enviar notificaciones, solo debe modificarse GestorNotificaciones.

Open/Closed Principle (OCP)

Definición: Las clases deben estar abiertas para extensión y cerradas para modificación.

Aplicación

Es posible agregar nuevos motivos de reporte o nuevos tipos de notificación sin modificar la estructura principal.

Ejemplo

Agregar el motivo "Desinformación" implica extender la enumeración correspondiente sin alterar el flujo del caso de uso.

Liskov Substitution Principle (LSP)

Definición: Una subclase debe poder reemplazar a su clase base sin alterar el comportamiento esperado.

Aplicación

Moderador hereda de Usuario.

En cualquier contexto donde se espere un Usuario, un Moderador puede utilizarse sin inconvenientes.

Interface Segregation Principle (ISP)

Definición: Las clases no deben depender de interfaces que no utilizan.

Aplicación

Cada componente expone únicamente las operaciones necesarias para cumplir su responsabilidad.

Por ejemplo, RepositorioReportes ofrece operaciones relacionadas con reportes y no incorpora métodos ajenos a esa función.

Dependency Inversion Principle (DIP)

Definición: Los módulos de alto nivel deben depender de abstracciones y no de implementaciones concretas.

Aplicación

ControladorReportes delega las operaciones de persistencia y notificación a componentes especializados.

En una implementación real, estos componentes serían interfaces implementadas por clases concretas e inyectadas mediante un mecanismo de inversión de control.

