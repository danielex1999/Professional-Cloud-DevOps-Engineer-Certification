# Madurez organizativa para adoptar SRE

Antes de implementar los diversos principios de **SRE**, es importante evaluar el nivel de madurez de la organización.

La ingeniería de confiabilidad de sitios puede entenderse como un recorrido de tres partes:

```text
┌─────────────────────────────┐
│     SLO con consecuencias   │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│       Mejorar el mañana     │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│    Regular la carga de      │
│          trabajo            │
└─────────────────────────────┘
```

---

# Niveles de madurez organizativa

## Madurez baja

El nivel de madurez organizativa se considera **bajo** cuando la organización aún no ha adoptado los principios, las prácticas y la cultura de SRE.

## Madurez alta

El nivel de madurez organizativa se considera **alto** cuando:

* Existe un equipo establecido de SRE.
* Los principios de SRE se han comprendido, implementado e incorporado en gran medida.
* Las prácticas de SRE se han comprendido, implementado e incorporado en gran medida.
* La cultura de SRE se ha comprendido, implementado e incorporado en gran medida.

---

# Características de una organización con alta madurez SRE

Una organización con un nivel alto de madurez de SRE debería contar con:

### SLO bien documentados

SLO centrados en los usuarios, donde el nivel objetivo de confiabilidad corresponda idealmente con la satisfacción del cliente.

### Porcentajes de error aceptable

Los porcentajes de error aceptable representan presupuestos para fallas.

> **Porcentaje de error aceptable = diferencia entre la perfección y tu SLO**

Esto permite que los equipos de TI avancen rápido siempre que no se exceda ese porcentaje, con acciones definidas para mejorar la confiabilidad si el servicio de producción falla.

### Cultura de análisis retrospectivos

Una cultura de análisis retrospectivos **sin buscar culpables**.

Esta cultura reconoce que habrá aspectos que fracasarán y que los errores humanos son, en realidad, problemas sistémicos.

### Baja tolerancia al trabajo repetitivo

El trabajo repetitivo consiste en tareas que suelen ser:

* Manuales.
* Repetitivas.
* Automatizables.
* Tácticas.
* Sin valor perdurable.

Además, se escala linealmente a medida que crece el servicio.

---

# Adopción de los principios SRE

Estos principios pueden ser adoptados por cualquier equipo responsable de los sistemas de producción, más allá del nombre del equipo, antes del armado del equipo de SRE y durante este.

Entre los principios técnicos analizados se encuentran los **SLO** y los **porcentajes de error aceptable**.

Según Google, no se pueden alcanzar determinados objetivos comerciales sin antes:

```text
Definir SLO
    +
Definir porcentajes de error aceptable
    +
Establecer políticas
          ↓
Alineación de incentivos
          +
Equilibrio entre velocidad y confiabilidad
          +
Colaboración eficiente
```

---

# Recorrido hacia SRE

El primer paso del recorrido hacia SRE puede variar según:

* La cultura de la organización.
* Las necesidades empresariales.

Sin embargo, Google recomienda cuatro pasos.

Una vez definidos:

* Los SLO.
* Los porcentajes de error aceptable.
* La cultura de análisis retrospectivos.

La organización estará mejor preparada para comenzar a definir y organizar los equipos de SRE.

Posteriormente, se pueden comenzar a implementar:

* Prácticas de automatización.
* Regulación de la carga de trabajo.

---

# Evaluación con DORA

También se puede realizar una revisión rápida sobre DevOps mediante una herramienta llamada **DORA** para obtener una recomendación sobre cómo comenzar.

Se trata de una evaluación rápida de **cinco preguntas** sobre las prácticas de ingeniería actuales.

**Herramienta:**
https://www.devops-research.com/quickcheck.html

---

# Evaluar dónde se encuentra la organización

Es importante trabajar junto con los equipos de **ingeniería y operaciones** para determinar en qué lugar del recorrido se encuentra la organización.

```text
             RECORRIDO SRE
                  │
                  ▼
        Evaluar madurez actual
                  │
        ┌─────────┴─────────┐
        │                   │
        ▼                   ▼
      Baja                 Alta
        │                   │
        ▼                   ▼
Adoptar principios,   Continuar con la
prácticas y cultura   implementación
        │                   │
        └─────────┬─────────┘
                  ▼
           Avanzar en SRE
```

Es posible que una organización todavía no siga los principios de SRE, lo cual no es un problema.

Lo importante es comprender los principios para poder comenzar.
