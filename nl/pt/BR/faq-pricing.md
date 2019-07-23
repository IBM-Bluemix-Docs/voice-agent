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

# Perguntas frequentes sobre precificação
{: #faq-pricing}

## Qual é o preço para usar o serviço padrão do {{site.data.keyword.iva_short}}?
{: #faq-pricing-zero}
{: faq}

 Para obter mais informações, consulte a [página de precificação](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}.

## O que significa "precificação por minuto"?
{: #faq-pricing-one}
{: faq}

O preço é baseado na quantia (número de minutos) de áudio que você envia para o serviço. O preço não depende de quanto tempo o serviço leva para processar o áudio.


## Você calcula para o minuto mais próximo de cada chamada para a API?
{: #faq-pricing-two}
{: faq}

'{{site.data.keyword.IBM_notm}} não calcula o comprimento do áudio para cada chamada de API que o serviço recebe para o minuto mais próximo. Em vez disso, o {{site.data.keyword.IBM_notm}} agrega o uso para o mês e, em seguida, calcula para o minuto mais próximo no término do mês. A duração de cada chamada é arredondada para o próximo minuto. Por exemplo, se você fizer a primeira chamada para 3,1 s e a segunda chamada para 25,9 s, o {{site.data.keyword.IBM_notm}} calculará a primeira chamada para 4 s e a segunda chamada para 26 s. Em seguida, a duração do áudio total será calculada para um minuto.'


## Como a conexão simultânea é calculada e em que ela é aplicada?
{: #faq-pricing-three}
{: faq}

A conexão simultânea é aplicável apenas à chamada de voz (Não SMS). A conexão simultânea é calculada como o número de conexões com quaisquer números de telefone definidos na instância de serviço simultaneamente. O número máximo diário real de conexões simultâneas usadas é faturado, rateado com base no encargo mensal.

## Qual é a definição de conexão máxima simultânea e como mudá-la?

{: #faq-pricing-four}
{: faq}

A conexão simultânea máxima é o número máximo de conexões que são permitidas a qualquer momento e é o número máximo de conexões que são faturadas. As conexões simultâneas máximas podem ser definidas e mudadas no [painel](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency). A capacidade máxima simultânea em um plano padrão é de 50 conexões e, se você precisar de mais, poderá abrir um chamado de suporte.

## Como as mensagens de SMS/MMS de entrada e de saída são faturadas?

{: #faq-pricing-five}
{: faq}

As mensagens de entrada não são faturadas até que uma resposta seja enviada para o usuário. Uma sessão é criada quando uma mensagem não enviada é enviada ao usuário por meio do Voice Gateway ou como uma resposta para uma mensagem de entrada. Ambas as mensagens de entrada e de saída que são respondidas são faturadas, se aplicável.
Ambas as mensagens de saída e de entrada são faturadas até que a sessão atinja o tempo limite. Após a sessão atingir o tempo limite, o contexto de conversa será descartado. O tempo limite da sessão padrão é de 3600 s e os usuários podem configurar a duração do tempo limite da sessão no painel.
