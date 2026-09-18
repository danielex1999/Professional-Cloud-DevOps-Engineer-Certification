# Redes VPC en Google Cloud

En esta sección se explora cómo funciona **Compute Engine**, enfocándose en las redes virtuales.

Cuando comienzan a usar Cloud, muchos usuarios definen su propia **nube privada virtual (VPC)** en su primer proyecto o utilizan la VPC predeterminada.

## ¿Qué es una VPC?

Una **VPC (Virtual Private Cloud)** es un modelo privado, individual y seguro de computación en la nube alojado dentro de una nube pública como Google Cloud.

Permite:

* Ejecutar código.
* Almacenar datos.
* Alojar sitios web.

Las VPC combinan la **escalabilidad y conveniencia** de la nube pública con el **aislamiento de datos** de la nube privada.

---

## Redes VPC

Las redes VPC conectan los recursos de Google Cloud entre sí y con Internet.

Permiten:

* Segmentar redes.
* Utilizar reglas de firewall para restringir el acceso a instancias.
* Crear rutas estáticas para reenviar tráfico a destinos específicos.

### VPC globales

Una característica importante de las redes VPC de Google es que son **globales**.

Una VPC puede tener subredes en diferentes regiones de Cloud:

```text id="m2v8qx"
VPC
├── Subred → us-east1
└── Subred → asia-east1
```

Las **subredes** son porciones segmentadas de una red más grande y abarcan las zonas que forman una región.

Esto facilita la creación de diseños de red con alcance global.

---

## Subredes

Los recursos pueden estar en diferentes zonas de una misma subred.

También es posible ampliar el tamaño de una subred aumentando el rango de direcciones IP asignadas.

Esto **no afecta a las máquinas virtuales que ya están configuradas**.

---

## Ejemplo

Supongamos una red VPC llamada `vpc1` con dos subredes:

```text id="q7x3ka"
vpc1
├── us-east1
└── asia-east1
```

Si la VPC tiene tres VMs de Compute Engine conectadas a ella, pueden compartir la misma subred incluso si están ubicadas en diferentes zonas.

```text id="r8n4vz"
             VPC: vpc1
                  │
              Subred
        ┌─────────┼─────────┐
        ↓         ↓         ↓
       VM1       VM2       VM3
     Zona A     Zona B    Zona C
```

Esta capacidad permite crear **soluciones resilientes ante interrupciones** manteniendo un diseño de red sencillo.
