---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Usando instâncias de serviço em outras áreas de trabalho do {{site.data.keyword.Bluemix_notm}}
{: #other_service}

É possível configurar seu agente de voz para usar instâncias de serviço {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} que pertencem a áreas de trabalho em outras contas do {{site.data.keyword.Bluemix_short}}.
{: shortdesc}

Para conectar o seu agente de voz a outras instâncias de serviço, é possível utilizar o nome de usuário e as credenciais de senha
ou uma chave API para as suas instâncias de serviço.

1. Na guia _Agentes de voz_ no painel _Gerenciar_, selecione **Criar um novo agente de voz** ou um agente de voz que deseja editar.

1. No {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} selecione **Outra instância de serviço** para o **Tipo de serviço** e, então, selecione a **Região**.

1. Escolha um **Nome de usuário e senha** ou **Chave API** e insira as suas credenciais de
serviço.
  Para localizar esses valores, acesse a instância de serviço que você deseja configurar e selecione **Credenciais de serviço** e, em seguida, **Visualizar credenciais**.

  * **Nome de usuário e senha**: nos campos **URL**, **Nome do
usuário** e **Senha**, configure as credenciais para as suas instâncias de serviço do {{site.data.keyword.conversationshort}},
do {{site.data.keyword.speechtotextshort}} ou do {{site.data.keyword.texttospeechshort}}.
  * **Chave API**: nos campos **URL** e **Chave API**, configure as
credenciais para as suas instâncias de serviço do {{site.data.keyword.conversationshort}}, do
{{site.data.keyword.speechtotextshort}} ou do {{site.data.keyword.texttospeechshort}}.

  As credenciais não são seu nome de usuário e senha do {{site.data.keyword.Bluemix_notm}}, mas credenciais criptografadas para a instância de serviço específica.
  {:tip}

1. Digite as informações da instância de serviço.

  * **{{site.data.keyword.conversationshort}}:** No campo **ID da área de trabalho**, insira o ID da área de trabalho que deseja usar com seu agente de voz. Para localizar o ID da área de trabalho, ative a ferramenta e, na área de trabalho que você deseja integrar, clique no ícone Ações (**&vellip;**) e selecione **Visualizar detalhes**.
  * **{{site.data.keyword.speechtotextshort}}:** para **Selecionar tipo de modelo**, escolha **Banda estreita**, **Banda larga** ou **Banda larga e banda estreita** e, então, selecione o **Modelo** de idioma.
  * **{{site.data.keyword.texttospeechshort}}:** No campo **Voz**, selecione o idioma e a voz que seu serviço usa. Deve-se especificar uma voz para o seu serviço.

**Lembre-se:** para que seu agente de voz funcione, deve-se configurar seu {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} para o mesmo idioma. Consulte [Idiomas suportados](about.html#supported-languages).
