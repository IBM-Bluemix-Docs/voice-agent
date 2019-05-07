---

copyright:
  years: 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configurando vários números de telefone para um _único agente_
{: #multi_num}

[comment]: # (Após ter criando sua instância de serviço do {{site.data.keyword.iva_full}}, )

É possível incluir vários números de telefone em um único agente, de modo que a configuração do agente afetará todos os números associados a ele. A página do painel _Gerenciar instância de serviço_ mostrará o **Número primário** associado ao agente. Consulte [Configurando um número primário](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

É possível acessar a caixa de diálogo **Gerenciar** clicando em **Gerenciar** ao lado de **Número do telefone** na página _Criar um agente de voz_ ou _Editar agente de voz_.

  * _**NOTA:**_ há um limite de 1.000 números exclusivos por
configuração do agente.
{: shortdesc}


## Incluindo um novo número
{: #add_num}

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_ para abrir a caixa
de diálogo **Gerenciar**.

1. Clique no ícone "Incluir número" próximo à parte superior direita da caixa de diálogo **Gerenciar**. Uma nova entrada vazia será criada na lista.

1. {: #format_num} Para o **Número de telefone**, inclua o número do
seu tronco SIP, incluindo os códigos de país e de área. Por exemplo, para um número 800 dos Estados Unidos, especifique o número de telefone como 18883334444. O número de telefone pode ter espaços e os caracteres + ( ) - e um máximo de
30 caracteres.  

  * _**NOTA:**_ há um limite de 1.000 números exclusivos por
configuração do agente de voz.

1. Você pode, opcionalmente, fornecer uma descrição para seu número de telefone no campo **Descrição**, com no máximo 64 caracteres.

1. Clique no ícone "Visto" para salvar o número na lista ou clique no ícone "X" para cancelar a inclusão.

1. Uma mensagem "Sucesso!" será mostrada na parte superior, juntamente com uma entrada na lista com o novo número. Caso contrário, será mostrada uma mensagem de erro com uma descrição.

1. O número terá um visto **Verde** na coluna Status na lista, indicando que o número está livre de erros.

1. Clique em **Pronto** para salvar e confirmar o número para o agente.

## Editando um número e/ou uma descrição
{: #edit_num}

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. Como alternativa,
se você já tem vários números no agente de voz, basta clicar no campo **Número do telefone** esmaecido para abrir a caixa de diálogo **Gerenciar**.

1. Destaque a entrada de número que você deseja editar e clique na lista de opções, representada
pelo ícone **três pontos**, que aparece no lado direito da lista.

1. No menu suspenso que aparece, selecione **Editar**.

1. Agora é possível editar e fazer mudanças no **Número do telefone** e/ou
na **Descrição**.

1. Clique no ícone "Visto" para aceitar a atualização ou clique no ícone "X" para descartar a atualização.

1. Uma mensagem "Sucesso!" será mostrada na parte superior, juntamente com a entrada na lista que está sendo atualizada. Caso contrário, será mostrada uma mensagem de erro com uma descrição.

1. Clique em **Pronto** para salvar as mudanças no agente.

## Excluindo números
{: #delete_num}

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. 

1. Marque a caixa branca ao lado de todos os números que você deseja excluir. Para selecionar _todos_ os números, basta marcar a caixa branca ao lado do cabeçalho **Número
do telefone**.

1. Clique no ícone "Excluir item" próximo à parte superior direita da caixa de diálogo **Gerenciar**.

1. Uma mensagem "Sucesso!" será mostrada na parte superior e as entradas selecionadas serão removidas da lista. Caso contrário, será mostrada uma mensagem de erro com uma descrição.

1. Como alternativa, para excluir um único número, em vez de marcar a caixa, é possível destacar
a entrada de número que você deseja excluir e clicar na lista de opções, representada pelo ícone
**três pontos**, que aparece no lado direito da lista.

1. No menu suspenso que aparece, selecione **Excluir**.

1. Uma mensagem "Sucesso!" será mostrada na parte superior e a entrada destacada será removida da lista. Caso contrário, será mostrada uma mensagem de erro com uma descrição.

1. Clique em **Pronto** para salvar e confirmar a exclusão dos números do agente.

## Importando números
{: #import_num}

Uma lista de números pode ser carregada no agente de uma só vez. A lista _deve_ ser
um arquivo do tipo **.csv**. O arquivo pode ter até e incluindo 1.000 **Números
de telefone** exclusivos, com um número por linha, juntamente com uma **Descrição** opcional para cada número.

  * _**NOTA:**_ fazer upload de números de um arquivo .CSV substituirá _TODOS_ os números atuais no agente. A lista de números _não_ será anexada com os números do arquivo .CSV.

  * Números no arquivo .CSV _devem_ estar de acordo com o mesmo formato que ao
incluir um número no Painel e devem ser exclusivos. Consulte [Formato numérico](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. 

1. Clique no ícone "Fazer upload do arquivo CSV" próximo à parte superior direita da caixa
de diálogo **Gerenciar**.

1. Você será apresentado a uma janela para confirmar que substituirá todos os números existentes
na lista pelos números do arquivo .CSV. Clique em **OK** para confirmar e continuar.

1. Na nova janela, navegue para o arquivo .CSV, selecione-o e clique em **Abrir**.

1. Uma mensagem "Sucesso!" será mostrada na parte superior e todos os novos números serão incluídos na lista. Caso contrário, será mostrada uma mensagem de erro com uma descrição, juntamente com mensagens de erro próximas a cada número com um problema.

1. Os números importados individuais terão um visto **Verde** na coluna _Status_ na lista, indicando que o número está livre de erros. Caso contrário, um erro específico será exibido na coluna _Status_.

1. Clique em **Pronto** para salvar e confirmar a inclusão dos números do agente.

## Exportando números
{: #export_num}

Uma lista de números e suas descrições podem ser exportadas do agente para um arquivo **.CSV** e transferidas por download para o seu computador. Isso permitirá que
você modifique os números e/ou as descrições que desejar e poderá fazer upload deles novamente para
o agente. Consulte [Importando números](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. 

1. Clique no ícone "Fazer download do arquivo CSV" próximo à parte superior direita da caixa
de diálogo **Gerenciar**.

1. Um arquivo .CSV de todos os números salvos no agente será transferido por download para o seu computador.

1. É possível clicar em **Pronto** para sair da caixa de diálogo **Gerenciar**.

## Configurando um número primário
{: #primary_num}

O _Número primário_ é somente para propósitos de exibição e não serve a nenhum
propósito funcional. Por padrão, o primeiro número incluído no agente será rotulado como o **Número primário**, que é o número exibido na página de painel _Gerenciar instância de serviço_. Pelo menos um **Número primário** deve existir em um agente de voz.

É possível mudar o rótulo **Número primário** para qualquer número que
você desejar no agente de voz.

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. 

1. Destaque a entrada de número que você deseja editar e clique na lista de opções, representada
pelo ícone **três pontos**, que aparece no lado direito da lista.

1. No menu suspenso que aparece, selecione **Configurar como primário**.

1. Uma mensagem "Sucesso!" será mostrada na parte superior. Sua entrada escolhida terá o rótulo **Primário** na coluna _Status_. Caso contrário, será mostrada uma mensagem de erro com uma descrição.

1. Clique em **Pronto** para salvar as mudanças no agente.

## Classificando e navegando números de telefone
{: #sort_num}

É possível classificar a lista de números com base nos _Números de telefone_ ou nas _Descrições_, em ordem crescente ou decrescente. Por padrão, a lista de números de telefone é classificada por ordem crescente pelo **Número do telefone**.

1. Clique no cabeçalho **Número do telefone** para classificar numericamente
os números na lista.

1. Clique no cabeçalho **Descrição** para classificar os números alfabeticamente
por sua _Descrição_ na lista.  

Também é possível escolher quantidades variáveis de números mostrados por página na lista. É possível mostrar 5, 10 ou 30 números por página. Também é possível navegar para diferentes páginas de números.

1. Clique no número ao lado de **Itens por página** para escolher quantas entradas de número serão mostradas na lista. Por padrão, são mostrados cinco por página.

1. Clique na seta _Direita_ ou _Esquerda_ acima do cabeçalho **Status** para navegar entre as páginas.

1. Como alternativa, clique no número entre as setas para escolher manualmente uma página para navegar.

1. Clique em **Pronto** para salvar as mudanças no agente.

## Salvando mudanças
{: #save_changes}

Se você desejar fazer mudanças na lista de números no agente de voz, _deverá_ salvar as mudanças na caixa de diálogo **Gerenciar** e depois salvar as mudanças na página _Editar agente de voz_.

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. 

1. Faça quaisquer mudanças nos números na lista, conforme desejar.

1. Clique em **Pronto** para salvar as mudanças no agente.

1. Você será levado de volta para a página _Editar agente de voz_, clique em **Salvar mudanças** na parte superior direita para aplicar todas as suas mudanças.

* _**NOTA:**_ _Deve-se_ clicar em **Concluído** na caixa de diálogo **Gerenciar** _e_**Salvar mudanças** na página _Editar agente de voz_ para
salvar suas mudanças, caso contrário, elas serão descartadas.

## Procurando números ou descrição
{: #search_num}

É possível procurar números armazenados procurando o número ou a descrição.

1. Clique em **Gerenciar** ao lado de **Número do telefone**
na página _Criar um agente de voz_ ou _Editar agente de voz_. 

1. Na barra de _Procura_, é possível digitar um número ou uma descrição para
procurar na lista. Conforme você digita, os resultados da pesquisa serão atualizados automaticamente.

1. Clique em **Pronto** para salvar as mudanças no agente.
