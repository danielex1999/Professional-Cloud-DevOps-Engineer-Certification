# Google Kubernetes Engine (GKE)

## ¿Qué es GKE?

**GKE (Google Kubernetes Engine)** es un servicio administrado de **Kubernetes** alojado por Google en la nube.

El entorno de GKE consta de varias máquinas, principalmente **instancias de Compute Engine**, que se agrupan para formar un clúster.

---

## GKE vs Kubernetes

Desde la perspectiva del usuario, GKE simplifica la administración de Kubernetes.

GKE administra los componentes del **plano de control**.

También:

* Expone una dirección IP para enviar solicitudes a la API de Kubernetes.
* Aprovisiona y administra la infraestructura del plano de control.
* Elimina la necesidad de administrar un plano de control independiente.

---

## Modos de GKE

La configuración y administración de los nodos depende del modo utilizado.

```text
GKE
├── Autopilot
└── Standard
```

### Autopilot

**Autopilot** es el modo recomendado y está optimizado para producción.

GKE administra:

* Infraestructura subyacente.
* Configuración de nodos.
* Escalado automático.
* Actualizaciones automáticas.
* Configuraciones de seguridad.
* Configuraciones de red de referencia.

También ayuda a mantener una postura de seguridad fuerte y fomenta la eficiencia operativa.

### Standard

En **Standard**, el usuario administra la infraestructura subyacente.

Esto incluye la configuración de los nodos individuales.

El usuario es responsable de:

* Configurar el clúster.
* Administrar el clúster.
* Optimizar el clúster.

> A menos que necesites un nivel específico de control de GKE Standard, se recomienda utilizar **Autopilot**.

---

## Crear un clúster

Puedes crear un clúster de Kubernetes con GKE mediante:

* Consola de Google Cloud.
* `gcloud`, disponible en el SDK de Cloud.

Los clústeres de GKE pueden personalizarse con diferentes:

* Tipos de máquinas.
* Cantidades de nodos.
* Configuraciones de red.

---

## Kubernetes en GKE

Kubernetes proporciona los mecanismos para interactuar con el clúster.

Los comandos y recursos de Kubernetes permiten:

* Implementar aplicaciones.
* Administrar aplicaciones.
* Realizar tareas de administración.
* Definir políticas.
* Supervisar el estado de las cargas de trabajo.

---

## Funcionalidades de administración

Un clúster de GKE incluye funciones avanzadas de administración proporcionadas por Google Cloud:

* Balanceo de cargas de Google Cloud para GCE.
* Grupos de nodos.
* Ajuste de escala automático de los nodos.
* Actualizaciones automáticas del software.
* Reparación automática de nodos.
* Registro y supervisión con **Google Cloud Observability**.

### Grupos de nodos

Permiten designar subconjuntos de nodos dentro de un clúster.

```text
Cluster
├── Node Group A
│   ├── Node
│   └── Node
└── Node Group B
    ├── Node
    └── Node
```

---

## Crear un clúster con gcloud

Para iniciar Kubernetes en un clúster de GKE:

```
gcloud container clusters create k1
```

---

## Puntos clave

| Concepto                       | Descripción                                         |
| ------------------------------ | --------------------------------------------------- |
| **GKE**                        | Servicio administrado de Kubernetes en Google Cloud |
| **Autopilot**                  | Modo recomendado y administrado                     |
| **Standard**                   | Permite administrar la infraestructura y los nodos  |
| **Compute Engine**             | Proporciona las instancias que forman el clúster    |
| **Node Groups**                | Agrupan subconjuntos de nodos                       |
| **Cloud Load Balancing**       | Balanceo de cargas para GCE                         |
| **Google Cloud Observability** | Registro y supervisión del clúster                  |
