# Google Cloud Storage

## ¿Qué es?

Cloud Storage es el servicio de **almacenamiento de objetos** de Google Cloud.

Se utiliza para almacenar grandes cantidades de datos como:

- Imágenes
- Videos
- Audio
- Backups
- Archivos grandes
- Resultados de procesamiento

## Conceptos principales

### Bucket

Los objetos se almacenan dentro de **buckets**.

Cada bucket necesita:

- Un nombre único a nivel global
- Una ubicación

La ubicación debe elegirse considerando dónde están los usuarios para reducir la latencia.

### Objetos

Los archivos almacenados en Cloud Storage son **objetos**.

Los objetos son **inmutables**: no se modifican directamente. Cuando se realiza un cambio, se crea una nueva versión.

## Versionado

**Object Versioning** permite conservar versiones anteriores de los objetos.

Permite:

- Recuperar versiones anteriores
- Restaurar objetos
- Eliminar versiones específicas

## Seguridad

El acceso puede controlarse mediante:

### IAM

Es la opción habitual para administrar permisos.

Los permisos pueden heredarse desde el proyecto hacia el bucket y los objetos.

### ACL

Las listas de control de acceso permiten un control más detallado.

Una ACL define:

- **Quién** tiene acceso
- **Qué puede hacer**, por ejemplo leer o escribir

## Lifecycle Management

Permite automatizar acciones sobre los objetos.

Ejemplos:

- Eliminar objetos después de 365 días
- Eliminar objetos creados antes de una fecha
- Conservar solo las últimas 3 versiones

Esto ayuda a controlar los costos de almacenamiento.

## Para recordar

**Cloud Storage = Objetos + Buckets + Inmutabilidad + Versionado + IAM + Lifecycle**