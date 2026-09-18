# Escalado y Balanceo en Compute Engine

Con **Compute Engine** puedes elegir las propiedades de máquina más apropiadas para tus instancias, como:

* CPU virtuales
* Memoria

Puedes utilizar tipos de máquina predefinidos o crear tipos personalizados.

## Escalado automático

Compute Engine cuenta con una función de **escalado automático** que permite agregar o quitar VMs de una aplicación según las métricas de carga.

```text id="k4p7mz"
Mayor carga
    ↓
Agregar VMs
    ↓
Distribuir tráfico

Menor carga
    ↓
Quitar VMs
```

Este proceso también implica **balancear el tráfico entrante** entre las VMs.

La **VPC de Google** admite diferentes tipos de balanceo de cargas.

## Escalado horizontal y vertical

Compute Engine permite configurar VMs de gran tamaño, que pueden ser adecuadas para:

* Cargas de trabajo de bases de datos en memoria.
* Análisis con uso intensivo de CPU.

Sin embargo, la mayoría de los clientes comienzan escalando **horizontalmente** en lugar de verticalmente.

```text id="n8x3qa"
Escalado vertical
VM pequeña → VM más grande

Escalado horizontal
1 VM → 2 VMs → 3 VMs → ...
```

## Límite de CPU

La cantidad máxima de CPU por VM depende de:

* La **familia de máquina**.
* La **cuota disponible** del usuario.
* La **zona** donde se ejecuta la VM.

### Referencia

Especificaciones de los tipos de máquinas de VM:

`cloud.google.com/compute/docs/machine-types`
