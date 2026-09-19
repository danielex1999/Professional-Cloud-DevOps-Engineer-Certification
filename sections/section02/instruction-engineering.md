# IA Generativa, LLM e Ingeniería de Instrucciones

La IA generativa y los **LLM** son herramientas poderosas, pero para aprovechar sus capacidades es importante comprender su arquitectura y las recomendaciones para implementar estas tecnologías.

## Objetivo

El módulo **Google Cloud: Guía de ingeniería de instrucciones** aborda:

* ¿Qué es la IA generativa?
* ¿Qué es un modelo de lenguaje grande?
* ¿Qué es la ingeniería de instrucciones?
* ¿Cuáles son las prácticas recomendadas de la ingeniería de instrucciones?

---

# IA generativa

La **Inteligencia Artificial generativa (IA generativa)** es un subconjunto de la Inteligencia Artificial capaz de crear:

* Texto
* Imágenes
* Otros datos

Los modelos generativos suelen crear este contenido en respuesta a instrucciones.

Los modelos de IA generativa aprenden los patrones y la estructura de los datos utilizados durante el entrenamiento y crean datos nuevos con características similares.

La IA generativa se utiliza en diferentes industrias, como:

* Desarrollo de software
* Atención de salud
* Finanzas
* Entretenimiento
* Atención al cliente
* Ventas

---

# IA generativa vs LLM

Aunque los términos pueden utilizarse indistintamente, no son idénticos.

| Concepto          | Descripción                                                                     |
| ----------------- | ------------------------------------------------------------------------------- |
| **IA generativa** | Abarca modelos capaces de generar diferentes tipos de contenido, no solo texto. |
| **LLM**           | Subconjunto de modelos de IA generativa enfocados en tareas de lenguaje.        |

---

# Modelos de lenguaje grandes (LLM)

Los **LLM** son modelos de lenguaje de uso general y de gran tamaño que pueden entrenarse previamente y después ajustarse para fines específicos.

## ¿Qué significa "grande"?

Hace referencia a:

* El tamaño del conjunto de datos de entrenamiento.
* La cantidad de parámetros.

El conjunto de datos de entrenamiento puede llegar a una escala de petabytes.

Los **parámetros** representan los recuerdos y conocimientos que la máquina aprendió durante el entrenamiento.

Pueden alcanzar tamaños de miles de millones o incluso billones.

## Uso general

Los LLM pueden solucionar problemas comunes debido a los aspectos comunes del lenguaje humano, aunque las tareas específicas sean diferentes.

## Preentrenamiento y ajuste

Los LLM:

1. Se preentrenan para uso general con un conjunto de datos grande.
2. Se ajustan para objetivos específicos con un conjunto de datos más pequeño.

---

# ¿Cómo funcionan los LLM?

Cuando se envía una instrucción a un LLM, este calcula la probabilidad de la respuesta a partir de su modelo previamente entrenado.

El entrenamiento previo utiliza grandes cantidades de:

* Texto
* Imágenes
* Código

Esto permite que el modelo aprenda la estructura y los patrones subyacentes del lenguaje.

El LLM funciona de forma similar a un **autocompletado**, sugiriendo la respuesta más probable para una instrucción.

---

# Alucinaciones

A veces un LLM puede entregar una respuesta completamente incorrecta. Esto se denomina **alucinación**.

Las alucinaciones pueden ser palabras o frases que:

* No tienen sentido.
* Contienen errores gramaticales.
* Generan información incorrecta o engañosa.

Los LLM solo comprenden la información con la que fueron entrenados.

Por eso, es posible que:

* No conozcan los datos específicos de un negocio.
* No conozcan información específica de un dominio.
* No tengan acceso a información en tiempo real.
* Solo entiendan la información proporcionada explícitamente en la instrucción.
* Supongan que la información de la instrucción es verdadera.
* No puedan pedir más información de contexto.

## Factores que pueden provocar alucinaciones

* Datos insuficientes para el entrenamiento.
* Datos ruidosos o sucios.
* Falta de contexto.
* Falta de restricciones.

La ingeniería de instrucciones permite trabajar para minimizar este problema.

---

# Gemini

**Gemini** es un modelo de IA generativa que puede actuar como un colaborador siempre activo.

Puede ayudar a usuarios de Google Cloud, incluyendo:

* Desarrolladores
* Científicos de datos
* Operadores

Gemini está incorporado en muchos productos de Google Cloud.

Tiene acceso a datos como:

* Documentación de Google Cloud.
* Instructivos.
* Muestras.

Con las instrucciones correctas, puede proporcionar sugerencias y guías sobre recursos.

También puede crear comandos de `gcloud` y llevarlos a Cloud Shell.

---

# Ingeniería de instrucciones

Una **instrucción** es el texto que se entrega al modelo.

La **ingeniería de instrucciones** es la forma de articular las instrucciones para obtener la mejor respuesta del modelo.

> Cuanto mejor estructurada esté la instrucción, mejor será el resultado.

## Tipos de instrucciones

Existen cuatro categorías:

```text
Instrucciones
├── Sin ejemplos
├── Con un ejemplo
├── Con varios ejemplos
└── Instrucciones de rol
```

### Sin ejemplos

No contienen contexto o ejemplos para ayudar al modelo.

Ejemplo:

> ¿Cuál es la capital de Francia?

### Con un ejemplo

Proporcionan un ejemplo para dar contexto.

Ejemplo:

> Italia → Roma

### Con varios ejemplos

Proporcionan al menos dos ejemplos para dar contexto.

Ejemplo:

> Italia → Roma
> Japón → Tokio

### Instrucciones de rol

Proporcionan un marco de referencia que el modelo debe utilizar al responder.

Ejemplo:

> Quiero que actúes como un profesor de negocios. Te daré un término y explicarás correctamente su significado.

Este tipo de instrucción puede proporcionar un punto de referencia claro para la respuesta.

---

# Elementos de una instrucción

Una instrucción puede tener dos elementos principales:

```text
Instrucción
├── Preámbulo
└── Entrada
```

## Preámbulo

Es el texto de introducción utilizado para proporcionar instrucciones y contexto al modelo antes de la pregunta o solicitud principal.

Puede incluir:

* Contexto de la tarea.
* La tarea.
* Ejemplos.

## Entrada

Es la solicitud central que se realiza al LLM.

Ejemplo:

> Comentario: No sé qué pensar del video. La opinión es:

Según el preámbulo, Gemini puede revisar la entrada y sugerir si la opinión es:

* Positiva.
* Neutra.
* Negativa.

No todos los componentes son necesarios en una instrucción y el formato puede cambiar según la tarea.

El orden de los elementos también puede cambiar.

---

# Ejemplo de una instrucción mejorada

Una instrucción puede incluir un contexto de rol.

Ejemplo:

> Quiero que actúes como un arquitecto de nube en Google Cloud. ¿Cómo puedo usar gcloud para crear una red que use subredes IPv4 e IPv6?

También se puede continuar una interacción existente agregando más contexto:

> Quiero que actúes como un arquitecto de nube en Google Cloud. ¿Cómo ajusto el comando gcloud proporcionado para crear una subred y garantizar que sea de pila doble?

---

# Prácticas recomendadas

## 1. Escribir instrucciones detalladas y explícitas

Cuanto más vaga sea la instrucción, mayor será la posibilidad de obtener un resultado que no se pueda utilizar.

Las instrucciones deben ser:

* Claras.
* Concisas.
* Con límites definidos.

Es mejor indicar al modelo **qué hacer** en lugar de qué no hacer.

También se pueden proporcionar resultados alternativos para diferentes situaciones.

Ejemplo:

> Aún estoy aprendiendo sobre eso.

Esto puede utilizarse cuando el modelo no tenga certeza.

---

## 2. Adoptar un perfil

Agregar un perfil al modelo proporciona contexto para que se enfoque en preguntas relacionadas.

Por ejemplo:

> Eres un arquitecto de nube.

Esto puede ayudar a mejorar la exactitud de las respuestas.

---

## 3. Usar oraciones concisas

Las oraciones largas pueden producir resultados deficientes.

Es mejor dividirlas en:

* Frases más cortas.
* Tareas más sencillas.

---

# Caso de Sasha

Sasha es una arquitecta de nube que necesita crear el diseño de un prototipo de arquitectura de red de VPC de Google Cloud para **Cymbal Bank**.

Quiere combinar sus conocimientos de arquitectura de nube con herramientas de IA generativa para crear un diseño de prototipo utilizable.

Utiliza **Gemini**, disponible en la consola de Google Cloud.

## Ejemplo de instrucción

Sasha utiliza una instrucción como:

> Eres un arquitecto de nube. Deseas crear una red de VPC de Cloud que pueda administrarse centralizadamente. También te conectas a otras redes de VPC en otras regiones de tu empresa. No quieres mantener muchos conjuntos diferentes de políticas de firewall. ¿Qué tipos de arquitectura de red recomendarías?

Con esta instrucción, Gemini propone una arquitectura de **concentrador y radio** que se ajusta a sus necesidades.

Sasha puede seguir perfeccionando y cambiando las instrucciones para que Gemini responda con el enfoque y nivel de detalle correctos.

---

# Conceptos clave

| Concepto                        | Descripción                                                        |
| ------------------------------- | ------------------------------------------------------------------ |
| **IA generativa**               | Puede generar texto, imágenes y otros datos                        |
| **LLM**                         | Modelo de IA generativa enfocado en tareas de lenguaje             |
| **Parámetros**                  | Recuerdos y conocimientos aprendidos durante el entrenamiento      |
| **Alucinación**                 | Respuesta generada que puede ser incorrecta o no tener sentido     |
| **Gemini**                      | Modelo de IA generativa integrado en productos de Google Cloud     |
| **Instrucción**                 | Texto entregado al modelo                                          |
| **Ingeniería de instrucciones** | Forma de estructurar instrucciones para obtener mejores respuestas |
| **Preámbulo**                   | Texto que proporciona contexto e instrucciones                     |
| **Entrada**                     | Solicitud central realizada al modelo                              |
| **Instrucción de rol**          | Define un marco de referencia para la respuesta                    |

---

# Regla rápida

```text
IA generativa
    ↓
Genera contenido

LLM
    ↓
Se enfoca en lenguaje

Instrucción
    ↓
Texto enviado al modelo

Ingeniería de instrucciones
    ↓
Mejor estructura de la instrucción
    ↓
Mejor resultado
```
