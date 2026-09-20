# Cultura de SRE: objetivos, transparencia y decisiones basadas en datos

Como ya analizamos, una práctica importante de la **SRE** es medir todo, especialmente:

* La confiabilidad.
* El trabajo repetitivo.

Para poder medir todo, es necesario contar con una cultura basada en:

```text
          CULTURA DE SRE
                │
     ┌──────────┼──────────┐
     │          │          │
     ▼          ▼          ▼
 Objetivos  Transparencia  Datos
     │          │          │
     └──────────┼──────────┘
                ▼
       Mejores decisiones
```

---

# Definición de objetivos

Se debería elaborar un proceso de definición de objetivos basado en datos.

Para ello, se deben determinar:

| Elemento         | Pregunta                          |
| ---------------- | --------------------------------- |
| **KPI**          | ¿Qué se va a medir?               |
| **Propósito**    | ¿Para qué se realiza la medición? |
| **Responsables** | ¿Quiénes realizan la medición?    |
| **Enfoque**      | ¿Qué medir y cómo hacerlo?        |

## OKR

Google utiliza **objetivos y resultados clave (OKR)** como KPI.

Los OKR generalmente se califican en una escala de **0.0 a 1.0**:

```text
0.0 ─────────────────────────────── 1.0
No logrado                    Completamente logrado
```

### Consideraciones al calificar OKR

* El punto óptimo para una calificación de OKR es entre **60 % y 70 %**.
* Se debe pensar en grande al desarrollar los OKR.
* Los OKR no son lo mismo que una evaluación de rendimiento.
* Los OKR muestran las contribuciones individuales y su impacto.
* Los OKR organizativos se califican públicamente para exponer su progreso.
* Las reuniones frecuentes a lo largo del trimestre ayudan a los equipos y sus miembros a mantener el progreso.

---

# Transparencia

La organización debe incorporar la **transparencia**.

> La transparencia es una forma de demostrarles a los empleados que son considerados personas confiables y con sentido común.

Ofrecer más contexto sobre lo que está sucediendo, cómo y por qué, permite realizar las tareas con mayor eficacia.

---

## ¿Cómo fomentar la transparencia?

Según las prácticas y la cultura de SRE, existen diferentes formas de fomentar la transparencia:

* Compartir herramientas de supervisión.
* Compartir las comunicaciones.
* Compartir los ciclos de reacción.

### Herramientas compartidas

Google utiliza una herramienta de seguimiento de errores llamada **Buganizer**.

Todas las personas de la empresa pueden acceder a ella.

Los equipos de desarrollo y operaciones pueden:

```text
Revisar errores
      ↓
Ver el progreso
      ↓
Revisar las resoluciones
```

Las herramientas compartidas por ambos equipos promueven la transparencia.

Sin embargo:

> Compartir las herramientas solamente no alcanza para mantener la transparencia de la organización.

También se debe contar con una **cultura de información compartida que derive de los sistemas**.

---

# Ciclos de reacción

Los ciclos de reacción son fáciles de comprender.

```text
       Producir
           ↓
      Evaluar información
           ↓
        Mejorar
           ↓
       Producir
           ↓
          ...
```

Cuando produces algo:

1. Evalúas información sobre la producción.
2. Utilizas esa información para mejorar la producción.
3. Repites el proceso.

Es un ciclo constante de **supervisión y mejora**.

Los líderes de TI deben convertir estos ciclos en una prioridad dentro de sus organizaciones.

Para ello, se debe recordar el modelo de:

* **Cabeza**
* **Corazón**
* **Pies**

---

# Toma de decisiones basadas en datos

La toma de decisiones basada en datos es otro aspecto importante de la cultura de SRE.

Para tomar decisiones basadas en datos es necesario **suprimir los sesgos involuntarios**.

Los sesgos involuntarios o estereotipos sociales sobre grupos de personas específicos se crean de forma inconsciente.

Existen diferentes sesgos comunes que pueden influir en la forma de tomar decisiones.

---

## Tipos de sesgos

### Sesgo de afinidad

Se aplica a quienes se parecen a ti.

Pueden parecerse en distintos aspectos, como:

* Origen étnico.
* Género.
* Contexto socioeconómico.
* Nivel de educación.

Las personas tienden a acercarse a quienes se parecen a ellas.

---

### Sesgo de confirmación

Es la tendencia a buscar información o datos que respalden las ideas preconcebidas.

---

### Sesgo de etiquetado

Es la tendencia a juzgar a las personas por factores externos como:

* Aspecto.
* Vestimenta.

---

### Sesgo de atención selectiva

Consiste en prestar atención a las situaciones, ideas y contribuciones de personas con las que se siente afinidad.

---

# Impacto de los sesgos

Todos estos sesgos pueden crear entornos que no son muy diversos ni inclusivos.

También afectan:

* Creatividad.
* Innovación.
* Moral.
* Compromiso.
* Rotación.

Cuando los empleados ven que se toman decisiones basadas en estos sesgos, se daña el entorno laboral.

---

# ¿Cómo reducir los sesgos involuntarios?

## 1. Cuestiona tus primeras impresiones

No te quedes con la primera decisión que se te viene a la mente, especialmente cuando decides:

* A quién ascender.
* A quién contratar.
* A quién sumar a un equipo.

---

## 2. Justifica tus decisiones

Si debes rendir cuentas por tus decisiones, tendrás menos sesgos involuntarios.

---

## 3. Explica tus acciones

Explica a otros el motivo de tus acciones.

Si no tienes a quién explicárselo, escribe tu razonamiento.

---

## 4. Toma decisiones en grupo

Pide a otros que:

* Repitan lo que escucharon.
* Controlen los sesgos involuntarios de sus pares.

Exponer un sesgo involuntario puede convertirse en un momento de aprendizaje.

> Si crees haber detectado un sesgo, no guardes silencio.

Algunas veces estarás equivocado, pero no debes preocuparte por eso.

---

# Cultura basada en datos

Cuando se crea una cultura de decisiones basadas en datos y se reducen los sesgos involuntarios:

```text
        Datos objetivos
              │
              ▼
      ┌───────────────┐
      │   Decisiones  │
      │ basadas datos │
      └───────┬───────┘
              │
              ▼
       Menos sesgos
              │
              ▼
      Mayor confianza
```

Los equipos pueden observar los datos objetivamente y decidir qué hacer sin sesgos.

Incluso si existe un sesgo, las personas tendrán la confianza de exponerlo si consideran que afecta las decisiones que se toman.
