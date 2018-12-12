---

copyright:
  years: 2018
lastupdated: "2018-11-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Segurança de informações e privacidade de dados
{: #infosec}

A IBM está comprometida em fornecer aos nossos clientes e parceiros soluções inovadoras de privacidade de dados, segurança e governança.
{: shortdesc}

## Manipulação de informações e opções de configuração
{: #configure_infosec}

O {{site.data.keyword.iva_short}} não armazena, coleta nem processa dados recebidos dos clientes. Em vez disso, os dados são roteados para diferentes serviços para processamento. Durante a conversa, os usuários podem compartilhar informações que contêm Informação protegida de saúde (PHI), Informações pessoalmente identificáveis (PII) ou dados do Padrão de Segurança de Dados do Setor de Cartão de Pagamento (PCI DSS). Consulte [Arquitetura](about.html#architecture){: new_window} para saber mais sobre o fluxo de conversa e a arquitetura do {{site.data.keyword.iva_short}}.

Considere os recursos a seguir ao configurar sua instância de agente de voz para suportar privacidade de dados e manipulação segura.

### Transferência de chamada
{:  #calltransfer_infosec}

Ao incluir recursos de transferência de chamada em seu agente de voz, você fornece um número do telefone ao configurar o URI do SIP de destino de transferência. Os usuários não devem fornecer um número do telefone pessoal para esse destino de transferência.

Consulte [Configurando transferência de chamada](call-transfer.html) para saber mais sobre configurar seu Tronco SIP e o URI do SIP para transferência de chamada.

### Encaminhamento de Eventos
{: #event_forwarding}

É possível configurar seu agente de voz para encaminhar eventos de relatório a uma instância de banco de dados do {{site.data.keyword.cloudantfull}}. Esses eventos de relatório podem incluir dados de PII, PHI e PCI DSS sobre seus responsáveis pela chamada na forma de transcrições, eventos de turno de conversa e eventos de registro de detalhe de chamada (CDR). Os dados de chamada e os eventos de relatório não são armazenados, processados nem coletados no {{site.data.keyword.iva_short}} e os usuários devem configurar seus serviços externos do {{site.data.keyword.cloudant_short_notm}} apropriadamente. **Por padrão, o encaminhamento de eventos é desativado.**

Consulte [Ativando o encaminhamento de eventos](event-forwarding.html) para configurar seus agentes de voz para encaminhar eventos de relatórios.

Consulte [**{{site.data.keyword.cloudant_short_notm}}: segurança**](../Cloudant/offerings/security.html#security){: new_window} para obter mais informações sobre privacidade de dados e segurança de informações para o {{site.data.keyword.cloudant_short_notm}}.

### Armazenamento em cache de Texto para fala
{: #tts_caching}

Para conversar com clientes, o {{site.data.keyword.conversationshort}} produz respostas como texto, que são passadas para o serviço {{site.data.keyword.texttospeechshort}} e faladas em voz alta no {{site.data.keyword.iva_short}}. As respostas que o {{site.data.keyword.conversationshort}}
cria podem conter informações confidenciais. Para impedir o {{site.data.keyword.iva_short}} de armazenar em cache respostas recebidas do serviço {{site.data.keyword.texttospeechshort}} que contenham dados pessoais, é possível permitir que o comando de ação `vgwActExcludeFromTTSCache` impeça elocuções que contenham certos tipos de informações de serem armazenadas em cache. Consulte [Programando os agentes de voz usando a API](api.html#action-sequences).

### Conexões Seguras
{: #secure_trunking}

O {{site.data.keyword.iva_short}} é baseado no {{site.data.keyword.Bluemix_notm}} e integra-se aos Troncos SIP que os usuários configuram. Como os Troncos SIP são externos e se conectam ao {{site.data.keyword.iva_short}}, é possível ativar conexões seguras entre seus Troncos SIP e o {{site.data.keyword.iva_short}} usando o Protocolo de Transporte em Tempo Real Seguro (SRTP) e criptografia usando SIP seguro (SIPS), que conta com a Segurança da Camada de Transporte (TLS). Consulte [Protegendo Conexões](secure-trunking.html).

### Configuração do mecanismo de orquestração de serviço (SOE)
{: #SOE_config}

É possível usar um mecanismo de orquestração de serviço (SOE) para processar informações que passam entre o {{site.data.keyword.iva_short}} e o {{site.data.keyword.conversationshort}} para customizar conversas com os responsáveis pela chamada. Para manter conexões seguras, assegure-se de configurar seu SOE usando uma URL segura (`https`) e a autenticação de usuário.

Consulte [Configurando o {{site.data.keyword.conversationshort}} para seu agente de voz](managing_SOE.html#conversation_va) e [Arquitetura com um mecanismo de orquestração de serviço](about.html#arch-soe).

## Serviços relacionados ao {{site.data.keyword.iva_short}}
{: #related_services}

O {{site.data.keyword.iva_short}} orquestra diferentes serviços do {{site.data.keyword.Bluemix_notm}} para coordenar a comunicação entre usuários finais e serviços cognitivos baseados em nuvem. O {{site.data.keyword.iva_short}} em si não armazena, coleta nem processa dados de uma forma que viola direitos de usuário final. Entretanto, dependendo de como você configura os serviços relacionados, esses serviços integrados podem coletar informação protegida de saúde (PHI), informações pessoalmente identificáveis (PII) ou dados do Padrão de Segurança de Dados do Setor de Cartão de Pagamento (PCI DSS) que os usuários compartilham durante a conversa. Para saber mais sobre a arquitetura do {{site.data.keyword.iva_short}} e o fluxo de conversa, consulte [Arquitetura](about.html#architecture){: new_window}.

Consulte os recursos a seguir para localizar considerações para cada serviço e para o {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: conformidade de segurança**](../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}: segurança de informações**](../conversation/information-security.html){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: segurança de informações**](../text-to-speech/information-security.html){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: segurança de informações**](../speech-to-text/information-security.html){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: segurança**](../Cloudant/offerings/security.html#security){: new_window}
