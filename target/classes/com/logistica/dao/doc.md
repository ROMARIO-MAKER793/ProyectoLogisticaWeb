# Paquete `com.logistica.dao`

## Objetivo del paquete

El paquete `com.logistica.dao` contiene las interfaces DAO (Data Access Object) del proyecto.

Su función es definir las operaciones que podrán realizarse sobre la base de datos sin preocuparse todavía por cómo se implementarán.

Este paquete representa el contrato que deberá cumplir cualquier implementación de acceso a datos.

---

# ¿Qué es un DAO?

DAO significa:


Data Access Object


Es un patrón de diseño utilizado para separar el acceso a datos de la lógica de negocio.

Gracias a este patrón:


Service no conoce SQL.
Resource no conoce SQL.
Angular no conoce SQL.


Toda la comunicación con MySQL queda centralizada en las implementaciones DAO.

---

# Interfaces incluidas

## ClienteDAO

Responsable de definir las operaciones relacionadas con clientes.

Operaciones esperadas:


Registrar cliente.
Actualizar cliente.
Eliminar cliente.
Buscar cliente por ID.
Listar clientes.


---

## ConductorDAO

Responsable de definir las operaciones relacionadas con conductores.

Operaciones esperadas:

Registrar conductor.
Actualizar conductor.
Buscar conductor.
Listar conductores.

---

## VehiculoDAO

Responsable de definir las operaciones relacionadas con vehículos.

Operaciones esperadas:

Registrar vehículo.
Actualizar vehículo.
Buscar vehículo.
Listar vehículos.

---

## EnvioDAO

Responsable de definir las operaciones relacionadas con envíos.

Operaciones esperadas:

Registrar envío.
Actualizar envío.
Eliminar envío.
Buscar envío por ID.
Buscar envío por código.
Listar envíos.
Buscar por estado.

---

## SeguimientoEnvioDAO

Responsable de definir las operaciones relacionadas con el seguimiento.

Operaciones esperadas:

Registrar seguimiento.
Actualizar seguimiento.
Buscar seguimiento por ID.
Listar seguimientos.
Listar seguimientos por envío.
Buscar por código de seguimiento.

---

# Responsabilidades del paquete DAO

Las interfaces DAO deben:

Definir operaciones CRUD.
Definir consultas necesarias.
Servir como contrato para las implementaciones.
Mantener independencia de la lógica de negocio.

---

# Qué NO debe hacer este paquete

Las interfaces DAO NO deben:

Ejecutar SQL.
Abrir conexiones.
Cerrar conexiones.
Generar códigos de seguimiento.
Validar reglas de negocio.
Generar JSON.
Generar XML.
Enviar notificaciones Socket.
Crear Threads.
Responder peticiones HTTP.

Todo eso corresponde a otras capas del proyecto.

---

# Relación con otros paquetes

Relación principal:

resource
    ↓
service
    ↓
dao
    ↓
dao.impl
    ↓
MySQL

Los Services utilizarán estas interfaces para acceder a los datos.

---

# Ventajas de utilizar DAO

Separación de responsabilidades.
Código más mantenible.
Facilidad para realizar pruebas.
Menor acoplamiento.
Mejor organización del proyecto.

---

# Resumen

El paquete:

com.logistica.dao

define qué operaciones estarán disponibles para trabajar con la base de datos.

No contiene SQL ni lógica de negocio.

Únicamente define los contratos que deberán implementar las clases del paquete:

com.logistica.dao.impl

que serán las encargadas de comunicarse realmente con MySQL.
