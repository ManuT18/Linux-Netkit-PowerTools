# Linux|NetKit PowerTools :hammer_and_wrench::toolbox::computer:

+ **COMANDOS A UTILIZAR ANTE ERRORES DE SEVIDOR SMTP**
 - [x] nslookup [mx.cs.uns.edu.ar]
 - [x] ping [200.49.226.11]
 - [x] telnet [200.49.226.11 25]
 - [x] traceroute [200.49.226.11]


## Tabla de comandos para diagnosticar problemas con el servidor SMTP

| Escenario | Comando | Explicación | Identificación de error | Mensaje de error |
|---|---|---|---|---|
| 1. Falla en la resolución de nombres | `nslookup mx.cs.uns.edu.ar` | Traduce el nombre de dominio `mx.cs.uns.edu.ar` a una dirección IP. | * Si el comando muestra un mensaje de error, indica que hay un problema con la resolución de nombres. \n * Si el comando muestra la dirección IP del servidor SMTP (200.49.226.11), la resolución de nombres funciona correctamente. | - Mensaje de error: Servidor desconocido **mx.cs.uns.edu.ar** |
| 2. No se puede alcanzar al servidor sin filtrado de ICMP Echo | `ping 200.49.226.11` | Envía paquetes ICMP Echo Request al servidor SMTP. | * Si el comando muestra un mensaje de "Destino inalcanzable", indica que el servidor SMTP no está disponible o que hay un problema de red. \n * Si el comando muestra respuestas ICMP Echo Reply, el servidor SMTP está disponible y responde a los pings. | - Mensaje de error: Destino inalcanzable. Tiempo de espera excedido. |
| 3. No se puede alcanzar al servidor con filtrado de ICMP Echo | `telnet 200.49.226.11 25` | Intenta establecer una conexión TCP con el servidor SMTP en el puerto 25. | * Si el comando muestra un mensaje de "Conexión rechazada", indica que el servidor SMTP no está escuchando en el puerto 25 o que hay un firewall que bloquea la conexión. \n * Si el comando establece la conexión y muestra un mensaje de bienvenida, el servidor SMTP está disponible y escucha en el puerto 25. | - Mensaje de error: Conexión rechazada |
| 4. Sospecha de problema de enrutamiento | `traceroute 200.49.226.11` | Rastrea la ruta que toman los paquetes para llegar al servidor SMTP. | * Si el comando muestra que los paquetes se pierden o se retrasan en un router específico, indica que hay un problema de enrutamiento en ese router. \n * Si el comando muestra que los paquetes llegan al servidor SMTP sin problemas, el enrutamiento funciona correctamente. | - Mensaje de error: De 100 paquetes enviados, 64 han llegado con éxito, 36 han fallado (perdida de paquetes). |
| 5. Se alcanza al servidor pero no se sabe si está ejecutando el servicio SMTP | `telnet 200.49.226.11 25` | Intenta establecer una conexión TCP con el servidor SMTP en el puerto 25. | * Si el comando muestra un mensaje de "Conexión rechazada", indica que el servidor SMTP no está ejecutando el servicio SMTP o que hay un problema de configuración. \n * Si el comando establece la conexión y muestra un mensaje de bienvenida, el servidor SMTP está ejecutando el servicio SMTP y está disponible para enviar y recibir correos electrónicos. | - Mensaje de error: 220 mx.cs.uns.edu.ar ESMTP Sendmail 8.15.1 |
