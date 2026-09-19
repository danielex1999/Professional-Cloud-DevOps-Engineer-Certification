# Cloud Run Functions

Muchas aplicaciones contienen partes controladas por **eventos**.

Por ejemplo, una aplicación puede permitir que los usuarios suban imágenes. Cuando esto sucede, la imagen puede:

* Convertirse a un formato estándar.
* Cambiar el tamaño de la miniatura.
* Almacenarse en un repositorio.

Esta función podría integrarse directamente en una aplicación, pero sería necesario proporcionarle recursos de procesamiento independientemente de la frecuencia con la que ocurra.

## ¿Qué es Cloud Run Functions?

**Cloud Run Functions** permite escribir funciones de un solo propósito que se ejecutan automáticamente cuando ocurre un evento.

Es una solución:

* Ligera.
* Asíncrona.
* Basada en eventos.
* Sin necesidad de administrar servidores ni entornos de ejecución.

```text
Evento
  ↓
Cloud Run Functions
  ↓
Función
  ↓
Procesamiento
```

## Usos

Cloud Run Functions puede utilizarse para:

* Crear flujos de trabajo de aplicaciones.
* Ejecutar tareas de lógica empresarial.
* Conectar servicios de Cloud.
* Extender servicios de Cloud.

## Ejemplo: procesamiento de imágenes

```text
Usuario
   ↓
Sube una imagen
   ↓
Cloud Storage
   ↓
Cloud Run Functions
   ↓
Procesar imagen
   ├── Convertir formato
   ├── Cambiar tamaño
   └── Almacenar nuevo archivo
```

La función se ejecuta automáticamente cuando se sube una nueva imagen.

## Facturación

La facturación se realiza a los **100 ms más cercanos** y solo durante el tiempo que se ejecuta el código.

## Lenguajes

Cloud Run Functions permite escribir código fuente en:

* Node.js
* Python
* Go
* Java
* .NET Core
* Ruby
* PHP

## Activación por eventos

Los eventos de **Cloud Storage** y **Pub/Sub** pueden activar Cloud Run Functions de forma asíncrona.

También se puede utilizar una invocación **HTTP** para una ejecución síncrona.

```text
Asíncrono
├── Cloud Storage
└── Pub/Sub

Síncrono
└── HTTP
```
