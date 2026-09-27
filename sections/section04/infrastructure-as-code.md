# Infraestructura como código

## ¿Por qué IaC?

Migrar a la nube implica un cambio de mentalidad.

El modelo **a pedido y de pago por uso** de la computación en la nube es diferente al aprovisionamiento de infraestructura local.

### Infraestructura local

En un modelo local tradicional:

* Se compran máquinas.
* Las máquinas se ejecutan de forma continua.
* La infraestructura suele tener algunas máquinas grandes.
* Las máquinas representan un **gasto de capital** que se devalúa con el tiempo.

```text
Infraestructura local

   Comprar máquinas
          │
          ▼
   Máquinas grandes
          │
          ▼
   Ejecución continua
          │
          ▼
   Gasto de capital
```

### Infraestructura en la nube

En la nube, los recursos se alquilan en lugar de comprarse.

Por ello, se busca desactivar las máquinas cuando sea posible para reducir costos.

El enfoque consiste en:

* Tener muchas máquinas pequeñas.
* Escalar horizontalmente en lugar de verticalmente.
* Operar preparándose para las fallas.

Las máquinas representan un **gasto operativo mensual**.

```text
Nube

   Alquilar recursos
          │
          ▼
   Muchas máquinas
       pequeñas
          │
          ▼
   Escalamiento
    horizontal
          │
          ▼
   Gasto operativo
```

En otras palabras:

> En la nube, toda la infraestructura debe ser desechable.

---

# Infraestructura como código (IaC)

La **infraestructura como código (IaC)** permite automatizar:

* Aprovisionamiento.
* Implementación.
* Configuración.

```text
              IaC
               │
      ┌────────┼────────┐
      ▼        ▼        ▼
Aprovisionar Implementar Configurar
```

Esto permite:

* Minimizar riesgos.
* Eliminar errores manuales.
* Admitir implementaciones repetibles.
* Facilitar el escalamiento.
* Operar con mayor rapidez.

Una implementación de **1 o 100 máquinas requiere el mismo esfuerzo**.

---

# Automatización

La automatización puede alcanzarse mediante:

* Secuencias de comandos.
* Herramientas declarativas, como Terraform.

Es importante evitar dedicar tiempo a reparar máquinas con errores o instalar parches y actualizaciones.

Estas actividades pueden producir problemas cuando el entorno se recree posteriormente.

### Enfoque recomendado

Si una máquina necesita mantenimiento:

```text
Máquina con problemas
          │
          ▼
       Eliminar
          │
          ▼
    Crear una nueva
```

---

# Entornos efímeros

Para reducir costos, se pueden aprovisionar **entornos efímeros**, como los entornos de prueba.

Estos pueden replicar el entorno de producción y eliminarse cuando no estén en uso.

```text
Producción
     │
     ├──────────────► Entorno de prueba
     │                     │
     │                     ▼
     │                  Uso temporal
     │                     │
     │                     ▼
     └────────────────── Eliminar
```

---

# Aprovisionamiento a pedido

La infraestructura como código permite aprovisionar y quitar infraestructura rápidamente.

El aprovisionamiento a pedido de una implementación puede integrarse en una **canalización de integración continua**, facilitando la ruta hacia la implementación continua.

```text
       Código
          │
          ▼
Integración continua
          │
          ▼
   Aprovisionamiento
       a pedido
          │
          ▼
    Implementación
```

La infraestructura automatizada puede:

* Aprovisionarse a pedido.
* Administrar la complejidad de la implementación mediante código.
* Modificarse a medida que cambian los requisitos.

Además, todos los cambios ocurren en un lugar.

---

# Terraform

**Terraform** es una herramienta utilizada para infraestructura como código.

Google Cloud admite Terraform.

Terraform es una herramienta de código abierto para aprovisionar recursos de Google Cloud.

```text
                 Terraform
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
   Aprovisionar  Configurar   Eliminar
        │
        ▼
 Recursos de
 Google Cloud
```

Terraform permite aprovisionar recursos de Google Cloud como:

* Máquinas virtuales.
* Contenedores.
* Almacenamiento.
* Redes.

Estos recursos se definen mediante **archivos de configuración declarativos**.

---

# Configuración de Terraform

Las implementaciones de Terraform se encuentran en un archivo conocido como **configuración**.

En ella se detallan todos los recursos que se deben aprovisionar.

```text
Configuración
     │
     ├── Recurso 1
     ├── Recurso 2
     ├── Recurso 3
     └── Recurso N
```

Los parámetros de configuración pueden modularse mediante plantillas.

Esto permite abstraer recursos en componentes reutilizables entre implementaciones.

---

# Lenguaje de configuración de HashiCorp (HCL)

El **lenguaje de configuración de HashiCorp (HCL)** permite describir los recursos de forma concisa mediante:

* Bloques.
* Argumentos.
* Expresiones.

Una implementación puede repetirse una y otra vez con resultados coherentes.

También es posible borrar una implementación completa con un solo comando o clic.

---

# Enfoque declarativo

La ventaja de un enfoque declarativo es que permite especificar **cuál debe ser la configuración** y dejar que el sistema determine los pasos que deben seguirse.

No se implementan los recursos por separado.

En su lugar, se especifica el conjunto de recursos que compone la aplicación o el servicio.

```text
             Configuración
                   │
                   ▼
        ┌──────────────────┐
        │ Conjunto de      │
        │ recursos         │
        └────────┬─────────┘
                 │
                 ▼
             Terraform
                 │
                 ▼
          Infraestructura
```

Esto permite enfocarse en la aplicación.

---

# Implementación en paralelo

A diferencia de Cloud Shell, Terraform implementa recursos en paralelo.

Terraform utiliza las **APIs subyacentes de cada servicio de Google Cloud** para implementar los recursos.

Esto permite implementar recursos como:

* Instancias.
* Plantillas de instancias.
* Grupos.
* Redes de VPC.
* Reglas de firewall.
* Túneles VPN.
* Cloud Routers.
* Balanceadores de cargas.

---

# Herramientas de IaC

Google Cloud admite varias herramientas de infraestructura como código:

* Terraform.
* Chef.
* Puppet.
* Ansible.
* Packer.

En este curso, el enfoque está en **Terraform**.

---

# Lenguaje de Terraform

El lenguaje de Terraform es la interfaz utilizada para declarar recursos.

### Recursos

Los recursos son objetos de infraestructura, como:

* Compute Engine.
* Almacenamiento.
* Contenedores.

### Configuración

Una configuración de Terraform es un documento en el lenguaje de Terraform que indica al servicio cómo administrar una determinada colección de infraestructura.

Una configuración puede constar de:

* Varios archivos.
* Varios directorios.

---

# Sintaxis de Terraform

La sintaxis del lenguaje de Terraform incluye:

### Bloques

Los bloques representan objetos y pueden tener cero o más etiquetas.

Un bloque tiene un cuerpo que permite declarar:

* Argumentos.
* Bloques anidados.

### Argumentos

Los argumentos se utilizan para asignar un valor a un nombre.

### Expresiones

Las expresiones se utilizan para asignar valores a distintos identificadores.

```text
Terraform
   │
   ├── Bloques
   │     ├── Etiquetas
   │     ├── Argumentos
   │     └── Bloques anidados
   │
   ├── Argumentos
   │
   └── Expresiones
```

---

# Terraform en diferentes nubes

Terraform puede utilizarse en:

* Nubes públicas.
* Nubes privadas.

Además, **Terraform ya viene instalado en Cloud Shell**.

---

# Ejemplo de configuración

Un archivo de configuración de Terraform puede comenzar indicando que el proveedor es **Google Cloud**.

Después puede continuar con:

```text
Proveedor
   │
   ▼
Google Cloud
   │
   ▼
Instancia de Compute Engine
   │
   ▼
Disco
   │
   ▼
Salida
   │
   ▼
Direcciones IP
```

La sección de salida permite obtener las **direcciones IP de la instancia aprovisionada** para la implementación.

---

# Resumen visual

```text
                         INFRAESTRUCTURA COMO CÓDIGO
                                      │
                                      ▼
                              Automatización
                                      │
                    ┌─────────────────┼─────────────────┐
                    ▼                 ▼                 ▼
              Aprovisionar       Implementar       Configurar
                    │                 │                 │
                    └─────────────────┼─────────────────┘
                                      ▼
                                  Terraform
                                      │
                                      ▼
                              Archivo de configuración
                                      │
                                      ▼
                               Recursos declarativos
                                      │
                    ┌─────────────────┼──────────────────┐
                    ▼                 ▼                  ▼
                  VMs            Contenedores       Almacenamiento
                    │
                    ▼
                  Redes
                    │
                    ▼
             Implementación
               repetible
```
