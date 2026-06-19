# Paquete `com.logistica.dao.impl`

## Objetivo del paquete

El paquete `com.logistica.dao.impl` contiene las implementaciones concretas de los DAO del proyecto.

Mientras que el paquete:

com.logistica.dao

define qué operaciones existen, este paquete define cómo se ejecutan realmente dichas operaciones sobre MySQL.

Aquí es donde se escribirán las consultas SQL y se utilizará JDBC para interactuar con la base de datos.

---

# ¿Qué significa impl?

La palabra:

impl

proviene de:

Implementation

Es decir:

Implementación

Estas clases implementarán las interfaces definidas en:

com.logistica.dao

---

# Clases incluidas

## ClienteDAOImpl

Implementación del DAO de clientes.

Responsabilidades:

Registrar clientes.
Actualizar clientes.
Eliminar clientes.
Buscar clientes.
Listar clientes.

Utilizará consultas SQL contra la tabla:

cliente

---

## ConductorDAOImpl

Implementación del DAO de conductores.

Responsabilidades:

Registrar conductores.
Actualizar conductores.
Buscar conductores.
Listar conductores.

---

## VehiculoDAOImpl

Implementación del DAO de vehículos.

Responsabilidades:

Registrar vehículos.
Actualizar vehículos.
Buscar vehículos.
Listar vehículos.

---

## EnvioDAOImpl

Implementación del DAO de envíos.

Responsabilidades:

Registrar envíos.
Actualizar envíos.
Eliminar envíos.
Buscar envíos.
Buscar por código.
Buscar por estado.
Listar envíos.

---

## SeguimientoEnvioDAOImpl

Implementación del DAO de seguimiento.

Responsabilidades:

Registrar seguimientos.
Actualizar seguimientos.
Buscar seguimientos.
Listar seguimientos.
Consultar historial por envío.
Consultar historial por código.

---

# Responsabilidades del paquete

Las clases DAOImpl serán responsables de:

Abrir conexiones JDBC.
Ejecutar consultas SQL.
Ejecutar INSERT.
Ejecutar UPDATE.
Ejecutar DELETE.
Ejecutar SELECT.
Mapear resultados a objetos Java.
Cerrar recursos correctamente.

---

# Ejemplo conceptual

Cuando un usuario registra un envío:

Angular
↓
EnvioResource
↓
EnvioService
↓
EnvioDAOImpl
↓
MySQL

La clase:

EnvioDAOImpl

será quien ejecute realmente:

INSERT INTO envio (...)
VALUES (...)

---

# Qué NO debe hacer este paquete

Las clases DAOImpl NO deben:

Validar reglas de negocio.
Generar códigos de seguimiento.
Crear respuestas HTTP.
Enviar notificaciones Socket.
Crear Threads.
Exportar JSON.
Exportar XML.
Generar PDF.
Tomar decisiones del negocio.

Todo eso pertenece a otras capas.

---

# Relación con otros paquetes

resource
↓
service
↓
dao
↓
dao.impl
↓
MySQL

---

# Uso de JDBC

Las implementaciones utilizarán:

Connection
PreparedStatement
ResultSet

para comunicarse con la base de datos.

Ejemplo conceptual:

Obtener conexión.
Preparar consulta.
Ejecutar consulta.
Procesar resultados.
Cerrar recursos.

---

# Importancia dentro del proyecto

Este paquete es el único responsable de comunicarse directamente con MySQL.

Si en el futuro cambia la base de datos:

MySQL
↓
PostgreSQL

la mayor parte de los cambios se concentrarán en este paquete.

---

# Buenas prácticas

Se recomienda:

```txt
Usar PreparedStatement.
Cerrar conexiones correctamente.
Evitar SQL duplicado.
Capturar excepciones.
Retornar objetos del modelo.
Mantener métodos pequeños y claros.
```

---

# Resumen

El paquete:

```txt
com.logistica.dao.impl
```

contiene la implementación real de acceso a datos.

Es el encargado de ejecutar SQL y comunicarse con MySQL utilizando JDBC.

Representa la capa más cercana a la base de datos y debe limitarse exclusivamente a operaciones de persistencia.
