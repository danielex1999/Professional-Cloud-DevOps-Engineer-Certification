# Cloud DNS y Cloud CDN

## Cloud DNS

**DNS (Domain Name System)** traduce los nombres de host de Internet a direcciones.

Uno de los servicios DNS públicos más conocidos de Google es:

```text
8.8.8.8
```

Para las aplicaciones integradas en Google Cloud, existe **Cloud DNS**, un servicio DNS administrado que funciona sobre la infraestructura de Google.

### Características

* Baja latencia.
* Alta disponibilidad.
* Información DNS entregada desde ubicaciones redundantes.
* Administración mediante:

  * Consola de Cloud
  * Línea de comandos
  * API
* Permite administrar millones de zonas y registros DNS.

```text
Nombre de host
      ↓
  Cloud DNS
      ↓
  Dirección
      ↓
Aplicación
```

---

## Cloud CDN

Google cuenta con un sistema global de **cachés perimetrales**.

La caché perimetral permite almacenar contenido **más cerca de los usuarios**.

**Cloud CDN (Content Delivery Network)** utiliza este sistema para acelerar la entrega de contenido de las aplicaciones.

```text
        Aplicación
            ↓
        Cloud CDN
        ↙      ↘
    Caché 1   Caché 2
       ↓         ↓
   Usuarios   Usuarios
```

### Beneficios

Cloud CDN permite:

* Reducir la latencia de red.
* Reducir la carga del origen del contenido.
* Potencialmente ahorrar dinero.

### Habilitación

Después de configurar un **balanceador de cargas de aplicaciones**, Cloud CDN puede habilitarse con una sola casilla de verificación.

---

## CDN Interconnect

Existen muchas otras CDN disponibles.

Si ya utilizas una CDN externa, es posible que forme parte del programa **CDN Interconnect** de Google Cloud, permitiendo continuar utilizándola.

### Resumen

| Servicio             | Función principal                                          |
| -------------------- | ---------------------------------------------------------- |
| **8.8.8.8**          | DNS público de Google                                      |
| **Cloud DNS**        | Gestionar nombres de host y direcciones                    |
| **Cloud CDN**        | Acelerar la entrega de contenido mediante caché perimetral |
| **CDN Interconnect** | Integración con determinados proveedores de CDN            |
