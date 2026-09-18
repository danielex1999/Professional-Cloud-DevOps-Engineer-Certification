# Kubernetes y Google Kubernetes Engine (GKE)

Kubernetes ayuda a administrar y escalar aplicaciones alojadas en contenedores.

**Google Kubernetes Engine (GKE)** permite utilizar Kubernetes para administrar y escalar aplicaciones y cargas de trabajo.

## ¿Qué es Kubernetes?

Kubernetes es una **plataforma de código abierto** para administrar cargas de trabajo y servicios en contenedores.

Permite:

* Organizar contenedores en muchos hosts.
* Escalarlos como microservicios.
* Implementar lanzamientos y reversiones.

Kubernetes también es un conjunto de APIs que permite implementar contenedores en un conjunto de nodos denominado **clúster**.

## Clúster y nodos

Un **Cluster** es un conjunto de nodos donde Kubernetes ejecuta las aplicaciones y contenedores.

Está compuesto principalmente por:

- **Control Plane:** administra el clúster y determina cómo debe ejecutarse la aplicación.
- **Nodes:** ejecutan los Pods y los contenedores.

```text
                 Kubernetes Cluster
                        │
              ┌─────────┴─────────┐
              │                   │
        Control Plane           Nodes
                                  │
                        ┌─────────┼─────────┐
                        │         │         │
                       Pod       Pod       Pod

```

Un Node es una instancia de procesamiento donde Kubernetes ejecuta los Pods.

En Google Cloud, un Node normalmente corresponde a una máquina virtual de Compute Engine.

```text
Node
 │
 ├── Pod
 │    └── Container
 │
 ├── Pod
 │    └── Container
 │
 └── Pod
      └── Container
```


## Pod

Un **Pod** es la unidad más pequeña en Kubernetes que se puede crear o implementar.

Representa un proceso en ejecución en el clúster, como un componente de una aplicación o una aplicación completa.

Por lo general, un Pod contiene un solo contenedor, pero también puede contener varios contenedores cuando existe una dependencia obligatoria entre ellos.

Los contenedores dentro de un mismo Pod pueden compartir:

* Recursos de red.
* Almacenamiento.

El Pod proporciona:

* Una IP de red única.
* Un conjunto de puertos.
* Opciones configurables que determinan cómo deben ejecutarse los contenedores.

```text
Pod
 │
 ├── Container
 │
 └── Container
```
---

## Deployment

Para ejecutar un contenedor en un Pod se utiliza `kubectl`, que inicia un objeto **Deployment**.

Un **Deployment** es un grupo de réplicas del mismo Pod y mantiene los Pods en ejecución incluso cuando fallan los nodos donde se ejecutan.

```text
Deployment
    │
    ├── Pod 1
    ├── Pod 2
    └── Pod 3
```

Un Deployment puede representar:

* Un componente de una aplicación.
* Una aplicación completa.

Para ver los Pods en ejecución:

`kubectl get pods`

---

## Service

Kubernetes crea un **Service** con una IP fija para los Pods.

Un Service es una abstracción que define:

* Un conjunto lógico de Pods.
* Una política para acceder a ellos.

Los Pods reciben sus propias IP, pero estas direcciones no se mantienen estables en el tiempo.

El Service proporciona un **extremo estable o dirección IP fija**.

```text
             Service
                │
        ┌───────┼───────┐
        │       │       │
      Pod 1   Pod 2   Pod 3
```

### Ejemplo

Puedes tener dos conjuntos de Pods:

* `frontend`
* `backend`

Cada uno puede estar detrás de su propio Service.

Los Pods del backend pueden cambiar, pero los Pods del frontend no necesitan conocer esos cambios.

Simplemente hacen referencia al **Service del backend**.

---

## Load Balancer

Un Service puede utilizar un **balanceador de cargas externo** con una IP pública para permitir que los usuarios fuera del clúster accedan a la aplicación.

En GKE, el balanceador de cargas se crea como un **balanceador de cargas de red**.

El cliente accede a la IP pública y el tráfico se dirige hacia los Pods del Service.

```text
Internet
    │
    ▼
Load Balancer
    │
    ▼
Service
    │
    ├── Pod
    ├── Pod
    └── Pod
```

## Escalado

Para escalar un Deployment se utiliza:

`kubectl scale`

Por ejemplo, un Deployment puede tener tres Pods detrás de un Service y compartir una dirección IP fija.

También se puede utilizar el **escalado automático**.

Por ejemplo, se puede configurar que los Pods aumenten cuando el uso de CPU alcance un límite determinado.

---

# Modelo imperativo

Los comandos imperativos permiten ejecutar acciones directamente sobre Kubernetes.

Ejemplos:

`kubectl expose`

`kubectl scale`

Este enfoque es útil para aprender y probar Kubernetes paso a paso.

---

# Modelo declarativo

La verdadera fortaleza de Kubernetes surge al trabajar de forma **declarativa**.

En lugar de indicar comandos para cada acción, se proporciona un archivo de configuración que indica a Kubernetes cómo se quiere que sea el **estado deseado**.

Kubernetes determina cómo alcanzar ese estado.

Esto se realiza mediante un archivo de configuración del **Deployment**.

Para comprobar las réplicas del Deployment:

`kubectl get deployments`

También se puede utilizar:

`kubectl describe deployments`

### Cambiar las réplicas

Si se desea ejecutar 5 réplicas en lugar de 3:

1. Actualizar el archivo de configuración del Deployment.
2. Ejecutar `kubectl apply` para aplicar la configuración actualizada.

Para obtener la IP externa del Service:

`kubectl get services`

Luego se puede acceder a la dirección IP pública desde un cliente.

---

# Actualización de aplicaciones

Cuando se desea actualizar una nueva versión de una aplicación, lanzar todos los cambios al mismo tiempo puede ser arriesgado.

Para realizar la actualización se puede utilizar:

`kubectl rollout`

También se puede cambiar el archivo de configuración del Deployment y aplicar el cambio con:

`kubectl apply`

Kubernetes creará nuevos Pods según la estrategia de actualización definida.

Una estrategia de actualización puede crear nuevos Pods de la nueva versión y esperar a que haya un Pod nuevo disponible antes de destruir uno antiguo.

---

# Conceptos clave

| Concepto                | Descripción                                                 |
| ----------------------- | ----------------------------------------------------------- |
| **Kubernetes**          | Plataforma de código abierto para administrar contenedores  |
| **GKE**                 | Servicio de Google Kubernetes Engine                        |
| **Clúster**             | Conjunto de nodos donde se ejecutan los contenedores        |
| **Plano de control**    | Administra y coordina el clúster                            |
| **Nodo**                | Instancia de procesamiento donde se ejecutan los Pods       |
| **Pod**                 | Unidad más pequeña que Kubernetes puede crear o implementar |
| **Deployment**          | Administra réplicas de Pods                                 |
| **Service**             | Proporciona un acceso estable a un conjunto de Pods         |
| **kubectl**             | Herramienta para interactuar con Kubernetes                 |
| **Escalado automático** | Aumenta los Pods según determinadas métricas                |
| **Modelo imperativo**   | Indica directamente qué acción ejecutar                     |
| **Modelo declarativo**  | Define el estado deseado                                    |
| **Rolling Update**      | Crea nuevos Pods antes de eliminar los antiguos             |
