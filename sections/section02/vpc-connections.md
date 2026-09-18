# Conectividad de Google Cloud

Los clientes pueden necesitar conectar sus **VPC de Google Cloud** con otras redes, como:

* Redes locales.
* Redes de otros proveedores de nube.

Google Cloud ofrece varias opciones para lograrlo.

## Opciones de conectividad

```text id="c8m4vx"
                Google Cloud VPC
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
   Cloud VPN       Interconexión    Cross-Cloud
                       │
                 Dedicada / Socio
```

---

## Cloud VPN + Cloud Router

**Cloud VPN** permite crear una conexión mediante un túnel sobre Internet.

Para hacer la conexión dinámica se puede utilizar **Cloud Router**.

Cloud Router permite que la VPC y otras redes intercambien información de rutas mediante **BGP (Border Gateway Protocol)**.

```text id="p7x2ka"
Red local
    ↕
Cloud VPN
    ↕
Cloud Router
    ↕
Google Cloud VPC
```

Cuando se agrega una nueva subred a la VPC, la red local puede conocer automáticamente la nueva ruta.

---

## Intercambio de tráfico (Peering)

El **intercambio de tráfico** permite conectar redes mediante un router ubicado en el mismo centro de datos público que un punto de presencia de Google.

Google cuenta con más de **100 puntos de presencia** en todo el mundo.

Si un cliente no está ubicado en uno de ellos, puede utilizar un socio del programa de **intercambio de tráfico por proveedores**.

### Consideración

El intercambio de tráfico **no está cubierto por un ANS de Google**.

---

## Interconexión dedicada

La **Interconexión dedicada** permite establecer una o más conexiones privadas directas con Google.

Si la topología cumple los requisitos establecidos por Google, puede estar cubierta por un **ANS de hasta 99.99%**.

```text id="m3n8qz"
Red local
    │
    │ Conexión privada
    ↓
Google Cloud
```

---

## Interconexión de socio

La **Interconexión de socio** proporciona conectividad entre una red local y una VPC mediante un proveedor de servicios admitido.

Es útil cuando:

* El centro de datos está fuera del alcance de una instalación de Interconexión dedicada.
* Las necesidades de datos no justifican una conexión de **10 Gbps**.

También puede configurarse según las necesidades de disponibilidad.

Si la topología cumple los requisitos de Google, puede tener un **ANS de hasta 99.99%**.

Sin embargo, Google no es responsable de los aspectos de la conexión proporcionados por el proveedor externo ni de problemas fuera de la red de Google.

---

## Cross-Cloud Interconnect

**Cross-Cloud Interconnect** permite establecer conectividad dedicada de alto ancho de banda entre Google Cloud y otro proveedor de servicios en la nube.

Google aprovisiona una conexión física dedicada entre ambas redes.

```text id="v5r9tx"
Google Cloud
     │
     │ Conexión física dedicada
     │
     ↓
Otro proveedor Cloud
```

Permite:

* Estrategias de múltiples nubes.
* Conectividad entre diferentes proveedores Cloud.
* Transferencia de datos entre sitios.
* Menor complejidad.
* Encriptación.

### Velocidades

Las conexiones Cloud Interconnect están disponibles en:

| Opción     | Velocidad |
| ---------- | --------: |
| Conexión 1 |   10 Gbps |
| Conexión 2 |  100 Gbps |
