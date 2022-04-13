# Ejercicio de promoción - Ejercicio 12 TP2-HTTP
Programar en el lenguaje que sea de su elección un servidor HTTP/1.0
reducido que sólo implementará lo enumerado a continuación:
*NOTA: para quienes hagan la promoción, este será un ejercicio “entregable”. En la entrega deberán incluir el código fuente debidamente comentado y un README, o README.md que explique cómo generar el programa, cómo ejecutarlo y cómo testearlo.* 

<ol type="A">
  <li>Deberá recibir requerimientos HTTP 1.0 y 1.1 para procesarlos y determinar sí la solicitud es válida. Si detecta que el requerimiento no es válido responderá con un error 400 </li>
  <li>Sólo debe implementar el método GET. Sí el método es otro responderá con un error 405 </li>
  <li>La respuesta será una página HTML generada automáticamente que incluye en su cuerpo el string del recurso HTTP solicitado.</li>
  <li>
 La respuesta HTTP debe ser válida, respetando el protocolo, e incluír las cabeceras apropiadas para indicar el tipo de contenido, el tamaño, la fecha y el tipo de servidor</li>
 <li>Todas las cabeceras envíadas por el cliente deben ser válidas y en principio ignoradas.</li>
 <li>Debe ser programado utilizando la API de socket, es decir las llamadas, `socket`, `listen`, `accept`,
etc</li>
<li>El servidor debe ser testeado con un navegador/user-agent http tradicional. Por ejemplo, sí ejecuta-
mos el servidor localmente en puerto 80 las siguientes serían algunas interacciones posibles:</li>
</ol>

**Ejemplo1:**

```shell
$ telnet localhost 80
GET /index.html HTTP/1.0

HTTP/1.0 200 OK
Date: Wed, 16 Mar 2022 15:26 GMT
Server: Silly/0.1
Content-Length: 33
Content-Type: text/html
Connection: Closed

<HTML><H1>/index.html</H1></HTML>
Connection closed by foreign host.
```

**Ejemplo2:**
```shell
$ telnet localhost 80
GET dir/subdir/test.html HTTP/1.1

Host: 127.0.0.1:8000
Connection: keep-alive
User-Agent: Mozilla/5.0 (X11; Linux x86_64)
HTTP/1.0 200 OK
Date: Wed, 16 Mar 2022 15:39 GMT
Server: Silly/0.1
Content-Length: 42
Content-Type: text/html
Connection: Closed

<HTML><H1>dir/subdir/test.html</H1></HTML>
Connection closed by foreign host.
```
**Ejemplo3**


```shell
$ telnet localhost 80
FFF /

HTTP/1.0 400 Bad Request
Connection closed by foreign host.````shell

```

**Ejemplo4**
```shell
$ telnet localhost 80
....GET

HTTP/1.0 400 Bad Request
Connection closed by foreign host
```

**Ejemplo5**
```shell

$ telnet localhost 80
HEAD /index.html HTTP/1.0

HTTP/1.0 405 Method Not Allowed
Connection closed by foreign host.
```
