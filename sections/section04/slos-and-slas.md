# Selección de SLO y relación con SLA

La **relevancia de los SLO** es fundamental. Los objetivos deben ayudar a mejorar la experiencia del usuario.

Es fácil definir SLO basándose en lo que resulta sencillo de medir en lugar de aquello que realmente es útil.

## Características de un SLO

Para que un SLO sea claro, debe especificar:

* Cómo se mide.
* En qué condiciones es válido.

Por ejemplo:

> Disponibilidad medida mediante un uptime check de 10 segundos, agregada por minuto.

---

# Objetivos de disponibilidad

No es realista ni conveniente establecer un objetivo del **100%**.

Un objetivo del 100% puede generar:

* Soluciones costosas.
* Diseños demasiado conservadores.
* Mayor complejidad.
* Un objetivo que aun así puede ser difícil de alcanzar.

Es mejor realizar un seguimiento de la frecuencia con la que se incumplen los SLO y trabajar para mejorarla.

En muchos casos, una disponibilidad del **99%** puede ser suficiente y más sencilla de alcanzar.

También puede resultar más rentable.

---

# Considerar el caso de uso

Los SLO deben definirse teniendo en cuenta el uso real del servicio.

Por ejemplo, para un servicio HTTP de carga de fotografías:

> 99% de las cargas deben completarse en menos de 100 ms, agregadas por minuto.

Esto puede ser poco realista o innecesario si la mayoría de los usuarios utilizan teléfonos móviles.

En ese caso, un SLO del **80%** puede ser más alcanzable y suficiente.

---

# Múltiples SLO

En algunos casos es conveniente definir varios SLO para representar diferentes niveles de rendimiento.

Por ejemplo:

```text
90% de las solicitudes HTTP GET < 50 ms

99% de las solicitudes HTTP GET < 100 ms

99.9% de las solicitudes HTTP GET < 500 ms
```

Esto permite representar mejor la forma de la curva de rendimiento.

---

# SLO y decisiones de negocio

La selección de SLO tiene implicaciones de producto y de negocio.

Se deben considerar restricciones como:

* Personal.
* Tiempo de lanzamiento.
* Presupuesto.

El objetivo es **mantener satisfechos a los usuarios**, no establecer un SLO que requiera esfuerzos extraordinarios para mantenerse.

---

# Recomendaciones para seleccionar SLO

## 1. Mantenerlos simples

Los SLI demasiado complejos pueden ocultar cambios importantes en el rendimiento.

## 2. Evitar valores absolutos

Un objetivo de disponibilidad del **100%** no es realista.

Además, puede aumentar:

* Tiempo de desarrollo.
* Complejidad.
* Costos operativos.

## 3. Minimizar la cantidad de SLO

Un error común es definir demasiados SLO.

La recomendación es tener únicamente los necesarios para cubrir los atributos principales del sistema.

## 4. No establecerlos demasiado altos

Es mejor comenzar con SLO más bajos y ajustarlos con el tiempo a medida que se aprende sobre el sistema.

Esto evita definir objetivos inalcanzables que requieran demasiado esfuerzo y costo.

---

# Buenas prácticas

Los buenos SLO deben:

* Reflejar lo que les importa a los usuarios.
* Servir como una guía para los equipos de desarrollo.
* Evitar objetivos demasiado ambiciosos.
* Evitar objetivos demasiado relajados.

Un SLO demasiado ambicioso puede generar trabajo innecesario.

Un SLO demasiado relajado puede resultar en un producto deficiente.

---

# SLA

Un **SLA (Service Level Agreement)** es un contrato comercial entre el proveedor del servicio y el cliente.

Si el proveedor no mantiene los niveles acordados, puede existir una penalización.

No todos los servicios tienen un SLA, pero **todos los servicios deberían tener SLO**.

Los SLA deben establecerse de forma conservadora porque son difíciles de cambiar o eliminar cuando proporcionan poco valor o generan mucho trabajo.

Además, pueden tener implicaciones financieras mediante compensaciones al cliente.

---

# Relación entre SLO y SLA

El umbral del **SLA debe ser inferior al SLO**.

```text
SLO
 ↓
Margen de seguridad
 ↓
SLA
```

Esto permite tomar acciones antes de que se produzca un incumplimiento del SLA.

---

# SLI, SLO y SLA

Comprender la relación entre estos tres conceptos es fundamental.

```text
SLI → Cómo se mide el servicio

SLO → Qué objetivo debe alcanzar la medición

SLA → Qué se acuerda con el cliente y qué ocurre si no se cumple
```

---

# Problemas por mediciones inconsistentes

Puede ocurrir que el equipo de SRE considere que el SLO se está cumpliendo mientras el SLA de un usuario realmente se está incumpliendo.

Esto puede ocurrir por diferentes motivos.

## 1. Medición inconsistente del SLI

Por ejemplo:

**SLO:**

> Latencia promedio ≤ 200 ms

**SLA:**

> Percentil 99 de latencia > 300 ms genera compensación.

El promedio puede ocultar problemas de rendimiento para un grupo de usuarios.

Ejemplo:

```text
99% de solicitudes → Muy rápidas
1% de solicitudes  → Extremadamente lentas
```

El promedio puede seguir siendo bueno aunque ese 1% incumpla el SLA basado en el percentil 99.

---

## 2. Diferentes ventanas de medición

El SLO puede calcularse sobre un período amplio:

> Promedio diario.

Mientras que el SLA puede utilizar períodos más cortos:

> Cualquier minuto individual.

Un aumento breve de latencia puede incumplir un SLA sin afectar significativamente el promedio del SLO a largo plazo.

---

## 3. Diferencia de alcance

El SLO puede medir el rendimiento agregado de todos los usuarios.

El SLA normalmente representa un compromiso con usuarios individuales.

Por lo tanto:

```text
Rendimiento general
        ↓
Puede cumplir el SLO

Usuario específico
        ↓
Puede experimentar degradación
        ↓
Puede incumplir su SLA
```

---

# Cómo evitar discrepancias

Para evitar estas diferencias, el **SLI, SLO y SLA** deben diseñarse utilizando:

* Métricas consistentes.
* Métodos de medición consistentes.
* Alcance consistente.

Además:

> **Los SLO deben ser siempre más estrictos que los SLA.**

Esto proporciona un margen para actuar antes de que se incumpla un SLA.
