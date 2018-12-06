---

copyright:
  years: 2018
lastupdated: "2018-10-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Eventos do rastreador de atividade
{: #activity-tracker}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e aplicativos interagem com o serviço {{site.data.keyword.iva_full}} no {{site.data.keyword.Bluemix}}. {: shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.Bluemix_notm}}. Para obter mais informações, consulte o [{{site.data.keyword.cloudaccesstrailshort}}](../cloud-activity-tracker/index.html#getting-started-with-cla).

## Lista de eventos
{: #event-List}

A tabela a seguir lista as ações que geram um evento.

|Action| descrição |
| --- | ---- |
| `create agent: POST /config/submitconfig` | Criar um novo agente de voz |
| `update agent: POST /config/submitconfig` | Atualizar um agente de voz |
| `Update concurrency: POST /config/updatemax` | Atualizar a simultaneidade máxima de chamada |
| `delete agent: POST /config/submitconfig` | Excluir um agente de voz |
{: caption="Tabela 1. Ações que geram eventos" caption-side="top"}

## Onde visualizar eventos de atividade
{: #view-event}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no domínio de contas do {{site.data.keyword.cloudaccesstrailshort}} que está disponível na região do {{site.data.keyword.Bluemix_notm}} na qual os eventos são gerados.

## Eventos de Filtragem
{: #filter_events}

### Filtrando por ID de agente de voz
{: #filter_id}

É possível filtrar a lista de eventos de atividade de um agente de voz específico pelo ID de instância dele.

1. Acesse a página **Gerenciar** no {{site.data.keyword.cloudaccesstrailshort}}.
2. Insira `target.name_str` no **Campo de procura** e seu ID de instância do agente de voz no campo **Procura** como uma sequência. Verifique se o ID da instância do agente de voz é percentualmente codificado e se você usa uma procura de caracteres curinga, _*_.

Por exemplo, para procurar seu ID da instância do agente de voz, `serviceInstanceId=crn%3A...`.

  * **Campo de procura**: `target.name_str`
  * **Procura**: `"*crn%3A...*"`

### Filtrando por evento de ação
{: #filter_action}

Também é possível filtrar a lista de eventos de atividades para eventos de ação específicos

1. Acesse a página **Gerenciar** no {{site.data.keyword.cloudaccesstrailshort}} e insira o valor de configuração a seguir para cada um dos campos.

  * **Visualizar logs**: `Space logs`
  * **Campo de procura**: `action_str`
  * **Procura**: `"action string"`

## Criando filtros avançados
{: #advanced_filters}

Também é possível criar filtros avançados usando `AND` ou `OR` para combinar termos de procura no campo **Procura**.

Por exemplo, filtre por um ID de instância do agente de voz específico e uma ação específica.

* **Visualizar logs**: `Space logs`
* **Campo de procura**: `target.name_str`
* **Procura**: `"*crn%3A...*" AND action_str:"action string"`

**Lembrete**: verifique se o ID da instância do agente de voz é percentualmente codificado e se você usa uma procura de caracteres curinga, _*_.
