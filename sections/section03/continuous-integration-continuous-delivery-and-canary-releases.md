# Cambios graduales: CI/CD y versiones Canary

En el mundo de la TI hay diferentes perspectivas sobre cómo abordar el desarrollo de software.

Culturalmente, los desarrolladores tienden a enfocarse en lograr metas muy ambiciosas para poder implementar grandes cambios de software que generan importantes avances y que podrían cambiar profundamente la sociedad, pero que también tienen altas probabilidades de fracasar.

En cambio, los SRE se enfocan en los cambios graduales con los que pueden probar modificaciones más pequeñas que tendrán un impacto menor en los usuarios en caso de fallar.

Los SRE llevan a la práctica el pilar de DevOps de implementar cambios graduales de formas diferentes para reducir el costo de las fallas.

Los SRE creen que los cambios son mejores cuando son pequeños y frecuentes.

Si bien los cambios son riesgosos, provocarán menos interrupciones para los usuarios si se lanzan en etapas más pequeñas.

La cultura SRE de Google se enfoca en:

* Integración continua y entrega continua o CI/CD.
* Versiones Canary.

## 1. Integración continua y entrega continua

### Integración continua

La integración continua, por lo general, se refiere a:

* Compilar.
* Integrar.
* Probar el código dentro del entorno de desarrollo.

El objetivo principal de esta práctica es permitirles a los ingenieros trabajar en el código y probarlo con mayor frecuencia.

Como resultado:

* La calidad del código aumenta.
* Se pueden evitar los problemas importantes de forma anticipada.

### Entrega continua

La entrega continua se refiere a que puedes implementar en producción con mayor frecuencia, aunque puedes optar por no hacerlo por lo general, debido a que las empresas prefieren un ritmo de implementación más lento.

Esta etapa incluye:

* Integración continua.
* Automatización de las pruebas.
* Automatización de la implementación.

## 2. Proceso de implementación de software

Si consideras a la implementación de software como un proceso, puedes dividirlo en estas categorías:

1. Codificar.
2. Compilar.
3. Integrar.
4. Probar.
5. Lanzar.
6. Implementar.
7. Operar.

### Desarrollo ágil

En el desarrollo ágil, el proceso comprende los pasos de:

* Codificar.
* Compilar.

### DevOps

La filosofía de DevOps se extiende desde el paso de codificar hasta el de operar.

### CI/CD

La integración continua y la entrega continua se ubican en el medio, desde:

* Codificar.
* Probar.
* Lanzar.
* Implementar.

## 3. CI/CD y reducción del costo de las fallas

La práctica de CI/CD ayuda a reducir el costo de las fallas cuando se implementan cambios graduales de diferentes formas:

* Ayuda a superar los desafíos de la transformación ágil.
* Minimiza los inconvenientes con la integración de código.
* Reduce los errores humanos.
* Promueve un código de calidad más alta.
* Facilita la recuperación cuando hay una falla.
* Permite automatizar todo lo que sea posible, ahorrando tiempo y dinero.
* Ofrece visibilidad del progreso hacia la finalización del proyecto.
* El tiempo de salida al mercado es más corto.
* Ofrece más métricas para revisar y tomar medidas.

## 4. Versiones Canary

La otra práctica que usan los SRE para implementar cambios graduales son las versiones Canary.

Es posible que hayas oído la frase:

> "Un canario en una mina de carbón"

Esta es una metáfora de algo que advierte sobre un peligro inminente.

Los mineros de carbón llevaban canarios a las minas para detectar gases peligrosos.

Los canarios son más pequeños y respiran más rápido que las personas. Por eso, si el canario moría, los mineros sabían que estaban en peligro.

### Metáfora de las versiones Canary

Podemos simplificar esta metáfora:

* Contamos con algo de gran tamaño que no queremos dañar.
* También tenemos una parte pequeña que aceptamos que podemos perder.
* La parte pequeña detecta un peligro cuando entramos en terreno desconocido.

### Versiones Canary en producción

Tenemos un servicio extenso que queremos conservar.

Perder una pequeña parte de él está dentro de lo aceptable.

Implementamos un cambio en producción con un impacto desconocido en la parte pequeña para detectar los peligros.

Con las versiones Canary, se implementa un cambio en un servicio para un grupo de usuarios que no saben sobre el cambio que reciben con el objetivo de:

1. Evaluar el impacto en ese grupo.
2. Decidir cómo continuar.

Si el cambio incluye errores, el costo será mucho menor que si se hubiese lanzado a todo el sistema y se puede revertir rápidamente.

## 5. Requisitos de las versiones Canary

### Grupo representativo

El grupo de usuarios de la versión Canary debe ser lo suficientemente grande para ser un subconjunto representativo en comparación con el grupo de control.

### Diferencia entre grupos

La diferencia entre el grupo de la versión Canary y el grupo de control, en la medida de lo posible, debería ser únicamente el cambio de producción que se está probando.

### Tamaño del grupo Canary

El grupo de la versión Canary debería ser lo suficientemente pequeño como para no poner en peligro la calidad del servicio en su totalidad en caso de que la versión Canary tenga defectos.

### Complejidad

La implementación de versiones Canary no debería ser muy compleja ni imponer una carga cognitiva significativa al operador.

En otras palabras, debería ser lo suficientemente sencilla para:

* Comprender el impacto del proceso de versiones Canary en el estado general del servicio actual.
* Poder cancelarla fácilmente si se presentan problemas.
