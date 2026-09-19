## DevOps y SRE

La práctica de DevOps busca alinear principios, prácticas e incentivos entre equipos.

La ingeniería de confiabilidad de sitios (SRE) se desarrolló como un conjunto de principios y prácticas para cambiar la forma de pensar, medir e incentivar la fiabilidad.

### Caso de un minorista en línea

Un minorista en línea cuenta con una aplicación donde los clientes pueden:

- Navegar por el catálogo.
- Añadir artículos a sus carritos.
- Completar sus compras.

El equipo de operaciones realiza revisiones semanales de las métricas clave.

Durante una revisión, observaron que el tiempo entre el clic en pagar y el estado de confirmado estaba aumentando lentamente.

Aunque no era un problema crítico, decidieron abordarlo y el equipo dedicó tiempo a trabajar en el problema de latencia.

Mientras tanto, el equipo de desarrollo de productos continuó enviando nuevas funciones.

Los desarrolladores comenzaron a trabajar horas extras para mantenerse al día con el envío de nuevas funciones y, al mismo tiempo, resolver el problema de latencia identificado anteriormente.

Los equipos de producto no estaban satisfechos con el ritmo de desarrollo, mientras que los equipos de TI tuvieron que realizar un esfuerzo adicional para satisfacer las necesidades de la empresa y solucionar el problema.

Esto provocó agotamiento en los equipos de TI al intentar satisfacer tanto las necesidades de la empresa como las de confiabilidad.

Posteriormente, los equipos de producto reconocieron que, si hubieran conocido el problema de latencia, habrían priorizado corregirlo antes de enviar nuevas funciones.

Sin embargo, la empresa y el equipo de TI no tenían estándares compartidos de comunicación, por lo que esto no ocurrió.

### Aprendizajes

Google consideró que un buen punto de partida era cambiar la forma de pensar, medir e incentivar la fiabilidad.

Este conjunto de principios y prácticas se denomina **Ingeniería de Confiabilidad de Sitios (SRE)**.

### DevOps y SRE

DevOps es un movimiento que, al igual que la SRE, busca alinear principios, prácticas e incentivos entre equipos.

DevOps y SRE tienen mucho en común y suelen abordarse en conjunto.

Ambos comparten aspectos y se complementan.