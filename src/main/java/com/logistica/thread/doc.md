# Paquete `com.logistica.thread`

## Objetivo del paquete

El paquete `com.logistica.thread` contiene las clases encargadas de ejecutar procesos concurrentes mediante hilos.

En este proyecto, los hilos se utilizarán principalmente para comparar exportaciones realizadas de forma secuencial contra exportaciones realizadas en paralelo.

---

# ¿Por qué usamos Threads?

Uno de los temas vistos en el curso es el manejo de hilos.

En este proyecto se aplicarán para demostrar:

Procesamiento concurrente.
Ejecución de tareas en paralelo.
Comparación de tiempos.
Mejora de rendimiento en tareas repetitivas.

---

# Clases incluidas

## ExportarClientesThread.java

Responsable de exportar la información de clientes.

---

## ExportarEnviosThread.java

Responsable de exportar la información de envíos.

---

## ExportarSeguimientosThread.java

Responsable de exportar la información de seguimientos.

---

## ExportarConductoresThread.java

Responsable de exportar la información de conductores.

---

## ExportarVehiculosThread.java

Responsable de exportar la información de vehículos.

---

# Uso principal

Los hilos serán utilizados en el módulo de exportación.

Ejemplo:

Exportación secuencial:

1. Exportar clientes.
2. Exportar envíos.
3. Exportar seguimientos.
4. Exportar conductores.
5. Exportar vehículos.

Con hilos:

Exportación concurrente:

Hilo 1: Exportar clientes.
Hilo 2: Exportar envíos.
Hilo 3: Exportar seguimientos.
Hilo 4: Exportar conductores.
Hilo 5: Exportar vehículos.

---

# Comparación de tiempos

El sistema deberá medir cuánto tarda cada proceso.

Ejemplo:

Exportación sin hilos:
Tiempo total: 4500 ms

Exportación con hilos:
Tiempo total: 2100 ms

Esto permitirá demostrar la diferencia entre ejecutar tareas una por una y ejecutarlas en paralelo.

---

# Responsabilidades del paquete

Las clases Thread deben:

Ejecutar una tarea específica.
Exportar información.
Trabajar de forma independiente.
Permitir comparación de tiempos.
Apoyar al módulo de exportaciones.

---

# Qué NO debe hacer este paquete

Las clases Thread NO deben:

Definir endpoints REST.
Responder peticiones HTTP.
Validar reglas de negocio principales.
Registrar envíos.
Actualizar estados.
Enviar notificaciones Socket directamente.
Contener lógica visual de Angular.
Manejar decisiones del negocio.

---

# Relación con otros paquetes

resource
↓
service
↓
service.impl
↓
thread
↓
util

El paquete `thread` será utilizado principalmente por:

ExportacionServiceImpl.java

---

# Flujo conceptual

Cuando Angular solicita una exportación con hilos:

Angular
↓
ExportacionResource
↓
ExportacionService
↓
ExportacionServiceImpl
↓
ExportarClientesThread
ExportarEnviosThread
ExportarSeguimientosThread
ExportarConductoresThread
ExportarVehiculosThread
↓
Archivos JSON/XML

---

# Beneficio académico

Este paquete permite demostrar claramente el uso de hilos en un caso práctico.

La explicación para la exposición sería:

Usamos hilos para ejecutar varias exportaciones al mismo tiempo.
Luego comparamos el tiempo de ejecución contra una exportación secuencial.

---

# Buenas prácticas

Se recomienda:

Usar un hilo por tarea.
Evitar modificar los mismos datos desde varios hilos.
Usar hilos principalmente para lectura/exportación.
Medir tiempos con System.currentTimeMillis().
Manejar errores dentro de cada hilo.
Esperar a que todos los hilos terminen antes de devolver la respuesta.

---

# Importancia dentro del proyecto

Este paquete demuestra el uso práctico de concurrencia.

Aunque el Web Service puede funcionar sin hilos, este módulo permite aplicar uno de los temas enseñados durante el curso y comparar resultados de rendimiento.

---

# Resumen

El paquete:

com.logistica.thread

contiene las clases encargadas de ejecutar tareas concurrentes.

Su objetivo principal es realizar exportaciones en paralelo y comparar el tiempo de ejecución frente a un proceso secuencial.
