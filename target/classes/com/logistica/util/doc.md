# Paquete `com.logistica.util`

## Objetivo del paquete

El paquete `com.logistica.util` contiene clases utilitarias y funciones de apoyo utilizadas por las diferentes capas del proyecto.

Su finalidad es centralizar funcionalidades reutilizables para evitar duplicación de código y mantener una arquitectura más limpia.

---

# ¿Qué es un Util?

Una clase Util es una clase auxiliar que contiene funcionalidades genéricas que pueden ser utilizadas por múltiples módulos del sistema.

Ejemplos:

Conexiones.
Fechas.
Generación de códigos.
Conversión JSON.
Conversión XML.
Respuestas comunes.

Estas clases no contienen lógica de negocio.

---

# Clases incluidas

## ConexionBD.java

Responsable de gestionar la conexión con MySQL.

Responsabilidades:

Abrir conexiones.
Cerrar conexiones.
Centralizar parámetros de conexión.
Facilitar acceso a JDBC.

Será utilizada principalmente por:

dao.impl

---

## CodigoSeguimientoUtil.java

Responsable de generar códigos únicos de seguimiento.

Ejemplos:

ENV-0001
ENV-0002
ENV-0003

Responsabilidades:

Generar códigos.
Mantener formato estándar.
Evitar duplicación de lógica.

---

## FechaUtil.java

Responsable de trabajar con fechas del sistema.

Responsabilidades:

Obtener fecha actual.
Formatear fechas.
Convertir formatos de fecha.
Facilitar cálculos relacionados con fechas.

---

## JsonUtil.java

Responsable de apoyar procesos relacionados con JSON.

Responsabilidades:

Convertir objetos a JSON.
Generar archivos JSON.
Facilitar exportaciones.

Trabajará junto con:

Jackson

---

## XmlUtil.java

Responsable de apoyar procesos relacionados con XML.

Responsabilidades:

Convertir objetos a XML.
Generar archivos XML.
Facilitar exportaciones.

Trabajará junto con:

JAXB

---

## RespuestaUtil.java

Responsable de centralizar respuestas comunes del sistema.

Responsabilidades:

Mensajes estándar.
Respuestas reutilizables.
Ayuda en manejo de errores.

Ejemplos:

Registro exitoso.
Registro no encontrado.
Operación completada.
Error interno.

---

# Responsabilidades del paquete

Las clases Util deben:

Contener funciones reutilizables.
Evitar duplicación de código.
Facilitar mantenimiento.
Apoyar otras capas.
Centralizar tareas comunes.

---

# Qué NO debe hacer este paquete

Las clases Util NO deben:

Ejecutar SQL directamente.
Definir endpoints REST.
Implementar lógica de negocio.
Registrar envíos.
Actualizar estados.
Enviar notificaciones Socket.
Controlar flujo principal del sistema.

Su función es únicamente brindar apoyo a otras capas.

---

# Relación con otros paquetes

dao.impl
↓
util

service.impl
↓
util

thread
↓
util

Prácticamente cualquier módulo puede utilizar herramientas del paquete util cuando sea necesario.

---

# Ejemplo conceptual

Generación de código de seguimiento:

EnvioServiceImpl
↓
CodigoSeguimientoUtil
↓
ENV-0001

---

Exportación JSON:

ExportacionServiceImpl
↓
JsonUtil
↓
envios.json

---

Exportación XML:

ExportacionServiceImpl
↓
XmlUtil
↓
envios.xml

---

Conexión a MySQL:

EnvioDAOImpl
↓
ConexionBD
↓
MySQL

---

# Beneficios dentro del proyecto

La utilización de clases utilitarias permite:

Reducir código repetido.
Mejorar organización.
Facilitar mantenimiento.
Centralizar funcionalidades comunes.
Aumentar reutilización.

---

# Buenas prácticas

Se recomienda:

Mantener métodos pequeños.
Crear utilidades genéricas.
Evitar lógica de negocio.
Documentar funciones reutilizables.
Mantener independencia de otras capas.

---

# Importancia dentro del proyecto

Este paquete ayuda a mantener una arquitectura limpia y ordenada.

Permite que las demás capas se enfoquen en sus responsabilidades específicas sin repetir código.

---

# Resumen

El paquete:

com.logistica.util

contiene herramientas y funciones reutilizables utilizadas por todo el proyecto.

Su responsabilidad principal es apoyar a las demás capas mediante utilidades comunes como conexiones, fechas, generación de códigos, exportaciones JSON/XML y respuestas estándar.
