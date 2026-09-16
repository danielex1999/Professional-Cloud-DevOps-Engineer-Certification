# Formas de Acceder a Google Cloud

Existen cuatro maneras de acceder a Google Cloud e interactuar con sus recursos:

```text id="m8k2qp"
Google Cloud
├── Consola de Cloud
├── SDK de Cloud y Cloud Shell
├── APIs
└── App de Google Cloud
```

## 1. Consola de Cloud

La **Consola de Cloud** es la interfaz gráfica de usuario (GUI) de Google Cloud.

Permite:

* Implementar y escalar recursos.
* Diagnosticar desafíos de producción.
* Encontrar recursos.
* Verificar su estado.
* Administrar recursos.
* Definir presupuestos.
* Controlar gastos.
* Buscar recursos.
* Conectarse mediante SSH desde el navegador.

---

## 2. SDK de Cloud y Cloud Shell

### SDK de Cloud

El **SDK de Cloud** es un conjunto de herramientas para administrar recursos y aplicaciones alojadas en Google Cloud.

Incluye:

* **Google Cloud CLI**: interfaz de línea de comandos principal para productos y servicios de Cloud.
* **bq**: herramienta de línea de comandos de BigQuery.

Cuando se instalan, las herramientas del SDK de Cloud se encuentran en el directorio `bin`.

### Cloud Shell

**Cloud Shell** proporciona acceso mediante línea de comandos a los recursos de la nube desde un navegador.

Es una VM basada en **Debian** con un directorio principal persistente de **5 GB**.

Con Cloud Shell, `gcloud` y otras utilidades están:

```text id="d7n5kr"
Instaladas
   ↓
Disponibles
   ↓
Actualizadas
   ↓
Autenticadas
```

---

## 3. APIs

Los servicios de Google Cloud ofrecen **APIs** para que el código pueda controlarlos.

La Consola de Cloud incluye el **Explorador de APIs de Google**, que permite:

* Ver las APIs disponibles.
* Consultar sus versiones.
* Probar las APIs.
* Probar APIs que requieren autenticación de usuario.

### Bibliotecas cliente

Google proporciona bibliotecas cliente para facilitar el uso de Google Cloud desde código.

Lenguajes incluidos:

```text id="x2q6mn"
Java
Python
PHP
C#
Go
Node.js
Ruby
C++
```

---

## 4. App de Google Cloud

La **app de Google Cloud** permite administrar recursos desde dispositivos móviles.

Con ella puedes:

### Compute Engine

* Iniciar instancias.
* Detener instancias.
* Conectarte mediante SSH.
* Ver registros de cada instancia.

### Cloud SQL

* Iniciar instancias.
* Detener instancias.

### App Engine

* Administrar aplicaciones implementadas.
* Ver errores.
* Revertir implementaciones.
* Cambiar divisiones del tráfico.

### Facturación

La aplicación proporciona:

* Datos de facturación actualizados.
* Alertas de facturación para proyectos que superan el presupuesto.

### Métricas

Permite configurar gráficos personalizables con métricas como:

* Uso de CPU.
* Uso de red.
* Solicitudes por segundo.
* Errores de servidor.

También ofrece:

* Administración de incidentes.
* Alertas.

## Descarga

`cloud.google.com/app`
