# Contenedores

## ¿Qué son?

Un contenedor es una unidad ligera que empaqueta:

- Código
- Dependencias
- Entorno necesario para ejecutar una aplicación

A diferencia de una VM, el contenedor **no necesita un sistema operativo completo propio**.

## VM vs Contenedor

| VM | Contenedor |
|---|---|
| Virtualiza hardware | Virtualiza el SO |
| Incluye SO completo | Comparte el kernel |
| Más pesado | Más ligero |
| Inicio más lento | Inicio rápido |
| Mayor consumo de recursos | Menor consumo |
| Menos portátil | Muy portátil |

### Idea clave

**VM → cada aplicación puede tener su propio SO**

**Contenedor → varias aplicaciones comparten el kernel**

## Ventajas

- Inicio en segundos
- Escalamiento rápido
- Menor consumo de recursos
- Alta portabilidad
- Facilita pasar de desarrollo → pruebas → producción
- Ideal para microservicios

## Contenedores y microservicios

Una aplicación puede dividirse en varios contenedores:

```text
Aplicación
├── Contenedor Web
├── Contenedor API
├── Contenedor Usuarios
└── Contenedor Pagos