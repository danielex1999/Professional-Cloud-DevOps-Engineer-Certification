# Cloud Identity

Con frecuencia, los clientes nuevos de Google Cloud acceden a la consola de Google Cloud con una cuenta de **Gmail** y utilizan **Grupos de Google** para colaborar con compañeros de equipo que tienen roles similares.

Aunque esta estrategia es sencilla al principio, puede presentar desafíos porque las identidades del equipo **no se administran de manera centralizada**.

## Problema

Si una persona deja de trabajar en la organización, este método no permite quitar inmediatamente su acceso a los recursos en la nube del equipo.

```text id="g7x3pd"
Cuenta Gmail
     ↓
Grupos de Google
     ↓
Recursos de Cloud
```

## Cloud Identity

**Cloud Identity** permite definir políticas y administrar usuarios y grupos desde la **Consola del administrador de Google**.

Los administradores pueden acceder a los recursos de Cloud utilizando los mismos nombres de usuario y contraseñas que utilizaban en sistemas existentes de:

* Active Directory
* LDAP

### Administración de usuarios

Cuando una persona deja la organización, un administrador puede:

```text id="p3k8vz"
Deshabilitar su cuenta
        +
Eliminarla de los grupos
        ↓
Quitar su acceso a los recursos
```

## Ediciones

Cloud Identity está disponible en:

* **Edición sin costo**
* **Edición Premium**, que ofrece funcionalidades para administrar dispositivos móviles.

Si eres cliente de **Google Cloud y Google Workspace**, esta funcionalidad ya está disponible en la **Consola del administrador de Google**.
