# Compute Engine

**Compute Engine** es la solución de **IaaS (Infraestructura como servicio)** de Google Cloud.

Permite crear y ejecutar **máquinas virtuales (VMs)** sobre la infraestructura de Google Cloud.

## Máquinas virtuales

No requiere inversiones iniciales y permite ejecutar miles de CPU virtuales en un sistema diseñado para ofrecer un rendimiento rápido y constante.

Cada VM tiene la potencia y funcionalidad de un sistema operativo completo.

Puede configurarse especificando:

* CPU
* Memoria
* Almacenamiento
* Sistema operativo

```text id="m7x2qa"
VM
├── CPU
├── Memoria
├── Almacenamiento
└── Sistema operativo
```

## Crear instancias

Las instancias de VM pueden crearse mediante:

* Consola de Google Cloud
* API de Compute Engine
* Google Cloud CLI

Las instancias pueden ejecutar imágenes de:

* Linux
* Windows Server

También es posible utilizar versiones personalizadas de estas imágenes y crear imágenes de otros sistemas operativos.

---

## Cloud Marketplace

**Cloud Marketplace** ofrece soluciones de Google y de proveedores externos.

Permite comenzar rápidamente sin configurar manualmente:

* Software
* Instancias de VM
* Almacenamiento
* Redes

Estos elementos pueden modificarse antes de iniciar la solución cuando sea necesario.

La mayoría de los paquetes no tienen un costo adicional más allá de las tarifas normales por uso de los recursos de Google Cloud.

Algunas imágenes de terceros tienen tarifas adicionales por uso, especialmente aquellas que incluyen software con licencia comercial.

Antes de iniciar estas imágenes, se muestran estimaciones del cobro mensual.

---

# Precios y facturación

Para el uso de VMs, Compute Engine factura **por segundo**, con un mínimo de un minuto.

Si el uso se prolonga, se aplican automáticamente **descuentos por uso continuo**.

Cuando una VM se ejecuta durante más del **25% de un mes**, Compute Engine aplica automáticamente un descuento por cada minuto adicional.

## Descuentos por compromiso de uso

Para cargas de trabajo predecibles y estables, se puede comprar una cantidad específica de CPU virtuales y memoria con descuentos de hasta el **57%** sobre los precios normales.

El compromiso puede ser de:

```text id="a5q9kc"
1 año
o
3 años
```

---

# VMs interrumpibles y Spot

Para cargas de trabajo que no requieren que alguien espere hasta que terminen, como trabajos por lotes, se pueden utilizar **VMs interrumpibles o Spot**.

En algunos casos, permiten ahorrar hasta un **90%**.

La principal diferencia con una VM común es que Compute Engine puede finalizar el trabajo si los recursos se necesitan para otra tarea.

Por eso, el trabajo debe poder:

```text id="v4x8pn"
Detenerse
   ↓
Reiniciarse
```

### VMs interrumpibles vs. Spot

Las VMs Spot ofrecen más funciones que las VMs interrumpibles.

Por ejemplo:

| Característica             | Interrumpible | Spot       |
| -------------------------- | ------------- | ---------- |
| Tiempo máximo de ejecución | 24 horas      | Sin máximo |
| Precio                     | Igual         | Igual      |

Actualmente, el precio de ambos tipos de VM es el mismo.

---

# Almacenamiento y tipos de máquina

Compute Engine incorpora de forma predeterminada la capacidad de elegir entre almacenamiento y procesamiento sin requerir una opción o tipo de máquina específico para obtener una alta capacidad de procesamiento.

Con los **tipos personalizados de máquinas**, solo se paga por lo que se necesita.

Es posible elegir las propiedades de las instancias, como:

* Cantidad de CPU virtuales.
* Cantidad de memoria.

Se pueden utilizar:

```text id="r6w3tz"
Tipos de máquina predefinidos
          o
Tipos de máquina personalizados
```
