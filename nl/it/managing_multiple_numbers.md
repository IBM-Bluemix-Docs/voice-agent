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


# Configurazione di più numeri di telefono per un _singolo agent_
{: #multi_num}

[comment]: # (Dopo che hai creato la tua istanza del servizio {{site.data.keyword.iva_full}}, )

Puoi aggiungere più numeri di telefono a un singolo agent in modo che la configurazione dell'agent interesserà tutti i numeri a esso associati. La pagina del dashboard _Manage Service Instance_ mostrerà il numero primario (**Primary Number**) associato all'agent. Vedi [Impostazione di un numero primario](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Puoi accedere alla finestra di dialogo **Manage** facendo clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

  * _**NOTA:**_ c'è un limite di 1000 numeri univoci per ogni configurazione di agent.
{: shortdesc}


## Aggiunta di un nuovo numero
{: #add_num}

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_ per aprire la finestra di dialogo **Manage**.

1. Fai clic sull'icona di aggiunta di un numero ("Add Number") vicino alla parte superiore destra della finestra di dialogo **Manage**. Nell'elenco verrà creata una nuova voce vuota.

1. {: #format_num} Per **Phone Number**, aggiungi il numero dal tuo trunk SIP, inclusi il prefisso internazionale e quello nazionale. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come 18883334444. Il numero di telefono può avere spazi e i caratteri + () - e un massimo di 30 caratteri.  

  * _**NOTA:**_ c'è un limite di 1000 numeri univoci per ogni configurazione di Voice Agent.

1. Facoltativamente, puoi fornire una descrizione per il tuo numero di telefono nel campo **Description**, fino a un massimo di 64 caratteri.

1. Fai clic sull'icona di "segno di spunta" per salvare il numero nell'elenco oppure fai clic sull'icona "X" per annullare l'aggiunta.

1. Nella parte superiore verrà visualizzato un messaggio "Success!". insieme a una voce nell'elenco con il nuovo numero. Altrimenti verrà visualizzato un messaggio di errore con una descrizione.

1. Il numero avrà un segno di spunta **verde** sotto la colonna Status nell'elenco che indica che il numero non presenta errori.

1. Fai clic su **Done** per salvare e confermare il numero per l'agent.

## Modifica di un numero e/o di una descrizione
{: #edit_num}

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_. In alternativa, se già hai più numeri di telefono nel Voice Agent, fai semplicemente clic sul campo **Phone Number** presentato in grigio per aprire la finestra di dialogo **Manage**.

1. Evidenzia la voce del numero che desideri modificare e fai clic sull'elenco di opzioni, rappresentato da un'icona di **tre punti** che viene visualizzata sul lato destro dell'elenco.

1. Dal menu a discesa che viene visualizzato, seleziona **Edit**.

1. Puoi ora apportare modifiche al numero di telefono (**Phone Number**) e/o alla descrizione (**Description**).

1. Fai clic sull'icona di "segno di spunta" per accettare l'aggiornamento oppure fai clic sull'icona "X" per annullare l'aggiornamento.

1. Nella parte superiore verrà visualizzato un messaggio "Success!". insieme alla voce nell'elenco che si sta aggiornando. Altrimenti verrà visualizzato un messaggio di errore con una descrizione.

1. Fai clic su **Done** per salvare le modifiche all'agent.

## Eliminazione di numeri
{: #delete_num}

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

1. Seleziona la casella bianca accanto a tutti i numeri che desideri eliminare. Per selezionare _tutti_ i numeri, seleziona semplicemente la casella bianca accanto all'intestazione **Phone Number**.

1. Fai clic sull'icona di eliminazione di elemento ("Delete Item") vicino alla parte superiore della finestra di dialogo **Manage**.

1. Nella parte superiore verrà visualizzato un messaggio "Success!" e le voci selezionate verranno rimosse dall'elenco. Altrimenti verrà visualizzato un messaggio di errore con una descrizione.

1. In alternativa, per eliminare un singolo numero, invece di selezionare la casella puoi evidenziare la voce del numero che desideri eliminare e fare clic sull'elenco di opzioni, rappresentato da un'icona di **tre punti**, che viene visualizzata sul lato destro dell'elenco.

1. Dal menu a discesa che viene visualizzato, seleziona **Delete**.

1. Nella parte superiore verrà visualizzato un messaggio "Success!" e la voce evidenziata verrà rimossa dall'elenco. Altrimenti verrà visualizzato un messaggio di errore con una descrizione.

1. Fai clic su **Done** per salvare e confermare l'eliminazione del numero o dei numeri dall'agent.

## Importazione di numeri
{: #import_num}

Un elenco di numeri può essere caricato nell'agent in una singola operazione. L'elenco _deve_ essere un file di tipo **.csv**. Il file può avere fino a, e comprendere, 1000 numeri di telefono (**Phone Numbers**) univoci, con un numero per ogni riga, insieme a una descrizione (**Description**) facoltativa per ciascun numero.

  * _**NOTA:**_ il caricamento dei numeri da un file .CSV sostituirà _TUTTI_ i numeri correnti nell'agent. L'elenco dei numeri _non_ verrà accodato ai numeri dal file .CSV.

  * I numeri nel file .CSV _devono_ essere conformi allo stesso formato dell'aggiunta di un numero mediante il dashboard e devono essere univoci. Vedi la sezione relativa al [formato dei numeri](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

1. Fai clic sull'icona di caricamento del file CSV ("Upload CSV File") accanto alla parte superiore destra della finestra di dialogo **Manage**.

1. Ti verrà presentata una finestra per confermare che sostituirai tutti i numeri esistenti nell'elenco con i numeri dal file .CSV. Fai clic su **OK** per confermare e procedere.

1. Nella nuova finestra, vai al file .CSV, selezionalo e fai clic su **Open**.

1. Nella parte superiore verrà visualizzato un messaggio "Success!" e tutti i nuovi numeri verranno aggiunti all'elenco. Altrimenti, verrà visualizzato un messaggio di errore con una descrizione, insieme ai messaggi di errore accanto a ciascun numero che presenta un problema.

1. I singoli numeri importati avranno un segno di spunta **verde** sotto la colonna _Status_ nell'elenco che indica che il numero non presenta errori. Altrimenti, nella colonna _Status_ verrà visualizzato uno specifico errore.

1. Fai clic su **Done** per salvare e confermare l'aggiunta del numero o dei numeri dall'agent.

## Esportazione di numeri
{: #export_num}

Un elenco di numeri e relative descrizioni può essere esportato dall'agent in un file **.CSV** e scaricato sul tuo computer. Ciò ti consentirà di modificare i numeri e/o le descrizioni come desideri e puoi caricarli nuovamente sull'agent. Vedi [Importazione di numeri](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

1. Fai clic sull'icona di download del file CSV ("Download CSV File") accanto alla parte superiore destra della finestra di dialogo **Manage**.

1. Un file .CSV di tutti i numeri salvati nell'agent verrà scaricato sul tuo computer.

1. Puoi fare clic su **Done** per uscire dalla finestra di dialogo **Manage**.

## Impostazione di un numero primario
{: #primary_num}

Il numero primario (_Primary Number_) è solo per scopi di visualizzazione e non ha alcuno scopo funzionale. Per impostazione predefinita, il primo numero aggiunto all'agent verrà etichettato come numero primario (**Primary Number**), che è il numero visualizzato nella pagina del dashboard _Manage Service Instance_. In un Voice Agent deve esistere almeno un numero primario (**Primary Number**).

Puoi modificare l'etichetta **Primary Number** in qualsiasi numero che desideri nel Voice Agent.

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

1. Evidenzia la voce del numero che desideri modificare e fai clic sull'elenco di opzioni, rappresentato da un'icona di **tre punti** che viene visualizzata sul lato destro dell'elenco.

1. Dal menu a discesa che viene visualizzato, seleziona **Set as primary**.

1. Nella parte superiore verrà visualizzato un messaggio "Success!". La voce da te scelta avrà l'etichetta **Primary** sotto la colonna _Status_. Altrimenti verrà visualizzato un messaggio di errore con una descrizione.

1. Fai clic su **Done** per salvare le modifiche all'agent.

## Ordinamento ed esplorazione dei numeri di telefono
{: #sort_num}

Puoi ordinare l'elenco di numeri in base ai _numeri di telefono_ o alle _descrizioni_, in ordine crescente o decrescente. Per impostazione predefinita, l'elenco dei numeri di telefono è ordinato in modo crescente in base al **numero di telefono**.

1. Fai clic sull'intestazione **Phone Number** per ordinare i numeri numericamente nell'elenco.

1. Fai clic sull'intestazione **Description** per ordinare i numeri alfabeticamente in base alla loro _descrizione_ nell'elenco.  

Puoi anche scegliere diverse quantità di numeri visualizzate per ogni pagina nell'elenco. Puoi visualizzare 5, 10, o 30 numeri per ogni pagina. Puoi anche spostarti tra le pagine dell'elenco.

1. Fai clic sul numero accanto a **Items per page** per scegliere quante voci di numero verranno visualizzate nell'elenco. Per impostazione predefinita, ne vengono visualizzate 5 per ogni pagina.

1. Fai clic sulla freccia rivolta a _destra_ o a _sinistra_ sopra l'intestazione **Status** per spostarti tra le pagine.

1. In alternativa, fai clic sul numero tra le frecce per scegliere manualmente una pagina da esplorare.

1. Fai clic su **Done** per salvare le modifiche all'agent.

## Salvataggio delle modifiche
{: #save_changes}

Se desideri apportare delle modifiche all'elenco di numeri nel Voice Agent, _devi_ salvare le modifiche nella finestra di dialogo **Manage** e salvare quindi le modifiche nella pagina _Edit Voice Agent_.

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

1. Apporta le eventuali modifiche ai numeri nell'elenco come desideri.

1. Fai clic su **Done** per salvare le modifiche all'agent.

1. Verrai riportato alla pagina _Edit Voice Agent_; fai clic su **Save Changes** nella parte superiore destra per applicare tutte le tue modifiche.

* _**NOTA:**_ _devi_ fare clic sia su **Done** nella finestra di dialogo **Manage** _sia su_ **Save Changes** nella pagina _Edit Voice Agent_ per salvare le tue modifiche, altrimenti verranno ignorate.

## Ricerca di numeri o descrizioni
{: #search_num}

Puoi cercare i numeri archiviati in base al numero o alla descrizione.

1. Fai clic su **Manage** accanto a **Phone Number** dalla pagina _Create a Voice Agent_ o _Edit Voice Agent_.

1. Nella barra _Search_, puoi immettere un numero o una descrizione da cercare nell'elenco. Man mano che digiti, i risultati della ricerca vengono aggiornati automaticamente.

1. Fai clic su **Done** per salvare le modifiche all'agent.
