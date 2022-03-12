## PARTE I. - JUGANDO A SER UN CLIENTE HTTP
Abra una terminal Linux o consola de comandos Windows.
Realice una conexión síncrona TCP/IP a través de Telnet al siguiente servidor:
Host: www.escuelaing.edu.co
Puerto: 80
Teniendo en cuenta los parámetros del comando telnet:
```
telnet HOST PORT
```
![image](https://user-images.githubusercontent.com/25957863/157165706-60783fa1-0a95-4162-9bfb-ea44153c8b0d.png)

Antes de que el servidor cierre la conexión por falta de comunicación:
Revise la página 36 del RFC del protocolo HTTP, sobre cómo realizar una petición GET. Con esto, solicite al servidor el recurso ‘sssss/abc.html’, usando la versión 1.0 de HTTP.

El comando usado fue: 
```
GET /sssss/abc.html HTTP/1.0
```

Asegúrese de presionar ENTER dos veces después de ingresar el comando.
Revise el resultado obtenido. ¿Qué codigo de error sale?, revise el significado del mismo en la lista de códigos de estado HTTP.

![image](https://user-images.githubusercontent.com/25957863/157165577-f16d0601-8137-4cf9-a327-78ff292daab2.png)

El codigo que salio fue el 400 lo que significa que **El servidor no logro encontrar o procesar la solicitud por un error aparente del cliente como sintaxis, tamaño o enrutamiento.**

¿Qué otros códigos de error existen?, ¿En qué caso se manejarán?

Codigos de error existen los siguientes:
+ **301 Movido permanentemente:** Es un código de estado de HTTP que indica que el host ha sido capaz de comunicarse con el servidor pero que el recurso solicitado ha sido movido a otra dirección permanentemente.
+ **400 Peticion incorrecta:** El servidor no logro encontrar o procesar la solicitud por un error aparente del cliente como sintaxis, tamaño o enrutamiento
+ **401 No autorizado:** es similar al error 403, se trata del error lanzado cuando la autentificacion no se proporciono o es incorrecta
+ **402 Pago rquerido:** Este codigo esta reservado para uso futuro, en el cual se puedan notificar errores en pagos digitales, pero actualmente algunas empresas lo han utilizado para expresas otras cosas como Google debelopers que lo usa en caso de que el usuario haya superado el limite diario de solicitudes
+ **403 Prohibido:** La solicitud realzada es correcta debido a que si tiene los datos validos y el servidor la entiende, pero el servidor la esta rechazando, esto puede darse por gestion de permisos, necesita una cuenta especifica o son acciones prohibidas
+ **404 No encontrado:** No fue posible encontrar el recurso solicitado
+ **405 Metodo no permitido:** No se admite un método de solicitud para el recurso solicitado; por ejemplo, una solicitud GET en un formulario que requiere que los datos se presenten a través de POST , o una solicitud PUT en un recurso de solo lectura.
+ **406 No aceptable:** El recurso solicitado es capaz de generar solo contenido no aceptable de acuerdo con los encabezados de aceptación enviados en la solicitud.
+ **407 Se requiere autenticación de proxy:** El cliente primero debe autenticarse con el proxy 
+ **408 Solicitar tiempo de espera:** El servidor agotó el tiempo de espera de la solicitud. De acuerdo con las especificaciones HTTP: "El cliente no produjo una solicitud dentro del tiempo en que el servidor estaba preparado para esperar. El cliente PUEDE repetir la solicitud sin modificaciones en cualquier momento posterior". 
+ **409 Conflicto:** Indica que la solicitud no se pudo procesar debido a un conflicto en el estado actual del recurso, como un conflicto de edición entre varias actualizaciones simultáneas.
+ **410 desaparecido:** Indica que el recurso solicitado ya no está disponible y no volverá a estar disponible. Esto debe usarse cuando un recurso se ha eliminado intencionalmente y el recurso debe purgarse. 
+ **411 Longitud requerida:** La solicitud no especificó la longitud de su contenido, que es requerida por el recurso solicitado.
+ **412 Precondición fallida:** El servidor no cumple una de las condiciones previas que el solicitante puso en los campos del encabezado de la solicitud.
+ **413 Carga útil demasiado grande:** La solicitud es mayor de lo que el servidor desea o puede procesar. Anteriormente llamado "entidad de solicitud demasiado grande".
+ **414 URI demasiado largo:** El URI proporcionado era demasiado largo para que el servidor lo procesara. A menudo, el resultado de la codificación de demasiados datos como una cadena de consulta de una solicitud GET, en cuyo caso debe convertirse en una solicitud POST. Anteriormente denominado "Request-URI Too Long".
+ **415 Tipo de medio no admitido:** La entidad de solicitud tiene un tipo de medio que el servidor o recurso no admite. Por ejemplo, el cliente carga una imagen como image / svg + xml , pero el servidor requiere que las imágenes usen un formato diferente.
+ **416 Rango no satisfactorio:** El cliente ha solicitado una parte del archivo ( servicio de bytes ), pero el servidor no puede proporcionar esa parte. Por ejemplo, si el cliente solicita una parte del archivo que se encuentra más allá del final del archivo. Anteriormente denominado "Rango solicitado no satisfactorio". 
+ **417 Expectativa fallida:** El servidor no puede cumplir con los requisitos del campo Expect request-header.
+ **418 Soy una tetera:** Este código se definió en 1998 como una de las bromas tradicionales de IETF April Fools , en RFC 2324 , Protocolo de control de cafetera Hyper Text , y no se espera que sea implementado por servidores HTTP reales
+ **421 Solicitud mal dirigida:** La solicitud se dirigió a un servidor que no puede producir una respuesta
+ **422 Entidad no procesable :** La solicitud estaba bien formada, pero no se pudo seguir debido a errores semánticos
+ **423 Bloqueado:** El recurso al que se accede está bloqueado.
+ **424 Dependencia fallida:** La solicitud falló porque dependía de otra solicitud y esa solicitud falló
+ **425 demasiado pronto:** Indica que el servidor no está dispuesto a correr el riesgo de procesar una solicitud que podría reproducirse.
+ **426 Requiere actualización:** El cliente debe cambiar a un protocolo diferente, como TLS / 1.0 , que se proporciona en el campo de encabezado de actualización 
+ **428 Requisito previo:** El servidor de origen requiere que la solicitud sea condicional. Con la intención de evitar el problema de la 'actualización perdida', donde un cliente obtiene el estado de un recurso, lo modifica y lo devuelve al servidor, cuando mientras tanto un tercero ha modificado el estado en el servidor, lo que lleva a un conflicto.
+ **429 Demasiadas solicitudes:** El usuario ha enviado demasiadas solicitudes en un período de tiempo determinado. Diseñado para su uso con esquemas de limitación de velocidad .
+ **431 Campos de encabezado de solicitud demasiado grandes:** El servidor no está dispuesto a procesar la solicitud porque un campo de encabezado individual o todos los campos de encabezado en conjunto son demasiado grandes.
+ **451 No disponible por motivos legales:** Un operador de servidor ha recibido una demanda legal para denegar el acceso a un recurso oa un conjunto de recursos que incluye el recurso solicitado. 

Realice una nueva conexión con telnet, esta vez a:
Host: www.httpbin.org
Puerto: 80

![image](https://user-images.githubusercontent.com/25957863/157165902-ea8c4d0b-5306-4fcc-8f4e-89edea8b5319.png)

Versión HTTP: 1.1
Ahora, solicite (GET) el recurso /html. ¿Qué se obtiene como resultado?

```
GET /html HTTP/1.1
```
![image](https://user-images.githubusercontent.com/25957863/157166022-d65fca77-d000-4345-980c-3435fec7ef10.png)

Seleccione el contenido HTML de la respuesta y copielo al cortapapeles CTRL-SHIFT-C. Ejecute el comando wc (word count) para contar palabras con la opción -c para contar el número de caracteres:

wc -c 
Pegue el contenido del portapapeles con CTRL-SHIFT-V y presione CTRL-D (fin de archivo de Linux). Si no termina el comando wc presione CTRL-D de nuevo. No presione mas de dos veces CTRL-D indica que se termino la entrada y puede cerrarle la terminal. Debe salir el resultado de la cantidad de caracteres que tiene el contenido HTML que respondió el servidor.

Claro está, las peticiones GET son insuficientes en muchos casos. Investigue: ¿Cuál es la diferencia entre los verbos GET y POST? ¿Qué otros tipos de peticiones existen?

En la practica no se utiliza telnet para hacer peticiones a sitios web sino el comando curl con ayuda de la linea de comandos:

```
curl www.httpbin.org
```
![image](https://user-images.githubusercontent.com/25957863/157166798-51012744-6571-411c-aec7-4759e9992a77.png)

Utilice ahora el parámetro -v y con el parámetro -i:

```
curl -v www.httpbin.org
```
![image](https://user-images.githubusercontent.com/25957863/157166847-28192291-e2d6-44a3-a0ff-d7dfaa327262.png)

```
curl -i www.httpbin.org
```
![image](https://user-images.githubusercontent.com/25957863/157166902-e44e5ee9-8fe1-4157-93b6-a3606d0f54d5.png)

#### ¿Cuáles son las diferencias con los diferentes parámetros?

Con el comando ```curl -v www.httpbin.org``` fue posible evidenciar el detalle de la conexion, mostrando la direccion IP el puerto y el host ademas de poder observar si fue aceptado, posterior a esto se evidencia la pagina web

Con el comando ```curl -i www.httpbin.org``` fue posible evidenciar la fecaha y hora en que se realizo la consulta del HTML, con la longitud, el tipo de conexion, y el servidor al cual se conecto para fianalmente mostrar la pagina HTML
