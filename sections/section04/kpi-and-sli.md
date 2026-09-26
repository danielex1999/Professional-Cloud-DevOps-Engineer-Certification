# KPI, SLI, SLO y ANS

Para administrar correctamente un servicio es importante entender qué comportamientos importan, cómo medirlos y cómo evaluarlos.

Estas mediciones deben considerarse dentro de las restricciones existentes, como:

* Tiempo.
* Finanzas.
* Personas.

El tipo de sistema determina los datos que pueden medirse.

---

# Métricas según el sistema

## Sistemas orientados al usuario

| Pregunta                                | Métrica                    |
| --------------------------------------- | -------------------------- |
| ¿Se respondió una solicitud?            | Disponibilidad             |
| ¿Cuánto tardó en responder?             | Latencia                   |
| ¿Cuántas solicitudes se pueden manejar? | Capacidad de procesamiento |

## Sistemas de almacenamiento de datos

| Pregunta                                   | Métrica        |
| ------------------------------------------ | -------------- |
| ¿Cuánto tarda la lectura y escritura?      | Latencia       |
| ¿Hay datos cuando se necesitan?            | Disponibilidad |
| ¿Se pierden datos cuando ocurre una falla? | Durabilidad    |

La clave es que estas preguntas pueden responderse mediante los datos recopilados de los servicios.

---

# KPI

Los encargados de las decisiones de negocio utilizan **KPI** para medir el valor de los proyectos.

Los KPI pueden clasificarse en:

```text
KPI
├── Comerciales
└── Técnicos
```

## KPI comerciales

Miden lo que el negocio valora en relación con un proyecto o servicio.

Ejemplos:

* ROI.
* Ganancias antes de intereses e impuestos.
* Deserción de clientes.
* Rotación de personal.

## KPI técnicos

Miden aspectos relacionados con el software.

Ejemplos:

* Páginas vistas.
* Registros de usuarios.
* Cantidad de confirmaciones de compra.

Los KPI técnicos deben estar alineados con los objetivos comerciales.

---

# Objetivos vs KPI

Un **objetivo** es el resultado que se quiere lograr.

Un **KPI** es una métrica que indica el progreso hacia ese objetivo.

```text
Objetivo
   ↓
KPI
   ↓
Medición del progreso
```

Para cada objetivo se deben definir KPI que permitan supervisar y medir el progreso.

Para cada KPI también se debe establecer cómo se define el éxito.

### Ejemplo

**Objetivo:** aumentar las ventas de una tienda en línea.

**KPI:** porcentaje de conversiones del sitio web.

Supervisar los KPI en función de los objetivos permite realizar ajustes según los comentarios.

---

# Características de un KPI

Para que los KPI sean eficaces deben ser:

### Específicos

No deben ser generales.

Por ejemplo:

> Fácil de usar

es subjetivo.

Mientras que:

> Accesible en virtud del artículo 508

es más específico.

### Medibles

La medición permite saber si se está avanzando hacia el objetivo o alejándose de él.

### Alcanzables

El KPI debe establecer una meta que pueda alcanzarse.

Por ejemplo, esperar un **100% de conversiones** en un sitio web no es un objetivo alcanzable.

### Relevantes

El KPI debe estar relacionado directamente con el objetivo.

### Limitados en el tiempo

El período de medición debe estar definido.

Por ejemplo:

* Disponibilidad por día.
* Disponibilidad por mes.
* Disponibilidad por año.

---

# Terminología del nivel de servicio

Para ofrecer un determinado nivel de servicio se utilizan:

```text
SLI → Indicador de nivel de servicio
SLO → Objetivo de nivel de servicio
ANS → Acuerdo de nivel de servicio
```

---

# SLI

Un **SLI (Service Level Indicator)** es una medida cuantitativa de algún aspecto del nivel de servicio proporcionado.

Algunos ejemplos son:

* Capacidad de procesamiento.
* Latencia.
* Tasa de error.

Los indicadores deben ser **medibles**.

Por ejemplo:

> Tiempo de respuesta rápido

no es medible.

En cambio:

> Solicitudes GET de HTTP que responden en un período de 400 ms agregadas por minutos

sí es medible.

De forma similar:

> Alta disponibilidad

no es medible.

Mientras que:

> Porcentaje de solicitudes exitosas en relación con todas las solicitudes agregadas por minuto

sí es medible.

---

# SLO

Un **SLO (Service Level Objective)** es un objetivo o rango de valores acordado para un nivel de servicio medido mediante un SLI.

Puede expresarse mediante límites inferiores y superiores.

### Ejemplo

> La latencia promedio de las solicitudes HTTP del servicio debe ser menor que 100 milisegundos.

El SLO define el nivel de servicio que se espera alcanzar.

---

# ANS

El **ANS (Acuerdo de Nivel de Servicio)** es un acuerdo entre un proveedor de servicios y un consumidor.

Define:

* Responsabilidades relacionadas con la entrega del servicio.
* Consecuencias cuando esas responsabilidades no se cumplen.

El ANS es una versión más restrictiva del SLO.

Lo ideal es diseñar una solución y mantener un SLO acordado con capacidad libre respecto al ANS.

```text
SLO
 ↓
Margen de capacidad
 ↓
ANS
```

---

# Agregación de métricas

Los indicadores no solo deben ser medibles; también es importante definir cómo se agregan.

Por ejemplo, para las solicitudes por segundo:

```text
Medición cada segundo
        vs
Promedio durante un minuto
```

Una medición puntual puede ocultar aumentos de actividad que ocurren durante algunos segundos.

### Ejemplo

Un servicio recibe:

```text
Segundos pares   → 1,000 solicitudes/segundo
Segundos impares → 0 solicitudes/segundo
```

El promedio durante un minuto podría informarse como:

```text
500 solicitudes/segundo
```

Sin embargo, en determinados momentos la carga real es el doble del promedio.

---

# Percentiles

Los promedios también pueden ocultar la experiencia del usuario, especialmente en métricas como la latencia.

Pueden ocultar solicitudes que tardan mucho más que el promedio.

Por ello, es mejor utilizar **percentiles**.

```text
Percentil 50 → Caso típico
Percentil 99 → Valores del peor caso
```

Un percentil de orden superior, como el **99%**, permite observar valores más cercanos a los peores casos.

---

# Resumen

```text
Objetivo
   ↓
KPI
   ↓
Medir progreso

SLI
   ↓
Mide un aspecto del servicio

SLO
   ↓
Define el objetivo del SLI

ANS
   ↓
Define el acuerdo y las consecuencias
```

## Conceptos clave

| Concepto                       | Definición                                                      |
| ------------------------------ | --------------------------------------------------------------- |
| **KPI**                        | Métrica que indica el progreso hacia un objetivo                |
| **SLI**                        | Medida cuantitativa de un aspecto del servicio                  |
| **SLO**                        | Objetivo o rango acordado para un SLI                           |
| **ANS**                        | Acuerdo entre proveedor y consumidor sobre el nivel de servicio |
| **Disponibilidad**             | Indica si una solicitud o dato está disponible                  |
| **Latencia**                   | Tiempo que tarda una operación o respuesta                      |
| **Capacidad de procesamiento** | Cantidad de solicitudes que puede manejar un sistema            |
| **Durabilidad**                | Indica si los datos se conservan ante fallas                    |
| **Percentil 50**               | Representa un caso típico                                       |
| **Percentil 99**               | Muestra valores cercanos a los peores casos                     |
