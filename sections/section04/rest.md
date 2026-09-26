# Diseño de microservicios basados en REST y HTTP

## Microservicios independientes

Uno de los aspectos más importantes de las aplicaciones basadas en microservicios es poder implementar los microservicios **completamente independientes entre sí**.

Para lograrlo, cada microservicio debe proporcionar un:

> **Contrato bien definido**

Sus clientes pueden ser:

* Otros microservicios.
* Aplicaciones.

```text id="2xqf6k"
┌──────────────┐
│ Microservicio│
│      A       │
└──────┬───────┘
       │
       │ Contrato
       ▼
┌──────────────┐
│ Microservicio│
│      B       │
└──────────────┘
```

---

# Contratos y control de versiones

Los servicios no deben finalizar estos contratos con control de versiones hasta determinar que **ningún microservicio depende de contratos con versiones específicas**.

Esto es importante porque otros microservicios pueden necesitar:

> **Revertir a una versión de código anterior**

y esa versión puede requerir un contrato previo.

Por ello, esta posibilidad debe considerarse dentro de las políticas de baja.

### Desafío organizativo

Mantener una cultura basada en contratos bien definidos y con control de versiones puede ser uno de los aspectos organizativos más desafiantes de una aplicación estable basada en microservicios.

---

# Comunicación entre servicios

En un nivel inferior de detalle, los servicios se comunican mediante **HTTPS**.

Utilizan cargas útiles basadas en texto, como:

* JSON
* XML

Y utilizan verbos HTTP como:

* `GET`
* `POST`

Estos verbos proporcionan significado a las acciones solicitadas.

```text id="jv3y6x"
Cliente
   │
   │ HTTPS
   │
   ├── GET
   ├── POST
   │
   ▼
Servicio
```

El cliente solo necesita conocer los detalles mínimos para utilizar el servicio:

```text id="ys7c89"
URI
 │
 ├── Solicitud
 │
 └── Formato de respuesta
```

---

# REST y acoplamiento bajo

La arquitectura **REST** admite el acoplamiento bajo.

REST significa:

> **Transferencia de estado representacional**

REST no depende de protocolos.

El protocolo **HTTP** es el más común, pero **gRPC** también se utiliza ampliamente.

```text id="d4g9vf"
              REST
               │
       ┌───────┴───────┐
       ▼               ▼
     HTTP             gRPC
```

Aunque REST admite el acoplamiento bajo, se necesitan prácticas de ingeniería robustas para mantenerlo.

---

# Contratos de API

Un buen punto de partida es tener un:

> **Contrato bien definido**

Las implementaciones basadas en HTTP pueden utilizar un estándar como:

**OpenAPI**

Mientras que:

**gRPC → búferes de protocolo**

```text id="f4ct1a"
Contrato
   │
   ├── HTTP → OpenAPI
   │
   └── gRPC → Búferes de protocolo
```

---

# Retrocompatibilidad

Para mantener el acoplamiento bajo es crucial:

* Mantener la retrocompatibilidad del contrato.
* Diseñar una API alrededor de un dominio.
* Evitar diseñar la API alrededor de casos de uso o clientes particulares.

Si se diseña alrededor de casos de uso o clientes particulares:

```text id="b4x0zo"
Nuevo caso de uso
       │
       ▼
Nueva API REST
       │
       ▼
API con propósito especial
```

Cada caso de uso o aplicación nueva requeriría otra API REST con propósito especial, independientemente del protocolo.

---

# Solicitudes, respuestas y transmisiones

El procesamiento de solicitudes y respuestas es el caso de uso típico.

Sin embargo, también pueden requerirse **transmisiones**, lo que puede influir en la elección del protocolo.

Por ejemplo:

> **gRPC admite transmisiones.**

---

# Recursos y URI

Los **URI** o extremos identifican los recursos.

Las respuestas a las solicitudes devuelven una representación de la información del recurso.

```text id="v0zv0u"
URI
 │
 ▼
Recurso
 │
 ▼
Representación
```

Las aplicaciones REST proporcionan interfaces coherentes y uniformes y pueden vincular recursos adicionales.

---

# Hipermedia

**Hipermedia como motor del estado de la aplicación** es un componente de REST.

Permite que el cliente requiera poco conocimiento previo de un servicio.

Esto se consigue porque las respuestas pueden ofrecer vínculos a recursos adicionales.

```text id="y9h6di"
Respuesta
   │
   ├── Recurso
   ├── Recurso adicional
   └── Recurso adicional
```

---

# Diseño de API

El diseño de API debe formar parte del proceso de desarrollo.

Idealmente, se debe implementar un conjunto de reglas de diseño de API que ayude a las APIs REST a proporcionar una:

> **Interfaz uniforme**

Por ejemplo:

* Cada servicio informa los errores de manera constante.
* La estructura de las URLs es coherente.
* El uso de las páginas es coherente.

También se debe considerar el **almacenamiento en caché** para:

* Optimizar los recursos inmutables.
* Mejorar el rendimiento.

---

# Recursos y representaciones

En REST, un cliente y un servidor intercambian:

> **Representaciones de un recurso**

Un **recurso** es una noción abstracta de información.

Una **representación de un recurso** es una copia de la información de este.

### Ejemplo

Un recurso puede representar un perro.

```text id="6gd7kj"
              RECURSO
                 │
              "Perro"
                 │
        ┌────────┴────────┐
        ▼                 ▼
     Chocolate           Berta
     Schnoodle           Mestiza
```

Chocolate y Berta representan dos representaciones diferentes del recurso.

---

# URI y representación

El **URI** proporciona acceso a un recurso.

Cuando se realiza una solicitud para ese recurso, la respuesta devuelve una representación de este.

Por lo general, la representación se devuelve en formato:

> **JSON**

```text id="4e5t8u"
Cliente
   │
   │ Solicitud al URI
   ▼
Recurso
   │
   │ Representación
   ▼
 JSON
```

---

# Elementos y conjuntos

Los recursos solicitados pueden ser:

* Elementos únicos.
* Conjuntos de elementos.

Por motivos de rendimiento, puede ser beneficioso mostrar conjuntos de elementos en lugar de elementos individuales.

Estas operaciones suelen llamarse:

> **APIs en lotes**

---

# Formatos de representación

La representación de un recurso entre un cliente y los servicios normalmente se realiza mediante formatos estándar basados en texto.

Los principales formatos mencionados son:

```text id="3qgc3p"
Formatos basados en texto
        │
        ├── JSON
        └── XML
```

### JSON

JSON es la norma para los formatos basados en texto.

En las APIs orientadas al público o externas:

> **JSON es el formato estándar.**

### gRPC

En servicios internos se puede utilizar **gRPC**, especialmente cuando el rendimiento es clave.

---

# Resumen

```text id="4a0s2f"
Microservicios independientes
          │
          ▼
  Contratos bien definidos
          │
          ▼
   Retrocompatibilidad
          │
          ▼
      Acoplamiento bajo
          │
     ┌────┴────┐
     ▼         ▼
   REST      gRPC
     │
     ▼
HTTP + JSON/XML
     │
     ▼
  Recursos
     │
     ▼
Representaciones
```

### Conceptos clave

* Contratos bien definidos.
* Control de versiones.
* Retrocompatibilidad.
* REST.
* HTTP.
* HTTPS.
* URI.
* Recursos.
* Representaciones.
* JSON.
* XML.
* OpenAPI.
* gRPC.
* Búferes de protocolo.
* APIs en lotes.
* Hipermedia.
* Caché.
* Acoplamiento bajo.
