# SRE, SLO, SLI y Porcentaje de Error Aceptable

La filosofía de **DevOps** surgió, en parte, por la naturaleza aislada del desarrollo y las operaciones.

Los desarrolladores no suelen conocer bien los sistemas donde se ejecuta su código, mientras que los operadores deben lidiar con código que puede ser inestable y que llega rápidamente desde los equipos de desarrollo.

Para evitar una mentalidad de **“romper y arreglar”**, es necesario eliminar los silos entre:

```text
Empresa
   ↓
Desarrollo
   ↓
Operaciones
```

La **SRE** utiliza prácticas que promueven la **propiedad compartida** entre desarrollo y operaciones y ayudan a mantener la confiabilidad de los servicios.

---

# Confiabilidad

Una forma sencilla de pensar en la confiabilidad es:

```text
Confiabilidad =
Tiempo "bueno"
----------------
Tiempo total
```

Sin embargo, este enfoque no funciona bien en sistemas distribuidos y complejos.

Por ejemplo:

* ¿Cómo medir el tiempo "bueno" de un servidor que no recibe solicitudes?
* ¿Qué sucede si uno de tres servidores está caído?
* ¿El servicio está activo o caído?

Un enfoque más sofisticado define la disponibilidad como:

```text
Interacciones buenas
--------------------
Interacciones totales
```

Esto representa la proporción de usuarios que disfrutan de un servicio disponible y funcional.

---

# Porcentaje de error aceptable

El porcentaje de error aceptable representa la cantidad de tiempo de inactividad que se está dispuesto a tolerar mientras se busca alcanzar un determinado nivel de confiabilidad.

El **100% de confiabilidad** no necesariamente debe ser el objetivo.

Dedicar todo el tiempo a conseguir un 100% de confiabilidad puede ralentizar el lanzamiento de nuevas funciones.

Mientras el servicio se encuentre por encima del objetivo de confiabilidad y exista porcentaje de error aceptable, se pueden impulsar nuevas funciones.

El porcentaje restante también puede utilizarse para:

* Cambios esperados en el sistema.
* Fallos inevitables de hardware y redes.
* Tiempo de inactividad planificado.
* Experimentos arriesgados.

## Objetivo

El porcentaje de error aceptable es un acuerdo que ayuda a **priorizar el trabajo de ingeniería**.

También crea un equilibrio entre:

```text
Innovación ↔ Confiabilidad
```

Los fallos de infraestructura consumen porcentaje de error aceptable, creando responsabilidad compartida entre los equipos.

---

# SLO

Los **objetivos de nivel de servicio (SLO)** son objetivos numéricos precisos para la confiabilidad de un sistema.

Se acuerdan entre las partes interesadas y comparten la responsabilidad de la confiabilidad.

Los SLO ayudan a determinar qué tan rápido pueden trabajar los equipos de desarrollo sin afectar las expectativas de los usuarios.

Medir el rendimiento de los SLO proporciona una indicación del costo de confiabilidad de nuevas funciones.

Si un servicio se mantiene dentro del SLO, esto indica que se puede avanzar sin causar problemas a los usuarios.

---

# SLI

Los **indicadores de nivel de servicio (SLI)** indican en todo momento la eficacia de un servicio.

Un SLI es una **medida cuantificable de la confiabilidad del servicio**.

Se recomienda expresar los SLI como:

```text
Eventos buenos
--------------
Eventos válidos
× 100%
```

El resultado se encuentra entre:

```text
0% → Nada funciona
100% → Nada está roto
```

Los SLI deben representar las expectativas de los usuarios, como:

* Tiempo de respuesta.
* Latencia.
* Calidad.
* Procesamiento de datos.
* Corrección y actualidad.
* Latencia y capacidad de procesamiento del almacenamiento.

---

# Relación entre SLI y SLO

Un **SLO** es el objetivo de un SLI agregado a lo largo del tiempo.

Por ejemplo:

```text
SLI → Medición de confiabilidad
          ↓
SLO → Objetivo de esa medición
```

Si el SLI se expresa como un porcentaje entre 0% y 100%, el SLO normalmente será algo inferior al 100%.

Ejemplo:

```text
99,9% → "Tres nueves"
```

El SLO establece la línea entre las expectativas de los clientes satisfechos e insatisfechos.

```text
Por encima del SLO
        ↓
Expectativa cumplida

Por debajo del SLO
        ↓
Expectativa no cumplida
```

---

# SLA

Un **SLA (Service Level Agreement)** es la promesa que se hace a los clientes sobre el estado del servicio.

Define qué puede hacer el negocio si no se cumplen los objetivos estratégicos.

Por ejemplo:

```text
Incumplimiento del SLA
        ↓
Reembolso de dinero
```

---

# Relación entre SLI, SLO y SLA

```text
SLI
 ↓
Mide la confiabilidad

SLO
 ↓
Define el objetivo de confiabilidad

SLA
 ↓
Define la promesa al cliente
```

---

# SRE y propiedad compartida

La SRE ayuda a romper los silos entre desarrollo y operaciones mediante prácticas que establecen una responsabilidad compartida sobre la confiabilidad.

Los **porcentajes de error aceptable** y los **SLO** permiten acordar:

* Cómo medir la confiabilidad.
* Qué hacer cuando no se alcanzan los objetivos.
* Cómo compartir la responsabilidad de la confiabilidad.

---

# Conceptos clave

| Concepto                          | Descripción                                                        |
| --------------------------------- | ------------------------------------------------------------------ |
| **SRE**                           | Prácticas que promueven la propiedad compartida y la confiabilidad |
| **Porcentaje de error aceptable** | Cantidad de error o inactividad que se puede tolerar               |
| **SLI**                           | Medida cuantificable de la confiabilidad                           |
| **SLO**                           | Objetivo numérico de confiabilidad                                 |
| **SLA**                           | Promesa realizada a los clientes sobre el servicio                 |

# Regla rápida

```text
SLI → ¿Cómo está funcionando?

SLO → ¿Qué nivel queremos alcanzar?

Porcentaje de error aceptable → ¿Cuánto error podemos tolerar?

SLA → ¿Qué prometemos al cliente?
```
