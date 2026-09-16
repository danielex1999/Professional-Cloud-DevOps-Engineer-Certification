# Precios, Presupuestos y Cuotas en Google Cloud

## Facturación

Google fue uno de los primeros en ofrecer **facturación por segundo** para su oferta de infraestructura como servicio, **Compute Engine**.

Actualmente, también se ofrece facturación por segundo en:

* **Google Kubernetes Engine (GKE)**
* **Dataproc**
* **VMs del entorno flexible de App Engine**

## Compute Engine

Compute Engine ofrece **descuentos por uso continuo**, aplicados automáticamente al ejecutar una instancia de VM durante gran parte del mes de facturación.

Cuando ejecutas una instancia por más del **25% de un mes**, Compute Engine aplica un descuento automático por cada minuto incremental de uso.

### VMs personalizadas

Los tipos de VMs personalizados permiten ajustar:

* CPU virtual
* Memoria

Esto permite adaptar las VMs a las necesidades de las aplicaciones y las cargas de trabajo.

---

## Calculadora de precios

Google Cloud ofrece una **calculadora de precios en línea** para estimar los costos.

`cloud.google.com/products/calculator`

---

## Presupuestos y alertas

Para evitar acumular accidentalmente una factura grande, puedes definir **presupuestos**:

* A nivel de cuenta de facturación.
* A nivel de proyecto.

Un presupuesto puede ser:

* Un límite fijo.
* Asociado a otra métrica, como un porcentaje del gasto del mes anterior.

También puedes configurar **alertas** para recibir una notificación cuando se alcance determinado porcentaje del presupuesto.

### Ejemplo

Si el presupuesto es de **$20,000** y configuras una alerta al **90%**:

```text
Presupuesto: $20,000
       ↓
90%
       ↓
Alerta en $18,000
```

Las alertas suelen definirse en:

```text
50% → 90% → 100%
```

También pueden personalizarse.

---

## Informes

Los **informes** son una herramienta de la consola de Cloud que permite supervisar los gastos de:

* Un proyecto.
* Servicios.

---

# Cuotas

Google Cloud utiliza **cuotas** para evitar el consumo excesivo de recursos por error o por un ataque malicioso.

También ayudan a proteger a los propietarios de las cuentas y a toda la comunidad de Google Cloud.

Existen dos tipos de cuotas:

```text
Cuotas
├── Cuotas de frecuencia
└── Cuotas de asignación
```

Ambas se aplican a nivel de **proyecto**.

### Cuotas de frecuencia

Se restablecen después de un período específico.

Por ejemplo, de forma predeterminada, **GKE** aplica una cuota de:

```text
3,000 llamadas a la API
por proyecto
cada 100 segundos
```

Una vez transcurrido ese período, el límite se restablece.

### Cuotas de asignación

Controlan la cantidad de recursos disponibles en los proyectos.

Por ejemplo, cada proyecto de Cloud tiene una cuota predeterminada de hasta:

```text
15 redes de nube privada virtual
```

Todos los proyectos comienzan con las mismas cuotas, pero se puede solicitar un aumento para algunas de ellas al equipo de **Asistencia de Google Cloud**.
