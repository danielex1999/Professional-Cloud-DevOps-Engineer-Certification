# Microservicios

## ¿Qué son los microservicios?

Los **microservicios** dividen un programa grande en múltiples servicios independientes y pequeños.

```text
Aplicación monolítica
┌─────────────────────────────┐
│      Todas las funciones    │
│      en una sola base       │
│          de código          │
│                             │
│      Base de datos          │
│      compartida             │
└─────────────────────────────┘

              VS.

Microservicios
┌──────────┐  ┌──────────┐  ┌──────────┐
│ Servicio │  │ Servicio │  │ Servicio │
│    A     │  │    B     │  │    C     │
└──────────┘  └──────────┘  └──────────┘
```

Los microservicios son una tendencia actual de la industria, pero es importante tener un buen motivo para seleccionar esta arquitectura.

### Principal motivo

La razón principal es permitir que los equipos:

* Trabajen de forma independiente.
* Realicen entregas a producción a su propio ritmo.
* Escalen la organización agregando equipos.
* Escalen los microservicios de forma independiente según los requisitos.

---

## Arquitectura

Tanto una aplicación monolítica como una basada en microservicios debe tener:

> **Componentes modulares + límites claros**

### Monolítica

Todos los componentes se empaquetan y se implementan juntos.

### Microservicios

Los componentes individuales pueden implementarse de forma independiente.

---

## Google Cloud

Google Cloud proporciona diferentes servicios de procesamiento que facilitan la implementación de microservicios:

```text
┌─────────────────┐
│  Microservicios │
└────────┬────────┘
         │
 ┌───────┼────────┬──────────────┐
 ▼       ▼        ▼              ▼
App     Cloud     GKE       Cloud Functions
Engine   Run
```

Cada uno ofrece diferentes niveles de detalle y control.

---

## Almacén de datos

Para lograr la independencia entre los servicios:

> **Cada servicio debe tener su propio almacén de datos.**

Esto permite:

* Elegir la mejor solución de almacén de datos para ese servicio.
* Mantener la independencia.
* Evitar el acoplamiento entre servicios mediante un almacén de datos.

---

# Objetivos de una arquitectura de microservicios

Una arquitectura diseñada de manera apropiada puede ayudar a:

| Objetivo                                                                                               |
| ------------------------------------------------------------------------------------------------------ |
| Definir contratos sólidos entre los microservicios                                                     |
| Permitir ciclos de implementación independientes, incluida la reversión                                |
| Facilitar pruebas de versiones A/B simultáneas en subsistemas                                          |
| Minimizar la automatización de pruebas y la sobrecarga del control de calidad                          |
| Mejorar la claridad de los registros y la supervisión                                                  |
| Dar contabilización de costos detallada                                                                |
| Aumentar la escalabilidad y la confiabilidad general mediante el escalamiento de unidades más pequeñas |

> Las ventajas deben compensar los desafíos de este estilo de arquitectura.

---

# Desafíos

## Límites entre servicios

Dificultad para definir límites claros entre servicios que permitan el desarrollo y la implementación independientes.

## Infraestructura

Los servicios distribuidos generan:

* Mayor complejidad de infraestructura.
* Más puntos de fallas.

## Latencia

La comunicación mediante redes introduce mayor latencia.

También es necesario crear resiliencia para controlar posibles:

* Fallas.
* Retrasos.

## Seguridad

La comunicación de servicio a servicio requiere seguridad, lo que aumenta la complejidad de la infraestructura.

## Versionado

Es necesario:

* Administrar las interfaces de los servicios.
* Aplicar control de versiones.
* Mantener la retrocompatibilidad.

Esto es especialmente importante porque los servicios pueden implementarse de manera independiente.

---

# Descomposición de una aplicación

Desglosar una aplicación en microservicios es uno de los desafíos técnicos más grandes del diseño de aplicaciones.

Las técnicas como el **diseño basado en dominios** ayudan a identificar grupos funcionales lógicos.

### Primer paso

Desglosar la aplicación según:

```text
Función
   │
   └──► Grupo funcional
             │
             └──► Minimizar dependencias
```

---

## Ejemplo: aplicación de venta minorista en línea

Los grupos funcionales lógicos podrían ser:

```text
Aplicación de venta minorista
│
├── Administración de productos
├── Opiniones
├── Cuentas
└── Pedidos
```

Estos grupos forman varias aplicaciones que exponen una API.

A nivel interno, múltiples microservicios implementan cada una de estas aplicaciones.

Cada microservicio debería poder:

* Implementarse independientemente.
* Escalar independientemente.

También se pueden identificar servicios compartidos, como la **autenticación**, que luego se aíslan y se implementan de forma independiente.

---

# Servicios sin estado y con estado

## Sin estado

Los servicios que no mantienen un estado, sino que lo obtienen del entorno, son más fáciles de administrar.

Su falta de estado facilita:

```text
Escalar
   +
Administrar
   +
Migrar a nuevas versiones
```

## Con estado

No siempre es posible evitar los servicios con estado.

Por eso, desde las primeras etapas del diseño es importante entender:

> **¿Cómo se administrará el estado?**

Los servicios con estado presentan desafíos significativos para:

* Escalar.
* Mejorar los servicios.

---

# Estado compartido en memoria

El estado compartido tiene implicaciones que pueden afectar algunos beneficios de una arquitectura de microservicios.

El ajuste de escala automático puede verse obstaculizado porque las solicitudes posteriores del cliente deben enviarse al mismo servidor utilizado inicialmente.

Esto requiere configurar los balanceadores de carga para utilizar:

> **Afinidad de sesión**

En Google Cloud, esto se conoce como **afinidad de sesión**.

---

# Backend para servicios con estado

Una práctica recomendada es utilizar servicios de almacenamiento de backend que sean compartidos por los servicios sin estado de frontend.

### Estado persistente

Se pueden utilizar servicios de datos administrados por Google Cloud como:

* **Firestore**
* **Cloud SQL**

### Caché

Para mejorar la velocidad de acceso a los datos, se pueden almacenar en caché.

**Memorystore**, un servicio de alta disponibilidad basado en Redis, es ideal para esta tarea.

---

# Separación de frontend y backend

Una solución integral puede separar las etapas de procesamiento del frontend y backend.

```text
              Balanceador de cargas
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
      Frontend                 Backend
          │                       │
          │                       ▼
          │              Servicios con estado
          │                       │
          │              ┌────────┴────────┐
          │              ▼                 ▼
          │         Almacenamiento       Caché
          │         persistente
          │
          └──────── Escalamiento ────────┘
```

El balanceador de cargas distribuye las solicitudes entre los servicios de frontend y backend.

Esto permite que el backend escale cuando necesita estar al nivel de la demanda del frontend.

Los servicios con estado también pueden aislarse y utilizar:

* Almacenamiento persistente.
* Almacenamiento en caché.

---

# Idea principal

El aislamiento de los servicios con estado permite que una gran parte de la aplicación utilice la:

**Escalabilidad + tolerancia a errores**

de los servicios de Google Cloud como servicios sin estado.

Además:

> **Al aislar los servidores y servicios con estado, los desafíos de escalar y actualizar se limitan a un subconjunto del conjunto general de servicios.**
