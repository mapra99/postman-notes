# Curso de Postman

## Conceptos de APIs
### Protocolo HTTP
Un protocolo son una serie de reglas que especifican cómo va a ser la comunicación entre dos entes. HTTP fue creado exclusivamente para la web, significa Hypertext Transfer Protocol.

HTTP tiene una serie de verbos que indican acciones:
- **GET** sirve para solicitar datos o algún recurso al servidor.
- **HEAD** es *una parte pequeña de GET*. HEAD trae headers, no datos.
- **POST** sirve para enviar datos sobre un recurso al servidor. Se usa para la creación de recursos
- **PUT** sirve para reemplazar por completo a un recurso.
- **PATCH** sirve para actualizar algunos atributos del recurso.
- **DELETE** elimina un recurso

Una vez enviada una petición HTTP, la respuesta de esa petición va acompañada de un status. Cada status tiene un código estándar:
- **1xx**: Indican que la petición está en proceso, no ha terminado
- **2xx**: Indican que la petición se procesó satisfactoriamente.
- **3xx**: Indican que la petición requiere alguna acción adicional por ejecutar. Por ejemplo en web se usa mucho para indicar redirecciones. En APIs no se suelen trabajar redirecciones porque las APIs no conservan estados (por ejemplo no conservan una sesión).
- **4xx**: Indican errores del lado del cliente. Un parámetro faltante, uno mal ingresado, etc.
- **5xx**: Indican errores del lado del servidor.

Los códigos más usados:
- **200** es el estatus *todo está bien*.
- **201** se retorna cuando un recurso fue creado satisfactoriamente.
- **204** indica que la petición se procesó completamente pero no hay contenido para devolver en la respuesta
- **400** *Bad Request*, algo quedó mal en la solicitud. Por lo general el contenido de la respuesta indica qué error hubo.
- **401** *Unauthorized*, no se puede procesar la solicitud porque no se ha autenticado con el servidor.
- **403* *Forbidden*, ya está autenticado pero no está autorizado.
- **404** *Not found*, no se encontró el recurso.
- **500** *Servr error*

### Arquitectura REST
REST es un modelo de arquitectura de información con el que se suelen construir APIs. REST provee una forma de estructurar la API alrededor de estos conceptos:

- Recurso: Es la representación de un objeto o de una entidad en el sistema.
- Colecciones: Conjunto de recursos
- URLs: Uniform Resource Locator es la ruta en la cual puede ubicarse un recurso y hacer operaciones sobre él
- Endpoints: Los endpoints son los puntos de comunicación que dispone la API para conectarse. En REST cada endpoint tiene una URL, y sigue una estructura que combina los recursos en cuestión con las operaciones que se pueden hacer sobre ellos.
**Ejemplo** Existe el recurso `courses` y el recurso `videos`.
- `GET /courses` trae la colección de cursos.
- `POST /courses` crea un nuevo recurso, un nuevo curso.
- `DELETE /courses` elimina todos los cursos

- `GET /courses/:id` trae el curso con id especificada. Lo mismo para los demás verbos

- `GET /courses/:id/videos` trae los videos del curso con id dado
- `GET /courses/:course_id/videos/:video_id` trae el video con id dado, del curso con id dado
