# Paquete `com.logistica.config`

## Objetivo del paquete

El paquete `com.logistica.config` contiene la configuración principal del Web Service REST.

Su responsabilidad es indicar cómo se inicializa la API y cuál será la ruta base desde donde se expondrán los endpoints del proyecto.

---

# Clase incluida

## `AppConfig.java`

Esta clase será la configuración principal de JAX-RS/Jersey.

Sirve para registrar el Web Service REST dentro del proyecto y definir la ruta base de la API.

Ejemplo de ruta base esperada:

/api

Esto significa que los recursos REST estarán disponibles bajo rutas como:

/api/clientes
/api/envios
/api/seguimientos
/api/exportaciones

---

# Responsabilidades de `AppConfig.java`

La clase `AppConfig.java` tendrá las siguientes responsabilidades:

Configurar JAX-RS.
Definir la ruta base del Web Service.
Permitir que Jersey detecte los recursos REST.
Servir como punto de entrada de configuración para los endpoints.

---

# Qué NO debe hacer esta clase

`AppConfig.java` no debe contener lógica de negocio.

No debe:

Conectarse directamente a MySQL.
Registrar clientes.
Registrar envíos.
Actualizar estados.
Generar códigos de seguimiento.
Exportar archivos.
Enviar notificaciones Socket.
Manejar hilos.
Consumir Angular.

---

# Relación con otros paquetes

`AppConfig.java` se relaciona principalmente con el paquete:

com.logistica.resource

Porque los recursos REST definidos en ese paquete serán expuestos mediante la configuración de JAX-RS.

---

# Ejemplo conceptual

Si se define la ruta base como:

/api

y existe un recurso:

ClienteResource

con la ruta:

/clientes

entonces el endpoint final será:

/api/clientes

---

# Importancia dentro del proyecto

Este paquete es importante porque sin la configuración de JAX-RS/Jersey, los endpoints REST no podrán ser reconocidos correctamente por Tomcat.

En resumen:

AppConfig.java permite que el proyecto funcione como Web Service REST.
