---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Preguntas frecuentes sobre precios
{: #faq-pricing}

## ¿Cuánto cuesta utilizar el servicio estándar de {{site.data.keyword.iva_short}}?
{: #faq-pricing-zero}
{: faq}

 Para obtener más información, consulte la [página de precios](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}.

## ¿Qué significa "precio por minuto"?
{: #faq-pricing-one}
{: faq}

El precio se basa en la cantidad (número de minutos) de audio que envía al servicio. El precio no depende de cuánto tarda el servicio en procesar el audio.


## ¿Se redondea al minuto más cercano para cada llamada a la API?
{: #faq-pricing-two}
{: faq}

'{{site.data.keyword.IBM_notm}} no calcula la duración del audio para cada llamada de API que el servicio recibe hasta el minuto más cercano. Lo que hace {{site.data.keyword.IBM_notm}} es sumar el uso mensual y luego redondear al minuto más cercano a final de mes. La duración de cada llamada se redondea al minuto siguiente. Por ejemplo, si la primera llamada dura 3,1 segundos y la segunda dura 25,9 segundos, {{site.data.keyword.IBM_notm}} calcula 4 segundos para la primera llamada y 26 segundos para la segunda. Luego la duración del audio total se calcula en un minuto.'


## ¿Cómo se calcula la conexión simultánea y dónde se aplica?
{: #faq-pricing-three}
{: faq}

La conexión simultánea solo se aplica a las llamadas de voz (no a SMS). La conexión simultánea se calcula como el número de conexiones a cualquier número de teléfono definido en la instancia de servicio simultáneamente. Se factura el número máximo diario real de conexiones simultáneas utilizadas, prorrateado según el cargo mensual.

## ¿Cuál es la definición de número máximo de conexiones simultáneas y cómo se modifica?

{: #faq-pricing-four}
{: faq}

El número máximo de conexiones simultáneas es el número máximo de conexiones permitidas en un momento dado, y es el número máximo de conexiones que se facturan. El número máximo de conexiones simultáneas se puede definir y modificar en el [panel de control](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency). La capacidad máxima simultánea de un plan estándar es de 50 conexiones, y, si necesita más, puede abrir una incidencia de soporte.

## ¿Cómo se facturan los mensajes de SMS/MMS de entrada y de salida?

{: #faq-pricing-five}
{: faq}

Los mensajes de entrada no se facturan hasta que se envía una respuesta al usuario. Se crea una sesión cuando se envía un mensaje de salida al usuario a través de Voice Gateway o como respuesta a un mensaje de entrada. Tanto los mensaje de salida como los mensaje de entrada a los que se responde se facturan, si procede.
Tanto los mensajes de salida como de entrada se facturan hasta que se excede el tiempo de espera de la sesión. Cuando la sesión supera el tiempo de espera, el contexto de la conversación se descarta. El tiempo de espera excedido predeterminado de una sesión es de 3600 segundos y los usuarios pueden configurar la duración del tiempo de espera excedido de una sesión en el panel de control.
