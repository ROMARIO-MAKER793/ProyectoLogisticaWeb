# Paquete `com.logistica.service.impl`

## Objetivo del paquete

El paquete `com.logistica.service.impl` contiene las implementaciones de los servicios del proyecto.

Aquí se desarrolla la lógica de negocio del Web Service.

Mientras que el paquete:

com.logistica.service

define qué operaciones existen, este paquete define cómo se realizan esas operaciones.

---

# ¿Qué es un ServiceImpl?

Un `ServiceImpl` es una clase que implementa una interfaz Service.

Su función es coordinar el flujo entre:

Resource
DAO
Socket
Thread
Util

Ejemplo:

EnvioResource
    ↓
EnvioService
    ↓
EnvioServiceImpl
    ↓
EnvioDAO

---

# Clases incluidas

## ClienteServiceImpl.java

Implementa la lógica relacionada con clientes.

Responsabilidades:

Validar datos del cliente.
Registrar cliente.
Actualizar cliente.
Eliminar cliente.
Buscar cliente.
Listar clientes.
Llamar a ClienteDAO.

---

## ConductorServiceImpl.java

Implementa la lógica relacionada con conductores.

Responsabilidades:

Validar datos del conductor.
Registrar conductor.
Actualizar conductor.
Buscar conductor.
Listar conductores.
Llamar a ConductorDAO.

---

## VehiculoServiceImpl.java

Implementa la lógica relacionada con vehículos.

Responsabilidades:

Validar datos del vehículo.
Registrar vehículo.
Actualizar vehículo.
Buscar vehículo.
Listar vehículos.
Llamar a VehiculoDAO.

---

## EnvioServiceImpl.java

Implementa la lógica principal de envíos.

Responsabilidades:

Validar datos del envío.
Generar código de seguimiento.
Registrar envío.
Actualizar envío.
Cambiar estado del envío.
Buscar envío por ID.
Buscar envío por código.
Listar envíos.
Listar envíos por estado.
Crear seguimiento inicial.
Generar seguimiento por cambio de estado.
Enviar notificación Socket.
Llamar a EnvioDAO.

Esta será una de las clases más importantes del proyecto.

---

## SeguimientoEnvioServiceImpl.java

Implementa la lógica relacionada con los seguimientos.

Responsabilidades:

Registrar seguimiento.
Actualizar seguimiento.
Buscar seguimiento.
Listar seguimientos.
Listar seguimientos por envío.
Listar seguimientos por código.
Validar que el seguimiento pertenezca a un envío.
Llamar a SeguimientoEnvioDAO.

---

## ExportacionServiceImpl.java

Implementa la lógica de exportación.

Responsabilidades:

Exportar datos en JSON.
Exportar datos en XML.
Ejecutar exportación secuencial.
Ejecutar exportación concurrente con Threads.
Medir tiempos de ejecución.
Comparar resultados.
Generar respuesta con tiempo y archivos creados.

---

# Responsabilidades del paquete

Las clases ServiceImpl deben:

Aplicar reglas de negocio.
Validar datos antes de llamar al DAO.
Coordinar varias operaciones.
Llamar a los DAO correspondientes.
Usar utilidades del paquete util.
Disparar notificaciones Socket cuando corresponda.
Ejecutar exportaciones mediante Threads.
Retornar resultados hacia los Resources.

---

# Qué NO debe hacer este paquete

Las clases ServiceImpl NO deben:

Definir rutas REST.
Usar anotaciones @GET, @POST, @PUT o @DELETE.
Construir directamente respuestas HTTP.
Ejecutar SQL directamente.
Abrir conexiones JDBC directamente.
Contener código visual de Angular.
Depender de la interfaz gráfica.

---

# Relación con otros paquetes

resource
    ↓
service
    ↓
service.impl
    ↓
dao
    ↓
dao.impl
    ↓
MySQL

También puede relacionarse con:

util
socket
thread

---

# Ejemplo conceptual: registrar envío

Cuando se registra un envío:

1. EnvioResource recibe la petición.
2. EnvioResource llama a EnvioService.
3. EnvioServiceImpl valida los datos.
4. EnvioServiceImpl genera el código ENV-0001.
5. EnvioServiceImpl llama a EnvioDAO para guardar.
6. EnvioServiceImpl crea seguimiento inicial.
7. EnvioServiceImpl envía notificación Socket.
8. EnvioResource devuelve respuesta al cliente.

---

# Ejemplo conceptual: cambiar estado

Cuando se cambia el estado de un envío:

1. Se valida que el nuevo estado sea permitido.
2. Se actualiza el estado del envío.
3. Se crea un nuevo seguimiento.
4. Se envía una notificación Socket.
5. Se devuelve la respuesta al Resource.

---

# Ejemplo conceptual: exportación con hilos

Cuando se ejecuta una exportación concurrente:

1. ExportacionResource llama a ExportacionService.
2. ExportacionServiceImpl inicia varios Threads.
3. Cada Thread exporta un conjunto de datos.
4. Se espera a que todos terminen.
5. Se calcula el tiempo total.
6. Se devuelve el resultado.

---

# Importancia dentro del proyecto

Este paquete es importante porque aquí vive la lógica real del negocio.

Si el Resource es la puerta de entrada y el DAO es el acceso a datos, el ServiceImpl es el encargado de decidir qué debe pasar en cada operación.

---

# Buenas prácticas

Se recomienda que las clases ServiceImpl:

No mezclen SQL.
No mezclen rutas REST.
Sean claras y separadas por responsabilidad.
Usen los DAO para persistencia.
Usen utilidades para código repetitivo.
Mantengan métodos entendibles.
Centralicen las reglas del negocio.

---

# Resumen

El paquete:

com.logistica.service.impl

contiene la implementación de la lógica del proyecto.

Es la capa que coordina validaciones, DAO, sockets, seguimientos, exportaciones e hilos.

Representa el corazón funcional del Web Service.
