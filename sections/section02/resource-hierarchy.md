# Jerarquía de Recursos en Google Cloud

La jerarquía de recursos de Google Cloud consta de **cuatro niveles**, en orden ascendente:

```text id="3h5k2a"
Recursos
   ↓
Proyectos
   ↓
Carpetas
   ↓
Nodo de organización
```

## 1. Recursos

Representan elementos de Google Cloud, como:

* Máquinas virtuales
* Buckets de Cloud Storage
* Tablas de BigQuery
* Otros recursos de Google Cloud

Los recursos se organizan dentro de **proyectos**.

---

## 2. Proyectos

Los proyectos son la base para habilitar y utilizar servicios de Google Cloud.

Permiten, entre otras cosas:

* Administrar APIs.
* Habilitar la facturación.
* Agregar y quitar colaboradores.
* Habilitar otros servicios de Google.

Cada proyecto es una entidad independiente dentro del nodo de organización y cada recurso pertenece únicamente a un proyecto.

Los proyectos pueden tener diferentes propietarios y usuarios, y se facturan por separado.

### Identificación de un proyecto

Cada proyecto tiene tres atributos:

| Atributo                | Característica                                                     |
| ----------------------- | ------------------------------------------------------------------ |
| **ID del proyecto**     | Único globalmente, asignado por Google y no puede cambiarse.       |
| **Nombre del proyecto** | Creado por el usuario, no tiene que ser único y puede modificarse. |
| **Número del proyecto** | Asignado por Google y utilizado principalmente a nivel interno.    |

El **ID del proyecto** es inmutable y se utiliza para identificar el proyecto exacto con el que se trabajará.

### Resource Manager

**Cloud Resource Manager** permite administrar proyectos de forma programática.

Es una API que permite:

* Listar proyectos asociados a una cuenta.
* Crear proyectos.
* Actualizar proyectos.
* Eliminar proyectos.
* Recuperar proyectos eliminados previamente.

Se puede acceder mediante APIs de **RPC** y **REST**.

---

## 3. Carpetas

Las carpetas permiten organizar proyectos y recursos de forma jerárquica.

Una carpeta puede contener:

```text id="xq7m3n"
Carpeta
├── Proyecto
├── Proyecto
└── Carpeta
    └── Proyecto
```

También permiten asignar políticas y permisos a los recursos.

Los recursos de una carpeta **heredan las políticas y permisos** asignados a ella.

### Ejemplo

Si dos proyectos son administrados por el mismo equipo, pueden colocarse dentro de una carpeta común:

```text id="2y7n4p"
Carpeta
├── Proyecto A
└── Proyecto B
```

Las políticas pueden establecerse en la carpeta en lugar de repetirlas en cada proyecto.

Esto facilita la administración y evita tener que modificar las mismas políticas en diferentes lugares.

Las carpetas también permiten agrupar recursos por departamentos y delegar derechos administrativos para que los equipos trabajen de forma independiente.

---

## 4. Nodo de organización

El **nodo de organización** es el nivel superior de la jerarquía de Google Cloud.

```text id="w8x2kd"
Nodo de organización
├── Carpetas
│   ├── Proyectos
│   └── Proyectos
│
└── Proyectos
```

Todo lo que se adjunta a una cuenta se encuentra dentro de este nodo, incluyendo:

* Proyectos
* Carpetas
* Recursos

Existen roles especiales asociados al nodo de organización.

Por ejemplo:

* **Administrador de políticas de la organización:** controla quién puede modificar las políticas.
* **Creador de proyectos:** controla quién puede crear proyectos y, por lo tanto, quién puede generar gastos.

---

# Herencia de políticas

Las políticas pueden definirse en:

* Proyecto
* Carpeta
* Nodo de organización
* Recursos individuales, cuando el servicio lo permite

Las políticas se heredan de forma descendente.

```text id="b3qv8a"
Organización
      ↓
   Carpeta
      ↓
  Proyecto
      ↓
   Recurso
```

Por ejemplo, una política aplicada a una carpeta también se aplica a los proyectos que se encuentran dentro de ella.

---

# Creación del nodo de organización

La forma de crear un nodo de organización depende de si la empresa utiliza **Google Workspace**.

### Google Workspace

Si se tiene un dominio de Workspace, los proyectos de Google Cloud pertenecen automáticamente al nodo de organización.

### Cloud Identity

Si no se tiene Google Workspace, se puede utilizar **Cloud Identity**, la plataforma de Google para administrar identidades, accesos, aplicaciones y extremos.

Al obtener un nuevo nodo de organización, cualquier persona del dominio puede crear proyectos y cuentas de facturación, igual que antes.

Después de tener el nodo, se pueden crear carpetas y colocar proyectos dentro de ellas.

Las carpetas y los proyectos se consideran **elementos secundarios** del nodo de organización.
