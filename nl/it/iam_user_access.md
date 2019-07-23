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

# Configurazione di IAM e dell'accesso utente
{: #iam}

Questa esercitazione è pensata per aiutarti ad iniziare ad utilizzare velocemente IBM Cloud Identity and Access Management (IAM) invitando degli utenti nel tuo account e assegnando l'accesso Cloud IAM a tali utenti per un'istanza {{site.data.keyword.iva_short}}.
{:shortdesc}

## Prima di cominciare
{: #iam-before-you-begin}

Se non hai esperienza con l'utilizzo di IAM, consulta la seguente documentazione per comprendere meglio le funzioni, i concetti e i componenti del sistema di gestione dell'accesso.

* [IBM Cloud Identity and Access Management](/docs/iam?topic=iam-iamoverview) fornisce una veloce panoramica di cosa è IAM in IBM, delle funzioni disponibili e dei link alla documentazione CLI e API disponibile.
* [Concetti di IAM](/docs/iam?topic=iam-iamconcepts) illustra i concetti di alto livello in IAM che possono aiutarti a comprendere i diversi componenti quando inizi ad utilizzarli.
* [Accesso IAM](/docs/iam?topic=iam-userroles) fornisce un'analisi approfondita di come funziona la gestione dell'accesso utilizzando le politiche di accesso.

Questa guida illustrerà gli scenari più comuni per l'aggiunta e l'assegnazione dell'accesso agli utenti. Esistono molte altre opzioni e configurazioni per i ruoli e l'accesso utente. I precedenti link forniscono ulteriori dettagli. 

## Passo 1. Invita gli utenti e assegna l'accesso iniziale
{: #step1}

Puoi invitare uno o più utenti e impostare una politica di accesso iniziale per gli utenti al momento dell'invito. Se inviti più utenti in un unico invito, lo stesso accesso viene assegnato a ciascuno degli utenti. Nella sezione **Accesso** della pagina **Invita utenti**, sono visualizzati solo i ruoli utente che sei autorizzato ad assegnare. 

Il proprietario dell'account può assegnare i ruoli Cloud IAM agli utenti che sono stati invitati nella sezione **Servizi**. Come proprietario dell'account, puoi fornire l'accesso a:
* tutte le risorse in un gruppo di risorse
* a tutte le risorse per un servizio specifico in un gruppo di risorse  
* a tutti i servizi abilitati per l'accesso e l'identità nell'account 
* a una singola risorsa nell'account
* l'accesso ai servizi di gestione dell'account 

Utilizza la seguente procedura per assegnare i ruoli Cloud IAM agli utenti nel tuo account.

1. Vai a **Gestisci** &gt; **Accesso (IAM)** e seleziona **Utenti**.
2. Fai clic su **Invita utenti**.
3. Specifica l'indirizzo e-mail degli utenti che vuoi invitare.
4. Nella sezione **Accesso**, espandi l'opzione **Servizi**.
5. Scegli di assegnare l'accesso a una **Risorsa**, alle risorse all'interno di un **Gruppo di risorse** o ai **Servizi di gestione dell'account**.
6. A seconda della tua selezione, segui le istruzioni per specificare l'accesso desiderato. Se hai selezionato l'opzione _Gruppo di risorse_, puoi anche fornire all'utente l'accesso per visualizzare, modificare o gestire l'accesso al gruppo risorse selezionando un ruolo per l'accesso al gruppo di risorse. 
7. Nella casella di input **Servizi**, seleziona *{{site.data.keyword.iva_short}}* dal menu a discesa o immettilo nella casella e premi Invio. 
8. Seleziona la **Regione** e l'**Istanza del servizio** appropriate.
9. Nella sezione **Seleziona ruoli**, scegli tra *Gestore*, *Scrittore* e *Lettore*. Se la tua *Istanza del servizio* {{site.data.keyword.iva_short}} sta utilizzando SMS, **devi** selezionare il ruolo *Scrittore* o *Gestore*, in aggiunta a tutti gli altri ruoli che desideri concedere.
    - Per ulteriori informazioni sui **Ruoli**, vedi [Ruoli di accesso al servizio](/docs/iam?topic=iam-userroles#service_access_roles).
10. Se disponi dell'autorizzazione, puoi anche assegnare l'accesso a Cloud Foundry o all'infrastruttura al momento dell'invito.
11. Fai clic su **Invita utenti**.

Per ulteriori informazioni, vedi [Invito di utenti e assegnazione dell'accesso](/docs/iam?topic=iam-iamuserinv#iamuserinv).

## Passo 2. Crea i gruppi di accesso
{: #step2}

Per semplificare il processo di assegnazione dell'accesso agli utenti nel tuo account, puoi creare i gruppi di accesso. I gruppi di accesso sono un modo per organizzare gli utenti e gli ID servizio a cui puoi assegnare facilmente l'accesso definendo una singola politica per l'intero gruppo.

### Configura i tuoi gruppi
{: #group_setup}

Per creare un gruppo di accesso, completa la seguente procedura.

1. Dalla barra dei menu, fai clic su **Gestisci** &gt; **Accesso (IAM)** e seleziona **Gruppi di accesso**.
2. Fai clic su **Create**.
3. Immetti un nome per il tuo gruppo. L'aggiunta della descrizione è facoltativa.
4. Fai clic su **Create**.

Successivamente, continua a configurare il tuo gruppo aggiungendo utenti o ID servizio.

1. Sarai portato alla pagina del gruppo di accesso appena creato. Questo gruppo sarà visualizzato anche nell'elenco _Gruppo_ nella pagina **Gruppi di accesso** nella barra dei menu.
2. Fai clic su **Aggiungi utenti**.
3. Seleziona gli utenti che vuoi aggiungere dall'elenco e fai clic su **Aggiungi al gruppo**.
4. Per aggiungere gli ID servizio al gruppo, fai clic su **ID servizio**.
5. Seleziona gli ID che vuoi aggiungere dall'elenco e fai clic su **Aggiungi al gruppo**.

### Assegna l'accesso ai tuoi gruppi
{: #group_access}

Dopo aver creato i tuoi gruppi, puoi assegnare l'accesso a tutte le entità all'interno del gruppo con un'unica politica o più politiche.

1. Dalla barra dei menu, fai clic su **Gestisci** &gt; **Accesso (IAM)** e seleziona **Gruppi di accesso**.
2. Seleziona il gruppo a cui vuoi assegnare l'accesso.
3. Dalla scheda **Politiche di accesso**, fai clic su **Assegna accesso** per configurare una politica di accesso. Ripeti secondo necessità per assegnare ulteriore accesso.

Organizzando gli utenti in gruppi di accesso, puoi assegnare l'accesso a un gruppo di utenti a una singola politica, il che riduce il numero complessivo di politiche che devi gestire.
{: tip}


## Passo 3. Gestisci l'accesso per gli utenti esistenti
{: #user_access_manage}

La seguente sezione illustra come gestire e modificare l'accesso per gli utenti e i gruppi che hai già configurato nel tuo account.

### Assegnazione del nuovo accesso
{: #new_access}

Per assegnare una nuova politica di accesso, completa la seguente procedura:

1. Dalla barra dei menu, fai clic su **Gestisci** &gt; **Accesso (IAM)** e seleziona **Utenti**.
2. Seleziona il nome dell'utente a cui vuoi assegnare l'accesso.
3. Fai clic su **Politiche di accesso**.
4. Fai clic su **Assegna accesso**.
5. Scegli in che modo assegnare l'accesso:
    * Seleziona **Assegna l'accesso in un gruppo di risorse** per assegnare l'accesso a tutte le risorse all'interno di un gruppo oppure alle risorse designate per uno specifico servizio all'interno di un gruppo. Puoi anche concedere agli utenti l'autorizzazione per visualizzare, modificare o gestire l'accesso al gruppo di risorse assegnandogli un ruolo utente per il gruppo di risorse. Seleziona **Nessun accesso** se vuoi concedere a un utente l'accesso solo alla risorsa specificata e non a tutto il gruppo di risorse.
    * Seleziona **Assegna l'accesso alle risorse** per assegnare l'accesso a tutte le risorse abilitate all'accesso e l'identità nell'account, a tutte le risorse di uno specifico servizio nell'account, a una singola istanza o a una singola risorsa all'interno di una specifica istanza del servizio.
    * Seleziona **Assegna l'accesso ai servizi di gestione account** per assegnare l'accesso a tutti i servizi di gestione dell'account o solo a uno di essi.
5. Seleziona qualsiasi combinazione di ruoli per definire l'ambito di accesso. Per ulteriori informazioni, vedi [Ruoli Cloud IAM](/docs/iam?topic=iam-userroles#iamusermanrol).
6. Fai clic su **Assegna**.


### Modifica dell'accesso esistente
{: #editing_access}

Puoi aggiornare l'accesso esistente modificando i ruoli assegnati per un utente.

1. Dalla barra dei menu, fai clic su **Gestisci** &gt; **Accesso (IAM)** e seleziona **Utenti**.
2. Seleziona il nome dell'utente per cui vuoi modificare l'accesso.
3. Fai clic su **Politiche di accesso**.
4. Fai clic su **Modifica** dal menu **Azioni** ![Icona Elenco di azioni](../icons/action-menu-icon.svg) sulla riga della politica che vuoi modificare.
4. Modifica la politica aggiornando i ruoli assegnati.
5. Fai clic su **Salva**.

Puoi rimuovere l'accesso da un utente facendo clic sull'opzione **Rimuovi** dal menu **Azioni** ![Icona Elenco di opzioni](../icons/action-menu-icon.svg) per la politica che vuoi rimuovere.

## Passo 4. Assegna l'accesso agli agent SMS o Voice + SMS (facoltativo)
{: #sms_access}

Se l'agent a cui stai assegnando l'accesso è un agent **SMS** o **Voice + SMS**, crea una *Nuova credenziale*.

### Creazione di una nuova credenziale
{: #new_cred}

Puoi creare le credenziali solo per i ruoli già attivi nel tuo account. Per gli agent SMS e Voice + SMS, ti deve essere stato assegnato il ruolo *Writer* o *Manager*. Vedi il [passo 9 di Invita gli utenti e assegna l'accesso iniziale](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. Sul *Dashboard* della tua istanza {{site.data.keyword.iva_short}}, fai clic su **New Credential (+)**. 
2. Nella nuova casella di dialogo che viene visualizzata, immetti un nome (**Name**) e nel menu a discesa **Role**, seleziona *Writer* o *Manager*. 
    - **NOTA:** per tutte le funzionalità correlate SMS, **_devi_** selezionare il ruolo *Writer* o *Manager*. 
3. Fai clic sul pulsante **Add**.

## Risoluzione dei problemi
{: #troubleshoot}

Se visualizzi un messaggio di errore nella pagina **Service Credentials** quando tenti di creare una *Nuova credenziale* che indica:
> You do not have the required permission to assign role ‘Writer’. Contact the account owner to update your access.

Devi seguire le istruzioni per assegnare l'accesso da *Writer* o *Manager* a te stesso, cosa **obbligatoria** per le funzioni correlate SMS. Vedi il [passo 9 dell'assegnazione dell'accesso](/docs/services/voice-agent?topic=voice-agent-iam#step1) e continua con la [creazione di una nuova credenziale](/docs/services/voice-agent?topic=voice-agent-iam#new_cred).

## Passi successivi
{: #next}

Per ulteriori informazioni su cosa può fare Cloud IAM consulta l'elenco delle [Funzioni Cloud IAM](/docs/iam?topic=iam-iamoverview#features).
