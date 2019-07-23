---

copyright:

  years: 2019

lastupdated: "2019-06-06"
subcollection: "voice-agent"

keywords: Voice Agent IAM, Voice Agent user access, get started with IAM, IAM tutorial, IAM quick start, user access, SMS IAM, SMS user access

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Configuración de IAM y del acceso de usuario
{: #iam}

Esta guía de aprendizaje está pensada para ayudarle a ponerse en marcha rápidamente con IBM Cloud Identity and Access Management (IAM) invitando a usuarios a su cuenta y asignando a dichos usuarios acceso de Cloud IAM sobre una instancia de {{site.data.keyword.iva_short}}.
{:shortdesc}

## Antes de empezar
{: #iam-before-you-begin}

Si es un nuevo usuario de IAM, consulte la documentación siguiente para obtener más información sobre las características, los conceptos y los componentes del sistema de gestión de accesos.

* [IBM Cloud Identity and Access Management](/docs/iam?topic=iam-iamoverview) contiene una visión general del funcionamiento de IAM en IBM, las características disponibles y enlaces con la documentación disponible sobre CLI y API.
* En [Conceptos de IAM](/docs/iam?topic=iam-iamconcepts) se ofrecen conceptos generales sobre IAM que le pueden ayudar a comprender los distintos componentes.
* [Acceso de IAM](/docs/iam?topic=iam-userroles) contiene una revisión más profunda sobre el funcionamiento de la gestión de accesos mediante políticas de acceso.

Esta guía cubre los escenarios más comunes para añadir y asignar acceso a los usuarios. Hay muchas otras opciones y configuraciones para el acceso de usuario y para los roles. Los enlaces anteriores proporcionan más detalles. 

## Paso 1. Invitar a usuarios y asignar acceso inicial
{: #step1}

Puede invitar a uno o varios usuarios y definir una política de acceso inicial para los usuarios en la invitación. Si invita a varios usuarios en una invitación, se asigna el mismo acceso a todos ellos. En la sección **acceso** de la página **Invitar a usuarios**, solo verá los roles de usuario que puede asignar.

El propietario de la cuenta puede asignar roles de Cloud IAM a los usuarios invitados en la sección **Servicios**. Como propietario de la cuenta, puede proporcionar acceso a:
* todos los recursos de un grupo de recursos
* todos los recursos correspondientes a un servicio específico en un grupo de recursos 
* todos los servicios de la cuenta habilitados para Identity and Access
* un solo recurso de la cuenta
* acceso a servicios de gestión de la cuenta

Utilice el procedimiento siguiente para asignar roles de Cloud IAM a los usuarios de la cuenta.

1. Vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**.
2. Pulse **Invitar a usuarios**.
3. Especifique la dirección de correo electrónico de los usuarios que desee invitar.
4. En la sección **Acceso**, expanda la opción **Servicios**.
5. Elija si desea asignar acceso a un **Recurso**, a los recursos de un **Grupo de recursos** o a los **Servicios de gestión de cuentas**.
6. En función de su selección, siga las indicaciones para especificar el acceso deseado. Si ha seleccionado la opción _Grupo de recursos_, también puede proporcionar al usuario acceso para ver, editar o gestionar el acceso al grupo de recursos seleccionando un rol para el acceso al grupo de recursos.
7. En el recuadro de entrada **Servicios**, seleccione *{{site.data.keyword.iva_short}}* en el menú desplegable, o bien escriba en el recuadro y pulse Intro. 
8. Seleccione la **Región** y la **Instancia de servicio** adecuadas.
9. En la sección **Seleccionar roles**, elija entre *Gestor*, *Escritor* y *Lector*. Si la *instancia de servicio* de {{site.data.keyword.iva_short}} utiliza SMS, **debe** seleccionar el rol de *Escritor* o de *Gestor*, además de los otros roles que desee otorgar.
    - Para obtener más información acerca de los **Roles**, consulte [Roles de acceso al servicio](/docs/iam?topic=iam-userroles#service_access_roles).
10. Si tiene permiso, también puede asignar acceso de Cloud Foundry o de infraestructura en la invitación.
11. Pulse **Invitar a usuarios**.

Para obtener más información, consulte [Invitación a usuarios y asignación de acceso](/docs/iam?topic=iam-iamuserinv#iamuserinv).

## Paso 2. Crear grupos de acceso
{: #step2}

Para agilizar el proceso de asignación de acceso a los usuarios de su cuenta, puede crear grupos de acceso. Los grupos de usuarios constituyen una manera de organizar usuarios e ID de servicio a los que luego puede asignar acceso fácilmente mediante la definición de una sola política para todo el grupo.

### Configuración de grupos
{: #group_setup}

Para crear un grupo de acceso, siga los pasos siguientes.

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Grupos de acceso**.
2. Pulse **Crear**.
3. Escriba un nombre para el grupo. La descripción es opcional.
4. Pulse **Crear**.

A continuación, siga configurando su grupo añadiendo usuarios o ID de servicio.

1. Irá a la página del grupo de acceso recién creado. Este grupo también aparecerá en la lista _Grupo_ de la página **Grupos de acceso** de la barra de menús.
2. Pulse **Añadir usuarios**.
3. Seleccione los usuarios de la lista que desea añadir y pulse **Añadir a grupo**.
4. Para añadir los ID de servicio al grupo, pulse **ID de servicio**.
5. Seleccione los ID de la lista que desea añadir y pulse **Añadir a grupo**.

### Asignación de acceso a los grupos
{: #group_access}

Después de crear los grupos, puede asignar acceso a todas las entidades del grupo con una sola política o con varias políticas.

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Grupos de acceso**.
2. Seleccione el grupo al que desea asignar acceso.
3. En el separador **Políticas de acceso**, pulse **Asignar acceso** para configurar una política de acceso. Repita este paso las veces que sea necesario para asignar más acceso.

Mediante la organización de usuarios en grupos de acceso, puede asignar a un grupo de usuarios acceso a una sola política, lo que reduce el número global de políticas que tiene que gestionar.
{: tip}


## Paso 3. Gestionar el acceso de usuarios existentes
{: #user_access_manage}

En la sección siguiente se detalla cómo gestionar y editar el acceso para usuarios y grupos que ya ha configurado en la cuenta.

### Asignación de nuevo acceso
{: #new_access}

Para asignar una nueva política de acceso, siga los pasos siguientes:

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**.
2. Seleccione el nombre del usuario al que desea asignar acceso.
3. Pulse **Políticas de acceso**.
4. Pulse **Asignar acceso**.
5. Elija la forma de asignar el acceso:
    * Seleccione **Asignar acceso dentro de un grupo de recursos** para asignar acceso a todos los recursos de un grupo, o a recursos que se han designado para un servicio específico dentro de un grupo. También puede otorgar a los usuarios permiso para ver, editar o gestionar el acceso al grupo de recursos, asignándoles un rol de usuario para el grupo de recursos. Seleccione **Sin acceso** si solo desea otorgar a un usuario acceso al recurso especificado y no al grupo de recursos.
    * Seleccione **Asignar acceso a recursos** para asignar acceso a todos los recursos habilitados para Identity and Access de la cuenta, a todos los recursos de un servicio específico de la cuenta, a una sola instancia o a un solo recurso dentro de una instancia de servicio específica.
    * Seleccione **Asignar acceso a servicios de gestión de cuentas** para asignar acceso a todos los servicios de gestión de cuentas o solo a un servicio de gestión de cuentas.
5. Seleccione cualquier combinación de roles para definir el ámbito del acceso. Para obtener más información, consulte [Roles de Cloud IAM](/docs/iam?topic=iam-userroles#iamusermanrol).
6. Pulse **Asignar**.


### Edición del acceso existente
{: #editing_access}

Puede actualizar el acceso existente editando los roles asignados a un usuario.

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**.
2. Seleccione el nombre del usuario cuyo acceso desea editar.
3. Pulse **Políticas de acceso**.
4. Pulse **Editar** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg) en la fila correspondiente a la política que desea editar.
4. Edite la política actualizando los roles asignados.
5. Pulse **Guardar**.

También puede eliminar el acceso de un usuario pulsando la opción **Eliminar** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg) correspondiente a la política que desea eliminar.

## Paso 4. Asignar acceso a los agentes de SMS o de Voz + SMS (Opcional)
{: #sms_access}

Si el agente al que está asignando acceso es un agente de **SMS** o de **Voz + SMS**, cree una *Nueva credencial*.

### Creación de una nueva credencial
{: #new_cred}

Solo puede crear credenciales para los roles que ya están activos en la cuenta. Para los agentes de SMS y de Voz + SMS, debe tener asignado el rol de *Escritor* o de *Gestor*. Consulte el [Paso 9 de la sección Invitar a los usuarios y asignar acceso inicial](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. En el *Panel de control* de la instancia de {{site.data.keyword.iva_short}}, pulse **Nueva credencial (+)**. 
2. En el nuevo recuadro de diálogo que aparece, especifique un **Nombre** y, en el menú desplegable **Rol**, seleccione *Escritor* o *Gestor*. 
    - **NOTA:** para cualquier funcionalidad relacionada con SMS, **_debe_** seleccionar el rol de *Escritor* o de *Gestor*. 
3. Pulse el botón
**Añadir**.

## Resolución de problemas
{: #troubleshoot}

Si ve un mensaje de error en la página **Credenciales de servicio** al intentar crear una *Nueva credencial* que dice:
> No tiene el permiso necesario para asignar el rol de ‘Escritor’. Póngase en contacto con el propietario de la cuenta para que actualice su acceso.

Debe seguir las instrucciones para asignarse el acceso de *Escritor* o de *Gestor* a usted mismo, acción **necesaria** para las funciones relacionadas con SMS. Consulte el [Paso 9 de asignación de acceso](/docs/services/voice-agent?topic=voice-agent-iam#step1) y luego continúe con [Creación de una nueva credencial](/docs/services/voice-agent?topic=voice-agent-iam#new_cred).

## Pasos siguientes
{: #next}

Para obtener más información sobre lo que puede hacer Cloud IAM, seleccione la lista [Características de Cloud IAM](/docs/iam?topic=iam-iamoverview#features).
