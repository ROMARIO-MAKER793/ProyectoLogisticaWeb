# Paquete `com.logistica.services`

## Objetivo del paquete

El paquete `com.logistica.services` contiene las interfaces de servicio del proyecto.

Estas interfaces definen las operaciones de negocio que estarán disponibles para cada módulo, pero no implementan la lógica directamente.

---

# ¿Qué es un Service?

Un Service representa la capa de lógica de negocio.

Sirve como intermediario entre:

Resource
↓
Service
↓
DAO

El Resource no debe llamar directamente al DAO.
Debe llamar primero al Service.

---

# Interfaces incluidas

## ClienteService.java

Define las operaciones relacionadas con clientes.

Operaciones esperadas:

Registrar cliente.
Actualizar cliente.
Eliminar cliente.
Buscar cliente por ID.
Listar clientes.

---

## ConductorService.java

Define las operaciones relacionadas con conductores.

Operaciones esperadas:

Registrar conductor.
Actualizar conductor.
Buscar conductor por ID.
Listar conductores.

---

## VehiculoService.java

Define las operaciones relacionadas con vehículos.

Operaciones esperadas:

Registrar vehículo.
Actualizar vehículo.
Buscar vehículo por ID.
Listar vehículos.

---

## EnvioService.java

Define las operaciones principales del módulo de envíos.

Operaciones esperadas:

Registrar envío.
Actualizar envío.
Eliminar envío.
Buscar envío por ID.
Buscar envío por código de seguimiento.
Listar envíos.
Listar envíos por estado.
Cambiar estado del envío.

---

## SeguimientoEnvioService.java

Define las operaciones relacionadas con el historial de seguimiento.

Operaciones esperadas:

Registrar seguimiento.
Actualizar seguimiento.
Eliminar seguimiento.
Buscar seguimiento por ID.
Listar seguimientos.
Listar seguimientos por envío.
Listar seguimientos por código de seguimiento.

---

## ExportacionService.java

Define las operaciones relacionadas con exportación de datos.

Operaciones esperadas:

Exportar datos en JSON.
Exportar datos en XML.
Exportar reporte sin hilos.
Exportar reporte con hilos.
Comparar tiempos de ejecución.

---

# Responsabilidades del paquete

Las interfaces Service deben:

Definir contratos de lógica de negocio.
Separar Resource de DAO.
Indicar qué operaciones estarán disponibles.
Facilitar futuras implementaciones.
Mantener ordenada la arquitectura.

---

# Qué NO debe hacer este paquete

Las interfaces Service NO deben:

Ejecutar SQL.
Abrir conexiones a MySQL.
Definir rutas REST.
Enviar respuestas HTTP.
Implementar lógica directamente.
Crear archivos.
Enviar sockets.
Crear hilos.

La lógica concreta estará en:

com.logistica.service.impl

---

# Relación con otros paquetes

resource
    ↓
services
    ↓
service.impl
    ↓
dao
    ↓
dao.impl
    ↓
MySQL

El paquete `resource` utilizará las interfaces Service.

Las clases del paquete `service.impl` implementarán estas interfaces.

---

# Diferencia entre `services` y `service.impl`

## `services`

Define lo que se puede hacer.

Ejemplo:

registrarEnvio()
buscarEnvioPorCodigo()
cambiarEstado()

## `service.impl`

Define cómo se hace.

Ejemplo:

Validar datos.
Generar código.
Guardar en MySQL.
Crear seguimiento.
Enviar socket.

---

# Ejemplo conceptual

EnvioResource
↓
EnvioService
↓
EnvioServiceImpl
↓
EnvioDAO
↓
EnvioDAOImpl
↓
MySQL

Esto permite que el Resource dependa de una interfaz y no de una implementación concreta.

---

# Importancia dentro del proyecto

Este paquete ayuda a mantener una arquitectura limpia.

Permite separar:

Rutas REST
Lógica de negocio
Acceso a datos

Gracias a esta separación, el código será más fácil de entender, probar y mantener.

---

# Buenas prácticas

Se recomienda que las interfaces Service:

Tengan nombres claros.
No tengan código SQL.
No tengan anotaciones REST.
Usen objetos del paquete model.
Definan métodos relacionados al negocio.
No mezclen responsabilidades.

---

# Resumen

El paquete:

com.logistica.services

contiene las interfaces de lógica de negocio.

No implementa la lógica directamente, solo define los métodos que luego serán desarrollados en:

com.logistica.service.impl
