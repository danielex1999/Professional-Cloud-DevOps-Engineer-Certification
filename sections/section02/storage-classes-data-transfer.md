# Cloud Storage: clases y transferencia

## Clases de almacenamiento

| Clase | Uso principal | Frecuencia aproximada |
|---|---|---|
| **Standard** | Datos activos | Frecuente |
| **Nearline** | Backups y datos poco usados | 1 vez al mes o menos |
| **Coldline** | Datos de acceso muy poco frecuente | 1 vez cada 90 días o menos |
| **Archive** | Archivado y recuperación ante desastres | Menos de 1 vez al año |

### Regla fácil

**Standard → uso frecuente**  
**Nearline → mensual**  
**Coldline → cada 90 días**  
**Archive → anual o menos**

## Características comunes

Todas las clases ofrecen:

- Almacenamiento escalable
- Alta durabilidad
- Baja latencia
- Seguridad
- APIs y herramientas uniformes
- Redundancia geográfica según la configuración

## Autoclass

**Autoclass** mueve automáticamente los objetos entre clases según sus patrones de acceso.

Ejemplo:

**Mucho acceso → Standard**

**Poco acceso → clases más frías**

Su objetivo es **optimizar costos automáticamente**.

## Seguridad

Cloud Storage:

- Encripta los datos en reposo antes de escribirlos en disco.
- Usa **HTTPS/TLS** para los datos que viajan hacia Google.

## Transferencia de datos

### gcloud storage
Permite subir datos usando la línea de comandos.

### Consola de Cloud
Puedes subir archivos mediante la interfaz web.

### Storage Transfer Service
Permite transferir grandes cantidades de datos desde:

- Otro proveedor cloud
- Otra región de Cloud Storage
- Un endpoint HTTP(S)

### Transfer Appliance

Dispositivo físico de alta capacidad.

Flujo:

**Datos → Transfer Appliance → Google → Cloud Storage**

Puede utilizarse para transferir hasta **1 PB** por dispositivo.

## Integración

Cloud Storage se integra con servicios como:

- BigQuery
- Cloud SQL
- App Engine
- Firestore
- Compute Engine

## Para memorizar

**Standard = frecuente**  
**Nearline = mensual**  
**Coldline = 90 días**  
**Archive = anual**  
**Autoclass = mueve automáticamente según uso**  
**Storage Transfer Service = transferencia online**  
**Transfer Appliance = transferencia física**