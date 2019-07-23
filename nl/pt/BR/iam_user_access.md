---

copyright:

  years: 2019

lastupdated: "2019-06-06"
subcollection: "voice-agent"

keywords: Voice Agent IAM, Voice Agent user access, get started with IAM, IAM tutorial, IAM quick start, user access, SMS IAM, SMS user access

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Configurando o IAM e o acesso ao usuário
{: #iam}

Este tutorial é destinado a ajudá-lo a funcionar rapidamente com o IBM Cloud Identity and Access Management (IAM), convidando usuários para a sua conta e designando o acesso do Cloud IAM a esses usuários para uma instância do {{site.data.keyword.iva_short}}.
{:shortdesc}

## Antes de começar
{: #iam-before-you-begin}

Se você for novo usando o IAM, efetue check-out da documentação a seguir para entender mais sobre os recursos, conceitos e componentes do sistema de gerenciamento de acesso.

* O [IBM Cloud Identity and Access Management](/docs/iam?topic=iam-iamoverview) fornece uma visão geral rápida do que é o IAM na IBM, os recursos disponíveis e links para a CLI disponível e os docs da API.
* [Conceitos do IAM](/docs/iam?topic=iam-iamconcepts) descreve os conceitos de alto nível no IAM que podem ajudá-lo a entender os diferentes componentes à medida que você começar.
* O [acesso ao IAM](/docs/iam?topic=iam-userroles) fornece uma revisão mais detalhada de como o gerenciamento de acesso funciona usando as políticas de acesso.

Este guia cobrirá os cenários mais comuns para incluir e designar acesso aos usuários. Há muitas outras opções e configurações para acesso de usuário e funções. Os links anteriores fornecem mais detalhes. 

## Etapa 1. Convidar os usuários e designar o acesso inicial
{: #step1}

É possível convidar um ou mais usuários e configurar uma política de acesso inicial para os usuários no convite. Se você convidar múltiplos usuários em um convite, o mesmo acesso será designado a cada um deles. Na seção **acesso** da página **Convidar usuários**, você vê apenas as funções de usuário que você tem permissão para designar.

O proprietário da conta pode designar funções do Cloud IAM para usuários que são convidados na seção **Serviços**. Como o proprietário da conta, é possível fornecer acesso a:
* todos os recursos em um grupo de recursos
* todos os recursos para um serviço específico em um grupo de recursos 
* todos os serviços ativados por Identidade e Acesso na conta
* um único recurso na conta
* acesso aos serviços de gerenciamento de conta

Use o procedimento a seguir para designar funções do Cloud IAM para os usuários em sua conta.

1. Acesse **Gerenciar** &gt; **Acesso (IAM)** e selecione **Usuários**.
2. Clique em  ** Convidar usuários **.
3. Especifique o endereço de e-mail dos usuários que você deseja convidar.
4. Na seção **Acesso**, expanda a opção **Serviços**.
5. Escolha designar acesso a um **Recurso**, aos recursos em um **Grupo de
recursos** ou aos **Serviços de gerenciamento de conta**.
6. Dependendo de sua seleção, siga os prompts para especificar o acesso desejado. Se você selecionou a opção _Grupo de recursos_, também poderá fornecer ao usuário acesso para visualizar, editar ou gerenciar o acesso ao grupo de recursos, selecionando uma função para acesso ao grupo de recursos.
7. Na caixa de entrada **Serviços**, selecione *{{site.data.keyword.iva_short}}* no menu suspenso ou digite-o na caixa e pressione Enter. 
8. Selecione a **Região** e a **Instância de serviço** apropriadas.
9. Sob a seção **Selecionar funções**, escolha entre *Gerenciador*, *Gravador* e *Leitor*. Se a sua {{site.data.keyword.iva_short}} *Instância de serviço* estiver usando o SMS, então, você **deverá** selecionar a função *Gravador* ou *Gerenciador*, além de quaisquer outras funções que você desejar conceder.
    - Para obter mais informações sobre **Funções**, consulte [Funções de acesso de serviço](/docs/iam?topic=iam-userroles#service_access_roles).
10. Se você tiver permissão, também será possível designar o acesso ao Cloud Foundry ou à infraestrutura no convite.
11. Clique em  ** Convidar usuários **.

Para obter mais informações, veja [Convidando usuários e designando acesso](/docs/iam?topic=iam-iamuserinv#iamuserinv).

## Etapa 2. Criar grupos de acesso
{: #step2}

Para aperfeiçoar o processo de designação de acesso a usuários em sua conta, é possível criar grupos de acesso. Os grupos de acesso são uma maneira de organizar usuários e IDs de serviço para os quais é possível designar facilmente o acesso, definindo uma única política para o grupo inteiro.

### Configure seus grupos
{: #group_setup}

Para criar um grupo de acesso, conclua as etapas a seguir.

1. Na barra de menus, clique em **Gerenciar** &gt; **Acesso (IAM)** e selecione **Grupos de acesso**.
2. Clique em **Criar**.
3. Insira um nome para o seu grupo. A inclusão de uma descrição é opcional.
4. Clique em **Criar**.

Em seguida, continue a configurar o seu grupo, incluindo usuários ou IDs de serviço.

1. Você será levado para a página de grupo de acesso recém-criada. Esse grupo também aparecerá na lista de _Grupos_ na página **Grupos de acesso** na barra de menus.
2. Clique em **Incluir usuários**.
3. Selecione os usuários que deseja incluir na lista e clique em **Incluir no grupo**.
4. Para incluir IDs de serviço no grupo, clique em **IDs de serviço**.
5. Selecione os IDs que deseja incluir na lista e clique em **Incluir no grupo**.

### Designe acesso aos seus grupos
{: #group_access}

Depois de criar seus grupos, é possível designar acesso a todas as entidades dentro do grupo com uma única política ou múltiplas políticas.

1. Na barra de menus, clique em **Gerenciar** &gt; **Acesso (IAM)** e selecione **Grupos de acesso**.
2. Selecione o grupo para o qual você deseja designar acesso.
3. Na guia **Políticas de acesso**, clique em **Designar acesso** para configurar uma política de acesso. Repita conforme necessário para designar mais acesso.

Organizando usuários em grupos de acesso, é possível designar a um grupo de usuários acesso a uma única política, o que reduz o número geral de políticas que você precisa gerenciar.
{: tip}


## Etapa 3. Gerenciar o acesso para os usuários existentes
{: #user_access_manage}

A seção a seguir detalha como gerenciar e editar o acesso para usuários e grupos que você já configurou em sua conta.

### Designando novo acesso
{: #new_access}

Para designar uma nova política de acesso, conclua as etapas a seguir:

1. Na barra de menus, clique em **Gerenciar** &gt; **Acesso (IAM)** e selecione **Usuários**.
2. Selecione o nome do usuário para quem você deseja designar acesso.
3. Clique em **Políticas de acesso**.
4. Clique em  ** Designar acesso **.
5. Escolha como deseja designar o acesso:
    * Selecione **Designar acesso dentro de um grupo de recursos** para designar acesso a todos os recursos dentro de um grupo ou a recursos que são designados para um serviço específico dentro de um grupo. Também é possível conceder aos usuários permissão para visualizar, editar ou gerenciar o acesso ao grupo de recursos, designando a eles uma função de usuário para o grupo de recursos. Selecione **Sem acesso** se você desejar conceder a um usuário acesso apenas ao recurso especificado e não ao grupo de recursos.
    * Selecione **Designar acesso a recursos** para designar acesso a todos os recursos ativados pelo Identity and Access na conta, todos os recursos de um serviço específico na conta, uma única instância ou um único recurso em uma instância de serviço específica.
    * Selecione **Designar acesso aos serviços de gerenciamento de conta** para designar
acesso a todos os serviços de gerenciamento de conta ou a apenas um serviço de gerenciamento de conta.
5. Selecione qualquer combinação de funções para definir o escopo de acesso. Para obter mais informações, veja [Funções do Cloud IAM](/docs/iam?topic=iam-userroles#iamusermanrol).
6. Clique em  ** Designar **.


### Editando acesso existente
{: #editing_access}

É possível atualizar o acesso existente editando as funções designadas para um usuário.

1. Na barra de menus, clique em **Gerenciar** &gt; **Acesso (IAM)** e selecione **Usuários**.
2. Selecione o nome do usuário para o qual você deseja editar o acesso.
3. Clique em **Políticas de acesso**.
4. Clique em **Editar** no menu **Ações** ![Ícone Lista de ações](../icons/action-menu-icon.svg) na linha para a política que você deseja editar.
4. Edite a política atualizando as funções designadas.
5. Clique em **Salvar (Save)**.

É possível remover o acesso de um usuário clicando na opção **Remover** no menu **Ações** ![Ícone Lista de ações](../icons/action-menu-icon.svg) para a política que você deseja remover.

## Etapa 4. Designar acesso aos agentes do SMS ou Voice + SMS (Opcional)
{: #sms_access}

Se o agente ao qual você está designando acesso for um agente do **SMS** ou **Voice + SMS**, crie uma *Nova credencial*.

### Criando uma nova credencial
{: #new_cred}

Será possível criar credenciais somente para funções que já estiverem ativas em sua conta. Para os agentes do SMS e Voice + SMS, deve-se ter a função *Gravador* ou *Gerenciador* designada. Consulte [Etapa 9 de Convidar os usuários e designar o acesso inicial](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. No *Painel* de sua instância do {{site.data.keyword.iva_short}}, clique em **Nova credencial (+)**. 
2. Na nova caixa de diálogo que aparece por pop-up, insira um **Nome** e sob o menu suspenso **Função**, selecione *Gravador* ou *Gerenciador*. 
    - **NOTA:** para qualquer funcionalidade relacionada ao SMS, **_deve-se_** selecionar a função *Gravador* ou *Gerenciador*. 
3. Clique no botão **Incluir**.

## Solução de Problemas
{: #troubleshoot}

Se você vir uma mensagem de erro na página **Credenciais de serviço** ao tentar criar uma *Nova credencial* que diga:
> Você não tem a permissão necessária para designar a função ‘Gravador’. Entre em contato com o proprietário da conta para atualizar o seu acesso.

Então, você deverá seguir as instruções para designar o acesso *Gravador* ou *Gerenciador* a você mesmo, que é **necessário** para funções relacionadas ao SMS. Consulte [Etapa 9 de Designar acesso](/docs/services/voice-agent?topic=voice-agent-iam#step1) e, em seguida, continue com [A criação de uma nova credencial](/docs/services/voice-agent?topic=voice-agent-iam#new_cred).

## Próximas etapas
{: #next}

Saiba mais sobre o que o Cloud IAM pode executar, efetuando check-out da lista de [Recursos do Cloud IAM](/docs/iam?topic=iam-iamoverview#features).
