# Infraestructura Global de Google Cloud

Google Cloud se ejecuta en la **red global de Google**.

Google ha invertido miles de millones de dólares durante años para desarrollar esta red, diseñada para brindar gran capacidad de procesamiento y bajas latencias.

## Red global

Google cuenta con más de **100 nodos de almacenamiento de contenido** en el mundo.

Estos son lugares donde el contenido con demanda se almacena en caché para permitir un acceso rápido.

```text
Usuario
   ↓
Ubicación con menor tiempo de respuesta
   ↓
Contenido en caché
```

La infraestructura utiliza:

* Regiones de nube redundantes
* Conectividad de alto ancho de banda
* Cables submarinos

Esto permite entregar servicios a usuarios sin importar dónde se encuentren.

---

## Ubicaciones de Google Cloud

La infraestructura de Google Cloud se basa en cinco ubicaciones geográficas:

```text
Norteamérica
Sudamérica
Europa
Asia
Australia
```

Tener múltiples ubicaciones es importante porque la ubicación de las aplicaciones afecta:

* **Disponibilidad**
* **Durabilidad**
* **Latencia**

La **latencia** es el tiempo que demora un paquete de información en viajar desde el origen hasta el destino.

---

## Regiones y zonas

Cada ubicación se divide en **regiones** y **zonas**.

### Región

Una región representa un **área geográfica independiente** y consta de varias zonas.

Por ejemplo:

```text
Londres
europe-west2
    ├── Zona
    ├── Zona
    └── Zona
```

Actualmente, Londres (`europe-west2`) consta de tres zonas.

### Zona

Una zona es un área en la que se implementan los recursos de Google Cloud.

Por ejemplo, si inicias una máquina virtual con **Compute Engine**, se ejecutará en la zona especificada.

---

## Uso de múltiples regiones

Los recursos pueden ejecutarse en diferentes regiones.

Esto permite:

* Acercar las aplicaciones a usuarios de todo el mundo.
* Protegerse ante problemas que afecten a una región completa, como un desastre natural.

```text
Región A ─── Aplicación
      │
      └──── Región B
              │
              └──── Región C
```

---

## Multirregión

Algunos servicios de Google Cloud permiten ubicar recursos en una **multirregión**.

Por ejemplo, con la configuración multirregional de **Spanner**, los datos de la base de datos pueden replicarse:

```text
Varias zonas
      +
Múltiples regiones
      ↓
Réplicas de datos
```

Estas réplicas permiten leer datos con baja latencia desde diferentes lugares cercanos a las regiones configuradas, como **Países Bajos y Bélgica**.

---

## Regiones y zonas actuales

Actualmente, Google Cloud admite:

```text
121 zonas
40 regiones
```

Esta cifra aumenta continuamente.

Para consultar las cifras más actualizadas:

`cloud.google.com/about/locations`
