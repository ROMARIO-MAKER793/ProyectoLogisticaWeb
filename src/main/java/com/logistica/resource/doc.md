# Paquete `com.logistica.resource`

## Objetivo del paquete

El paquete `com.logistica.resource` contiene las clases encargadas de exponer los endpoints REST del Web Service.

Estas clases reciben las peticiones HTTP enviadas desde Angular, Postman u otro cliente, y devuelven respuestas en formato JSON o XML.

---

# ¿Qué es un Resource?

Un Resource representa un punto de entrada HTTP del Web Service.

Aquí se definen rutas como:

/api/clientes
/api/envios
/api/seguimientos
/api/exportaciones

Utiliza anotaciones de JAX-RS como:

@Path
@GET
@POST
@PUT
@DELETE
@Consumes
@Produces

---

# Clases incluidas

## ClienteResource.java

Expone los endpoints relacionados con clientes.

Operaciones esperadas:

Listar clientes.
Buscar cliente por ID.
Registrar cliente.
Actualizar cliente.
Eliminar cliente.

---

## ConductorResource.java

Expone los endpoints relacionados con conductores.

Operaciones esperadas:

Listar conductores.
Buscar conductor por ID.
Registrar conductor.
Actualizar conductor.

---

## VehiculoResource.java

Expone los endpoints relacionados con vehículos.

Operaciones esperadas:

Listar vehículos.
Buscar vehículo por ID.
Registrar vehículo.
Actualizar vehículo.

---

## EnvioResource.java

Expone los endpoints relacionados con envíos.

Operaciones esperadas:

Listar envíos.
Buscar envío por ID.
Buscar envío por código de seguimiento.
Buscar envíos por estado.
Registrar envío.
Actualizar envío.
Cambiar estado del envío.
Eliminar envío.

---

## SeguimientoEnvioResource.java

Expone los endpoints relacionados con el historial de seguimiento.

Operaciones esperadas:

Listar seguimientos.
Buscar seguimiento por ID.
Listar seguimientos por envío.
Listar seguimientos por código de seguimiento.
Registrar seguimiento.
Actualizar seguimiento.
Eliminar seguimiento.

---

## ExportacionResource.java

Expone los endpoints relacionados con exportaciones.

Operaciones esperadas:

Exportar datos en JSON.
Exportar datos en XML.
Ejecutar exportación sin hilos.
Ejecutar exportación con hilos.
Comparar tiempos de ejecución.
```

---

# Responsabilidades del paquete

Las clases Resource deben:

Definir rutas REST.
Recibir parámetros desde la URL.
Recibir datos en el cuerpo de la petición.
Llamar a la capa Service.
Retornar respuestas HTTP.
Definir si la respuesta será JSON o XML.
Manejar códigos de estado HTTP.

Ejemplos de códigos HTTP:

200 OK
201 CREATED
400 BAD REQUEST
404 NOT FOUND
500 INTERNAL SERVER ERROR

---

# Qué NO debe hacer este paquete

Las clases Resource NO deben:

Ejecutar SQL.
Abrir conexiones a MySQL.
Contener reglas de negocio complejas.
Generar códigos de seguimiento directamente.
Crear seguimientos automáticamente.
Enviar sockets directamente.
Crear hilos directamente.
Manipular archivos directamente.

Esas responsabilidades pertenecen a las capas Service, DAO, Socket, Thread o Util.

---

# Relación con otros paquetes

Flujo normal:

Angular / Postman
    ↓
resource
    ↓
service
    ↓
dao
    ↓
dao.impl
    ↓
MySQL

Ejemplo:

EnvioResource
    ↓
EnvioService
    ↓
EnvioDAOImpl
    ↓
Base de datos

---

# Ejemplo conceptual

Cuando Angular registra un envío:

POST /api/envios

El flujo será:

EnvioResource recibe la petición.
EnvioResource llama a EnvioService.
EnvioService valida y procesa la lógica.
EnvioService guarda usando EnvioDAO.
EnvioService genera seguimiento y socket.
EnvioResource devuelve Response al cliente.

---

# Formatos de respuesta

## JSON

Será el formato principal utilizado por Angular.

Ejemplo:

{
  "codigoSeguimiento": "ENV-0001",
  "estado": "REGISTRADO",
  "mensaje": "Envío registrado correctamente"
}

---

## XML

Será utilizado para demostrar interoperabilidad.

Ejemplo:

<envio>
    <codigoSeguimiento>ENV-0001</codigoSeguimiento>
    <estado>REGISTRADO</estado>
    <mensaje>Envío registrado correctamente</mensaje>
</envio>

---

# Endpoints principales esperados

## Clientes

GET    /api/clientes
GET    /api/clientes/{id}
POST   /api/clientes
PUT    /api/clientes/{id}
DELETE /api/clientes/{id}

---

## Envíos

GET    /api/envios
GET    /api/envios/{id}
GET    /api/envios/codigo/{codigo}
GET    /api/envios/estado/{estado}
POST   /api/envios
PUT    /api/envios/{id}
PUT    /api/envios/{id}/estado
DELETE /api/envios/{id}

---

## Seguimientos

GET    /api/seguimientos
GET    /api/seguimientos/{id}
GET    /api/seguimientos/envio/{idEnvio}
GET    /api/seguimientos/codigo/{codigo}
POST   /api/seguimientos
PUT    /api/seguimientos/{id}
DELETE /api/seguimientos/{id}

---

## Exportaciones

GET /api/exportaciones/envios/json
GET /api/exportaciones/envios/xml
GET /api/exportaciones/reporte/sin-hilos
GET /api/exportaciones/reporte/con-hilos

---

# Buenas prácticas

Se recomienda que las clases Resource:

Sean simples.
No tengan SQL.
No tengan lógica pesada.
Solo reciban, llamen al Service y respondan.
Usen Response para devolver estados HTTP.
Usen nombres claros en las rutas.

---

# Importancia dentro del proyecto

Este paquete es importante porque será la cara visible del Web Service.

Todo cliente externo, como Angular, Postman o cualquier sistema consumidor, se comunicará con el proyecto a través de estas clases.

---

# Resumen

El paquete:

com.logistica.resource

contiene los endpoints REST del proyecto.

Su responsabilidad principal es recibir solicitudes HTTP, llamar a la lógica correspondiente y devolver respuestas en JSON o XML.
