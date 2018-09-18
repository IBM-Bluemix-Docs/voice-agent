---

copyright:
  years: 2018
lastupdated: "2018-08-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Seguridad de información y privacidad de datos
{: #infosec}

IBM está comprometido con ofrecer a nuestros clientes y partners soluciones innovadoras de privacidad, seguridad y control de los datos.
{: shortdesc}

## Manejo de información y opciones de configuración
{: #configure_infosec}

{{site.data.keyword.iva_short}} no almacena, recopila ni procesa datos recibidos de clientes. En su lugar, los datos se direccionan a distintos servicios para su proceso. Durante la conversación, los usuarios podrían compartir información que contiene PHI (información sanitaria personal), PII (información de identificación personal) o datos PCI DSS (PCI Data Security Standard). Consulte [Arquitectura](about.html#architecture){: new_window} para obtener más información sobre el flujo de conversación y la arquitectura de {{site.data.keyword.iva_short}}.

Tenga en cuenta las características siguientes al configurar la instancia del agente de voz para dar soporte a la privacidad de datos y al manejo seguro.

### Transferencia de llamada
{:  #calltransfer_infosec}

Al añadir prestaciones de transferencia de llamada a su agente de voz, proporcione un número de teléfono al configurar el URI SIP de destino de transferencia. Los usuarios no deberían proporcionar un número de teléfono personal para este destino de transferencia.

Consulte [Configuración de transferencia de llamada](call-transfer.html) para obtener información sobre cómo configurar la Conexión troncal SIP y URI SIP para la transferencia de llamadas.

### Reenvío de sucesos
{: #event_forwarding}

Puede configurar el agente de voz para reenviar sucesos de creación de informes a una instancia de base de datos de {{site.data.keyword.cloudantfull}}. Entre estos sucesos de creación de informes se pueden incluir datos PII, PHI y PCI DSS sobre los interlocutores en la forma de transcripciones, sucesos de turno de conversación y sucesos de registros de detalles de llamada (CDR). Los datos de llamada y los sucesos de creación de informes no se almacenan, procesan ni recopilan dentro de {{site.data.keyword.iva_short}}, y los usuarios deberían configurar sus servicios externos de {{site.data.keyword.cloudant_short_notm}} de forma apropiada. **De forma predeterminada, el reenvío de sucesos está inhabilitado.**

Consulte [Habilitación del reenvío de sucesos](event-forwarding.html) para configurar los agentes de voz para reenviar sucesos de creación de informes.

Consulte [**{{site.data.keyword.cloudant_short_notm}}: Seguridad**](../Cloudant/offerings/security.html#security){: #new_window} para obtener más información sobre la privacidad de datos y la seguridad de información para {{site.data.keyword.cloudant_short_notm}}.

### Almacenamiento en memoria caché de Text to Speech
{: #tts_caching}

Para conversar con los clientes, {{site.data.keyword.conversationshort}} personaliza respuestas como texto, que se pasan al servicio de {{site.data.keyword.texttospeechshort}} y se dicen en voz alta en {{site.data.keyword.iva_short}}. Las respuestas que crea {{site.data.keyword.conversationshort}} pueden contener información confidencial. Para impedir que {{site.data.keyword.iva_short}} almacene en memoria caché respuestas recibidas desde el servicio de {{site.data.keyword.texttospeechshort}} que contienen datos personales, puede habilitar el mandato de acción `vgwActExcludeFromTTSCache` para excluir que se almacenen en la memoria caché expresiones que contengan determinados tipos de información. Consulte [Programación de agentes de voz mediante la API](api.html#action-sequencess).

### Conexiones seguras
{: #secure_trunking}

{{site.data.keyword.iva_short}} se basa en {{site.data.keyword.Bluemix_notm}} y se integra con Conexiones troncales SIP que configuran los usuarios. Como las Conexiones troncales SIP son externas y se conectan con {{site.data.keyword.iva_short}}, puede habilitar conexiones seguras entre las Conexiones troncales SIP y {{site.data.keyword.iva_short}} utilizando SRTP (Secure Real Time Transport Protocol) y cifrado utilizando sip seguro (sips), que se basa en Transport Layer Security (TLS). Consulte [Protección de las conexiones](secure-trunking.html).

### Configuración del motor de orquestación de servicio (SOE)
{: #SOE_config}

Puede utilizar un motor de orquestación de servicio (SOE) para procesar información pasando entre {{site.data.keyword.iva_short}} y {{site.data.keyword.conversationshort}} para personalizar la conversación con los interlocutores. Para mantener las conexiones seguras, asegúrese de configurar su SOE utilizando un URL seguro, `https`, y autenticación de usuario.

Consulte [Configuración de {{site.data.keyword.conversationshort}} para el agente de voz](managing.html#conversation_va) y [Arquitectura con un motor de orquestación de servicio](about.html#arch-soe).

## Servicios relacionados con {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orquesta distintos servicios de {{site.data.keyword.Bluemix_notm}} para coordinar la comunicación entre usuarios finales y servicios cognitivos basados en la nube. {{site.data.keyword.iva_short}} en sí mismo no almacena, recopila ni procesa datos de una forma que infrinja los derechos del usuario final. Sin embargo, dependiendo de cómo configure los servicios relacionados, estos servicios integrados podrían recopilar PHI (información sanitaria personal), PII (información de identificación personal) o datos PCI DSS (PCI Data Security Standard) que los usuarios comparten durante la conversación. Para obtener más información sobre la arquitectura de {{site.data.keyword.iva_short}} y el flujo de conversación, consulte [Arquitectura](about.html#architecture){: new_window}.

Consulte los recursos siguientes para encontrar consideraciones para cada servicio y {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Conformidad de seguridad**](../../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}: Seguridad de información**](../conversation/information-security.html){: #new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Seguridad de información**](../text-to-speech/information-security.html){: #new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Seguridad de información**](../speech-to-text/information-security.html){: #new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Seguridad**](../Cloudant/offerings/security.html#security){: #new_window}
