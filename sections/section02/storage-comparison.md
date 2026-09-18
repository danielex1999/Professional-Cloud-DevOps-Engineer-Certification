# Comparación de almacenamiento en Google Cloud

## ¿Cuál usar?

| Servicio | Tipo | Úsalo cuando... |
|---|---|---|
| **Cloud Storage** | Objetos | Necesitas almacenar BLOBs grandes como imágenes, videos o archivos |
| **Cloud SQL** | Relacional | Necesitas SQL y aplicaciones tradicionales |
| **Spanner** | Relacional | Necesitas SQL + escalabilidad horizontal + alta disponibilidad |
| **Firestore** | NoSQL | Necesitas aplicaciones web/móviles con sincronización y consultas |
| **Bigtable** | NoSQL | Necesitas Big Data + alto volumen de lecturas/escrituras |

## Cloud Storage

Ideal para **BLOBs inmutables** grandes.

Ejemplos:

- Películas
- Imágenes grandes
- Archivos

Puede manejar petabytes de capacidad.

**Máximo por objeto: 5 TB**

---

## Cloud SQL

Úsalo cuando necesitas:

**SQL + transacciones + aplicación tradicional**

Ejemplos:

- Usuarios
- Credenciales
- Pedidos

Es especialmente adecuado para frameworks web y aplicaciones existentes.

---

## Spanner

Úsalo cuando necesitas:

**SQL + escalabilidad horizontal**

Si Cloud SQL no escala como necesitas y requieres una base de datos relacional distribuida, Spanner es una opción.

Puede manejar **petabytes**.

---

## Firestore

Úsalo para:

**Apps web/móviles + NoSQL + sincronización**

Características:

- Escalabilidad
- Consultas
- Soporte offline
- Sincronización de datos

**Máximo por entidad: 1 MB**

---

## Bigtable

Úsalo para:

**Big Data + NoSQL + muchas lecturas/escrituras**

Ejemplos:

- IoT
- Datos financieros
- AdTech
- Series temporales

No admite:

- Consultas SQL
- Transacciones de varias filas

---

## BigQuery

BigQuery no se considera simplemente almacenamiento.

Su principal objetivo es:

**Análisis de Big Data + consultas interactivas**
