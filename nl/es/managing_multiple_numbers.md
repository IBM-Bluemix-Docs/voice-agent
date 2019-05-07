---

copyright:
  years: 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuración de varios números de teléfono para un _Único agente_
{: #multi_num}

[comment]: # (Tras crear su instancia de servicio de {{site.data.keyword.iva_full}}, )

Puede añadir varios números de teléfono a un único agente, con lo que la configuración del agente afectará a todos los números que tenga asociados. La página del panel de control _Gestionar instancia de servicio_ mostrará el **Número principal** asociado con el agente. Consulte [Configuración de un número principal](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Puede acceder al recuadro de diálogo **Gestionar** pulsando en **Gestionar** junto al **Número de teléfono** desde la página _Crear un agente de voz_ o _Editar un agente de voz_.

  * _**NOTA:**_ hay un límite de 1000 números exclusivos por cada configuración de agente.
{: shortdesc}


## Adición un número nuevo
{: #add_num}

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_ para abrir el recuadro de diálogo **Gestionar**.

1. Pulse en el icono "Añadir número" cerca de la parte superior derecha del recuadro de diálogo **Gestionar**. Se creará una nueva entrada vacía en la lista.

1. {: #format_num} Para **Número de teléfono**, añada el número de su conexión troncal SIP, incluidos los códigos de país y de área. Por ejemplo, para un número 800 de Estados Unidos, especifique el número de teléfono como 18883334444. El número de teléfono puede tener espacios y los caracteres + ( ) - (con un máximo de 30 caracteres).  

  * _**NOTA:**_ hay un límite de 1000 números exclusivos por cada configuración de agente.

1. Si quiere, puede proporcionar una descripción para su número de teléfono en el campo **Descripción** de hasta 64 caracteres.

1. Pulse el icono "marca de selección" para guardar el número en la lista, o pulse el icono "X" para cancelar la adición.

1. En la parte superior aparecerá un mensaje "Correcto", junto con una entrada en la lista con el número nuevo. De lo contrario, se mostrará un mensaje de error con una descripción.

1. El número tendrá una marca de selección **Verde** en la columna Estado de la lista, indicando que el número no tiene errores.

1. Pulse **Terminado** para guardar y confirmar el número en el agente.

## Edición de un Número o Descripción
{: #edit_num}

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_. Como alternativa, si ya tiene varios números en el agente de voz, solo debe pulsar en el campo **Número de teléfono** desactivado para abrir el recuadro de diálogo **Gestionar**.

1. Seleccione la entrada del número que quiere editar y pulse en la lista de opciones, representada por el icono de **tres puntos** que aparece a la derecha de la lista.

1. En el menú desplegable que aparece, seleccione **Editar**.

1. Ahora puede editar y realizar cambios en el **Número de teléfono** y/o la **Descripción**.

1. Pulse en el icono de "marca de selección" para aceptar la actualización, o pulse en el icono "X" para descartar la actualización.

1. En la parte superior aparecerá un mensaje "Correcto", junto con la entrada en la lista que se actualiza. De lo contrario, se mostrará un mensaje de error con una descripción.

1. Pulse **Terminado** para guardar los cambios en el agente.

## Supresión de números
{: #delete_num}

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_.

1. Marque el recuadro en blanco junto a todos los números que quiera suprimir. Para seleccionar _todos_ los números, solo tiene que marcar el recuadro en blanco junto a la cabecera **Número de teléfono**.

1. Pulse en el icono "Suprimir elemento" cerca de la parte superior derecha del recuadro de diálogo **Gestionar**.

1. En la parte superior aparecerá un mensaje "Correcto", y las entradas seleccionadas se eliminarán de la lista. De lo contrario, se mostrará un mensaje de error con una descripción.

1. Para suprimir un solo número, en lugar de marcar el recuadro de selección, puede seleccionar la entrada del número que quiere suprimir y pulsar en la lista de opciones, representada por el icono de **tres puntos** que aparece a la derecha de la lista.

1. En el menú desplegable que aparece, seleccione **Suprimir**.

1. En la parte superior aparecerá un mensaje "Correcto", y la entrada seleccionada se eliminará de la lista. De lo contrario, se mostrará un mensaje de error con una descripción.

1. Pulse **Terminado** para guardar y confirmar la supresión de los números del agente.

## Importación de números
{: #import_num}

Se puede subir al agente una lista de números. La lista _debe_ ser un archivo de tipo **.csv**. El archivo podría tener hasta 1000 **números de teléfono** únicos, uno por línea, junto con una **Descripción** opcional para cada número.

  * _**NOTA:**_ al subir números desde un archivo .CSV, se sustituyen _TODOS_ los números actuales del agente. A la lista de números _no_ se le añaden los números del archivo CSV.

  * Los números del archivo CSV _deben_ ajustarse al mismo formato que cuando se añade un número al Panel de control, y deben ser exclusivos. Consulte [Formato de número](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_.

1. Pulse en el icono "Subir archivo CSV" cerca de la parte superior derecha del recuadro de diálogo **Gestionar**.

1. Le aparecerá una ventana para confirmar que va a sustituir todos los números existentes en la lista por los números del archivo .CSV. Pulse **Aceptar** para confirmar y continuar.

1. En la ventana nueva, busque el archivo CSV, selecciónelo y pulse **Abrir**.

1. En la parte superior aparecerá un mensaje "Correcto", y todos los números nuevos se añadirán a la lista. De lo contrario, se mostrará un mensaje de error con una descripción, con mensajes de error junto a cada número con problemas.

1. Los números concretos importados tendrán una marca de selección **Verde** en la columna _Estado_ de la lista, indicando que el número no tiene errores. De lo contrario, se mostrará un error específico en la columna _Estado_.

1. Pulse **Terminado** para guardar y confirmar la adición de los números del agente.

## Exportación de números
{: #export_num}

Se puede exportar una lista de números con sus descripciones del agente a un archivo **.CSV**, y descargarlos a su equipo. Esto le permite modificar los números y descripciones, y los puede volver a subir al agente. Consulte [Importación de números](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_.

1. Pulse en el icono "Descargar archivo CSV" cerca de la parte superior derecha del recuadro de diálogo **Gestionar**.

1. Se descargará a su equipo un archivo CSV con todos los números guardados en el agente.

1. Puede pulsar **Terminado** para salir del recuadro de diálogo **Gestionar**.

## Establecimiento de un Número principal
{: #primary_num}

El _Número principal_ es solo por motivos de visualización, y no tiene ninguna funcionalidad práctica. De forma predeterminada, el primer número añadido al agente es el que se etiqueta como **Número principal**, que es el que se muestra en la página del panel de control _Gestionar instancia de servicio_. En un agente de voz debe haber al menos un **Número principal**.

Puede cambiar la etiqueta del **Número principal** a cualquier otro número que quiera del agente de voz.

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_.

1. Seleccione la entrada del número que quiere editar y pulse en la lista de opciones, representada por el icono de **tres puntos** que aparece a la derecha de la lista.

1. En el menú desplegable que aparece, seleccione **Establecer como principal**.

1. En la parte superior aparecerá un mensaje "Correcto". La entrada que haya elegido tendrá la etiqueta **Principal** bajo la columna _Estado_. De lo contrario, se mostrará un mensaje de error con una descripción.

1. Pulse **Terminado** para guardar los cambios en el agente.

## Ordenación y desplazamiento por los números de teléfono
{: #sort_num}

Puede ordenar la lista de números según los _Números de teléfono_ o según las _Descripciones_, en orden ascendente o descendente. De forma predeterminada, la lista de números de teléfono se ordena de forma ascendente por el **Número de teléfono**.

1. Pulse en la cabecera **Número de teléfono** para ordenar la lista de números en orden numérico.

1. Pulse en la cabecera **Descripción** para ordenar la lista de números en orden alfabético según la _Descripción_.  

Es posible que quiera elegir el número de números por página de la lista. Puede mostrar 5, 10 o 30 números por página. También puede acceder a las páginas.

1. Pulse en el número junto a **Elementos por página** para elegir la cantidad de números que quiere en la lista. De forma predeterminada, se muestran 5 números por página.

1. Pulse la flecha _Derecha_ o _Izquierda_ sobre la cabecera **Estado** para desplazarse por las páginas.

1. También puede pulsar en el número entre las flechas para elegir una página manualmente.

1. Pulse **Terminado** para guardar los cambios en el agente.

## Cómo guardar los cambios
{: #save_changes}

Si quiere realizar cambios en la lista de números en el agente de voz, _debe_ guardar los cambios en el recuadro de diálogo **Gestionar**, seguido de Guardar cambios en la página _Editar agente de voz_.

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_.

1. Realice los cambios que quiera en los números de la lista.

1. Pulse **Terminado** para guardar los cambios en el agente.

1. Volverá a la página _Editar agente de voz_; pulse **Guardar cambios** en la parte superior derecha para aplicar todos sus cambios.

* _**NOTA:**_ Para guardar sus cambios, _debe_ pulsar tanto en **Terminado** en el recuadro de diálogo **Gestionar** _como en_ **Guardar cambios** en la página _Editar agente de voz_; de lo contrario, los cambios no se guardarán.

## Buscar números o descripción
{: #search_num}

Puede buscar los números almacenados, por el número o por la descripción.

1. Pulse **Gestionar** junto a **Número de teléfono** en la página _Crear un agente de voz_ o _Editar un agente de voz_.

1. En la barra _Buscar_, puede escribir un número o una descripción para buscar en la lista. A medida que escriba, los resultados de búsqueda se actualizan automáticamente.

1. Pulse **Terminado** para guardar los cambios en el agente.
