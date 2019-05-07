---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Resolución de problemas y soporte
{: #troubleshooting}

¿Tiene algún problema con {{site.data.keyword.iva_full}}? Revise los consejos de resolución de problemas comunes y póngase en contacto con la comunidad para responder cualquier pregunta.
{: shortdesc}

## Resolución de problemas de {{site.data.keyword.iva_short}}
{: #how-to}

Para resolver problemas con sus agentes de voz, puede utilizar el registro, el uso y el reenvío de sucesos para encontrar registros de errores y anomalías. Estos registros pueden ayudarle a diagnosticar y resolver problemas con sus agentes de voz. Si tiene problemas con {{site.data.keyword.iva_short}}, pruebe los pasos siguientes.

1. Si falla una llamada, el turno final de {{site.data.keyword.conversationshort}} podría describir el problema.

1. Los registros de uso muestran los errores que se pueden haber producido durante una determinada llamada. Consulte [Visualización de registros de uso y llamadas](/docs/services/voice-agent?topic=voice-agent-logging).

1. Consulte los registros de su proveedor de servicios en busca de errores de señalización. Por ejemplo, Twilio proporciona registros para cada conexión troncal SIP que aloja.

1. [Habilitando el reenvío de sucesos para los agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding), puede configurar su agente de voz para que reenvíe los registros de detalle de llamadas (CDR) a una base de datos de Cloudant y entonces determinar por qué ha fallado la llamada. Otros sucesos, como los sucesos de turno de {{site.data.keyword.conversationshort}}, pueden proporcionar detalles sobre cada turno de conversación de una llamada.

**Importante:** Los sucesos de turno, transcripción y CDR incluyen información de los usuarios que puede contener PHI (información sanitaria personal), PII (información de identificación personal) o datos PCI DSS (PCI Data Security Standard). Para evitar la exposición de información personal, debe asegurarse de que la instancia de {{site.data.keyword.cloudant_short_notm}} protege correctamente la información confidencial que los usuarios comparten en o durante la conversación.


## Obtención de ayuda
{: #help}

Si necesita ayuda, únase a nuestra comunidad de desarrolladores publicando sus preguntas o comentarios en cualquiera de los siguientes lugares, que se supervisan de forma activa.

* Publique en el [foro de dwAnswers ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/topics/voice-agent/) con la etiqueta `voice-agent`
* Publique en [StackOverflow ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} con la etiqueta `voice-agent`
* Póngase en contacto con nosotros en Slack en el equipo [IBM Cloud Technology ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) en el canal `#ibmvoicegateway`

**Recuerde**: Antes de publicar cualquier registro de las llamadas, elimine toda la información personal que los interlocutores y usuarios puedan haber compartido durante la conversación.

## Sugerencias de resolución de problemas
{: #troubleshooting-tips}

### ¿Por qué no obtengo respuesta por teléfono cuando llamo a mi agente de voz?

Seguramente, su llamada no se ha conectado a los servicios. Este problema se produce cuando la instancia de servicio de {{site.data.keyword.iva_short}} no está configurada correctamente. Compruebe los valores siguientes del agente de voz:

* Verifique que el número de teléfono del panel de control _Gestionar_ del agente de voz es el mismo número de teléfono que el de su proveedor de conexión troncal SIP, como NetFoundry o Twilio.

   **Nota:** Debe incluir el código de país y de área cuando especifique el número de teléfono en el panel de control _Gestionar_ del agente de voz. Por ejemplo, `18884253968`.

* Verifique que las credenciales de servicio de Watson, los URL y el ID de espacio de trabajo de {{site.data.keyword.conversationshort}} son válidos.
* Verifique que el diálogo de la habilidad de {{site.data.keyword.conversationshort}} se ha creado correctamente.
  * Puede importar la [conversación de ejemplo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) desde GitHub para una habilidad preconfigurada. Consulte el [Paso 3 de la *Guía de aprendizaje de iniciación*](/docs/services/voice-agent?topic=voice-agent-getting-started-tutorial#step3) para obtener detalles sobre cómo guardar la conversación de ejemplo como un archivo JSON y luego importar el archivo como una habilidad en la herramienta {{site.data.keyword.conversationshort}}.
  * Si ha creado su propio diálogo de {{site.data.keyword.conversationshort}}, verifique que el diálogo contiene un nodo con la condición `conversation_start` y un nodo con una respuesta predeterminada. Para obtener instrucciones detalladas, consulte [Creación de un diálogo](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog) en la documentación de {{site.data.keyword.conversationshort}}.
* Consulte si la llamada telefónica aparece en el panel de control _Uso_ del agente de voz. Si ve un elemento para su llamada telefónica, entonces el agente de voz se ha conectado al servicio de Watson.

### ¿Por qué no puedo especificar un número de teléfono al crear un agente de voz?

Consulte si el número de teléfono especificado está siendo utilizado por un agente de voz existente. Sólo puede tener un agente de voz para un número de teléfono. Puede indicar otro número de teléfono de su proveedor de conexión troncal SIP y utilizarlo para crear otro agente de voz. O bien, [suprima el agente de voz existente en el panel de control _Gestionar_](/docs/services/voice-agent?topic=voice-agent-managing#delete_va) para liberar el número de teléfono y luego cree un nuevo agente de voz.

### ¿Por qué las llamadas fallan con frecuencia?

Los agentes de voz pueden tener problemas cuando las llamadas fallan, porque un motor de orquestación de servicio (SOE) inicia una transacción larga, y no responde a su agente de voz de forma oportuna. Si una transacción supera el tiempo de espera predeterminado de {{site.data.keyword.conversationshort}}, la llamada falla. Para evitar fallos en llamadas, el SOE puede modificar el tiempo de espera predeterminado de {{site.data.keyword.conversationshort}} utilizando la variable de estado `vgwConversationResponseTimeout`. Consulte [Variables de estado definidas en el diálogo de {{site.data.keyword.conversationshort}}](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv).
