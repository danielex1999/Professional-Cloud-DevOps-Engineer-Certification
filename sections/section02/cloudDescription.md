# ☁️ Introducción a la Computación en la Nube

## 📌 ¿Qué es la computación en la nube?

La **computación en la nube (Cloud Computing)** es una forma de utilizar recursos de **Tecnologías de la Información (TI)** a través de Internet, bajo un modelo flexible, escalable y basado en el consumo.

El concepto de computación en la nube fue formalizado por el **National Institute of Standards and Technology (NIST)** de Estados Unidos.

### Características principales

La computación en la nube se caracteriza por cinco aspectos fundamentales:

#### 1. ⚡ Autoservicio y bajo demanda

Los usuarios pueden obtener los recursos que necesitan sin intervención humana directa del proveedor.

A través de una interfaz web pueden solicitar:

* 🖥️ Capacidad de procesamiento
* 💾 Almacenamiento
* 🌐 Redes
* Otros recursos de TI

#### 2. 🌍 Acceso a través de Internet

Los recursos de la nube pueden ser utilizados desde cualquier lugar mediante Internet.

Esto permite que los usuarios accedan a sus aplicaciones y recursos sin necesidad de encontrarse físicamente en el centro de datos.

#### 3. 🏢 Agrupación de recursos

El proveedor de servicios en la nube mantiene un **gran conjunto de recursos** y los asigna dinámicamente a diferentes clientes.

Esto permite al proveedor:

* Comprar infraestructura a gran escala.
* Compartir recursos entre múltiples clientes.
* Reducir costos.
* Trasladar parte de esos beneficios económicos a los clientes.

El cliente, además, normalmente no necesita conocer la ubicación física exacta de los recursos que está utilizando.

#### 4. 📈 Elasticidad

Los recursos pueden aumentar o disminuir rápidamente según las necesidades.

Por ejemplo:

```text
Mayor demanda
     ↓
Más recursos
     ↓
Mayor capacidad
```

Cuando la demanda disminuye:

```text
Menor demanda
     ↓
Menos recursos
     ↓
Menor capacidad
```

La **elasticidad** permite adaptar la infraestructura a las necesidades reales de cada momento.

#### 5. 💰 Pago por uso

Los clientes pagan por los recursos que utilizan o reservan.

```text
Uso de recursos → Pago
Menor uso       → Menor costo
Sin uso         → Se dejan de consumir esos recursos
```

Este modelo permite evitar grandes inversiones iniciales en infraestructura física.

---

# 🕐 Evolución hacia la Computación en la Nube

La computación en la nube no apareció de manera repentina. Su evolución puede entenderse mediante diferentes etapas.

## Primera ola: Colocación (Colocation)

La **colocación** permitió a las empresas alquilar espacio físico dentro de centros de datos.

En lugar de:

```text
Empresa
   ↓
Compra terreno
   ↓
Construye centro de datos
   ↓
Compra infraestructura
```

podían:

```text
Empresa
   ↓
Alquila espacio en un centro de datos
   ↓
Instala y administra sus equipos
```

Esto reducía la necesidad de invertir directamente en bienes raíces e infraestructura física para construir un centro de datos propio.

---

## Segunda ola: Virtualización

La siguiente etapa estuvo marcada por los **centros de datos virtualizados**.

La infraestructura física comenzó a representarse mediante recursos virtuales.

### Infraestructura tradicional

```text
Servidor físico
├── CPU
├── Memoria
├── Disco
└── Red
```

### Infraestructura virtualizada

```text
Servidor físico
│
├── Máquina virtual
│   ├── CPU virtual
│   ├── Memoria virtual
│   └── Disco virtual
│
├── Máquina virtual
│
└── Máquina virtual
```

La virtualización permitió aprovechar mejor los recursos físicos.

Sin embargo, las empresas todavía mantenían gran parte del control sobre la infraestructura.

Características:

* Infraestructura administrada por la empresa.
* Entorno controlado.
* Configuración realizada por los usuarios.
* Recursos virtualizados sobre infraestructura física.

---

## Tercera ola: Cloud Computing

Google identificó que el modelo tradicional de virtualización podía limitar la velocidad de crecimiento y desarrollo de sus servicios.

Como evolución, adoptó una arquitectura basada en **contenedores y servicios automatizados**.

La tercera ola se caracteriza por:

* ☁️ Cloud Computing
* 📦 Contenedores
* ⚙️ Automatización
* 📈 Elasticidad
* 🔄 Aprovisionamiento automático
* 💾 Datos escalables
* 🚀 Servicios administrados

En este modelo, los servicios pueden encargarse de aprovisionar y configurar la infraestructura necesaria para ejecutar aplicaciones.

```text
                    ☁️ Cloud
                       │
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
   Computación    Almacenamiento     Red
        │              │              │
        └──────────────┼──────────────┘
                       ↓
                  Aplicaciones
```

La infraestructura deja de ser el principal foco de atención del usuario y se facilita el desarrollo y ejecución de aplicaciones.

---

# 🔄 Comparación de las etapas

| Etapa | Modelo          | Característica principal                                |
| ----- | --------------- | ------------------------------------------------------- |
| 1️⃣   | Colocación      | Alquiler de espacio físico                              |
| 2️⃣   | Virtualización  | Infraestructura física convertida en recursos virtuales |
| 3️⃣   | Cloud Computing | Servicios automatizados, elásticos y escalables         |

La evolución puede resumirse así:

```text
🏢 Infraestructura propia
        ↓
📦 Colocación
        ↓
💻 Virtualización
        ↓
☁️ Cloud Computing
        ↓
⚙️ Automatización + Elasticidad
        ↓
🚀 Aplicaciones y servicios escalables
```

---

# Google Cloud y la tercera ola

La arquitectura de la tercera ola está disponible para los clientes de **Google Cloud**.

El objetivo es permitir que las empresas puedan utilizar infraestructura y servicios tecnológicos sin tener que administrar directamente todos los componentes físicos necesarios para ejecutarlos.

Esto facilita:

* Desarrollo de aplicaciones.
* Escalabilidad.
* Automatización.
* Gestión de infraestructura.
* Uso eficiente de recursos.
* Innovación tecnológica.

---

# Tecnología, software y datos

La evolución de la computación en la nube está relacionada con una transformación más amplia en las empresas.

La idea planteada es:

```text
Tecnología
    ↓
Software
    ↓
Datos
    ↓
Mejores decisiones
    ↓
Diferenciación empresarial
```

La tecnología tiene cada vez mayor importancia para que las empresas puedan diferenciarse.

Progresivamente, una mayor parte de esta tecnología se implementa mediante **software**.

A su vez, el software depende de **datos de calidad** para funcionar correctamente y generar valor.

## Concepto clave

> **Toda empresa es, o será, una empresa de datos.**

Esto significa que los datos se convierten en un componente fundamental para las organizaciones, independientemente de su tamaño o industria.

---

# Resumen

### Computación en la nube

Es un modelo que permite acceder a recursos de TI mediante Internet de forma:

* ⚡ Bajo demanda
* 🖥️ Autoservicio
* 🌍 Accesible desde cualquier lugar
* 🏢 Basada en recursos compartidos
* 📈 Elástica
* 💰 Basada en el consumo

### Evolución

```text
Colocación
    ↓
Virtualización
    ↓
Contenedores
    ↓
Automatización
    ↓
Cloud Computing
```

### Idea fundamental

La computación en la nube permite pasar de administrar directamente la infraestructura a **consumir recursos tecnológicos como servicios**, de manera flexible y escalable.

---

## 📚 Conceptos clave

| Concepto            | Definición                                                                 |
| ------------------- | -------------------------------------------------------------------------- |
| **Cloud Computing** | Uso de recursos de TI mediante servicios en la nube                        |
| **On-demand**       | Recursos disponibles cuando el usuario los necesita                        |
| **Autoservicio**    | El usuario obtiene recursos sin intervención humana directa                |
| **Elasticidad**     | Capacidad de aumentar o reducir recursos según la demanda                  |
| **Virtualización**  | Creación de recursos virtuales sobre infraestructura física                |
| **Contenedores**    | Tecnología para empaquetar y ejecutar aplicaciones de forma aislada        |
| **Escalabilidad**   | Capacidad de soportar un aumento de demanda                                |
| **Pay-as-you-go**   | Pago basado en el uso o reserva de recursos                                |
| **Centro de datos** | Instalación física donde se alojan recursos informáticos                   |
| **Datos**           | Información utilizada por aplicaciones y organizaciones para generar valor |
