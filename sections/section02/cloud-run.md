# Cloud Run

## ¿Qué es?

**Cloud Run** es una plataforma de procesamiento administrada que ejecuta **contenedores sin estado** mediante solicitudes web o eventos de Pub/Sub.

Cloud Run es una tecnología **sin servidores (serverless)**.

Esto permite que el desarrollador no tenga que administrar la infraestructura y pueda enfocarse en desarrollar aplicaciones.

Cloud Run se basa en **Knative**, una API abierta y un entorno de ejecución basado en Kubernetes.

Puede administrarse en:

* Google Cloud
* Kubernetes Engine
* Cualquier plataforma que ejecute Knative

---

## Características

Cloud Run puede:

* Aumentar y reducir la escala automáticamente.
* Escalar desde cero.
* Cobrar solo por los recursos utilizados.
* Calcular el uso con una precisión de **100 ms**.
* Agregar y quitar contenedores según las solicitudes.

No se paga por recursos sobreaprovisionados.

---

## Flujo de trabajo

El flujo de trabajo para desarrolladores de Cloud Run consta de 3 pasos:

```text
1. Escribir la aplicación
          ↓
2. Crear la imagen de contenedor
          ↓
3. Subirla a Artifact Registry
          ↓
       Cloud Run
```

### 1. Escribir la aplicación

Puedes utilizar tu lenguaje de programación favorito.

La aplicación debe iniciar un servidor que escuche solicitudes web.

### 2. Crear la imagen

La aplicación se compila y se empaqueta en una **imagen de contenedor**.

### 3. Artifact Registry

La imagen de contenedor se envía a **Artifact Registry**, desde donde Cloud Run la implementará.

Al implementar la imagen se obtiene una **URL HTTPS única**.

---

## Escalado automático

Cloud Run inicia los contenedores cuando recibe solicitudes.

Según la demanda:

```text
Más solicitudes
      ↓
Más contenedores

Menos solicitudes
      ↓
Menos contenedores

Sin solicitudes
      ↓
Escala a cero
```

---

# Implementación basada en código fuente

Cloud Run también permite utilizar un flujo de trabajo basado directamente en **código fuente**.

En este caso:

```text
Código fuente
      ↓
Cloud Run
      ↓
Buildpacks
      ↓
Imagen de contenedor
      ↓
Implementación
```

Cloud Run utiliza **Buildpacks**, un proyecto de código abierto, para compilar el código fuente y empaquetarlo en una imagen de contenedor.

---

## HTTPS

Cloud Run controla la entrega de **HTTPS**.

El desarrollador solo debe preocuparse por controlar las solicitudes web, mientras Cloud Run se encarga de agregar la encriptación.

---

# Precios

Cloud Run cobra por los recursos del sistema utilizados mientras un contenedor está procesando solicitudes web.

El cálculo se realiza con una precisión de **100 ms**.

También se cobra durante:

* Inicio del contenedor.
* Procesamiento de solicitudes.
* Apagado del contenedor.

Si el contenedor **no está procesando solicitudes**, no se paga por esos recursos.

Además, existe una pequeña tarifa por cada **millón de solicitudes** entregadas.

El costo del tiempo del contenedor aumenta según:

* CPU
* Memoria

Por lo tanto:

```text
Más CPU + más memoria
        ↓
Mayor costo
```

---

## Lenguajes

Cloud Run puede ejecutar cualquier binario compilado para **Linux de 64 bits**.

Puede utilizarse con lenguajes como:

* Java
* Python
* Node.js
* PHP
* Go
* C++

También permite ejecutar lenguajes como:

* COBOL
* Haskell
* Perl

Mientras la aplicación pueda controlar **solicitudes web**, puede ejecutarse en Cloud Run.

---

# Conceptos clave

| Concepto              | Descripción                                                     |
| --------------------- | --------------------------------------------------------------- |
| **Cloud Run**         | Plataforma administrada para ejecutar contenedores              |
| **Serverless**        | No requiere administrar infraestructura                         |
| **Knative**           | Base de Cloud Run                                               |
| **Artifact Registry** | Almacena las imágenes de contenedor                             |
| **Buildpacks**        | Permiten construir una imagen desde código fuente               |
| **Escalado a cero**   | Puede reducir los contenedores a cero cuando no hay solicitudes |
| **HTTPS**             | Cloud Run administra la entrega HTTPS                           |
| **100 ms**            | Precisión de facturación del uso de recursos                    |
