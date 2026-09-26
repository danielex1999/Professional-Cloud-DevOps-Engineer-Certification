# Diseño de APIs

## APIs coherentes

Es importante diseñar **APIs coherentes** para los servicios.

Google ofrece una guía con recomendaciones sobre:

* Nombres.
* Manejo de errores.
* Control de versiones.
* Compatibilidad.
* Entre otros.

También existe una guía de estilo para las APIs.

Para revisar ejemplos de prácticas recomendadas, se pueden consultar las APIs de Google Cloud.

---

# APIs de Google Cloud

Cada servicio de Google Cloud expone una **API de REST**.

Las funciones se definen con el formato:

```text id="u9xq4s"
servicio.colección.verbo
```

### Servicio

Representa el extremo del servicio.

Por ejemplo, para la API de Compute Engine:

```text id="z6jv5q"
https://compute.googleapis.com
```

### Colecciones

Para Compute Engine se incluyen:

```text id="t5tq6y"
instances
instanceGroups
instanceTemplates
```

### Verbos

Entre los verbos se incluyen:

```text id="v7l4d9"
LIST
GET
INSERT
```

Por ejemplo, para ver las instancias de Compute Engine, se realiza una solicitud `GET` al vínculo correspondiente.

---

# Parámetros

Los parámetros se pueden pasar:

```text id="6nq2xj"
┌─────────────┐
│ URL         │
└─────────────┘

      o

┌─────────────┐
│ Cuerpo      │
│ de solicitud│
│    JSON     │
└─────────────┘
```

---

# OpenAPI

**OpenAPI** es un estándar de la industria para exponer APIs a clientes.

La versión `2.0` de la especificación se conocía como **Swagger**.

Actualmente, Swagger es un kit de herramientas de código abierto basado en OpenAPI que, junto con sus herramientas asociadas, permite:

* Diseñar APIs.
* Crear APIs.
* Consumir APIs.
* Documentar APIs.

---

## Enfoque centrado en APIs

OpenAPI admite un enfoque **centrado en las APIs**.

Diseñar APIs con OpenAPI puede proporcionar una única fuente de información desde la cual se pueden crear automáticamente:

```text id="6j8f0p"
          OpenAPI
             │
    ┌────────┼────────┐
    ▼        ▼        ▼
Código     Stubs   Documentación
cliente   servidor   de usuarios
```

Esto permite generar:

* Código fuente para bibliotecas cliente.
* Stubs de servidor.
* Documentación para usuarios de API.

**Cloud Endpoints** y **Apigee** admiten OpenAPI.

---

# Ejemplo de OpenAPI

La documentación incluye una especificación de ejemplo de OpenAPI para una tienda de mascotas.

El URI es:

```text id="b8w6jz"
petstore.swagger.io/v1
```

Se puede observar la **versión** dentro del URI.

El ejemplo muestra el extremo:

```text id="7b6k4f"
/pets
```

Este extremo utiliza:

```text id="s8n6yv"
GET
```

y proporciona una lista de todas las mascotas.

---

# gRPC

**gRPC**, desarrollado en Google, es un protocolo binario muy útil para la comunicación interna de microservicios.

```text id="x0w4jm"
              gRPC
                │
      ┌─────────┼─────────┐
      ▼         ▼         ▼
  Muchos     Bajo       Alto
 lenguajes  acoplamiento rendimiento
```

### Características

* Admite muchos lenguajes de programación.
* Es compatible con el acoplamiento bajo mediante contratos definidos con búferes de protocolo.
* Tiene alto rendimiento por ser un protocolo binario.
* Se basa en HTTP/2.
* Admite transmisiones de clientes y servidores.

---

# Google Cloud y gRPC

Muchos servicios de Google Cloud admiten gRPC.

Entre ellos:

* Balanceador de cargas global.
* Cloud Endpoints para microservicios.
* GKE con un proxy Envoy.

---

# Herramientas para administrar APIs

Google Cloud ofrece tres herramientas para administrar APIs:

```text id="7w8h1k"
┌──────────────────┐
│ Cloud Endpoints  │
├──────────────────┤
│ Apigee           │
├──────────────────┤
│ API Gateway      │
└──────────────────┘
```

---

# Cloud Endpoints

**Cloud Endpoints** es una puerta de enlace de administración de APIs que ayuda a:

* Desarrollar APIs.
* Implementar APIs.
* Administrar APIs.

Puede utilizarse con cualquier backend de Google Cloud.

Se ejecuta en Google Cloud y utiliza gran parte de la infraestructura subyacente de Google.

---

# Apigee

**Apigee** es una plataforma empresarial de administración de APIs.

Permite realizar implementaciones:

```text id="e2x3r7"
Nube
  │
  ├── Local
  │
  └── Híbrida
```

### Funciones

Entre sus funciones se incluyen:

* Portal personalizable.
* Puerta de enlace de API para integrar socios y desarrolladores.
* Monetización.
* Análisis profundos en torno a APIs.

Apigee sirve para backends HTTP o HTTPS sin importar dónde se ejecuten:

* A nivel local.
* En cualquier nube pública.

---

# API Gateway

**API Gateway** permite brindar acceso seguro a los servicios de backend mediante una API de REST bien definida.

La API puede ser coherente en todos los servicios, independientemente de la implementación del servicio.

```text id="p6h2kd"
                API Gateway
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
       Servicio   Servicio   Servicio
          A          B          C
```

---

# Comparación de las herramientas

| Herramienta         | Descripción                                                                                                             |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Cloud Endpoints** | Puerta de enlace de administración de APIs para desarrollar, implementar y administrar APIs en backends de Google Cloud |
| **Apigee**          | Plataforma empresarial de administración de APIs para implementaciones en la nube, locales o híbridas                   |
| **API Gateway**     | Permite proporcionar acceso seguro a servicios de backend mediante una API de REST coherente                            |

---

# Funcionalidades compartidas

Las tres soluciones ofrecen herramientas para servicios como:

* Autenticación de usuarios.
* Supervisión.
* Protección.
* OpenAPI.
* gRPC.

```text
             Administración de APIs
                       │
       ┌───────────────┼───────────────┐
       ▼               ▼               ▼
Cloud Endpoints      Apigee       API Gateway
       │               │               │
       └───────────────┼───────────────┘
                       ▼
          Autenticación / Supervisión
              Protección / OpenAPI
                     / gRPC
```

---

# Resumen

```text
                    DISEÑO DE APIs
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
       REST API         OpenAPI          gRPC
          │               │               │
          │               │               └── HTTP/2
          │               └── Contratos
          │
          └── servicio.colección.verbo
                          │
                          ▼
              Administración de APIs
                          │
             ┌────────────┼────────────┐
             ▼            ▼            ▼
       Cloud Endpoints  Apigee   API Gateway
```

### Conceptos clave

* APIs coherentes.
* Guía de APIs.
* APIs de Google Cloud.
* `servicio.colección.verbo`.
* OpenAPI.
* Swagger.
* Contratos.
* gRPC.
* Búferes de protocolo.
* HTTP/2.
* Cloud Endpoints.
* Apigee.
* API Gateway.
* Autenticación.
* Supervisión.
* Protección.
