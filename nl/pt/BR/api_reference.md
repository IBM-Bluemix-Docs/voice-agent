---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tags de ação e variáveis de estado na API
{: #api-reference}

Use os materiais de referência para localizar as tags de ação que iniciam ações que o agente de voz executa durante uma sessão de conversa ou as variáveis de estado, que definem as características do agente de voz que persistem durante toda a conversa, a menos que mudem.
{: shortdesc}

Consulte [Programando os agentes de voz usando a API](/docs/services/voice-agent?topic=voice-agent-api) para obter exemplos de códigos e exemplos de como configurar os estados e iniciar as sequências de ação.

Como o {{site.data.keyword.iva_full}} é baseado no IBM Voice Gateway, a API funciona da mesma maneira. Se você estiver familiarizado com o Voice Gateway, poderá usar as mesmas ações e variáveis de estado em seus diálogos {{site.data.keyword.conversationshort}} com {{site.data.keyword.iva_short}}. Consulte [Tags de ação e variáveis de estado na API do
Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html).
{: tip}

## Comandos de ação e atributos
{: #actions-and-attributes}

A tabela a seguir lista as ações que podem ser especificadas no diálogo {{site.data.keyword.conversationshort}} e todos os atributos que podem ser definidos para cada ação.

| Comando de ação | Descrição | Atributos |
| ----- | ----- | ----- |
| `vgwActPlayText`| Reproduz uma elocução que é convertida em fala pelo serviço {{site.data.keyword.texttospeechshort}}. | <ul><li>`text`: uma lista de elocuções a serem reproduzidas. Opcional. <p>Por exemplo:<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> Por padrão, a ação reproduz uma lista de elocuções que são configuradas no campo `output.text`. </li><li>`errAudioURL`: uma URL para um arquivo de áudio que será reproduzido se o agente de voz não puder entrar em contato com o serviço {{site.data.keyword.texttospeechshort}} para concluir a ação. O arquivo de áudio deve estar no formato WAV.</li></ul>|
| `vgwActPlayUrl` | Reproduz um arquivo de áudio assim que o texto incluído é reproduzido, como para reproduzir música em espera (MOH) ou elocuções únicas comuns. Se nenhum texto for incluído, o áudio será reproduzido imediatamente. O arquivo deve ser de canal único (mono), codificado por PCM e ter uma taxa de amostragem de 8.000 Hz com 16 bits por amostra. | <ul><li>`url`: a URL a ser reproduzida. Necessário.</li><li> `playURLInLoop`: Opcionalmente, configure como `Yes` ou `No` para indicar se a URL deve ser reproduzida em um loop. O valor padrão é `Não`.</li></ul> |
| `vgwActHangup` | Desliga a chamada. | Nenhum atributo. |
| `vgwActSetSTTConfig` | Aplica um conjunto de parâmetros para o agente de voz para passar para o serviço {{site.data.keyword.speechtotextshort}} do Watson. O serviço {{site.data.keyword.conversationshort}} define dinamicamente os parâmetros com base na chamada. | Os atributos são transmitidos de forma transparente como propriedades JSON para o serviço {{site.data.keyword.speechtotextshort}}. |
| `vgwActSetTTSConfig` | Aplica um conjunto de parâmetros para o agente de voz para passar para o serviço {{site.data.keyword.texttospeechshort}} do Watson. O serviço {{site.data.keyword.conversationshort}} define dinamicamente os parâmetros com base na chamada. |  Os atributos são transmitidos de forma transparente como propriedades JSON para o serviço {{site.data.keyword.texttospeechshort}}.  |
| `vgwActSetConversationConfig` | Aplica um conjunto de parâmetros para o agente de voz para definir uma área de trabalho {{site.data.keyword.conversationshort}}. O serviço {{site.data.keyword.conversationshort}} define dinamicamente os parâmetros com base na chamada. | <ul><li>`url`: a credencial `url` para a API de serviço {{site.data.keyword.conversationshort}}.</li><li>`workspaceID`: ID da área de trabalho {{site.data.keyword.conversationshort}}</li><li>`username`: a credencial `username` para o serviço {{site.data.keyword.conversationshort}}, com até 64 caracteres.</li><li>`password`: a credencial `password` para o serviço {{site.data.keyword.conversationshort}}, com até 256 caracteres.</li></ul> |
| `vgwActCollectDtmf` | Instrui o agente de voz a coletar entrada de sinalização de multifrequência de sinal duplo (DTMF). | Um dos atributos a seguir deve ser definido. <ul><li> `dtmfTermKey`: a chave de finalização DTMF, que sinaliza o término da entrada DTMF. Por exemplo, "`#`". </li><li> `dtmfCount`: o número de dígitos DTMF a ser coletado.</li></ul> Quando qualquer uma dessas condições for atendida, o agente de voz parará de coletar a entrada DTMF. |
| `vgwActPauseDTMF` | Desativa a entrada DTMF. Toda entrada DTMF é ignorada até ser reativada pela ação `vgwActUnPauseDTMF`. | Nenhum atributo. |
| `vgwActUnPauseDTMF` | Ativa a entrada DTMF que foi desativada pela ação `vgwActPauseDTMF`. | Nenhum atributo. |
| `vgwActExcludeFromTTSCache` | Instrui o agente de voz a não armazenar em cache a resposta do serviço {{site.data.keyword.texttospeechshort}}. Por exemplo, as respostas que contêm dados confidenciais de PHI, PII e PCI DSS ou informações dinâmicas como nomes de clientes ou datas de nascimento devem ser excluídas. <br/>Essa tag de ação deve ser configurada no nó de diálogo do {{site.data.keyword.conversationshort}} para cada elocução que você não deseja armazenar em cache. | Nenhum atributo. |
| `vgwActPauseSTT` | Pausa o processamento de fala para texto até que ele seja reativado pela ação `vgwActUnPauseSTT`. Se a gravação for ativada e o processamento de fala para texto for pausado, o áudio do responsável pela chamada não será capturado. | Nenhum atributo. |
| `vgwActUnPauseSTT` | Retoma o processamento de fala para texto que foi pausado anteriormente pela ação `vgwActPauseSTT`. | Nenhum atributo. |
| `vgwActEnableSpeechBargeIn` | Permite interromper a fala para que os responsáveis pela chamada possam interromper a reprodução do agente de voz ao falar. | Nenhum atributo. |
| `vgwActDisableSpeechBargeIn` | Desativa a interrupção da fala para que a reprodução do agente de voz não seja interrompida quando os responsáveis pela chamada falarem. | Nenhum atributo. |
| `vgwActEnableDTMFBargeIn`| Ativa a interrupção de DTMF para que os responsáveis pela chamada possam interromper a reprodução do agente de voz pressionando uma tecla. | Nenhum atributo. |
| `vgwActDisableDTMFBargeIn` | Desativa a interrupção de DTMF para que a reprodução do agente de voz não seja interrompida quando os responsáveis pela chamada pressionarem as teclas. | Nenhum atributo. |
| `vgwActForceNoInputTurn` | Força um novo turno na conversa sem esperar pela entrada do responsável pela chamada. | Nenhum atributo. |
{: caption="Tabela 1. Ações que podem ser iniciadas por meio do serviço {{site.data.keyword.conversationshort}}" caption-side="top"}

## Variáveis de estado configuradas no diálogo {{site.data.keyword.conversationshort}}
{: #state-variables-conv}

É possível configurar as seguintes variáveis de estado dentro do diálogo {{site.data.keyword.conversationshort}} para modificar o comportamento do agente de voz.

| Nome da variável de estado | Valor esperado | Descrição |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | Usuário definido | Define um cabeçalho customizado em uma mensagem SIP BYE de saída. O valor do cabeçalho customizado é definido pelas variáveis de estado `vgwByeCustomHeaderVal`.  |
| `vgwByeCustomHeaderVal` | Usuário definido | Define o valor de um cabeçalho customizado em uma mensagem SIP BYE de saída. O cabeçalho customizado é definido pelas variáveis de estado `vgwByeCustomHeader`. |
| `vgwPostResponseTimeoutCount` | Tempo em milissegundos | O período de tempo a esperar por uma nova elocução depois de a resposta ser reproduzida para o responsável pela chamada. Se esse valor for excedido, o {{site.data.keyword.conversationshort}} receberá uma atualização de texto com a palavra "vgwPostResponseTimeout" para indicar que ocorreu um tempo limite.|
| `vgwConversationFailedMessage` | Sequência de texto | Mensagem transmitida ao responsável pela chamada se o serviço {{site.data.keyword.conversationshort}} falhar. Configure seu diálogo {{site.data.keyword.conversationshort}} para definir essa variável na primeira vez. |
| `vgwSessionInactivityTimeout` | Tempo em minutos <br/><br/>Padrão: `2` | O intervalo de tempo limite de inatividade. O valor do intervalo de tempo limite especifica em minutos quanto tempo o agente de voz permite que uma sessão fique inativa. Quando o tempo limite expira, o agente de voz termina a sessão. |
| `vgwErrAudioURL` | Usuário definido | Uma URL para um arquivo de áudio que será reproduzido se o serviço {{site.data.keyword.texttospeechshort}} não puder ser contatado quando o agente de voz tentar reproduzir uma resposta. O arquivo de áudio deve estar no formato WAV. |
{: caption="Tabela 2. Variáveis definidas pelo serviço {{site.data.keyword.conversationshort}}" caption-side="top"}

## Variáveis de estado definidas pelo agente de voz
{: #state-variables-iva}

| Nome da variável de estado | Valor esperado | Descrição |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | Definido pelo usuário <br/><br/> Padrão: `Call-ID` | Um cabeçalho de ID de sessão
customizado que é extraído da solicitação SIP INVITE. O valor representa o ID de sessão global que é usado em todos os logs de auditoria do agente de voz relacionados à sessão. |
| `vgwSIPCallID` | `Call-ID` SIP | O ID de chamada SIP associado à chamada. |
| `vgwSIPRequestURI` | `Request-URI` SIP | O URI de solicitação SIP que iniciou a chamada. |
| `vgwSIPToURI` | URI `To` SIP | O URI `To` SIP associado à chamada. |
| `vgwSIPFromURI` | URI `From` SIP | O URI `From` SIP associado à chamada. |
| `vgwBargeInOccurred` | `Yes` / `No` | Indica se ocorreu ou não a interrupção. |
| `vgwHangUp` | `Yes` / `No` | Indica se a conversa foi terminada. |
| `vgwHangupReason` | Sequência | Quando um desligamento é iniciado, seja pelo responsável pela chamada ou por causa
de um erro, essa variável é enviada para o serviço {{site.data.keyword.conversationshort}} para indicar o motivo da
desconexão da chamada. O texto na solicitação de mensagem que é enviado para o serviço {{site.data.keyword.conversationshort}} também inclui "vgwHangUp". |
| `vgwConversationResponseTimeout` | Tempo em segundos<br/><br/>Padrão: `5`  | O tempo em segundos que o agente de voz aguarda por uma resposta do serviço {{site.data.keyword.conversationshort}}. Se o tempo for excedido, o agente de voz tentará novamente contatar o serviço {{site.data.keyword.conversationshort}}. Se o serviço ainda não puder ser atingido, a chamada falhará. |
| `vgwSTTResponse` | Objeto JSON | A resposta final do serviço {{site.data.keyword.speechtotextshort}}
no formato JSON, incluindo a transcrição e a pontuação de confiança para a hipótese preferencial e quaisquer alternativas. <p>Por
exemplo, o formato a seguir corresponde exatamente ao formato que é recebido do serviço {{site.data.keyword.speechtotextshort}}:</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Yes` / `No` | Indica se a entrada para o serviço {{site.data.keyword.conversationshort}} é sinalização de multifrequência de sinal duplo (DTMF). |
{: caption="Tabela 3. Variáveis definidas pelo agente de voz" caption-side="top"}
