# Paquete `com.logistica.enums`

## Objetivo del paquete

El paquete `com.logistica.enums` contiene las enumeraciones utilizadas en el proyecto.

Una enumeración permite definir un conjunto cerrado de valores permitidos, evitando que se usen textos incorrectos en partes importantes del sistema.

---

# ¿Por qué usamos enums?

En este proyecto usaremos enums para controlar los estados válidos de un envío.

Esto evita errores como:

EN CAMINO
En camino
camino
EN_RUTAA
ENTREGADOO

En lugar de permitir cualquier texto, Java solo permitirá usar los valores definidos en el enum.

---

# Clase incluida

## `EstadoEnvio.java`

Representa los estados oficiales que puede tener un envío.

Valores permitidos:

REGISTRADO
EN_ALMACEN
EN_CAMINO
RETRASADO
ENTREGADO
CANCELADO

---

# Responsabilidades de `EstadoEnvio.java`

Esta clase enum debe:

Definir los estados válidos del envío.
Evitar valores incorrectos.
Centralizar los estados del proyecto.
Apoyar las validaciones del Service.
Mantener consistencia entre Java, JSON, XML y MySQL.

---

# Uso dentro del proyecto

El enum será utilizado principalmente por:

Envio.java
SeguimientoEnvio.java
EnvioServiceImpl.java
SeguimientoEnvioServiceImpl.java

Ejemplo conceptual:

private EstadoEnvio estado;

---

# Relación con la base de datos

En MySQL, el estado se almacenará como texto:

estado VARCHAR(30) NOT NULL

Ejemplo:

REGISTRADO
EN_CAMINO
ENTREGADO

Aunque MySQL lo guarde como texto, Java validará que solo se usen valores definidos en:

EstadoEnvio.java

---

# ¿Por qué no usamos ENUM de MySQL?

Para este proyecto se usará `VARCHAR(30)` en la base de datos porque facilita:

El uso con JDBC.
La conversión a JSON.
La conversión a XML.
El consumo desde Angular.
La lectura y escritura desde Java.
La corrección de errores durante el desarrollo.

La validación de estados se realizará en Java mediante el enum.

---

# Qué NO debe hacer este paquete

El paquete `enums` no debe:

Ejecutar SQL.
Conectarse a MySQL.
Exponer endpoints REST.
Enviar sockets.
Generar archivos.
Crear hilos.
Contener lógica de negocio compleja.

Su única función es definir valores constantes y controlados.

---

# Resumen

El paquete:

com.logistica.enums

contiene valores controlados del proyecto.

En esta primera versión tendrá el enum:

EstadoEnvio.java

que define los estados oficiales permitidos para los envíos.
