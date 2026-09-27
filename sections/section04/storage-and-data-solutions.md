# Selección de soluciones de datos y almacenamiento en Google Cloud

## 1. Características del almacenamiento

Google Cloud ofrece diferentes opciones administradas de almacenamiento y bases de datos:

* Almacenamiento de objetos
* Bases de datos relacionales
* NoSQL
* Almacenes de datos
* Almacenamiento en memoria

La elección depende de los requisitos:

* Tipo de datos
* Escala
* Durabilidad
* Disponibilidad
* Ubicación
* Patrones de lectura y escritura
* Costos

---

## 2. Disponibilidad

Los servicios tienen diferentes **ANS de disponibilidad**, que pueden depender de su configuración.

Por ejemplo:

* **Cloud Storage:** la disponibilidad varía según si el bucket es regional, multirregional o Coldline.
* **Cloud Spanner:** la configuración multirregional ofrece mayor disponibilidad que la de región única.
* **Firestore:** la configuración multirregional ofrece mayor disponibilidad que la de región única.

El ANS de disponibilidad suele definirse por mes.

### Porcentaje de tiempo de actividad mensual

Se calcula como:

**(Minutos totales del mes − minutos de inactividad) / minutos totales del mes**

Para consultar las cifras actualizadas de ANS, se debe revisar la documentación.

---

## 3. Durabilidad

La durabilidad representa la probabilidad de perder los datos.

Es una responsabilidad compartida:

* **Google Cloud:** garantiza que los datos continúen existiendo ante fallas de hardware.
* **Usuario:** debe crear copias de seguridad de sus datos.

### Ejemplos

**Cloud Storage**

* Durabilidad de **99,999999999%**.
* Incluye control de versiones.
* El usuario determina cuándo utilizarlo.

**Cloud SQL**

* Copias de seguridad automáticas.
* Recuperación de un momento determinado.
* Servidor de conmutación por error.
* Se pueden ejecutar copias de seguridad de las bases de datos SQL.

**Spanner y Firestore**

* Replicación automática.
* Se pueden ejecutar trabajos de exportación hacia Cloud Storage.

### Discos

La copia de los discos se realiza mediante **instantáneas**, que deben programarse.

---

## 4. Escalabilidad

Al seleccionar un servicio de almacenamiento, son importantes:

* Cantidad de datos.
* Operaciones de lectura.
* Operaciones de escritura.

Algunos servicios escalan horizontalmente agregando nodos:

* **Bigtable**
* **Spanner**

Otros escalan verticalmente:

* **Cloud SQL**
* **Memorystore**

También existen servicios que escalan automáticamente sin límites:

* **Cloud Storage**
* **BigQuery**
* **Firestore**

---

## 5. Coherencia de los datos

### Coherencia sólida

Las bases de datos con coherencia sólida actualizan las copias de los datos dentro de una transacción y garantizan que los usuarios obtengan la copia más reciente durante las lecturas.

Servicios mencionados:

* Cloud Storage
* Cloud SQL
* Spanner
* Firestore

### Coherencia eventual

Estas bases de datos suelen tener varias copias para ofrecer rendimiento y escalabilidad.

Una copia se actualiza de forma síncrona y las demás de forma asíncrona.

Por lo tanto, no se garantiza que todos los lectores vean los mismos valores inmediatamente.

Con el tiempo, los datos se vuelven coherentes.

Ejemplos:

* Cloud Bigtable
* Memorystore

---

## 6. Costos

Para seleccionar una solución de almacenamiento es importante calcular el **costo total por GB**.

* **Bigtable y Spanner:** están diseñados para conjuntos de datos grandes y no son muy rentables para conjuntos pequeños.
* **Firestore:** tiene un menor costo por GB almacenado, pero también se debe considerar el costo de las operaciones de lectura y escritura.
* **Cloud Storage:** tiene un costo bajo, pero solo es adecuado para determinados tipos de datos.
* **BigQuery:** el almacenamiento es relativamente económico, pero genera costos por consulta y no proporciona acceso rápido a los registros.

La elección depende principalmente de:

**Tipo de datos + tamaño de datos + patrones de lectura y escritura.**

---

## 7. Soluciones de datos y almacenamiento

### Datos relacionales

#### Cloud SQL

* Base de datos de esquema fijo.
* Límite de **64 TB**.
* MySQL, PostgreSQL y SQL Server.
* Adecuado para aplicaciones web, como comercio electrónico o CMS.

#### Cloud Spanner

* Base de datos relacional de esquema fijo.
* Escala de forma infinita.
* Puede ser regional o multirregional.
* Para bases de datos relacionales escalables de más de 30 GB.
* Alta disponibilidad y accesibilidad global.
* Casos de uso: administración de cadenas de suministro y manufactura.

#### AlloyDB

* Base de datos de esquema fijo.
* Compatible con PostgreSQL.
* Completamente administrada.
* Rendimiento y disponibilidad de nivel empresarial.
* Mantiene compatibilidad con PostgreSQL de código abierto.

---

### Archivos

#### Filestore

* Almacena archivos sin esquema.
* Alto rendimiento.
* Administración total.
* Requiere una interfaz de sistema de archivos y uso compartido de datos.
* Se puede combinar con Compute Engine y Google Kubernetes Engine.

---

### NoSQL

### Firestore

* Almacén de documentos completamente administrado.
* Admite documentos de hasta **1 MB**.
* Útil para datos jerárquicos.
* Ejemplos: estado de un juego y perfiles de usuario.

#### Cloud Bigtable

* Almacén NoSQL.
* Escala de forma infinita.
* Ideal para muchas lecturas y escrituras.
* Casos de uso: servicios financieros, Internet de las cosas y publicidad digital.

---

### Objetos

### Cloud Storage

* Almacenamiento de objetos.
* Sin esquema.
* Completamente administrado.
* Escala de forma infinita.
* Almacena datos de objetos binarios.
* Ideal para imágenes, multimedia y copias de seguridad.

---

### Bloques

#### Discos persistentes (PD)

* Almacenamiento en red.
* Durable.
* Sin esquema.
* Las VMs pueden acceder a ellos como si fueran discos físicos.
* Los datos de cada volumen se distribuyen entre múltiples discos físicos.

---

### Almacén de datos

### BigQuery

* Proporciona almacenamiento de datos.
* Usa un esquema fijo.
* Permite analizar datos mediante SQL.
* Completamente administrado.
* Adecuado para analítica y paneles de inteligencia empresarial.

---

### En memoria

### Memorystore

* Bases de datos Redis administradas.
* Sin esquema.
* Ideal para cachés de aplicaciones web y móviles.
* Permite acceso rápido al estado en arquitecturas de microservicios.

---

## 8. Tabla de decisión

La selección puede plantearse mediante preguntas:

### ¿Tus datos son estructurados?

**No →** ¿Necesitas un sistema de archivos compartido?

* **Sí → Filestore**
* **No → Cloud Storage**

**Sí →** ¿Tu carga de trabajo se enfoca en analítica?

* **Sí → Cloud Bigtable o BigQuery**, según las necesidades de latencia y actualización.

### BigQuery

* Almacén de datos.
* Predeterminado para datos tabulares.
* Optimizado para informes y análisis SQL ad hoc a gran escala.
* Permite actualizar, insertar y borrar datos.
* Tiene caché integrada.
* Funciona bien cuando los datos no cambian con frecuencia.

### Bigtable

* Base de datos NoSQL de columnas anchas.
* Optimizada para baja latencia.
* Muchas lecturas y escrituras.
* Mantiene el rendimiento a gran escala.
* También puede utilizarse como base de datos no relacional de búsqueda rápida para conjuntos de datos muy grandes.
* Casos mencionados: IoT, AdTech y FinTec.

---

### Si la carga no involucra análisis

¿Tus datos son relacionales?

**No →** ¿Necesitas almacenamiento en caché?

* **Sí → Memorystore**
* **No → Firestore**

**Sí →** ¿Necesitas procesamiento híbrido transaccional/analítico?

* **Sí → AlloyDB**
* **No →** ¿Necesitas escalabilidad global?

  * **Sí → Spanner**
  * **No → Cloud SQL**

Según la aplicación, se puede utilizar uno o varios de estos servicios.

---

## 9. Transferencia de datos

Para transferir datos en Google Cloud se deben considerar:

* Costo
* Tiempo
* Transferencia en línea o sin conexión
* Seguridad

Aunque migrar a Cloud Storage es gratis, pueden existir costos relacionados con:

* Almacenamiento.
* Dispositivos.
* Salida desde otro proveedor de servicios en la nube.

Para grandes conjuntos de datos, el tiempo de transferencia mediante una red puede ser demasiado elevado.

---

## 10. Servicio de transferencia de Cloud Storage

Para cargas pequeñas o programadas permite:

* Trasladar o respaldar datos hacia un bucket de Storage.
* Transferir desde Amazon S3.
* Transferir desde almacenamiento local.
* Transferir desde ubicaciones HTTP/HTTPS.
* Mover datos entre buckets de Cloud Storage.
* Mover datos regularmente en una canalización de procesamiento o flujo analítico.

También permite:

* Programar transferencias únicas o recurrentes.
* Borrar objetos del destino que no tengan coincidencia en la fuente.
* Borrar objetos de la fuente después de transferirlos.
* Programar sincronizaciones.
* Utilizar filtros por fechas de creación, nombres y horas.

---

## 11. Servicio de transferencia para datos locales

Está orientado a transferencias en línea a gran escala desde almacenamiento local hacia Cloud Storage.

Incluye:

* Validación de datos.
* Encriptación.
* Reintentos de error.
* Tolerancia a errores.

El software se instala localmente y el agente se incluye como contenedor de Docker.

La transferencia se configura desde Cloud.

El servicio paraleliza las transferencias entre muchos agentes y puede escalar a miles de millones de archivos y cientos de TB.

### Requisitos mencionados

* Fuente POSIX.
* Conexión de red de al menos 300 Mbps.
* Servidor Linux compatible con Docker.
* Acceso a los datos.
* Puertos 80 y 443 abiertos para conexiones salientes.

**Caso de uso:** transferir datos locales de tamaño superior a **1 TB**.

---

## 12. Transfer Appliance

Para grandes cantidades de datos locales que tardarían demasiado en transferirse mediante una red se puede utilizar **Transfer Appliance**.

Es un servidor de almacenamiento:

* En bastidores.
* Seguro.
* De alta capacidad.

Proceso:

**Solicitar dispositivo → recibirlo → transferir datos → enviarlo a Google → cargar datos en Cloud Storage → recibir notificación**

Los datos:

* Están protegidos.
* Permiten controlar la clave de encriptación.
* Se encriptan con AES256.
* Se eliminan del dispositivo según NIST-800-88 después de la transferencia.

Google utiliza sellos de seguridad en las cajas de transporte.

Los datos deben desencriptarse cuando se quieran utilizar.

---

## 13. Servicio de transferencia de datos para BigQuery

Este servicio automatiza la transferencia programada y administrada de datos desde aplicaciones SaaS hacia BigQuery.

Admite fuentes como:

* Google Ads Campaign Manager
* Google Ad Manager
* YouTube
* Teradata
* Amazon Redshift
* Amazon S3

El proceso consiste en:

**Seleccionar fuente → configurar programación → seleccionar destino → configurar formato de datos**
