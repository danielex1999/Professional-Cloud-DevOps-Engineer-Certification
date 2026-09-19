## ¿Qué es DevOps?

DevOps surgió como una forma de derribar las barreras entre los equipos de desarrollo y operaciones.

Tradicionalmente:

- Los desarrolladores son responsables de escribir el código de los sistemas.
- Los operadores son responsables de garantizar que los sistemas funcionen de forma confiable.

Los desarrolladores buscan trabajar más rápido, innovar y enviar código nuevo con rapidez, mientras que los operadores buscan mantener los sistemas estables y enfocarse en la confiabilidad y la coherencia.

Esta diferencia de prioridades generó tensión entre ambos equipos y no siempre estaba alineada con las necesidades de la empresa.

DevOps nació como una cultura para cerrar esta brecha entre desarrolladores y operadores.

## Las cinco áreas clave de DevOps

Google clasifica DevOps en cinco áreas clave:

### 1. Reducir los silos organizativos

Aumentar y fomentar la colaboración derribando las barreras entre equipos.

### 2. Aceptar que los errores son normales

Las computadoras son poco confiables por naturaleza y no se puede esperar una ejecución perfecta. Los errores forman parte inevitable del proceso.

### 3. Implementar cambios graduales

Los pequeños cambios incrementales son más fáciles de revisar. Si un cambio gradual libera un error en producción, permite reducir el tiempo de recuperación y facilita la reversión.

### 4. Aprovechar las herramientas y la automatización

Identificar el trabajo manual que se puede automatizar ayuda al equipo de TI a trabajar de forma eficiente y centrarse en las tareas que importan.

### 5. Medirlo todo

La medición es un indicador fundamental para el éxito. No es posible saber si lo que se hace tiene éxito si no existe una forma de medirlo.

DevOps es una **filosofía**, no una metodología de desarrollo ni una tecnología.

Aunque la filosofía de DevOps destaca formas críticas de operar para los equipos de TI, no ofrece orientación explícita sobre cómo una organización debe aplicar las prácticas para tener éxito.

## ¿Qué es la SRE?

La SRE evolucionó en Google a principios de los años 2000 independientemente de DevOps.

En 2003, Benjamin Treynor Sloss recibió la tarea de administrar a un equipo de ingenieros responsables de mantener los sitios web de Google en funcionamiento.

El equipo estaba compuesto por ingenieros de software, por lo que parte de su tiempo se dedicó a tareas de operaciones además de las tareas de desarrollo. Esto les permitió comprender mejor cómo se ejecutaba su código en producción.

Esta forma de trabajar llevó a ubicar la ingeniería de confiabilidad y el rol asociado en un lugar donde los SRE, que generalmente son ingenieros, son responsables de las operaciones.

Al igual que DevOps pretende cerrar la brecha entre el desarrollo de software y las operaciones de software, la SRE es una forma concreta de resolver los problemas que aborda la filosofía de DevOps.

La SRE es una **práctica y un rol**.

No todas las organizaciones que siguen los principios de la SRE necesariamente deben tener ingenieros con el título de SRE.

Las prácticas y los principios son el enfoque principal, mientras que los títulos y las estructuras de equipo son detalles de implementación.

## SRE y las áreas clave de DevOps

### Reducir los silos organizativos

Los SRE comparten la propiedad de producción con los desarrolladores.

Juntos definen:

- Objetivos de nivel de servicio (SLO).
- Porcentajes de error aceptables.
- La forma de determinar la confiabilidad.
- La forma de priorizar el trabajo.

Esto promueve una visión compartida y conocimiento, además de la colaboración y mejores comunicaciones.

### Aceptar que los errores son normales

Aceptar el error como un estado normal es una práctica importante dentro de la SRE.

Luego de un incidente se realiza un análisis post mortem libre de culpas para:

- Mejorar la comprensión del modo de falla.
- Identificar acciones preventivas eficaces.
- Reducir la probabilidad o el impacto de un incidente similar.

Aprender de los incidentes requiere una cultura de seguridad psicológica sin culpabilización.

### Implementar cambios graduales

Los SRE pretenden reducir el costo de los errores mediante el lanzamiento de cambios a un pequeño porcentaje de usuarios antes de que haya una disponibilidad general.

Culturalmente, esto promueve más design thinking y prototipado.

### Aprovechar las herramientas y la automatización

Los SRE se centran en la automatización del trabajo repetitivo mediante la reducción de su cantidad.

La automatización puede generar resistencia al cambio, por lo que los equipos necesitan comprender la psicología del cambio y cómo abordar la resistencia dentro del equipo.

### Medirlo todo

Los SRE trabajan para medir lo relacionado con:

- Trabajo repetitivo.
- Confiabilidad.
- Salud de los sistemas.

Para fomentar estas prácticas, las organizaciones necesitan una cultura de:

- Definición de objetivos.
- Transparencia.
- Toma de decisiones basada en datos.

## DevOps y SRE

Las prácticas de la SRE se alinean con las áreas de DevOps.

Además de implementar las prácticas técnicas de la SRE, también es necesario implementar las prácticas culturales.

Sin una cultura que las sustente, no es posible mantener los aspectos prácticos de la SRE.

Las prácticas pueden clasificarse de diferentes maneras según la organización. El idioma y las definiciones son menos fundamentales que alcanzar los objetivos de la organización y los resultados que se buscan ofrecer a los clientes.

Se puede discrepar en la terminología precisa, pero muchos de los principios subyacentes son los mismos.

El objetivo de la SRE es **servir a la empresa y al usuario, y no al revés**.