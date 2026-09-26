# Requisitos, Roles e Historias de Usuario

## Requisitos

Para definir los requisitos de un sistema, es útil que el arquitecto de nube responda cinco preguntas:

```text
Quiénes
Qué
Por qué
Cuándo
Cómo
```

### Quiénes

Permite determinar:

* Usuarios del sistema.
* Desarrolladores.
* Partes interesadas.

El objetivo es obtener un panorama completo de las personas que serán afectadas por el sistema, directa o indirectamente.

### Qué

Permite establecer las principales áreas de funcionalidad requeridas de forma clara y sin ambigüedades.

### Por qué

Permite entender:

* Qué problema busca solucionar el sistema.
* Por qué es necesario.

También ayuda a definir:

* KPI.
* SLO.
* ANS.

### Cuándo

Ayuda a:

* Determinar un cronograma realista.
* Limitar el alcance.

### Cómo

Permite determinar muchos de los requisitos no funcionales.

Algunos ejemplos:

* Cantidad de usuarios simultáneos.
* Tamaño promedio de la carga útil de las solicitudes.
* Requisitos de latencia.
* Ubicación de los usuarios.

Estos requisitos influyen en la solución que diseñará el arquitecto de nube.

---

# Roles de usuario

Los **roles** representan el objetivo de un usuario en un momento determinado y permiten analizar un requisito dentro de un contexto.

Un rol no necesariamente representa a una persona.

También puede representar a otro sistema, como un cliente de un microservicio que accede a otro microservicio.

El rol debe describir el objetivo del usuario cuando utiliza el sistema.

### Ejemplo

En una aplicación de comercio electrónico:

```text
Rol: Comprador
Objetivo: Realizar una compra
```

---

# Identificación de roles

Un proceso para determinar los roles consiste en:

```text
1. Intercambiar ideas
        ↓
2. Organizar
        ↓
3. Consolidar
        ↓
4. Definir
```

### 1. Intercambiar ideas

Crear un conjunto inicial de roles.

Cada rol debe representar a un solo usuario.

### 2. Organizar

Identificar:

* Roles que se superponen.
* Roles relacionados.

Luego agruparlos.

### 3. Consolidar

Resumir los roles y eliminar duplicados.

### 4. Definir

Definir mejor los roles, incluyendo:

* Roles internos.
* Roles externos.
* Diferentes patrones de usuarios.
* Nivel de experiencia en el dominio.
* Frecuencia de uso del software.

---

# Arquetipos

Un **arquetipo** es una representación imaginaria de un rol de usuario.

Su objetivo es ayudar al arquitecto y a los desarrolladores a considerar las características de los usuarios de forma más personalizada.

Un rol puede tener varios arquetipos.

### Ejemplo

En una aplicación bancaria:

**Jacinta** es madre y trabajadora, y tiene poco tiempo disponible.

Sus objetivos incluyen:

* Ahorrar tiempo.
* Ahorrar dinero.
* Realizar operaciones bancarias estándar en línea.
* Obtener beneficios como devoluciones de dinero.

El arquetipo proporciona un panorama más completo de los requisitos.

Por ejemplo, el deseo de ahorrar tiempo puede indicar que una tarea debería automatizarse, lo que influye en la latencia y en el diseño del servicio.

---

# Historias de usuario

Las **historias de usuario** describen lo que los usuarios desean que haga el sistema.

Un formato común es:

> Como tipo de usuario, deseo hacer algo para obtener algún beneficio.

Otro formato es:

> Según este contexto, cuando hago algo, debería ocurrir esto.

## Estructura

Cada historia debe comenzar con un título que describa su propósito.

Después se agrega una descripción concisa de una línea.

Esta descripción debe indicar:

```text
Rol
 ↓
Qué desea hacer
 ↓
Por qué
```

### Ejemplo

**Título:** Consulta de saldo

> Como titular de la cuenta, deseo consultar mi saldo disponible en cualquier momento del día para asegurarme de no sobregirar la cuenta.

Las historias permiten acordar claramente los requisitos con el cliente o usuario final.

---

# Criterios INVEST

Los criterios **INVEST** permiten evaluar la calidad de las historias de usuario.

| Letra | Concepto      | Descripción                                                                                                        |
| ----- | ------------- | ------------------------------------------------------------------------------------------------------------------ |
| **I** | Independiente | Debe ser independiente para evitar problemas de priorización y planificación.                                      |
| **N** | Negociable    | No es un contrato escrito; fomenta conversaciones entre cliente y desarrolladores hasta llegar a un acuerdo claro. |
| **V** | Valor         | Debe proporcionar valor a los usuarios y enfocarse en resultados e impacto.                                        |
| **E** | Estimable     | Debe poder estimarse. Si no, pueden faltar detalles o ser demasiado larga.                                         |
| **S** | Simple        | Debe ser simple para limitar el alcance, reducir la ambigüedad y facilitar los comentarios.                        |
| **T** | Testeable     | Debe poder comprobarse para verificar que se implementó correctamente y que se cumplieron los requisitos.          |

---

# Resumen

```text
Requisitos
    ↓
Quiénes + Qué + Por qué + Cuándo + Cómo
    ↓
Roles de usuario
    ↓
Arquetipos
    ↓
Historias de usuario
    ↓
Criterios INVEST
```

## Para recordar

* **Rol:** objetivo de un usuario dentro de un contexto.
* **Arquetipo:** representación imaginaria de un rol.
* **Historia de usuario:** describe lo que el usuario desea hacer y por qué.
* **INVEST:** criterios para evaluar la calidad de una historia.
