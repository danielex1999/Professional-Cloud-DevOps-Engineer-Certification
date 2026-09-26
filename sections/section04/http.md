# Solicitudes y respuestas HTTP

## Solicitud HTTP

Un cliente que accede a servicios HTTP forma una **solicitud HTTP**.

Una solicitud HTTP se compone de tres partes:

```text
┌──────────────────────────┐
│  Línea de solicitud      │
├──────────────────────────┤
│  Variables de encabezado │
├──────────────────────────┤
│  Cuerpo de la solicitud  │
└──────────────────────────┘
```

---

# 1. Línea de solicitud

La línea de solicitud contiene:

* Verbo HTTP: `GET`, `POST`, `PUT`, etc.
* URI solicitado.
* Versión del protocolo.

```text
GET /pets HTTP/1.1
```

---

# 2. Variables de encabezado

Los encabezados contienen **pares clave-valor**.

Algunos son estándar, como:

### User-Agent

Ayuda al receptor a identificar el agente de software que realiza la solicitud.

También pueden incluirse metadatos sobre:

* El formato del mensaje.
* Los formatos preferidos.

En los servicios REST basados en HTTPS también se pueden agregar **encabezados personalizados**.

---

# 3. Cuerpo de la solicitud

El cuerpo contiene los datos que se enviarán al servidor.

Es relevante para comandos HTTP que envían datos, como:

* `POST`
* `PUT`

---

# Ejemplos de solicitudes HTTP

## GET

Una solicitud GET HTTP a una URL utilizando HTTP/1.1:

```text
GET / HTTP/1.1
Host: pets.drehnstrom.com
```

En este caso existe una variable de encabezado:

```text
Host: pets.drehnstrom.com
```

---

## POST

Una solicitud POST HTTP a `/add` utilizando HTTP/1.1:

```text
POST /add HTTP/1.1
Host: pets.drehnstrom.com
Content-Type: application/json
Content-Length: 35

{
  "name": "Noir",
  "breed": "schnoodle"
}
```

La solicitud contiene tres variables de encabezado:

```text
Host
Content-Type: JSON
Content-Length: 35 bytes
```

El cuerpo contiene el documento JSON con:

```text
name  → Noir
breed → schnoodle
```

Esta es la representación que se agregó de la mascota.

---

# Verbos HTTP

El verbo HTTP indica al servidor la **acción que debe realizar sobre un recurso**.

HTTP proporciona nueve verbos, pero los cuatro que suele utilizar REST son:

| Verbo    | Uso                                              |
| -------- | ------------------------------------------------ |
| `GET`    | Recuperar recursos                               |
| `POST`   | Solicitar la creación de un recurso nuevo        |
| `PUT`    | Crear un recurso nuevo o modificar uno existente |
| `DELETE` | Quitar un recurso                                |

---

## GET

Se utiliza para:

> **Recuperar recursos**

---

## POST

Se utiliza para:

> **Solicitar la creación de un recurso nuevo**

El servicio crea el recurso y, por lo general, muestra al cliente el **ID único generado** para el nuevo recurso.

---

## PUT

Se utiliza para:

* Crear un recurso nuevo.
* Modificar un recurso existente.

Las solicitudes `PUT` deben ser **idempotentes**.

### ¿Qué significa idempotente?

Sin importar cuántas veces el cliente realice la misma solicitud al servicio:

> **Los efectos sobre el recurso siempre serán los mismos.**

---

## DELETE

Se utiliza para:

> **Quitar un recurso**

---

# Respuesta HTTP

Los servicios HTTP muestran respuestas en un formato estándar definido por HTTP.

Una respuesta HTTP también se compone de tres partes:

```text
┌───────────────────────────┐
│  Línea de respuesta       │
├───────────────────────────┤
│  Variables de encabezado  │
├───────────────────────────┤
│  Cuerpo de la respuesta   │
└───────────────────────────┘
```

---

# 1. Línea de respuesta

Contiene:

* Versión HTTP.
* Código de respuesta.

Los códigos de respuesta se organizan en rangos cercanos a 100.

### Códigos 2xx — Éxito

El rango `200` indica que la solicitud tuvo éxito.

| Código | Significado             |
| ------ | ----------------------- |
| `200`  | La solicitud tuvo éxito |
| `201`  | Se creó un recurso      |

---

### Códigos 4xx — Error del cliente

El rango `400` indica que la solicitud del cliente se encuentra en un estado de error.

| Código | Significado                                                |
| ------ | ---------------------------------------------------------- |
| `403`  | Prohibido: el solicitante no tiene los permisos necesarios |
| `404`  | No se encontró el recurso solicitado                       |

---

### Códigos 5xx — Error del servidor

El rango `500` indica que el servidor encontró un error y no puede procesar la solicitud.

| Código | Significado                                  |
| ------ | -------------------------------------------- |
| `500`  | Error interno del servidor                   |
| `503`  | No disponible; el servidor está sobrecargado |

---

# 2. Encabezado de respuesta

El encabezado de respuesta es un conjunto de pares clave-valor.

Por ejemplo:

```text
Content-Type
```

Este indica al receptor el tipo de contenido incluido en el cuerpo de la respuesta.

---

# 3. Cuerpo de la respuesta

El cuerpo contiene la representación del recurso solicitado.

El formato está especificado en el encabezado `Content-Type`.

Puede ser:

* JSON
* XML
* HTML
* Etc.

```text
Respuesta HTTP
      │
      ├── Línea de respuesta
      │
      ├── Encabezados
      │
      └── Cuerpo
             │
             └── Representación del recurso
```

---

# Diseño coherente de una API

Los siguientes lineamientos se enfocan en lograr **coherencia en la API**.

## Recursos individuales y colecciones

Se deben utilizar:

```text
Singular   → Recursos individuales
Plural     → Colecciones o conjuntos
```

### Ejemplo

Consideremos el recurso:

```text
/pet
```

Una solicitud:

```text
GET /pet/1
```

debería buscar una mascota con el ID `1`.

Mientras que:

```text
GET /pets
```

debería buscar todas las mascotas.

---

# URI y verbos HTTP

No se deben utilizar URI como:

```text
GET /getPets
```

El URI debe referirse al **recurso**, no a la acción sobre el recurso.

La acción es responsabilidad del:

> **Verbo HTTP**

```text
GET    → Acción
  +
/pets  → Recurso
```

---

# Consideraciones sobre los URI

Los URI:

* No distinguen mayúsculas de minúsculas.
* Incluyen información de la versión.

---

# Diagramación de servicios

Diagramar los servicios es una práctica recomendada.

Un servicio puede brindar acceso a un recurso conocido como:

> **Pets**

La representación del recurso es:

> **Pet**

```text
┌──────────────────┐
│     Servicio     │
└────────┬─────────┘
         │
         │ acceso
         ▼
┌──────────────────┐
│     Recurso      │
│      Pets        │
└────────┬─────────┘
         │
         │ representaciones
         ▼
┌──────────────────┐
│       Pet        │
└──────────────────┘
```

Cuando se realiza una solicitud para un recurso mediante el servicio, se muestran una o más representaciones de **Pet**.

---

# Resumen

```text
                 HTTP
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
    Solicitud             Respuesta
        │                   │
   ┌────┼────┐         ┌────┼────┐
   ▼    ▼    ▼         ▼    ▼    ▼
 Línea Enc. Cuerpo    Línea Enc. Cuerpo
   │                  │
   ▼                  ▼
 Verbo + URI       Código HTTP
```

### Conceptos clave

* Solicitud HTTP.
* Línea de solicitud.
* Encabezados.
* Cuerpo.
* URI.
* `GET`.
* `POST`.
* `PUT`.
* `DELETE`.
* Idempotencia.
* Respuesta HTTP.
* Códigos `2xx`, `4xx` y `5xx`.
* `Content-Type`.
* Recursos.
* Representaciones.
* Colecciones.
* Coherencia de API.
* Versionado.
* Diagramación de servicios.
