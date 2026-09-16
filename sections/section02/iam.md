# Identity and Access Management (IAM)

Cuando un nodo de organización tiene muchas carpetas, proyectos y recursos, es posible que sea necesario restringir el acceso.

Para esto, los administradores pueden utilizar **Identity and Access Management (IAM)**.

IAM permite aplicar políticas que definen:

```text id="8q3f2x"
Quién → Puede hacer qué → En qué recurso
```

## Principales

El **“quién”** de una política de IAM se conoce como **principal**.

Puede ser:

* Cuenta de Google
* Grupo de Google
* Cuenta de servicio
* Dominio de Cloud Identity

Cada principal tiene su propio identificador, que suele ser un correo electrónico.

---

## Roles y permisos

El **“puede hacer qué”** se define mediante los **roles**.

Un rol de IAM es una colección de permisos.

```text id="k3x8w1"
Rol
 ↓
Colección de permisos
 ↓
Acciones que puede realizar el principal
```

Por ejemplo, para administrar instancias de VM en un proyecto se necesitan permisos para:

* Crear máquinas virtuales.
* Borrar máquinas virtuales.
* Iniciar máquinas virtuales.
* Detener máquinas virtuales.
* Modificar máquinas virtuales.

Estos permisos se agrupan en un rol para facilitar su comprensión y administración.

---

## Herencia de políticas

Cuando se asigna un rol a una principal en un elemento específico de la jerarquía de recursos, la política se aplica al elemento elegido y a todos los elementos inferiores.

```text id="j4z9qa"
Organización
     ↓
 Carpeta
     ↓
 Proyecto
     ↓
 Recurso
```

---

## Políticas de denegación

También es posible definir reglas de **denegación** para impedir que determinadas principales utilicen ciertos permisos, independientemente de los roles que tengan asignados.

IAM verifica primero las políticas de denegación relevantes y después las políticas de permisos relevantes.

Las políticas de denegación también se heredan por la jerarquía de recursos.

---

# Tipos de roles de IAM

Existen tres tipos de roles:

```text id="7x2m5c"
Roles de IAM
├── Básicos
├── Predefinidos
└── Personalizados
```

## 1. Roles básicos

Los roles básicos tienen permisos bastante amplios.

Cuando se aplican a un proyecto de Cloud, afectan a todos los recursos del proyecto.

Los roles básicos son:

* **Propietario**
* **Visualizador**
* **Editor**
* **Administrador de facturación**

### Visualizador

Puede acceder a los recursos, pero **no puede realizar cambios**.

### Editor

Puede acceder a los recursos y **modificarlos**.

### Propietario

Puede acceder y modificar recursos.

Además, puede:

* Administrar roles y permisos.
* Configurar la facturación.

### Administrador de facturación

Permite controlar la facturación de un proyecto sin poder modificar sus recursos.

---

## 2. Roles predefinidos

Los roles predefinidos ofrecen conjuntos de permisos específicos para determinados servicios de Cloud.

Los servicios también definen cuándo se pueden aplicar.

Por ejemplo, **Compute Engine** ofrece roles predefinidos específicos, como `instanceAdmin`.

Estos roles pueden aplicarse a recursos de Compute Engine en:

* Un proyecto.
* Una carpeta.
* Toda una organización.

Quien recibe estos roles puede realizar un conjunto específico de acciones predefinidas.

---

## 3. Roles personalizados

Los roles personalizados permiten asignar permisos aún más específicos.

Muchas empresas utilizan el modelo de **privilegio mínimo**, donde cada persona posee únicamente los privilegios necesarios para realizar su trabajo.

Por ejemplo, se puede definir un rol `instanceOperator` que permita:

```text id="m2v7qd"
Iniciar VM ✓
Detener VM ✓
Reconfigurar VM ✗
```

Los roles personalizados permiten definir estos permisos exactos.

### Consideraciones

Antes de crear roles personalizados hay que tener en cuenta:

1. Se deben administrar los permisos que definen el rol personalizado.
2. Algunas organizaciones prefieren utilizar roles predefinidos por esta razón.
3. Los roles personalizados solo pueden aplicarse a nivel de **proyecto** o **organización**.

> Los roles personalizados **no se pueden aplicar a nivel de carpeta**.
