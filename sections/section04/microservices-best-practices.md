# Prácticas recomendadas sobre microservicios

## Aplicación de doce factores

La **app de doce factores** es un conjunto de prácticas recomendadas para crear aplicaciones web o de software como servicio.

El diseño de 12 factores ayuda a separar los componentes de una aplicación para que:

* Cada componente pueda implementarse en la nube.
* Se pueda realizar implementación continua.
* Los componentes puedan aumentar o reducir la escala vertical.
* Aumente la portabilidad entre distintos entornos.

Los factores no dependen de los lenguajes de programación ni de la pila de software, por lo que pueden utilizarse en diferentes aplicaciones.

---

# Los 12 factores

```text
┌──────────────────────────────────────────┐
│          DISEÑO DE 12 FACTORES           │
├──────────────────────────────────────────┤
│ 01. Base de código                       │
│ 02. Dependencias                         │
│ 03. Configuración                        │
│ 04. Servicios de respaldo                │
│ 05. Compilar, lanzar y ejecutar          │
│ 06. Procesos                             │
│ 07. Vinculación de puertos               │
│ 08. Simultaneidad                         │
│ 09. Capacidad de ser desechable           │
│ 10. Paridad entre desarrollo y producción│
│ 11. Registros                             │
│ 12. Procesos administrativos              │
└──────────────────────────────────────────┘
```

---

## 01. Base de código

Realiza un seguimiento de la base de código mediante un sistema de control de versiones como **Git**.

**CSR** brinda repositorios privados y con todas las funciones.

---

## 02. Dependencias

Hay dos consideraciones importantes:

```text
Dependencias
    │
    ├── Declaración
    │
    └── Aislamiento
```

### Declaración

Las dependencias se declaran explícitamente y se almacenan en el control de versiones.

Su seguimiento se realiza mediante herramientas específicas del lenguaje:

* **Maven** → Java
* **Pip** → Python

### Aislamiento

Una aplicación y sus dependencias pueden aislarse al empaquetarlas en un contenedor.

**Artifact Registry** puede utilizarse para:

* Almacenar las imágenes.
* Proporcionar un control de acceso detallado.

---

## 03. Configuración

Cada aplicación tiene una configuración para diferentes entornos:

```text
Desarrollo
    │
Pruebas
    │
Producción
```

La configuración debe ser **externa al código**.

Se mantiene en **variables de entorno** para proporcionar flexibilidad durante la implementación.

---

## 04. Servicios de respaldo

Cada servicio de respaldo, como:

* Base de datos.
* Caché.
* Servicio de mensajería.

Debe ser accesible mediante **URL** y definirse según la configuración.

Los servicios de respaldo actúan como abstracciones para el recurso subyacente.

### Objetivo

Poder intercambiar un servicio de respaldo por una implementación diferente de manera sencilla.

---

## 05. Compilar, lanzar y ejecutar

El proceso de implementación de software se divide en tres etapas:

```text
┌──────────┐
│ Compilar │
└────┬─────┘
     ▼
┌─────────┐
│ Lanzar  │
└────┬────┘
     ▼
┌─────────┐
│ Ejecutar│
└─────────┘
```

Cada etapa genera un artefacto identificable de manera inequívoca.

### Compilar

Crea un paquete de implementación a partir del código fuente.

### Lanzar

Cada paquete de implementación debe vincularse a un lanzamiento específico.

Este lanzamiento es el resultado de combinar:

```text
Entorno de ejecución
        +
    Compilación
        ↓
    Lanzamiento
```

Esto permite:

* Realizar reversiones sencillas.
* Mantener un registro de auditoría del historial de cada implementación en producción.

### Ejecutar

La etapa de ejecución efectúa la aplicación.

---

## 06. Procesos

Las aplicaciones se ejecutan como uno o más **procesos sin estado**.

Si se requiere estado, se debe utilizar la técnica de administración de estados vista anteriormente.

Por ejemplo:

* Cada servicio debe tener su propio almacén de datos.
* Se pueden utilizar cachés con **Memorystore** para almacenar en caché y compartirlos entre los servicios utilizados.

---

## 07. Vinculación de puertos

Los servicios deben exponerse mediante un **número de puerto**.

Las aplicaciones empaquetan al servidor web como parte de la aplicación.

A diferencia de Apache, no requieren un servidor independiente.

En Google Cloud, las aplicaciones pueden implementarse en:

* Compute Engine
* GKE
* App Engine
* Cloud Run

---

## 08. Simultaneidad

La aplicación debe **escalar horizontalmente**.

Esto significa que debe:

```text
Demanda ↑
   │
   ├── Iniciar nuevos procesos
   │
   └── Aumentar la escala
```

Y cuando sea necesario:

```text
Demanda ↓
   │
   └── Reducir la escala
```

Los procesos se ajustan según la demanda y la carga.

---

## 09. Capacidad de ser desechable

Las aplicaciones deben escribirse de forma que sean más confiables que la infraestructura subyacente en la que se ejecutan.

Deben ser capaces de:

* Soportar fallas temporales de la infraestructura.
* Apagarse rápidamente.
* Reiniciarse rápidamente.
* Aumentar la escala rápidamente.
* Reducir la escala rápidamente.
* Adquirir recursos según sea necesario.
* Liberar recursos según sea necesario.

---

## 10. Paridad entre desarrollo y producción

El objetivo es utilizar en:

```text
Desarrollo
    │
    ▼
Pruebas
    │
    ▼
Producción
```

los mismos entornos que se utilizan en producción.

La **IaC** y los **contenedores de Docker** facilitan esta tarea.

Los entornos pueden aprovisionarse y configurarse de forma rápida y coherente mediante variables de entorno.

### Herramientas de Google Cloud

Google Cloud ofrece herramientas que pueden crear flujos de trabajo y mantener la coherencia de los entornos:

* Cloud Source Repositories
* Cloud Storage
* Artifact Registry
* Terraform

### Terraform

Terraform utiliza las APIs subyacentes de cada servicio de Google Cloud para implementar los recursos.

---

## 11. Registros

Los registros proporcionan un reconocimiento del estado de las aplicaciones.

Es importante separar:

```text
Recopilación
     │
     ▼
Procesamiento
     │
     ▼
Análisis
```

de la lógica central de las aplicaciones.

Los registros deben escribirse en la **salida estándar** y agregarse en una sola fuente.

Esto resulta útil cuando las aplicaciones requieren escalamiento dinámico y se ejecutan en nubes públicas.

Permite eliminar la sobrecarga de administrar:

* La ubicación del almacenamiento de los registros.
* La agregación de VMs.
* La agregación de contenedores distribuidos y, a menudo, efímeros.

Google Cloud ofrece un paquete de herramientas para:

* Recopilación.
* Procesamiento.
* Análisis estructurado de los registros.

---

## 12. Procesos administrativos

Generalmente son procesos únicos que deben separarse de la aplicación.

Deben ser:

```text
Automatizados
     +
Repetibles
     ≠
Manuales
```

Según la implementación en Google Cloud, existen diferentes opciones:

* Trabajos cron en GKE.
* Tareas en la nube en App Engine.
* Cloud Scheduler.

---

# Resumen de los 12 factores

| #  | Factor                                | Idea principal                                      |
| -- | ------------------------------------- | --------------------------------------------------- |
| 01 | Base de código                        | Control de versiones                                |
| 02 | Dependencias                          | Declaración y aislamiento                           |
| 03 | Configuración                         | Variables de entorno                                |
| 04 | Servicios de respaldo                 | Recursos accesibles mediante URL                    |
| 05 | Compilar, lanzar y ejecutar           | Separación del proceso de implementación            |
| 06 | Procesos                              | Procesos sin estado                                 |
| 07 | Vinculación de puertos                | Exposición mediante un número de puerto             |
| 08 | Simultaneidad                         | Escalamiento horizontal                             |
| 09 | Capacidad de ser desechable           | Soportar fallas, apagarse y reiniciarse rápidamente |
| 10 | Paridad entre desarrollo y producción | Mantener los mismos entornos                        |
| 11 | Registros                             | Recopilación, procesamiento y análisis separados    |
| 12 | Procesos administrativos              | Procesos automatizados y repetibles                 |
