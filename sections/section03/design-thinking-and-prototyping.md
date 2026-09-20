# Design Thinking y prototipado en SRE

Cuando reduces el costo de las fallas mediante prácticas de cambio gradual como **CI/CD** y **versiones Canary**, los equipos pueden ser más innovadores.

> Saber que los cambios se probarán permite que las personas se atrevan a pensar en grande y no limiten su creatividad ni sus ideas.

Por eso, el **Design Thinking** y el **prototipado** son aspectos clave de la cultura organizativa de la SRE.

---

## Design Thinking

El **Design Thinking** es un enfoque que combina la **creatividad** y la **estructura** para resolver problemas complejos.

Google usa el Design Thinking como método para capacitar a los equipos y las personas en el pensamiento creativo, un paso importante en el proceso de innovación.

### Las 5 fases

```text
┌─────────────┐
│ 1. Empatizar│
└──────┬──────┘
       ↓
┌─────────────┐
│ 2. Definir  │
└──────┬──────┘
       ↓
┌─────────────┐
│ 3. Ideación │
└──────┬──────┘
       ↓
┌─────────────┐
│4. Prototipar│
└──────┬──────┘
       ↓
┌─────────────┐
│  5. Probar  │
└─────────────┘
```

### 1. Empatizar

Observa e interactúa con los **usuarios objetivo** para obtener más información sobre ellos y sumergirte en sus entornos.

La empatía ayuda a dejar de lado las suposiciones para conocer a los usuarios y sus necesidades.

### 2. Definir

Define el problema que buscas resolver.

Expresa el problema desde el **punto de vista del usuario**, en comparación con lo que buscas lograr.

### 3. Ideación

Una vez definido el problema, comienza a generar ideas de soluciones.

> Este es el momento de pensar de forma original.

### 4. Prototipado

Haz que las ideas que nacen en tu mente pasen al mundo real.

Esta fase debe ser **experimental**, para identificar la mejor solución posible antes de comprometerte.

### 5. Probar

Prueba tus prototipos de soluciones en un **entorno del mundo real** con los usuarios objetivo.

---

## Design Thinking aplicado al desarrollo de software

Desde el punto de vista del desarrollo de software:

```text
Usuario
   ↓
Pensamiento 10x
   ↓
Ideas
   ↓
Prototipo
   ↓
Prueba gradual
```

Primero deberías enfocarte en el **usuario** y poner en práctica el **"pensamiento 10x"**.

Luego:

* Intercambiar ideas sobre la solución.
* Crear un prototipo.
* Probarla de forma gradual con prácticas de SRE como **CI/CD** y **versiones Canary**.

Este enfoque incentiva a los equipos a pensar en lo que están intentando resolver desde la perspectiva del usuario.

---

## Importancia del prototipado

Fomentar el prototipado es muy importante para las organizaciones con equipos de SRE.

### Sin prototipado

Se prueban menos ideas.

```text
Menos ideas
    ↓
Errores más lentos
    ↓
Menos casos de éxito
```

### Con una cultura de prototipado

Se incentiva a los equipos a probar más ideas.

```text
Más ideas
    ↓
Errores más rápidos
    ↓
Más casos de éxito
```

---

## Formas de hacer prototipos

No existe una única forma correcta de hacer prototipos.

| Tipo                   | Descripción                                                                          |
| ---------------------- | ------------------------------------------------------------------------------------ |
| **Prototipado físico** | Compila un modelo con legos o con otros bloques pequeños.                            |
| **Dibujo en papel**    | Usa lápiz y papel para hacer un esquema de tus ideas.                                |
| **Prototipo digital**  | Crea una solución digital con software que simule la solución.                       |
| **Juego de roles**     | Invita a otras personas a asumir el papel de verificadores para probar el prototipo. |
| **Video**              | Graba la solución para ver cómo los usuarios interactúan con ella.                   |

---

## Características del prototipado

Independientemente del prototipado que uses, trata de que les resulte **realista a los usuarios**.

> Los prototipos más concretos aumentan el porcentaje de comentarios prácticos.

En Google, gracias a las interacciones de sus clientes, aprendieron que con la ayuda de **prototipos simples** los clientes pueden mejorar hasta los procesos más complejos.

Los prototipos incentivan el pensamiento creativo y estimulan a las personas a tener ideas audaces que posiblemente no tendrían desde sus escritorios o en una reunión habitual.

### Ejemplos

* Paneles de debate.
* Videos.
* Mapas de calor.
* Banners con notas.

---

## Caso de aplicación

Una de las tiendas en línea más importantes de **Países Bajos** usa la metodología de Design Thinking para intercambiar ideas sobre cambios en el proceso de producción.

### Proceso de prototipado

Los participantes utilizan **vasos descartables** para representar cada paso del proceso.

Los vasos de diferentes colores permiten identificar:

* Pasos que se deben mejorar.
* Pasos que se deben descartar.

---

## Design Thinking + Prototipado + SRE

```text
          DESIGN THINKING
                 │
                 ▼
        ┌─────────────────┐
        │   Comprender    │
        │    al usuario   │
        └────────┬────────┘
                 ↓
        ┌─────────────────┐
        │ Generar ideas   │
        └────────┬────────┘
                 ↓
        ┌─────────────────┐
        │   Prototipar    │
        └────────┬────────┘
                 ↓
        ┌─────────────────┐
        │     Probar      │
        └────────┬────────┘
                 ↓
          PRÁCTICAS SRE
        ┌─────────────────┐
        │      CI/CD      │
        │  Versiones      │
        │     Canary      │
        └─────────────────┘
```

Tus equipos necesitarán de tu participación para **promover e incentivar esta cultura**.
