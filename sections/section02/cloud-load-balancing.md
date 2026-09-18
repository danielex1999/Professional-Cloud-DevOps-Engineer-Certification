# Cloud Load Balancing

Cuando una aplicación utiliza varias VMs, **Cloud Load Balancing** permite distribuir el tráfico de los usuarios entre las diferentes instancias.

Esto permite que una aplicación pueda funcionar tanto con pocas VMs como con muchas, según la demanda.

```text id="x5q8mn"
             Usuarios
                 ↓
        Cloud Load Balancing
          ↙      ↓      ↘
        VM1     VM2     VM3
```

## ¿Qué hace?

Un balanceador de cargas:

* Distribuye el tráfico entre las instancias.
* Reduce el riesgo de problemas de rendimiento.
* Se adapta a cambios en usuarios y tráfico.
* No requiere administrar ni escalar VMs para el balanceador.

Cloud Load Balancing es un servicio **distribuido, definido por software y administrado**.

Puede utilizarse con:

* HTTP
* HTTPS
* TCP
* SSL
* UDP

También permite balanceo entre regiones y **conmutación por error automática multirregional** cuando los backends no están disponibles.

---

# Tipos de balanceadores

Las soluciones de balanceo de cargas de Google Cloud se clasifican según la capa del modelo **OSI** en la que operan y sus funcionalidades.

## Balanceadores de cargas de aplicaciones

Operan en la **capa de aplicación** y administran tráfico:

* HTTP
* HTTPS

Son adecuados para aplicaciones web que requieren funciones como:

* Enrutamiento basado en contenido.
* Terminación SSL/TLS.

Funcionan como **proxies inversos** y distribuyen el tráfico entre diferentes backends según las reglas configuradas.

Pueden utilizarse para aplicaciones:

* Internas.
* Externas disponibles en Internet.

---

## Balanceadores de cargas de red

Operan en la **capa de transporte** y administran tráfico como:

* TCP
* UDP
* Otros protocolos IP.

Se dividen en dos tipos principales:

### Network Load Balancer de proxy

Funcionan como proxies inversos:

```text id="p3v7ka"
Cliente
   ↓
Balanceador
   ↓
Backend
```

El balanceador finaliza las conexiones del cliente y crea nuevas conexiones hacia los servicios backend.

Ofrecen funciones avanzadas de administración del tráfico y admiten backends ubicados en:

* Infraestructura local.
* Diferentes entornos de nube.

### Network Load Balancer de transferencia

A diferencia de los anteriores, **no finalizan las conexiones**.

En su lugar, reenvían el tráfico directamente al backend conservando la dirección IP de origen.

Son adecuados para aplicaciones que:

* Requieren un retorno directo del servidor.
* Necesitan administrar un rango más amplio de protocolos IP.
