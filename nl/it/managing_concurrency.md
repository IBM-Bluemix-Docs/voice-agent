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

# Modifica del numero massimo di connessioni simultanee
{: #edit_concurrency}

Se utilizzi i piani _Standard_ o _Premium_, puoi modificare il numero massimo di connessioni simultanee dalle impostazioni predefinite.
{: shortdesc}

In tutti i piani, ricevi 2 connessioni simultanee gratuitamente. Per ulteriori informazioni, vedi i [Piani dei prezzi](https://console.bluemix.net/catalog/services/voice-agent-with-watson). Nel dashboard _Manage_, puoi visualizzare il numero massimo di connessioni simultanee consentite nel tuo piano elencate in **Maximum concurrent connections**. Puoi inoltre visualizzare il numero massimo di connessioni simultanee utilizzate dai tuoi agent vocali durante il mese corrente in **Maximum concurrent connections used**.

1. Vai alla scheda _Instances_ nel tuo dashboard _Manage_ per modificare il numero massimo di connessioni simultanee nel tuo piano. 
1. Se vuoi modificare il numero massimo di connessioni simultanee nel tuo piano, fai clic sull'icona **Edit**.
1. Nella finestra _Edit maximum concurrent connections_, scegli il numero massimo di connessioni simultanee e fai clic su **Save**.

Il numero minimo di connessioni simultanee che puoi impostare tramite la modalità self-service è 10 e il massimo è 50. Se hai bisogno di più di 50 connessioni simultanee per il tuo agent vocale, consulta [Richiesta di configurazione di rete assistita](connect-SIP.html#request-setup).

## Informazioni sul prezzo della connessione simultanea
{: #concurrent-charge}

  * I piani _Lite_ e _Standard_ includono 2 connessioni simultanee gratuitamente.
  * I piani _Premium_ sono personalizzati per istanza.
  * In un piano _Standard_ hai una capacità minima di 10 connessioni simultanee.
  * L'utilizzo della connessione simultanea viene addebitato mensilmente. Se utilizzi più di 2 connessioni simultanee al giorno, ti viene addebitata una tariffa giornaliera. Ad esempio, poiché il tuo piano supporta 2 connessioni simultanee gratuite e imposti un limite massimo di 12 connessioni. Se ne utilizzi solo 5 in un giorno, vieni addebitato per 3.
  * Se hai un piano _Standard_ o _Premium_, puoi acquistare una capacità di connessione simultanea maggiore.
  * Sei addebitato con una tariffa giornaliera per la capacità di connessione simultanea massima che utilizzi in un giorno.

Per ulteriori informazioni sui piani, le tariffe e le funzioni, consulta [Piani dei prezzi](https://console.bluemix.net/catalog/services/voice-agent-with-watson).
