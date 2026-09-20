## Análisis post mortem libre de culpas

Cuando se trabaja a alta velocidad, los errores son inevitables. Por eso, Google considera que aceptar los errores como algo normal es un pilar de la filosofía de DevOps.

Los ingenieros de confiabilidad de sitios experimentados están cómodos con los errores y saben que los incidentes y las interrupciones ocurrirán, aunque se hayan tomado todas las precauciones necesarias.

### Antes de una interrupción

Antes de una interrupción, se busca eliminar la ambigüedad mediante:

- Supervisión y observabilidad en la plataforma.
- Establecimiento y documentación de procesos para la administración y respuesta ante incidentes.
- Transferencias e interrupciones.

Esto permite centrarse con confianza en la cuestión relevante durante un incidente.

### Después de una interrupción

Tras una interrupción, es importante entender por qué se produjo el incidente y tomar medidas para evitar que vuelva a ocurrir de la misma manera.

Los SRE documentan y llevan a cabo un **análisis post mortem libre de culpas**, también conocido en algunos casos como retrospectivo.

Los SRE adoptan un enfoque sistemático para garantizar que el equipo aprenda colectivamente del incidente.

## Objetivo del análisis post mortem

El resultado de un análisis post mortem es un registro escrito del incidente que contiene:

- Detalles del incidente y su línea de tiempo.
- Medidas adoptadas para mitigar o resolver el incidente.
- Impacto del incidente.
- Desencadenante, causa o causas raíz.
- Acciones de seguimiento para evitar que se repita.

Un análisis post mortem libre de culpas se centra en las causas raíz de un incidente sin acusar a una persona o equipo, ni sus acciones o comportamiento.

Personas concretas redactarán y revisarán el análisis, pero todos los participantes del evento forman parte del proceso post mortem para recopilar la mayor cantidad de información posible.

## Objetivos del análisis post mortem

### Comprender todas las causas raíz

Es importante asegurarse de que el equipo entienda correctamente todas las causas raíz.

Casi todas las interrupciones tienen múltiples causas en su origen. Muchas veces, cada causa aislada puede no ser suficiente para causar un error, pero cuando se combinan pueden provocar un incidente.

La técnica de los **cinco porqués** puede utilizarse para analizar la causa de un incidente considerando todos los factores contribuyentes y no únicamente lo que inicialmente parece ser responsable.

### Evitar la recurrencia

El análisis permite definir y tomar medidas efectivas para evitar que el problema vuelva a ocurrir.

Aunque se hayan tomado medidas para resolver el impacto inmediato en los usuarios, el problema podría repetirse a corto o largo plazo.

Es necesario evitar que se repita y priorizar el trabajo necesario para conseguirlo.

### Reducir las interrupciones estresantes

Cada interrupción representa un factor de estrés para el equipo.

Google quiere que sus SRE dediquen tiempo a mejorar los sistemas y no a ocuparse de los incidentes.

Una buena higiene del sistema, incluida la prevención de interrupciones, es clave para la calidad de vida de los ingenieros.

### Evitar multiplicar la complejidad

Las soluciones rápidas pueden ser útiles para resolver incidentes y evitar que se repitan inmediatamente.

Cada una de estas soluciones puede convertirse en un parche dentro del sistema.

Si no se realizan buenos análisis post mortem y no se evita la recurrencia de forma permanente, las soluciones pueden volverse interdependientes y fijas porque cada una depende de la otra.

Esto hace que el sistema sea más complejo de lo necesario y menos mantenible, aumentando finalmente la probabilidad de errores futuros.

### Aprender de los errores

Cada fracaso es una oportunidad para aprender.

Los buenos SRE son pesimistas constructivos y muchos de sus instintos provienen de la experiencia de errores pasados.

Además de crear un registro documentado para que el equipo aprenda de él, la práctica de escribir un análisis post mortem proporciona un valor adicional a la organización.

## Cultura sin culpabilización

Centrarse en una cultura sin culpabilización ayuda a aumentar la eficacia de los equipos.

Los equipos pueden centrarse completamente en evitar que se produzca un problema, en lugar de preocuparse por recibir la culpa si algo sale mal.

También fomenta una cultura de **seguridad psicológica**.