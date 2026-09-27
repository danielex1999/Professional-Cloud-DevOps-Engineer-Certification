# Características clave del almacenamiento

## Panorama general

Google Cloud cuenta con una amplia variedad de opciones administradas de **almacenamiento y bases de datos**.

Conocer las características de cada solución y seleccionar la adecuada según los requisitos es una parte importante del proceso de diseño.

Los servicios abarcan:

```text
Almacenamiento
│
├── Objetos
├── Relacional
├── NoSQL
├── Almacén de datos
└── En memoria
```

Estos servicios pueden ser:

* Completamente administrados.
* Escalados.
* Respaldados por ANS.

---

# ¿Cómo elegir una solución de almacenamiento?

La elección depende de los requisitos y requiere equilibrar diferentes características:

```text
                 Requisitos
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
   Tipo de datos   Escala    Durabilidad
        │            │            │
        └────────────┼────────────┘
                     │
             ┌───────┴───────┐
             ▼               ▼
       Disponibilidad     Ubicación
             │               │
             └───────┬───────┘
                     ▼
          Solución de almacenamiento
```

---

# Disponibilidad

Los servicios de almacenamiento de datos tienen distintos **ANS de disponibilidad**.

La disponibilidad de un servicio puede depender de su configuración.

Por ejemplo, la disponibilidad de **Cloud Storage** varía según si se crean buckets:

* Regionales.
* Multirregionales.
* Coldline.

Lo mismo ocurre con **Cloud Spanner** y **Firestore**, ya que sus configuraciones multirregionales ofrecen una disponibilidad más alta que las de región única.

> Los requisitos son importantes para tomar decisiones fundamentadas sobre el almacenamiento.

---

## Porcentaje de Tiempo de Actividad Mensual

Los ANS de disponibilidad suelen definirse por mes.

El **Porcentaje de Tiempo de Actividad Mensual** se refiere a:

```text
Cantidad total de minutos del mes
                -
Cantidad de minutos de inactividad
                │
                ▼
        Dividido entre
                │
                ▼
Cantidad total de minutos del mes
```

Para consultar las cifras actualizadas de ANS, se debe consultar la documentación.

---

# Durabilidad

La **durabilidad de los datos** representa las probabilidades de perderlos.

Según la solución de almacenamiento, la durabilidad es una responsabilidad compartida.

### Responsabilidad de Google Cloud

Garantizar que los datos sigan existiendo en caso de que falle el hardware.

### Responsabilidad del usuario

Crear copias de seguridad de los datos.

```text
              Durabilidad
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
 Google Cloud               Usuario
        │                     │
        ▼                     ▼
 Fallas de hardware      Copias de seguridad
```

---

# Cloud Storage y durabilidad

Cloud Storage proporciona:

**99,999999999% de durabilidad**

Además, incluye control de versiones.

Sin embargo, es responsabilidad del usuario determinar cuándo utilizar esta función.

Se recomienda activar el control y mantener versiones antiguas archivadas como parte de la política de administración de la vida útil de los objetos.

---

# Copias de seguridad

En otros servicios de almacenamiento, lograr durabilidad generalmente implica realizar copias de seguridad de los datos.

## Discos

La copia de los discos se realiza mediante **instantáneas**, por lo que deben programarse.

## Cloud SQL

Google Cloud proporciona:

* Copias de seguridad automáticas.
* Recuperación de un momento determinado.
* Servidor de conmutación por error.

Para mejorar la durabilidad, se pueden ejecutar copias de seguridad de bases de datos SQL.

## Spanner y Firestore

Ofrecen replicación automática.

También se deben ejecutar trabajos de exportación para exportar los datos a Cloud Storage.

---

# Escalabilidad

Al seleccionar un servicio de almacenamiento, son importantes:

* La cantidad de datos.
* La cantidad de operaciones de lectura.
* La cantidad de operaciones de escritura.

Algunos servicios escalan horizontalmente al agregar nodos.

### Escalamiento horizontal

```text
        Datos
          │
          ▼
     ┌─────────┐
     │  Nodo 1 │
     └─────────┘
          +
     ┌─────────┐
     │  Nodo 2 │
     └─────────┘
          +
     ┌─────────┐
     │  Nodo 3 │
     └─────────┘
```

**Bigtable** y **Spanner** escalan horizontalmente.

### Escalamiento vertical

**Cloud SQL** y **Memorystore** escalan máquinas de forma vertical.

---

# Escalamiento automático

Algunos servicios escalan automáticamente sin límites.

Entre ellos:

* Cloud Storage.
* BigQuery.
* Firestore.

---

# Coherencia de los datos

La **coherencia sólida** es otra característica importante al diseñar soluciones de datos.

Las bases de datos con coherencia sólida:

* Actualizan todas las copias de los datos dentro de una transacción.
* Garantizan que todos los usuarios obtengan la copia más reciente de los datos al realizar lecturas.

### Servicios con coherencia sólida

```text
Cloud Storage
Cloud SQL
Spanner
Firestore
```

---

# Coherencia eventual

Las bases de datos con **coherencia eventual** suelen tener varias copias de los mismos datos para ofrecer rendimiento y escalabilidad.

Permiten manejar grandes volúmenes de operaciones de escritura.

Su funcionamiento consiste en:

```text
             Escritura
                │
                ▼
        Actualización síncrona
                │
                ▼
          Una copia
                │
                ▼
      Actualización asíncrona
                │
        ┌───────┼───────┐
        ▼       ▼       ▼
      Copia   Copia   Copia
```

Esto significa que no se garantiza que todos los lectores vean los mismos valores en un determinado momento.

Con el tiempo, los datos serán más coherentes, pero no será inmediato.

### Servicios con coherencia eventual

* Cloud Bigtable.
* Memorystore.

---

# Costos

Al diseñar una solución de almacenamiento es importante calcular el **costo total por GB** para determinar las consecuencias financieras de la decisión.

Cada solución tiene características diferentes.

| Servicio          | Consideración                                                                                                                      |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Bigtable**      | Diseñado para conjuntos de datos grandes; no es muy rentable para conjuntos pequeños.                                              |
| **Spanner**       | Diseñado para conjuntos de datos grandes; no es muy rentable para conjuntos pequeños.                                              |
| **Firestore**     | Más económico por GB almacenado, pero también se debe considerar el costo de las operaciones de lectura y escritura.               |
| **Cloud Storage** | No es tan costoso, pero solo es adecuado para ciertos tipos de datos.                                                              |
| **BigQuery**      | El almacenamiento es relativamente económico, pero no proporciona acceso rápido a los registros y genera costos por cada consulta. |

---

# Factores para elegir

No existe una única solución de almacenamiento adecuada para todos los casos.

La decisión depende principalmente de:

```text
              Solución de almacenamiento
                         │
        ┌────────────────┼────────────────┐
        ▼                ▼                ▼
 Tipo de datos      Tamaño de datos   Lecturas/escrituras
                         │
                         ▼
                    Requisitos
                         │
                         ▼
                   Decisión final
```

Los factores principales son:

* **Tipo de datos.**
* **Tamaño de los datos.**
* **Patrones de lectura.**
* **Patrones de escritura.**
* **Escala.**
* **Durabilidad.**
* **Disponibilidad.**
* **Ubicación.**
* **Costo total por GB.**
* **Coherencia.**

> Elegir la solución correcta depende de los requisitos y del equilibrio entre las características del almacenamiento.
