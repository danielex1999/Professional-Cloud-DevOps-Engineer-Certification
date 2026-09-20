# Automatización y trabajo repetitivo en SRE

> “Si necesitas que un operador humano modifique tu sistema durante las operaciones normales, el sistema tiene un error.”

Un pilar fundamental de la filosofía de DevOps de Google es **aprovechar las herramientas y la automatización**.

Enfocarse en estos aspectos permite que los equipos de ingeniería se centren en las tareas de desarrollo, en lugar de en las operaciones.

---

## Trabajo repetitivo

Los SRE se deshacen de las tareas operativas a las que llaman **“trabajo repetitivo”**.

> El trabajo repetitivo son las tareas directamente vinculadas a un servicio que son manuales, repetitivas, automatizables, tácticas, que no tienen un valor perdurable o que se escalan linealmente a medida que el servicio crece.

El trabajo repetitivo:

* No son solo tareas administrativas.
* No son simplemente tareas que no quieres hacer.
* No está vinculado al funcionamiento de un servicio de producción.

Con la eliminación del trabajo repetitivo, los SRE pueden dedicar la mayor parte de su tiempo a tareas que:

* Reducen el trabajo repetitivo futuro.
* Agregan funciones de servicio.
* Mejoran la confiabilidad.
* Mejoran el rendimiento.
* Mejoran la utilización.

---

## Ingeniería en SRE

Hasta ahora, aprendiste sobre el aspecto de la **confiabilidad** de la ingeniería de confiabilidad de sitios.

Reducir el trabajo repetitivo y escalar verticalmente los servicios es la parte de **ingeniería** de esta disciplina.

El trabajo de ingeniería permite que un equipo de SRE:

* Escale verticalmente los servicios.
* Administre los servicios de forma más eficiente que un equipo de desarrollo o de operaciones similar.

Si los SRE dedican menos del **50 % de su tiempo al trabajo repetitivo**, se destaca el rol de los SRE como algo muy diferente a un rol típico de operaciones.

---

## ¿Por qué el trabajo repetitivo es un problema?

El trabajo repetitivo puede crear diversos problemas en una organización.

### Estancamiento profesional

El progreso profesional de los miembros del equipo será más lento o se detendrá si dedican muy poco tiempo a proyectos.

Aunque Google recompensa el trabajo indeseable cuando es inevitable y tiene un gran impacto positivo, la carrera profesional no puede girar en torno a ese tipo de trabajo.

### Moral baja

Las personas tienen diferentes niveles de tolerancia respecto de la cantidad de trabajo repetitivo que pueden hacer, pero todo el mundo tiene un límite.

Demasiado trabajo repetitivo provoca:

* Agotamiento.
* Aburrimiento.
* Malestar.

### Confusión

En Google, se busca garantizar que todas las personas que trabajan en o con la organización de SRE comprendan que es una **organización de ingeniería**.

Las personas o equipos de SRE que se dedican demasiado al trabajo repetitivo pueden socavar la claridad de la comunicación y confundir a las personas respecto del rol de la SRE.

### Retraso del progreso

El exceso de estas tareas disminuye la productividad de los equipos.

La velocidad con que se lanzan las funciones de un producto se reducirá si el equipo de SRE está demasiado ocupado en tareas manuales y reaccionarias.

### Precedente

Si estás demasiado dispuesto a encargarte del trabajo repetitivo, tus colegas desarrolladores pueden sentirse incentivados a asignarte más tareas de este tipo.

También pueden asignar a los SRE tareas operativas que deberían realizar los desarrolladores.

Otros equipos podrían comenzar a esperar que los SRE se encarguen de este trabajo y, de ese modo, perpetuar el problema.

### Agotamiento

Incluso si personalmente no estás disconforme con el trabajo repetitivo, a tus colegas actuales o futuros podría disgustarles mucho más.

Si sumas demasiado trabajo repetitivo a los procedimientos de tu equipo, puedes incitar a los mejores ingenieros a buscar un trabajo más gratificante en otro lado.

### Abuso de la confianza

Los empleados o incorporaciones nuevas al equipo de SRE que llegan con la promesa de trabajar en un proyecto pueden sentirse engañados.

Esto puede provocar una disminución de la moral.

---

## El trabajo repetitivo no siempre es malo

Mucho trabajo repetitivo es nocivo a la hora de ejecutar un servicio, pero hacer algunas de estas tareas tiene sus beneficios.

El trabajo repetitivo:

* No le molesta a todo el mundo todo el tiempo.
* Puede ser tolerable en pequeñas cantidades.
* Puede resultar relajante cuando las tareas son predecibles y repetitivas.
* Puede provocar un sentimiento de deber cumplido y triunfos rápidos.
* Puede ser una actividad de bajo riesgo y estrés.

A algunas personas les atraen las tareas repetitivas y pueden hasta disfrutar de este tipo de trabajo.

Sin embargo, **no debería convertirse en la actividad principal de un SRE**.

---

## Equilibrio entre trabajo repetitivo y proyectos

El trabajo repetitivo debe ser una **parte acotada del rol del SRE**.

Si los SRE no tienen tiempo para hacer otras tareas, se dedican a actividades tradicionales de administradores del sistema que los DevOps se manifiestan en contra.

### Umbral del 50 %

Si se establece un umbral del **50 % para el trabajo repetitivo**, los SRE podrán dedicarse a las tareas de los proyectos que respaldan los objetivos de ingeniería y confiabilidad el resto del tiempo.

El trabajo principal en proyectos de los SRE son las tareas que tienen o pueden tener un impacto en los **SLO del equipo**.

Después de eso, deberían enfocarse en las tareas que causan el trabajo repetitivo para los SRE.

---

# Automatización

Un aspecto clave para eliminar el trabajo repetitivo es la **automatización**.

Los SRE buscan automatizar las tareas para no tener que hacerlas.

Esto implica determinar:

* Qué automatizar.
* En qué condiciones.
* Cómo hacerlo.

---

## Beneficios de la automatización

La automatización en un servicio de producción ofrece diversos beneficios.

### 1. Coherencia

Cualquier acción que realice una persona puede tener errores, especialmente cuando se realiza la misma acción cientos de veces.

Es poco probable que una persona pueda ser tan coherente como una máquina.

La falta de coherencia produce:

* Errores.
* Descuidos.
* Problemas con la calidad de los datos.
* Problemas de confiabilidad.

La automatización soluciona esto a través de la **coherencia**.

### 2. Plataforma extensible

Los sistemas automatizados proporcionan una plataforma que se puede extender y aplicar a más sistemas.

Contar con una plataforma también permite centralizar los errores para que se corrijan una sola vez en un solo lugar.

En el caso de los humanos, sería necesario comunicarse con varias personas para corregirlos, lo que podría crear más errores y hacer que se vuelva a introducir el error original.

### 3. Velocidad y precisión

Una plataforma puede ejecutar tareas adicionales:

* Más rápido.
* Con mayor precisión.

Además, puede exportar las métricas de rendimiento con mayor facilidad que un sistema manual.

Si la automatización se ejecuta con suficiente frecuencia y éxito, cualquier falla común puede resolverse más rápidamente.

Esto permite dedicar tiempo a otras tareas e impulsar la velocidad de los desarrolladores.

### 4. Detección temprana

Cuando se detecta un problema en etapas posteriores del ciclo de vida del producto, es más costoso corregirlo.

Por lo general, los problemas que pueden ocurrir en producción son los más costosos de resolver en tiempo y dinero.

Por ello, un sistema automatizado que detecta problemas apenas se presentan posiblemente reduzca el costo total del sistema.

### 5. Acción más rápida

Las máquinas reaccionan más rápido que las personas.

En los sistemas de producción grandes, la automatización es necesaria para la supervivencia, dado que la cantidad de trabajo necesario, por lo general, supera lo que se puede manejar manualmente.

### 6. Ahorro de tiempo

Programar un proceso automatizado puede representar una inversión significativa de tiempo.

Sin embargo, una vez finalizado, no se necesitará la capacitación continua de las personas sobre el mantenimiento del proceso.

> Una vez que una tarea se automatiza, cualquier persona puede ejecutarla.

---

## Automatización y SRE

```text
Trabajo repetitivo
        │
        ▼
   Automatización
        │
        ├── Coherencia
        │
        ├── Plataforma extensible
        │
        ├── Mayor velocidad
        │
        ├── Mayor precisión
        │
        ├── Detección temprana
        │
        ├── Acción más rápida
        │
        └── Ahorro de tiempo
```

Si la automatización no es común en una organización, es probable que haya resistencia al cambio de parte de los equipos cuando comience a incorporarse, así como con las prácticas de SRE.
