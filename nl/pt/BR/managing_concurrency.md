---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Editando o máximo de conexões simultâneas
{: #edit_concurrency}

Se você usar os planos _Padrão_ ou _Premium_, será possível mudar o número máximo de conexões simultâneas por meio das configurações padrão.
{: shortdesc}

Em todos os planos, você recebe duas conexões simultâneas gratuitamente. Para obter mais informações, consulte os
[Planos de precificação](https://console.bluemix.net/catalog/services/voice-agent-with-watson). No painel _Gerenciar_, é possível ver o número máximo de conexões simultâneas que são permitidas em seu
plano listado em **Máximo de conexões simultâneas**. Também é possível ver o número máximo de conexões simultâneas
que são usadas por seus agentes de voz durante o mês atual em **Máximo de conexões simultâneas usadas**.

1. Acesse a guia _Instâncias_ no painel _Gerenciar_ para editar o máximo de conexões simultâneas no plano. 
1. Se você deseja mudar o número máximo de conexões simultâneas em seu plano, clique no ícone **Editar**.
1. Na
janela _Editar máximo de conexões simultâneas_, escolha o número máximo de conexões simultâneas e clique em **Salvar**.

O número mínimo de conexões simultâneas que pode ser configurado por meio de autoatendimento é 10 e o máximo é 50. Se você precisar
de mais de 50 conexões simultâneas para o seu agente de voz, consulte [Solicitando
configuração de rede assistida](connect-SIP.html#request-setup).

## Informações de conexão simultânea
{: #concurrent-charge}

  * Os planos _Lite_ e _Padrão_ incluem duas conexões simultâneas grátis.
  * Os planos _Premium_ são customizados por instância.
  * Em um plano _Standard_, você tem uma capacidade mínima de 10 conexões simultâneas.
  * O uso de conexão simultânea é rateado por mês. Se você usar mais de duas conexões simultâneas por dia, a taxa diária será cobrada. Por exemplo, como o seu
plano suporta duas conexões simultâneas gratuitas e você configura um limite máximo de 12 conexões, se você usar apenas cinco em um
dia, você será cobrado por três.
  * Se você tiver um plano _Padrão_ ou _Premium_, será possível comprar uma maior
capacidade de conexão simultânea.
  * Uma taxa diária é cobrada para a capacidade máxima de conexões simultâneas usadas em um dia.

Para obter mais informações sobre planos, taxas e recursos, consulte
[Planos de precificação](https://console.bluemix.net/catalog/services/voice-agent-with-watson).
