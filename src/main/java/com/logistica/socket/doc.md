# Paquete `com.logistica.socket`

## Objetivo del paquete

El paquete `com.logistica.socket` contiene las clases encargadas de la comunicación mediante Java Sockets.

Su función principal es permitir que el sistema envíe notificaciones en tiempo real cuando ocurran eventos importantes dentro del Web Service.

Estas notificaciones podrán ser recibidas por:

Cliente Socket Java
Telnet
Consola de monitoreo

---

# ¿Por qué usamos Sockets?

Uno de los temas enseñados durante el curso es la comunicación mediante sockets.

Este proyecto utilizará sockets para demostrar:

Comunicación entre aplicaciones.
Envío de mensajes en tiempo real.
Comunicación cliente-servidor.
Monitoreo de eventos del sistema.

---

# Clases incluidas

## ServidorSocket.java

Representa el servidor principal de sockets.

Responsabilidades:

Escuchar conexiones entrantes.
Aceptar clientes conectados.
Mantener el servidor activo.
Recibir solicitudes.
Enviar respuestas.

Ejemplo conceptual:

Puerto: 5000

Cliente Socket
     ↓
ServidorSocket

---

## ClienteSocket.java

Representa un cliente de prueba.

Responsabilidades:

Conectarse al servidor.
Enviar mensajes.
Recibir mensajes.
Mostrar respuestas.

Será utilizado principalmente para pruebas.

---

## NotificadorSocket.java

Clase encargada de enviar mensajes cuando ocurre un evento importante.

Responsabilidades:

Enviar alertas.
Enviar cambios de estado.
Enviar mensajes de seguimiento.
Notificar eventos del sistema.

Será utilizada desde los Services.

---

# Eventos que generarán notificaciones

Los siguientes eventos deberán generar mensajes Socket:

Nuevo envío registrado.
Cambio de estado.
Envío retrasado.
Envío entregado.
Nuevo seguimiento registrado.

---

# Ejemplo conceptual

Registro de envío:

Angular
↓
EnvioResource
↓
EnvioServiceImpl
↓
EnvioDAO
↓
MySQL

↓

NotificadorSocket
↓
ServidorSocket
↓
Cliente conectado

Mensaje enviado:

[SOCKET]

Nuevo envío registrado.

Código:
ENV-0001

Estado:
REGISTRADO

---

# Ejemplo: cambio de estado

Cuando un envío cambia de estado:

REGISTRADO
↓
EN_CAMINO

El sistema podrá enviar:

[SOCKET]

ENV-0001

Estado actualizado:
EN_CAMINO

---

# Integración con Telnet

El servidor Socket podrá ser probado mediante:

telnet localhost 5000

Esto permitirá demostrar comunicación básica entre cliente y servidor.

Ejemplos:

PING

Respuesta:

Servidor activo

---

Consulta:

ENV-0001

Respuesta:

Estado:
EN_CAMINO

---

# Responsabilidades del paquete

Las clases Socket deben:

Escuchar conexiones.
Aceptar clientes.
Enviar mensajes.
Recibir mensajes.
Mantener la comunicación.
Permitir pruebas con Telnet.

---

# Qué NO debe hacer este paquete

Las clases Socket NO deben:

Ejecutar SQL.
Modificar la base de datos.
Registrar clientes.
Registrar envíos.
Generar JSON.
Generar XML.
Crear archivos.
Implementar lógica de negocio.
Crear endpoints REST.

Todas esas responsabilidades pertenecen a otras capas.

---

# Relación con otros paquetes

resource
↓
service
↓
service.impl
↓
socket

Los Services podrán utilizar el paquete Socket para informar eventos importantes.

---

# Beneficios dentro del proyecto

El uso de Sockets permitirá demostrar:

Programación distribuida.
Comunicación cliente-servidor.
Eventos en tiempo real.
Uso práctico de sockets.
Integración con Telnet.

---

# Buenas prácticas

Se recomienda:

Mantener un puerto configurable.
Cerrar conexiones correctamente.
Manejar excepciones.
Evitar lógica de negocio dentro del socket.
Separar servidor y cliente.
Mantener mensajes claros.

---

# Importancia dentro del proyecto

Este paquete es el encargado de demostrar uno de los temas principales del curso.

Aunque el Web Service funciona sin sockets, este módulo permitirá mostrar comunicación en tiempo real entre aplicaciones externas.

---

# Resumen

El paquete:

com.logistica.socket

contiene la implementación de comunicación mediante Java Sockets.

Su objetivo es notificar eventos importantes del sistema y demostrar comunicación cliente-servidor utilizando Java Socket y Telnet.
