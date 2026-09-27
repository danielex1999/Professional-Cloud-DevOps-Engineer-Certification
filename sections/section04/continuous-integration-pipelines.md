# Canalizaciones de integración continua

## ¿Qué es una canalización de integración continua?

Las **canalizaciones de integración continua** automatizan la compilación de aplicaciones.

Una visión simplificada del proceso es:

```text id="q1m8v4"
       Código
          │
          ▼
   ┌──────────────┐
   │ Repositorio  │
   └──────┬───────┘
          │
          ▼
    Pruebas unitarias
          │
          ▼
      ¿Superadas?
       │       │
      No       Sí
       │       │
       │       ▼
       │   Imagen Docker
       │       │
       │       ▼
       │ Artifact Registry
       │       │
       │       ▼
       │   Implementación
       │
       └──► Fin
```

La canalización se personaliza para cumplir con los requisitos de cada caso.

---

# Flujo de integración continua

### 1. Código

El proceso comienza subiendo código al repositorio.

### 2. Pruebas

Se ejecutan las pruebas de unidades.

### 3. Paquete de implementación

Si las pruebas se superan, se crea un paquete de implementación, como una **imagen de Docker**.

### 4. Registro de artefactos

La imagen se guarda en **Artifact Registry**.

Desde allí puede implementarse.

---

# Repositorios por microservicio

Cada microservicio debe tener su propio repositorio.

```text id="4y7z2j"
Repositorio
    │
    ├── Microservicio A
    │
    ├── Microservicio B
    │
    └── Microservicio C
```

---

# Pasos adicionales

Una canalización puede incluir otros pasos, como:

* Análisis del código con lint.
* Análisis de calidad con herramientas como SonarQube.
* Pruebas de integración.
* Informes de pruebas.
* Análisis de imágenes.

---

# Componentes de Google Cloud

Google Cloud proporciona los componentes necesarios para crear una canalización de integración continua.

```text id="w5j0qf"
┌──────────────────────────┐
│ Cloud Source Repositories│
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│       Cloud Build        │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    Artifact Registry     │
└──────────────────────────┘
```

---

# Cloud Source Repositories

Cloud Source Repositories proporciona **repositorios de Git privados alojados en Google Cloud**.

Permite desarrollar e implementar una aplicación o servicio en un espacio que proporciona:

* Funciones de colaboración.
* Control de versiones del código.

Al estar integrado en Google Cloud, proporciona una experiencia fluida para los desarrolladores.

---

## IAM y repositorios

Cloud Source Repositories utiliza **IAM** para agregar miembros del equipo al proyecto y otorgarles permisos para:

* Crear repositorios.
* Ver repositorios.
* Actualizar repositorios.

---

## Pub/Sub

Los repositorios pueden configurarse para publicar mensajes en un determinado tema de **Pub/Sub**.

Se pueden publicar mensajes cuando:

* Un usuario crea un repositorio.
* Un usuario borra un repositorio.
* Un usuario envía una confirmación.

---

## Otras funciones

Cloud Source Repositories también permite:

* Utilizar registros de auditoría para informar qué se hizo, dónde y cuándo.
* Realizar implementaciones directas en App Engine.
* Conectar un repositorio existente de GitHub o Bitbucket.

Los repositorios conectados se sincronizan automáticamente con la plataforma.

---

# Cloud Build

**Cloud Build** ejecuta las compilaciones en la infraestructura de Google Cloud.

Puede importar código fuente desde:

```text id="8qg4yo"
Cloud Storage
      │
      ├── Cloud Source Repositories
      │
      ├── GitHub
      │
      └── Bitbucket
```

Puede ejecutar una compilación según las especificaciones y producir artefactos como:

* Contenedores de Docker.
* Archivos de Java.

---

## Pasos de compilación

Cloud Build ejecuta la compilación como una serie de pasos que se realizan en un contenedor de Docker.

```text id="2k6x0v"
Cloud Build
     │
     ├── Paso 1
     ├── Paso 2
     ├── Paso 3
     └── Paso N
```

Un paso de compilación puede hacer lo mismo que en un contenedor, independientemente del entorno.

Existen pasos estándar, pero también se pueden definir pasos personalizados.

---

# Configuración de compilación

Se escribe una configuración de compilación para indicarle a Cloud Build qué tareas realizar.

Estas tareas se definen como una serie de pasos.

Cada paso es ejecutado por un **compilador en la nube**.

### Compilador en la nube

Es un contenedor con un lenguaje común y herramientas instaladas.

Puede configurarse para:

* Recuperar dependencias.
* Ejecutar pruebas de unidades.
* Ejecutar análisis estáticos.
* Ejecutar pruebas de integración.
* Crear artefactos.

Entre las herramientas mencionadas se encuentran:

* Docker.
* Gradle.
* Maven.
* Bazel.
* Gulp.

---

## Pasos proporcionados y personalizados

Los pasos pueden ser:

```text id="x9d7pm"
Pasos proporcionados
        +
Pasos personalizados
        │
        ▼
   Cloud Build
```

Se pueden utilizar pasos proporcionados por Cloud Build y su comunidad, o escribir pasos de compilación personalizados.

---

# Activadores de Cloud Build

Los **activadores de compilación** supervisan un repositorio y crean un contenedor cuando se envía código.

Son compatibles con:

* Maven.
* Compilaciones personalizadas.
* Docker.

Un activador de Cloud Build inicia automáticamente una compilación cada vez que se modifica el código fuente.

---

## Condiciones de activación

El activador puede configurarse para iniciar una compilación según:

* Confirmaciones de una rama específica.
* Confirmaciones que contengan una etiqueta determinada.

También se puede especificar una **expresión regular** para coincidir con el valor de la rama o etiqueta.

```text id="9n6q4c"
                 Activador
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
      Rama específica       Etiqueta
          │                   │
          └─────────┬─────────┘
                    ▼
              Cloud Build
```

---

# Configuración del activador

La configuración de compilación puede definirse en:

* Dockerfile.
* Archivo de Cloud Build.

La configuración requerida incluye:

### 1. Fuente

Puede ser:

* Cloud Source Repositories.
* GitHub.
* Bitbucket.

### 2. Repositorio

Se selecciona el repositorio de código fuente.

### 3. Configuración del activador

Incluye información como:

* Rama que se utilizará para la activación.
* Etiqueta que se utilizará para la activación.
* Configuración de compilación.

Por ejemplo:

```text id="7m2gq1"
Fuente
  │
  ▼
Repositorio
  │
  ▼
Activador
  │
  ├── Rama / Etiqueta
  │
  └── Dockerfile / Cloud Build
```

---

# Artifact Registry

**Artifact Registry** es un administrador de paquetes universal para:

* Artefactos.
* Dependencias de compilación.

Puede almacenar imágenes de contenedor OCI y Docker en un registro de Docker.

Se integra con los servicios de CI/CD de Cloud y con herramientas de CI/CD existentes.

Los artefactos de Cloud Build pueden almacenarse e implementarse en entornos de ejecución de Cloud como:

* Google Kubernetes Engine.
* Cloud Run.
* Compute Engine.
* Entorno flexible de App Engine.

---

## Control de acceso

**Identity and Access Management (IAM)** proporciona:

* Credenciales coherentes.
* Control de acceso coherente.

Artifact Registry implementa el protocolo de Docker para permitir enviar y extraer imágenes directamente mediante clientes Docker, incluida la herramienta de línea de comandos de Docker.

Los servicios de Cloud que suelen integrarse con Artifact Registry, como Cloud Build y Kubernetes Engine, se configuran con permisos predeterminados para acceder a repositorios del mismo proyecto.

---

# Artifact Analysis

**Artifact Analysis** proporciona servicios para:

* Análisis de composición de software.
* Almacenamiento de metadatos.
* Recuperación de metadatos.

Sus puntos de detección se incorporan en productos de Google Cloud como:

* Artifact Registry.
* Google Kubernetes Engine.

Esto permite una habilitación rápida y sencilla.

El servicio funciona con ambos productos de Google Cloud y también permite almacenar información de fuentes externas.

Los servicios de análisis utilizan un almacén común de vulnerabilidades para asociarlas a archivos.

---

# Autorización Binaria

La **Autorización Binaria** permite exigir que solo contenedores de confianza se implementen en GKE.

Es un servicio de Google Cloud basado en la especificación de **Kritis**.

Para utilizarlo:

```text id="7p2x6f"
Autorización Binaria
        │
        ▼
Clúster GKE
        │
        ▼
Política de imágenes
```

Es necesario:

* Habilitar la Autorización Binaria en el clúster de GKE donde se realizará la implementación.
* Tener una política para firmar las imágenes.

---

# Firma y certificación de imágenes

Cuando se compila una imagen con Cloud Build, un certificador verifica que provenga de un repositorio de confianza.

Por ejemplo:

```text id="z6y3w1"
Cloud Build
     │
     ▼
Imagen
     │
     ▼
Certificador
     │
     ▼
Repositorio de confianza
```

Artifact Registry incluye un **escáner de vulnerabilidades para contenedores**.

---

# Flujo completo

Un flujo de trabajo típico puede representarse así:

```text id="f7v4n2"
                 Código
                   │
                   ▼
          ┌─────────────────┐
          │  Cloud Build    │
          └────────┬────────┘
                   │
                   ▼
             Nueva imagen
                   │
                   ▼
          ┌─────────────────┐
          │Artifact Registry│
          └────────┬────────┘
                   │
                   ▼
        Análisis de vulnerabilidades
                   │
                   ▼
                Pub/Sub
                   │
                   ▼
          ┌─────────────────┐
          │ Kritis Signer   │
          └────────┬────────┘
                   │
                   ▼
            Certificación
                   │
                   ▼
       ┌──────────────────────┐
       │ Autorización Binaria │
       └──────────┬───────────┘
                  │
                  ▼
          Política de GKE
                  │
                  ▼
             Implementación
```

### Flujo explicado

1. Se sube código.
2. Se activa la compilación con **Cloud Build**.
3. Como parte de la compilación, **Artifact Registry** realiza un análisis de vulnerabilidades cuando se sube la nueva imagen.
4. La herramienta de análisis publica mensajes en **Pub/Sub**.
5. **Kritis Signer** escucha las notificaciones de Pub/Sub provenientes del escáner de vulnerabilidades de Artifact Registry.
6. Kritis Signer crea una certificación si la imagen supera el análisis de vulnerabilidades.
7. **Autorización Binaria** aplica la política que requiere certificaciones de Kritis Signer antes de implementar la imagen de contenedor.

---

# Visión general

```text id="8q3m1r"
                   INTEGRACIÓN CONTINUA
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
       Source Code     Cloud Build   Artifact Registry
             │             │             │
             │             │             ├── Imágenes
             │             │             ├── Paquetes
             │             │             └── Vulnerabilidades
             │             │
             │             ├── Pruebas
             │             ├── Análisis
             │             └── Artefactos
             │
             └─────────────┘
                           │
                           ▼
                    Pub/Sub / Kritis
                           │
                           ▼
                  Autorización Binaria
                           │
                           ▼
                        GKE
```

## Conceptos clave

* Canalizaciones de integración continua.
* Repositorios de Git.
* Cloud Source Repositories.
* Cloud Build.
* Activadores de compilación.
* Pasos de compilación.
* Compiladores en la nube.
* Artifact Registry.
* Artifact Analysis.
* IAM.
* Pub/Sub.
* Kritis Signer.
* Autorización Binaria.
* Análisis de vulnerabilidades.
* Docker.
* GKE.
