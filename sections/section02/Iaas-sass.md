# Modelos de Servicio en la Nube

El uso de centros de datos virtualizados presentó dos nuevos tipos de ofertas:

```text
IaaS → Infraestructura como servicio
PaaS → Plataforma como servicio
```

## IaaS — Infraestructura como servicio

Las ofertas de **IaaS** brindan:

* Computación sin procesar
* Almacenamiento
* Redes

Estos recursos están organizados de forma similar a los centros de datos físicos.

**Ejemplo:** `Compute Engine` de Google Cloud.

En el modelo IaaS, los clientes pagan por los **recursos que asignan por adelantado**.

---

## PaaS — Plataforma como servicio

Las ofertas de **PaaS** vinculan el código a bibliotecas con acceso a la infraestructura que la aplicación necesita.

Esto permite centrar más recursos en la **lógica de la aplicación**.

**Ejemplo:** `App Engine` de Google Cloud.

En el modelo PaaS, los clientes pagan por los **recursos que realmente usan**.

---

## Evolución de la nube

Con la evolución de la computación en la nube, el foco cambió hacia:

```text
Infraestructura
      ↓
Servicios administrados
      ↓
Mayor enfoque en los objetivos comerciales
```

Las empresas pueden aprovechar recursos y servicios administrados, reduciendo el tiempo y dinero dedicado a crear y mantener su infraestructura técnica.

También pueden entregar productos y servicios a sus clientes de forma más rápida y confiable.

---

## Tecnología sin servidores

La tecnología **sin servidores** es un paso más en la evolución de la computación en la nube.

Permite que los desarrolladores se centren en su código en lugar de la configuración del servidor, ya que elimina la necesidad de administrar la infraestructura.

### Google Cloud

Entre las tecnologías sin servidores de Google se encuentran:

| Servicio                | Descripción                                                                                                                   |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Cloud Run**           | Permite implementar aplicaciones basadas en microservicios alojados en contenedores en un entorno completamente administrado. |
| **Cloud Run Functions** | Usa código basado en eventos como un servicio de pago por uso.                                                                |

---

## SaaS — Software como servicio

El **SaaS** proporciona toda la pila de aplicaciones y entrega una aplicación completa basada en la nube para que los clientes accedan y usen.

Las aplicaciones SaaS:

* No están instaladas en la computadora local.
* Se ejecutan en la nube como un servicio.
* Los usuarios finales las consumen directamente por Internet.

### Ejemplos

Aplicaciones de Google que forman parte de **Google Workspace**:

```text
Gmail
Documentos
Drive
```

Estas son ejemplos de **SaaS**.
