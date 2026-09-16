# Cuentas de Servicio en Google Cloud

Las **cuentas de servicio** permiten asignar permisos a una máquina virtual para que pueda interactuar con otros servicios de Google Cloud **sin intervención humana**.

## ¿Cuándo utilizarlas?

Por ejemplo, una VM de **Compute Engine** ejecuta un programa que necesita acceder frecuentemente a otros servicios.

En lugar de que una persona otorgue acceso cada vez que se ejecuta el programa, se pueden asignar los permisos necesarios a la máquina virtual mediante una cuenta de servicio.

```text id="f8k3pd"
VM de Compute Engine
        ↓
Cuenta de servicio
        ↓
Permisos
        ↓
Otros servicios de Cloud
```

## Ejemplo: Cloud Storage

Supongamos que una aplicación ejecutada en una VM necesita almacenar datos en **Cloud Storage**, pero no se quiere que cualquier persona en Internet tenga acceso a esos datos.

Se puede crear una cuenta de servicio para autenticar la VM en Cloud Storage.

Las cuentas de servicio:

* Se identifican mediante una dirección de correo electrónico.
* Utilizan claves criptográficas para acceder a los recursos.

---

## Permisos de una cuenta de servicio

Los permisos asignados a una cuenta de servicio determinan lo que una aplicación puede hacer.

Por ejemplo, si una cuenta de servicio tiene el rol de **administrador de instancias de Compute Engine**, una aplicación que se ejecute en una VM asociada a esa cuenta podría:

* Crear VMs.
* Modificar VMs.
* Borrar VMs.

---

## Administración de cuentas de servicio

Las cuentas de servicio también deben administrarse.

Por ejemplo:

```text id="q4x7mz"
Alicia → Administrar cuentas de servicio
Roberto → Visualizar cuentas de servicio
```

Una cuenta de servicio es tanto una **identidad** como un **recurso**, por lo que puede tener sus propias políticas de IAM.

Por ejemplo:

* Alicia puede tener el rol de **editor** en una cuenta de servicio.
* Roberto puede tener el rol de **visualizador**.

Esto funciona de la misma forma que la asignación de roles en cualquier otro recurso de Google Cloud.
