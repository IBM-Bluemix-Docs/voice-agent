---

copyright:
  years: 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Visualización de registros de uso, llamadas y SMS
{: #logging}

Puede ver el historial de uso, registros de llamadas y registros de SMS correspondientes a los agentes de voz desde el panel de control de {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

## Acerca del registro

El registro se habilita automáticamente para {{site.data.keyword.iva_full}}. Puede ver los registros de llamadas del agente de voz en el panel de control _Uso_.

En el panel de control _Uso_ se muestran estadísticas rápidas sobre el uso del servicio y los recursos que quedan disponibles en el plan. Esta información incluye el número máximo de conexiones simultáneas que se han producido durante el mes actual y el número máximo de conexiones simultáneas disponibles en el plan. En el recuadro _Minutos de llamadas_, puede ver el número de minutos gratuitos incluidos en el plan y el número de minutos que se han utilizado. En la sección _Registros de llamadas_ se incluye un seguimiento de las _Estadísticas rápidas_. La sección _Registros de SMS_ muestra estadísticas de uso de SMS similares en los agentes. 

Puede filtrar los _Registros de llamadas_ y los _Minutos de llamadas_, por fecha y por nombres o números de agente de voz para reducir el número de llamadas visualizadas y aislar registros de llamadas específicos. Puede filtrar los _registros de SMS_ por fecha y por nombres o números de agente. Además, puede filtrar los _Registros de llamadas_ para mostrar solo las llamadas fallidas.

Para obtener más información sobre la creación y la edición de agentes de voz, consulte [Gestión de agentes de voz](/docs/services/voice-agent?topic=voice-agent-managing).

##  Visualización de registros de llamadas

1. Desde el panel de control de {{site.data.keyword.iva_short}}, vaya al panel de control _Uso_ para ver las _Estadísticas rápidas_ y los *Registros de llamadas*. Cada fila de la tabla _Registros de llamadas_ corresponde a una llamada.

      Para cada llamada, puede ver el nombre y el número de teléfono del agente de voz, las horas de inicio y detención y la duración de la llamada. También puede ver un símbolo de aviso junto al nombre del agente de voz, que indica que la llamada ha fallado.

1.  Puede filtrar la lista de llamadas para ver las llamadas de una fecha específica y para ver las llamadas de un nombre o número de agente de voz. También puede optar por mostrar solo las llamadas fallidas.

1. Para acceder a los registros de errores de llamada de una llamada individual, pulse los puntos de la columna **Acciones** de dicha llamada para ampliar el menú. A continuación, elija **Registros de error**. Esta opción solo aparece para las llamadas fallidas.

1. Puede examinar la lista detallada de registros de mensajes en la nueva vista mediante los métodos siguientes:
  * Buscar los registros de error
  * Filtrar los mensajes en función del tipo de registro, **Error** o **Aviso**
  * Descargar el conjunto de datos
  * Ordenar los registros de error por fecha y hora ascendente o descendente

1. Para ver cualquier mensaje de registro de error en detalle, pulse la flecha al principio de la fila que le interesa para ampliar la vista. Puede ver información más detallada sobre los mensajes de registro en [Mensajes de sistema de Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Pulse la flecha atrás al principio de la página para volver al panel de control _Uso_.

##  Visualización de registros de SMS

1. Desde el panel de control de {{site.data.keyword.iva_short}}, vaya al panel de control de _Uso_ para ver _Estadísticas rápidas_ y pulse *Registros de SMS*. Cada fila de la tabla _Registros de SMS_ corresponde a un agente y a un número.

      Para el agente, puede ver el número de teléfono del agente de voz y los mensajes de entrada, los mensajes de salida y los mensajes facturables. También puede ver un símbolo de aviso junto al nombre del agente de voz, lo que indica que los mensajes SMS han fallado.

      - Los **mensajes de entrada** son mensajes del usuario al agente y solo se facturan cuando el agente envía una respuesta al usuario. 

      - Los **mensajes de salida** son mensajes del agente al usuario. Estos mensajes se envían como respuesta a un mensaje de entrada, o cuando Voice Gateway envía un mensaje al usuario sin que se necesite ningún mensaje de entrada adicional. 

      - Los **mensajes facturables** son el número total de mensajes de entrada y salida a los que ha respondido el agente.

1.  Puede filtrar la lista de agentes visualizando los mensajes de una fecha específica y filtrando los mensajes por nombre o por número de agente de voz. 

1. Para acceder a los registros de SMS para un agente individual:

  - En la columna **Acciones** correspondiente a la llamada deseada, pulse los puntos para expandir el menú.
  
  - Pulse **Registros de SMS**.

1. Pulse la flecha atrás al principio de la página para volver al panel de control _Uso_.

## Enlaces relacionados
Lea más información detallada sobre el registro en [Resolución de problemas](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window} en la documentación de IBM Voice Gateway.
