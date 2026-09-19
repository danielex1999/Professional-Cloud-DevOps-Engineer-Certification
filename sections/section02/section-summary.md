# Conceptos básicos de Google Cloud: Infraestructura principal

## Módulo 1: Google Cloud y la computación en la nube

Se exploraron los siguientes temas:

- El concepto de la infraestructura administrada y los servicios administrados con IaaS (infraestructura como servicio) y PaaS (plataforma como servicio).
- La red de Google Cloud.
- El enfoque de Google Cloud sobre la seguridad en toda nuestra infraestructura.
- Cómo Google publica elementos clave de tecnología con licencias de código abierto.
- Las herramientas de facturación y la estructura de precios de Google Cloud.

## Módulo 2: Jerarquía de recursos de Google Cloud

Se conoció la jerarquía de recursos de Google Cloud, que consta de cuatro niveles:

- Recursos.
- Proyectos.
- Carpetas.
- Nodo de organización.

También se aprendió sobre:

- Cómo definir políticas y su herencia descendente.
- Cuándo usar Identity and Access Management o IAM.
- Las cuatro maneras de acceder a Google Cloud e interactuar con el servicio:
  - Consola de Google Cloud.
  - SDK de Cloud y Cloud Shell.
  - APIs.
  - App de Google Cloud.

## Módulo 3: Compute Engine y redes

Se exploró cómo funciona Compute Engine, con un enfoque en las redes virtuales y las máquinas virtuales.

Se presentó lo siguiente:

- VPC o nube privada virtual.
- Función de escalado automático de Compute Engine.
- Funciones importantes de compatibilidad de VPC de Google:
  - Tablas de enrutamiento.
  - Firewalls.
  - Intercambio de tráfico entre VPC.
  - VPC compartida.

Todas estas herramientas reducen la necesidad de administrar redes.

También se exploró Cloud Load Balancing, un servicio totalmente distribuido, definido por software y administrado para el tráfico.

Por último, se comparó cómo las redes en la nube o en entornos locales se pueden interconectar con una VPC de Google.

## Módulo 4: Almacenamiento

Se exploraron las 5 opciones de almacenamiento principales de Google Cloud:

- Cloud Storage.
- Bigtable.
- Cloud SQL.
- Spanner.
- Firestore.

También se examinaron las cuatro clases de almacenamiento que conforman Cloud Storage:

- **Standard Storage:** se usa para los datos activos a los que se accede con frecuencia.
- **Nearline Storage:** se usa para los datos en reposo a los que se accede con menos frecuencia.
- **Coldline Storage:** se usa para los datos en reposo a los que se accede con menos frecuencia.
- **Archive Storage.**

## Módulo 5: Contenedores y Kubernetes

Se revisaron los contenedores, que son cajas invisibles que rodean al código y sus dependencias.

También se presentó:

- Kubernetes, una plataforma de código abierto para cargas de trabajo y servicios.
- GKE, un servicio administrado de Kubernetes alojado por Google en la nube.

## Módulo 6: Desarrollo de aplicaciones en la nube

Se exploró el desarrollo de aplicaciones en la nube.

Se presentó:

- **Cloud Run:** una plataforma de procesamiento administrada para ejecutar contenedores sin estado a través de solicitudes web o eventos Pub/Sub.
- **Cloud Run Functions:** una solución de procesamiento liviana, basada en eventos y asíncrona para crear funciones de un solo propósito.

## Módulo 7: Ingeniería de instrucciones y Gemini

Se exploró cómo combinar el conocimiento de Google Cloud con la ingeniería de instrucciones para mejorar las respuestas de Gemini.

Se respondieron las siguientes preguntas:

- ¿Qué es la IA generativa?
- ¿Qué es un modelo de lenguaje grande?
- ¿Qué es la ingeniería de instrucciones?

El módulo terminó con las prácticas recomendadas de ingeniería de instrucciones.