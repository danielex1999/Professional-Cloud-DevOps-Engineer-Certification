# Implementaciones de equipos SRE

Una vez que se tienen prácticas clave y se ha empezado a capacitar y contratar personas para los roles de SRE, se puede evaluar cómo implementar el equipo de SRE.

La implementación puede variar según:

* El tamaño de la organización.
* El lugar de la organización en el recorrido hacia la SRE.

Se clasifican las implementaciones recomendadas en **seis categorías**:

```text

                    EQUIPOS SRE
                        │
     ┌──────────────────┼──────────────────┐
     │                  │                  │
     ▼                  ▼                  ▼
Multidisciplinario  Infraestructura    Herramientas
     │                  │                  │
     ├──────────────────┼──────────────────┤
     │                  │                  │
     ▼                  ▼                  ▼
Producto/Aplicación  Integrado       Asesoramiento
```

---

# 1. Equipo SRE multidisciplinario

Este tipo de equipo suele tener un alcance no delimitado y es un buen punto de partida si es el primer equipo de SRE.

Se recomienda para organizaciones que:

* Tienen pocas aplicaciones.
* Tienen recorridos del usuario con un alcance pequeño.
* Solo requieren un equipo.
* Necesitan un equipo específico de SRE para implementar las prácticas.

## Beneficios

* No hay brechas de cobertura entre los equipos de SRE al existir un solo equipo.
* Es fácil detectar patrones y encontrar similitudes entre servicios y proyectos.
* Los SRE pueden actuar como puente entre los diferentes equipos de desarrollo.
* Pueden crear soluciones en distintas partes del software.

## Desventajas

* Generalmente no hay un estatuto del equipo de SRE o este establece que todo lo relacionado con la empresa puede entrar en su alcance.
* Esto podría sobrecargar al equipo.
* Con el aumento de la complejidad de la empresa y del sistema, el equipo puede pasar de generar un impacto muy positivo a realizar aportes más superficiales.
* Los problemas del equipo podrían afectar negativamente a toda la empresa.

---

# 2. Equipo de infraestructura

Este tipo de equipo se enfoca en tareas en segundo plano que ayudan a que el trabajo de otros equipos sea más rápido y fácil.

Trabajan en:

* Mantenimiento de servicios compartidos.
* Componentes relacionados con la infraestructura.

No se enfocan en servicios relacionados con los productos, como el código orientado al cliente.

Se recomienda para empresas con muchos equipos de desarrollo que necesiten un equipo de infraestructura para definir estándares y prácticas comunes.

Las empresas grandes suelen tener:

```text
┌──────────────────┐
│ DevOps           │
│ Se centra en     │
│ las funciones    │
└──────────────────┘

┌──────────────────┐
│ SRE              │
│ Se centra en     │
│ la confiabilidad │
└──────────────────┘
```

## Beneficios

* Permite que los desarrolladores de productos utilicen prácticas de DevOps para mantener productos orientados al usuario sin discrepancias en la empresa.
* Los SRE pueden enfocarse en brindar una infraestructura muy confiable.
* Pueden definir estándares de producción como código.
* Pueden aplicar mejoras que simplifiquen las tareas de los desarrolladores de productos que ejecutan sus propios servicios.

## Desventajas

* Según el alcance de la infraestructura, los problemas del equipo podrían afectar negativamente a toda la empresa.
* La falta de contacto directo con los clientes puede generar un énfasis en mejoras de infraestructura que no necesariamente estén asociadas con la experiencia de los clientes.
* Cuando aumenta la complejidad, puede ser necesario dividir los equipos de infraestructura.
* Esto puede generar duplicación de la infraestructura base o divergencias en las prácticas.
* Puede limitar los conocimientos compartidos y la movilidad.
* Puede resultar ineficiente.

---

# 3. Equipo de herramientas

Este equipo se centra en crear software que ayude a los desarrolladores a:

* Medir la confiabilidad.
* Mantener la confiabilidad.
* Mejorar la confiabilidad del sistema.
* Trabajar en otros aspectos de SRE, como la planificación de la capacidad.

## Recomendación

Este tipo de equipo se recomienda para organizaciones que necesiten herramientas muy especializadas relacionadas con la confiabilidad.

## Riesgos y desventajas

Estos equipos pueden correr el riesgo de resolver los problemas incorrectos de la empresa.

Por eso, deben estar atentos a los problemas prácticos en los que trabajan los equipos de confiabilidad de primera línea.

Las desventajas son similares a las de los equipos de infraestructura.

Además:

* No deben convertirse involuntariamente en un equipo de infraestructura.
* No deben generar un incremento del trabajo repetitivo.
* No deben incrementar la carga de trabajo general.

Por lo general, esto se resuelve mediante un **estatuto del equipo aprobado por los líderes de la empresa**.

---

# 4. Equipo de producto/aplicación

Este tipo de equipo de SRE trabaja para mejorar la confiabilidad de una aplicación o área de negocio fundamental.

Se recomienda para organizaciones que ya cuenten con un equipo:

* Multidisciplinario.
* De infraestructura.
* De herramientas.

Y que además tengan una aplicación clave para usuarios con necesidades de alta confiabilidad.

Estas características justifican el gasto relativamente alto de contar con un grupo dedicado de SRE.

## Beneficio

Los esfuerzos del equipo tienen un enfoque claro y las prioridades de la empresa y los esfuerzos del equipo se vinculan directamente.

## Desventajas

Con el aumento de la complejidad de la empresa y del sistema:

* La organización necesitará nuevos equipos de producto/aplicación.
* Puede duplicarse la infraestructura base.
* Pueden generarse divergencias entre las prácticas.
* Puede limitarse el conocimiento compartido.
* Puede limitarse la movilidad.
* Puede resultar ineficiente.

---

# 5. Equipos integrados

Estos equipos tienen SRE integrados con sus pares desarrolladores, generalmente uno en cada equipo de desarrollo.

Los SRE integrados:

* Pueden compartir oficina con un desarrollador.
* También pueden trabajar de forma remota.
* Su relación laboral con los desarrolladores suele ser por proyecto o por tiempo.

Durante su participación suelen realizar tareas prácticas como:

* Modificar código.
* Modificar la configuración de los servicios dentro del alcance.

## ¿Cuándo utilizar este modelo?

Se recomienda para:

* Comenzar con una función de SRE.
* Escalar otra implementación.
* Proyectos o equipos que necesitan SRE durante un tiempo.

También puede aumentar el impacto del equipo de herramientas o infraestructura al impulsar la adopción.

## Beneficios

* Orienta conocimientos expertos de SRE hacia problemas o equipos específicos.
* Permite realizar demostraciones paralelas de las prácticas de SRE.
* Puede ser un método de capacitación eficaz.

## Desventajas

* Puede generar falta de estandarización entre los equipos.
* Puede generar discrepancias en las prácticas.
* Los SRE podrían tener poco tiempo con sus pares para asesorarlos.

---

# 6. Equipo de asesoramiento

Esta implementación es similar a la implementación integrada, pero los SRE suelen realizar menos tareas prácticas.

Los SRE suelen evitar modificar:

* El código.
* La configuración de los servicios.
* Los servicios dentro del alcance del cliente.

Sin embargo, pueden escribir código y configuración para compilar y mantener:

* Sus herramientas.
* Las herramientas de los desarrolladores.

Esto representa un híbrido entre los equipos de asesoramiento y de herramientas.

## ¿Cuándo utilizar este modelo?

Se recomienda esperar hasta que:

* La organización o su complejidad sean importantes.
* Las demandas hayan superado lo que pueden manejar los equipos de SRE existentes.

También se recomienda contratar **uno o dos asesores a tiempo parcial** antes de formar el primer equipo de SRE.

## Beneficio

El equipo de asesoramiento puede escalar el impacto positivo de un equipo de SRE existente al estar desligado de modificar directamente el código y la configuración.

## Desventajas

* A los asesores puede faltarles contexto suficiente para ofrecer consejos útiles.
* Existe el riesgo de que se los perciba como poco involucrados.
* No modifican el código ni la configuración, incluso cuando pueden generar un impacto técnico indirecto.

---

# Comparación de implementaciones

| Implementación          | Enfoque                                                                            |
| ----------------------- | ---------------------------------------------------------------------------------- |
| **Multidisciplinario**  | Prácticas de SRE para diferentes servicios y proyectos.                            |
| **Infraestructura**     | Servicios compartidos, infraestructura, estándares y prácticas comunes.            |
| **Herramientas**        | Software y herramientas relacionadas con la confiabilidad.                         |
| **Producto/Aplicación** | Confiabilidad de una aplicación o área de negocio fundamental.                     |
| **Integrado**           | SRE integrado con equipos de desarrollo durante proyectos o períodos determinados. |
| **Asesoramiento**       | Asesoramiento especializado con menos tareas prácticas.                            |

---

# Evaluación antes de formar un equipo SRE

Es importante evaluar:

```text
        MADUREZ DE LA ORGANIZACIÓN
                    │
                    ▼
          Identificar necesidades
                    │
                    ▼
       Identificar áreas de capacitación
                    │
                    ▼
          Evaluar implementación
                    │
                    ▼
             Equipo SRE
```

Antes de armar un primer equipo, es importante:

* Evaluar la madurez de la organización para adoptar SRE.
* Identificar áreas de capacitación.
* Evaluar qué implementación puede adaptarse a la organización.
