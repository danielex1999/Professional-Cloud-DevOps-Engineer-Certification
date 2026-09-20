# Medir todo

El último pilar de la filosofía de DevOps es **medir todo**.

Las mediciones permiten ver con claridad lo que sucede en los servicios.

> **No se puede mejorar lo que no se mide.**

---

## Objetivos de medir todo

En Google se consideran tres objetivos principales:

```text
                  MEDIR TODO
                      │
       ┌──────────────┼──────────────┐
       │              │              │
       ▼              ▼              ▼
   Comprender      Analizar       Colaborar
   el estado      los datos      con la empresa
   actual         y mejorar      y generar impacto
```

### 1. Comprender

El equipo de TI puede comprender de forma objetiva el estado actual del servicio.

La confiabilidad puede medirse mediante:

* **SLI**
* **SLO**
* Porcentajes de error aceptable

### 2. Analizar

El equipo puede analizar los datos e identificar las acciones necesarias para mejorar el estado del servicio.

### 3. Colaborar

El equipo de TI puede colaborar con la empresa para tomar decisiones y generar un mejor impacto en toda la organización.

Medir todo con estos objetivos conduce a una empresa basada en datos y ayuda a tomar mejores decisiones en función de los datos operativos recopilados.

---

# Tres prácticas esenciales de SRE

En relación con este pilar existen tres prácticas esenciales:

| Práctica                        | Objetivo                                                                         |
| ------------------------------- | -------------------------------------------------------------------------------- |
| **Medir la confiabilidad**      | Cuantificar la confiabilidad desde la perspectiva del usuario.                   |
| **Medir el trabajo repetitivo** | Identificar y cuantificar el esfuerzo dedicado al trabajo repetitivo.            |
| **Supervisar**                  | Obtener visibilidad del sistema para conocer su estado y diagnosticar problemas. |

---

# 1. Medir la confiabilidad

En SRE, la confiabilidad puede cuantificarse mediante porcentajes de error aceptable, **SLI** y **SLO**.

Elegir buenos SLI es clave para poder medir la confiabilidad.

## Medir desde la perspectiva del usuario

Al establecer una conexión entre los SLI y la experiencia del usuario, se debe decidir qué medir según su perspectiva.

Por ejemplo:

> Al usuario no le importa si la base de datos está inactiva o si los balanceadores de carga envían solicitudes a los backends equivocados.

Lo que experimenta es que:

```text
Página web carga lento
        ↓
Usuario insatisfecho
        ↓
Se puede cuantificar la lentitud
        ↓
Se puede definir un SLO
```

---

## ¿Qué deberías medir?

Algunas métricas pueden ser:

* Uso de CPU
* Uso de memoria
* Promedio de carga

Sin embargo, estas métricas no reflejan necesariamente si los usuarios están satisfechos.

### Métrica deficiente vs. métrica buena

| Métrica deficiente                                                  | Métrica buena                                                        |
| ------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Tiene mucha varianza.                                               | Tiene un rango de valores más acotado.                               |
| El rango normal se superpone con el rango durante una interrupción. | El rango normal difiere bastante del rango durante una interrupción. |
| Es más difícil identificar tendencias.                              | Las tendencias son más visibles y significativas.                    |
| Es más difícil definir un umbral significativo.                     | Es más fácil definir un umbral.                                      |
| Puede generar falsos positivos o falsos negativos.                  | Reduce la superposición de valores.                                  |
| Es un indicador menos útil de la satisfacción de los usuarios.      | Es un mejor indicador del nivel de satisfacción de los usuarios.     |

Los SLI deben proporcionar una definición clara de los **eventos buenos y malos**.

Cuando una métrica tiene mucha varianza y poca correlación con la experiencia del usuario, resulta más difícil definir un umbral significativo.

```text
Métrica deficiente
       │
       ├── Umbral acotado
       │      └── Riesgo de falsos positivos
       │
       ├── Umbral amplio
       │      └── Riesgo de falsos negativos
       │
       └── Punto intermedio
              └── Ambos riesgos
```

Con una métrica eficiente, resulta más fácil definir un umbral porque no hay superposición.

El mayor riesgo es que el SLI no se recupere después de una interrupción con la rapidez esperada.

---

# 2. Medir el trabajo repetitivo

El trabajo repetitivo está vinculado directamente con la ejecución de un servicio y es:

* Manual
* Repetitivo
* Automatizable
* Táctico
* Sin valor perdurable

## ¿Cómo medirlo?

Puede medirse en tres pasos:

### 1. Identificarlo

La persona idónea para identificarlo dependerá de la organización.

Idealmente, serán las partes interesadas y las personas que ejecutan el trabajo en cuestión.

### 2. Seleccionar una unidad de medida

La unidad debe expresar la cantidad de esfuerzo humano aplicado al trabajo.

Medirlo en **minutos y horas** es una buena opción, ya que es objetivo y todo el mundo lo entiende.

### 3. Hacer seguimiento continuo

Las mediciones deben realizarse:

```text
Antes
  ↓
Durante
  ↓
Después
```

Esto permite realizar un seguimiento de las mediciones antes, durante y después de las iniciativas para reducir el trabajo repetitivo.

La recopilación de mediciones debe optimizarse con herramientas o secuencias de comandos para evitar que medir se convierta en más trabajo repetitivo.

---

## Ejemplos para comenzar

Se puede comenzar con algo simple:

* Contar los tickets recibidos.
* Contar las alertas.
* Recopilar estadísticas de alertas.
* Analizar las causas.
* Analizar las acciones.

Estos datos pueden ser útiles para identificar el origen del trabajo repetitivo.

Para medir el tiempo dedicado al trabajo repetitivo se pueden recopilar datos directamente en el sistema de tickets o pedir al equipo que calcule el tiempo dedicado por día o semana.

---

# Beneficios de medir el trabajo repetitivo

Medir el trabajo repetitivo puede generar diferentes beneficios:

```text
               MEDIR EL TRABAJO
                  REPETITIVO
                       │
       ┌───────────────┼───────────────┐
       │               │               │
       ▼               ▼               ▼
   Reducirlo        Mejorar         Mejorar
                   decisiones       el equipo
```

### Reducción del trabajo

Identificar y cuantificar el trabajo repetitivo puede llevar a su eliminación de raíz.

### Decisiones basadas en datos

Un equipo cargado de trabajo repetitivo debería tomar decisiones basadas en datos para destinar mejor su tiempo y esfuerzos de ingeniería.

### Otros beneficios

* Incrementar las tareas de ingeniería del proyecto para reducir aún más el trabajo repetitivo.
* Impulsar la moral del equipo.
* Reducir el desgaste y agotamiento.
* Reducir los cambios de contexto por interrupciones.
* Aumentar la productividad.
* Obtener mayor claridad y estandarización de procesos.
* Mejorar las habilidades técnicas y el desarrollo profesional.
* Reducir el tiempo de capacitación.
* Reducir las interrupciones por errores humanos.
* Mejorar la seguridad.
* Reducir los tiempos de respuesta ante solicitudes de los usuarios.

---

# 3. Supervisar

Hacer una medición de todo implica supervisión.

La supervisión brinda visibilidad de un sistema, lo que es esencial para:

* Juzgar el estado del servicio.
* Diagnosticarlo cuando algo sale mal.

---

## ¿Qué deberías supervisar?

Se recomienda utilizar **alertas relacionadas con los síntomas en lugar de las causas**.

Al usuario no le importa si no puede acceder al sitio web porque:

* El router se está reiniciando.
* La base de datos está sobrecargada.

Tampoco le importa que el uso de CPU sea muy alto si puede acceder al sistema sin demoras.

### Alertas por síntomas vs. alertas por causas

```text
Alertas por cada causa
        ↓
Muchas alertas
        ↓
Alertas spam
```

Es mejor tener:

```text
Menos alertas
      +
Alertas sobre síntomas
      +
Buenas herramientas de depuración
      ↓
Identificación más sencilla de la causa
```

Las herramientas de depuración pueden incluir paneles en los que los responsables identifiquen la causa con facilidad.

---

# Alertas basadas en el porcentaje de error aceptable

Google recomienda utilizar alertas basadas en el uso del **porcentaje de error aceptable**.

Se puede avisar cuando el porcentaje de error se consume muy rápido.

### Ejemplo

Si se gastan **diez horas del porcentaje de error en una hora**, se puede generar una alerta.

También se puede crear un ticket para reducir la tasa de consumo.

Por ejemplo:

> Si se gastan tres días del porcentaje en tres días.

Básicamente, solo se deriva a alguien si existe riesgo de incumplir el **SLO del mes**.

Si el SLO está bien configurado, no será necesario contactar a alguien por problemas que no preocupan a los usuarios.

---

## Excepciones

Esta regla tiene excepciones.

Puede existir un problema sin síntomas visibles para los usuarios.

Las **alertas de capacidad** pueden ser un ejemplo.

Si se sabe que se alcanzará un límite determinado pronto, debería activarse una alerta incluso si no existen síntomas visibles para el usuario.

---

# Cuatro indicadores clave

Para simplificar, Google recomienda supervisar cuatro indicadores clave:

```text
┌──────────────┐
│   Latencia   │
├──────────────┤
│   Tráfico    │
├──────────────┤
│   Errores    │
├──────────────┤
│ Saturación   │
└──────────────┘
```

## Resumen

```text
                  MEDIR TODO
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
  Confiabilidad   Trabajo       Supervisión
                  repetitivo
        │             │             │
      SLI/SLO       Medición      Visibilidad
        │             │             │
        └─────────────┼─────────────┘
                      ▼
              Decisiones basadas
                   en datos
```

Las mediciones y la supervisión son prácticas importantes de SRE que permiten que los equipos de desarrollo se centren en las tareas esenciales.
