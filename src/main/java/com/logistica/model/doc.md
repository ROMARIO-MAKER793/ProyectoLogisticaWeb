# Paquete `com.logistica.model`

## Objetivo del paquete

El paquete `com.logistica.model` contiene las clases que representan las entidades principales del proyecto.

Estas clases reflejan la estructura de las tablas de la base de datos y serán utilizadas para transportar información entre las diferentes capas del sistema.

---

# ¿Qué es un Model?

Un Model representa un objeto del dominio del proyecto.

Ejemplo:

Cliente
Envio
SeguimientoEnvio
Conductor
Vehiculo

Cada clase tendrá atributos, constructores, getters y setters.

---

# Clases incluidas

## Cliente.java

Representa al cliente que solicita un envío.

Atributos principales:

idCliente
nombres
apellidos
documento
telefono
correo
direccion
estado
fechaRegistro

---

## Conductor.java

Representa al conductor asignado a uno o varios envíos.

Atributos principales:

idConductor
nombres
apellidos
dni
licencia
telefono
estado

---

## Vehiculo.java

Representa el vehículo utilizado para realizar envíos.

Atributos principales:

idVehiculo
placa
marca
modelo
capacidadKg
estado

---

## Envio.java

Representa el envío principal del sistema.

Atributos principales:

idEnvio
codigoSeguimiento
idCliente
idConductor
idVehiculo
origen
destino
descripcionPaquete
pesoKg
fechaRegistro
fechaEntregaEstimada
estado

---

## SeguimientoEnvio.java

Representa el historial o movimiento de un envío.

Atributos principales:

idSeguimiento
idEnvio
fechaHora
ubicacion
estado
descripcion

---

# Responsabilidades del paquete

Las clases Model deben:

Representar datos del proyecto.
Servir como puente entre DAO, Service y Resource.
Ser compatibles con JSON.
Ser compatibles con XML.
Contener atributos relacionados a la base de datos.
Permitir el transporte de información entre capas.

---

# Relación con la base de datos

Cada clase del paquete `model` se relaciona con una tabla de MySQL.

Cliente.java             → cliente
Conductor.java           → conductor
Vehiculo.java            → vehiculo
Envio.java               → envio
SeguimientoEnvio.java    → seguimiento_envio

---

# Relación con JSON

Los objetos Model podrán convertirse a JSON para ser enviados a Angular.

Ejemplo conceptual:

Objeto Envio
↓
JSON
↓
Angular

Ejemplo de respuesta:

{
  "codigoSeguimiento": "ENV-0001",
  "origen": "Lima Centro",
  "destino": "San Juan de Lurigancho",
  "estado": "EN_CAMINO"
}

---

# Relación con XML

Los objetos Model también podrán convertirse a XML para demostrar interoperabilidad.

Ejemplo conceptual:

Objeto Envio
↓
XML
↓
Sistema externo o archivo exportado

Ejemplo:

<envio>
    <codigoSeguimiento>ENV-0001</codigoSeguimiento>
    <origen>Lima Centro</origen>
    <destino>San Juan de Lurigancho</destino>
    <estado>EN_CAMINO</estado>
</envio>

---

# Qué NO debe hacer este paquete

Las clases Model NO deben:

Ejecutar SQL.
Abrir conexiones a MySQL.
Contener lógica de negocio compleja.
Generar códigos de seguimiento.
Enviar notificaciones Socket.
Crear Threads.
Crear endpoints REST.
Exportar archivos.
Generar PDF.

---

# Relación con otros paquetes

dao.impl
    ↓
model
    ↓
service
    ↓
resource

Los DAO convierten los datos de MySQL en objetos Model.

Los Services trabajan con esos objetos.

Los Resources los devuelven como respuesta en JSON o XML.

---

# Buenas prácticas

Las clases Model deben mantenerse simples.

Se recomienda que tengan:

Atributos privados.
Constructor vacío.
Constructor con parámetros.
Getters.
Setters.
toString opcional.
Anotaciones JAXB cuando sea necesario.

---

# Importancia dentro del proyecto

Este paquete es importante porque define la forma de los datos que manejará todo el Web Service.

Si el modelo está mal definido, se verán afectados:

DAO
Service
Resource
JSON
XML
Exportaciones
Angular

---

# Resumen

El paquete:

com.logistica.model

contiene las entidades del proyecto.

Estas clases representan los datos principales del sistema y son utilizadas por todas las capas para transportar información de forma ordenada.
