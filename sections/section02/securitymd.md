# Seguridad en Google Cloud

Nueve de los servicios de Google tienen más de mil millones de usuarios cada uno, por lo que la seguridad es una parte importante de su infraestructura.

La seguridad se explica mediante **capas progresivas**:

```text
Seguridad física
      ↓
Hardware
      ↓
Servicios
      ↓
Identidad
      ↓
Almacenamiento
      ↓
Internet
      ↓
Seguridad operativa
```

## Hardware

Esta capa cuenta con tres características principales:

### Diseño y origen del hardware

Google diseña las placas de servidor y los equipos de redes de sus centros de datos.

También diseña chips personalizados, incluido un **chip de seguridad de hardware**.

### Arranque seguro

Las máquinas de servidores utilizan tecnologías para garantizar que inicien la pila de software correcta.

Se utilizan firmas criptográficas para:

* BIOS
* Bootloader
* Kernel
* Imagen del sistema operativo base

### Seguridad de las instalaciones

Google diseña y construye sus propios centros de datos con varias capas de protección física.

El acceso está limitado a una pequeña cantidad de empleados.

También utiliza centros de datos de terceros, donde se implementan medidas de seguridad física controladas por Google además de las proporcionadas por el operador.

---

## Implementación de servicios

Una característica clave es la **encriptación de la comunicación entre servicios**.

La infraestructura proporciona integridad y privacidad criptográfica a los datos de las llamadas de procedimiento remoto (**RPC**).

Los servicios de Google se comunican mediante RPC y el tráfico de RPC entre centros de datos se encripta automáticamente.

Google también implementa aceleradores criptográficos de hardware para esta encriptación.

---

## Identidad de los usuarios

El servicio de identidad central de Google va más allá del uso de un nombre de usuario y una contraseña.

También considera factores de riesgo, como:

* Dispositivo utilizado.
* Ubicación desde la que se accede.

Los usuarios pueden utilizar segundos factores de autenticación, como dispositivos basados en **U2F (Universal 2nd Factor)**.

---

## Almacenamiento

En esta capa se encuentra la **encriptación en reposo**.

La encriptación con claves administradas centralmente se aplica en los servicios de almacenamiento.

Google también admite encriptación de hardware en:

* Discos duros
* SSD

---

## Comunicación en Internet

Los servicios de Google disponibles en Internet se registran con **Google Front End (GFE)**.

GFE asegura que las conexiones TLS utilicen:

* Claves públicas y privadas.
* Certificados X.509.
* Autoridades certificadoras.
* Prácticas recomendadas como la confidencialidad directa perfecta.

También proporciona protección contra ataques de **denegación de servicio (DoS)**.

La amplitud de la infraestructura permite absorber muchos ataques DoS y existen diferentes niveles y capas de protección.

---

## Seguridad operativa

La seguridad operativa de Google cuenta con cuatro funciones principales:

### 1. Detección de intrusiones

Las reglas y la IA envían advertencias a los equipos de seguridad sobre posibles incidentes.

Google también realiza ejercicios de **equipo rojo** para medir y mejorar sus mecanismos de detección y respuesta.

### 2. Reducción del riesgo de infiltración

Google limita y supervisa las actividades de los empleados con acceso de administrador a la infraestructura.

Además, los empleados utilizan **U2F**.

Las cuentas de los empleados deben utilizar llaves de seguridad compatibles con U2F para protegerse contra ataques de phishing.

### 3. Desarrollo seguro

Google utiliza:

* Control central de código fuente.
* Revisión de código por dos personas.
* Bibliotecas que ayudan a evitar determinadas clases de errores de seguridad.

### 4. Programa de recompensas

Google cuenta con un **Programa de recompensas por detección de vulnerabilidades** que ofrece pagos por descubrir e informar errores en la infraestructura o aplicaciones.

---

## Capas de seguridad

```text
Hardware
   ↓
Implementación de servicios
   ↓
Identidad
   ↓
Almacenamiento
   ↓
Comunicación en Internet
   ↓
Seguridad operativa
```

Más información:

`cloud.google.com/security/security-design`
