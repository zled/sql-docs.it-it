---
title: Note sulla versione di Microsoft SQL Operations Studio (anteprima) | Microsoft Docs
description: Note sulla versione di Microsoft SQL Operations Studio (anteprima)
ms.custom: tools|sos
ms.date: 05/08/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f461b78c3d76f7e6b848b83d8a2333dffe5de3c
ms.sourcegitcommit: a9da0abd3e17fbcd6339980d7331d0418cdada53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
ms.locfileid: "34473825"
---
# <a name="sql-operations-studio-preview-release-notes"></a>Note sulla versione di SQL Operations Studio (anteprima)

**[Scaricare l'anteprima pubblica di maggio](download.md)**


## <a name="may-2018-may-public-preview"></a>2018 maggio (maggio anteprima pubblica)

Data di rilascio: 7 maggio 2018  
versione: 0.29.3

Il *anteprima pubblica potrebbe* è incentrato sulla stabilizzazione e correzioni di bug. Questa generazione contiene le caratteristiche principali seguenti:  

- Annuncio relativo all'estensione di ricerca SQL Redgate disponibile in Gestione estensioni.
- Localizzazione di community disponibile per 10 lingue: tedesco, spagnolo, francese, italiano, giapponese, coreano, portoghese, russo, cinese semplificato e cinese tradizionale.
- Raccolta di dati di telemetria ridotta, migliorata l'esperienza di rifiutare esplicitamente e nel prodotto collegamenti all'informativa sulla Privacy.
- Gestore estensioni ha Marketplace una migliore esperienza per individuare facilmente le estensioni della community.
- Analisi utilizzo software consente di visualizzare i processi di estensione di SQL Agent e nella cronologia processo.
- Aggiornamenti per whoisactive ed estensioni di Server report.
- Migliorare la gestione proprietà Dashboard lo scorrimento.
- Risolvere i problemi di GitHub:
   - Correggere [emettere 703](https://github.com/Microsoft/sqlopsstudio/issues/703): immissione di testo HTML simile a quello nei dati di modifica comporta valore da visualizzare in modo non corretto finché l'aggiornamento
   - Correggere [emettere 821](https://github.com/Microsoft/sqlopsstudio/issues/821): dipendenza pacchetto sqlopsstudio.deb
   - Correggere [emettere 1260](https://github.com/Microsoft/sqlopsstudio/issues/1260): parola chiave 'distinct' non è evidenziato
   - Correggere [emettere 1332](https://github.com/Microsoft/sqlopsstudio/issues/1332): ripristino i dati di modifica riga non funziona
   - Correggere [emettere 1215](https://github.com/Microsoft/sqlopsstudio/issues/1215): estensione SQL Agent e la barra di stato
   - Correggere [emettere 1316](https://github.com/Microsoft/sqlopsstudio/issues/1316): SQL Agent non ridimensionare dopo la modifica delle dimensioni di windows


Per altre informazioni, vedere la [registro delle modifiche](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md), e [versioni](https://github.com/Microsoft/sqlopsstudio/releases).



## <a name="april-2018-april-public-preview"></a>2018 aprile (anteprima pubblica di aprile)

Data di rilascio: 25 aprile 2018  
versione: 0.28.6

Il *anteprima pubblica di aprile* include miglioramenti e correzioni di bug. 

- Miglioramenti all'estensione di anteprima di SQL Agent.
- Migliorato il supporto di file di grandi dimensioni e protetti per il salvataggio di amministratore protetto e > file 256M all'interno di SQL Studio operazioni.
- Integrato suddivisione Terminal per l'utilizzo di più terminali aperti in una sola volta.
- Footprint di conteggio file su disco di installazione ridotti di stampa per installazioni più veloce e tempi di avvio.
- Continuare a risolvere i problemi di GitHub:
   - Correggere [emettere 37](https://github.com/Microsoft/sqlopsstudio/issues/37): quando il Visualizzatore grafico genera un errore, si verifica un comportamento imprevisto.
   - Correggere [emettere 462](https://github.com/Microsoft/sqlopsstudio/issues/462): funzionalità richiesta: opzione per i gruppi di Server per essere espanso per impostazione predefinita.
   - Correggere [emettere 606](https://github.com/Microsoft/sqlopsstudio/issues/606): intellisense - suggerimento non valida per il comando 'update'.
   - Correggere [emettere 967](https://github.com/Microsoft/sqlopsstudio/issues/967): prevede che il piano di query quando seleziona showplan XML nella griglia di risultati.
   - Correggere [emettere 1023](https://github.com/Microsoft/sqlopsstudio/issues/1023): aggiungere delle parentesi quadre per chiamata ms_foreachdb da flyfishingdba.
   - Correggere [emettere 1048](https://github.com/Microsoft/sqlopsstudio/issues/1048): errore di handshake di pre-accesso SSL/TLS.
   - Correggere [emettere 1050](https://github.com/Microsoft/sqlopsstudio/issues/1050): consente di visualizzare informazioni dettagliate non crittografati prima della visualizzazione errore.
   - Correggere [emettere 1057](https://github.com/Microsoft/sqlopsstudio/issues/1057): nuove azioni di query in Esplora widget e ripristino vengono interrotte.
   - Correggere [emettere 1068](https://github.com/Microsoft/sqlopsstudio/issues/1068): Output Dashboard windows pop-up con messaggio di errore per il Database SQL di Azure.
   - Correggere [emettere 1069](https://github.com/Microsoft/sqlopsstudio/issues/1069): finestra di dialogo connessione viene visualizzato l'errore Server necessarie quando inizialmente visualizzato.
   - Correggere [emettere 1070](https://github.com/Microsoft/sqlopsstudio/issues/1070): gruppi di Server è ora necessario un doppio clic per espandere.
   - Correggere [emettere 1072](https://github.com/Microsoft/sqlopsstudio/issues/1072): sfondo del controllo selezionato è semi-trasparente.
   - Correggere [emettere 1115](https://github.com/Microsoft/sqlopsstudio/issues/1115): risolvere i problemi di accessibilità contrasto elevato tutti i in Studio operazioni SQL.
   - Correggere [emettere 1101](https://github.com/Microsoft/sqlopsstudio/issues/1101): ha esito negativo di estensione per l'aggiornamento "scaricare manualmente" collegamento passa alla posizione errata.
   - Correggere [emettere 1103](https://github.com/Microsoft/sqlopsstudio/issues/1103): V scorrimento non funziona nella scheda Home.
   - Correggere [emettere 1104](https://github.com/Microsoft/sqlopsstudio/issues/1104): schede dell'estensione SQL ha smesso di funzionare.


Un'evidenziazione significativa per l'anteprima pubblica di aprile è l'aggiornamento di codice sorgente della piattaforma Visual Studio codice 1.21. Verrà visualizzata in diversi aggiornamenti per l'editor dei componenti di base e workbench dal punto di 1.19 sincronizzazione precedente. Di seguito sono indicati alcuni esempi:

- [Nuova interfaccia utente delle notifiche](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui) - facilmente gestire ed esaminare le notifiche di Studio operazioni SQL.
- [Integrato suddivisione Terminal](https://code.visualstudio.com/updates/v1_21#_split-terminals) -lavorare con più terminali aperti contemporaneamente.
- [Salvare i file di grandi dimensioni e protected](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges) : consente di salvare amministratore protetto e > file 256 M all'interno di SQL Studio operazioni.
- [Migliorato il supporto di file di grandi dimensioni](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements) -ottimizzazioni di buffer di testo per file di grandi dimensioni.
- [Una funzionalità di ricerca impostazioni](https://code.visualstudio.com/updates/v1_20#_settings-search) - facilmente individuare l'impostazione a destra con la ricerca di linguaggio naturale.
- [I frammenti di codice globale](https://code.visualstudio.com/updates/v1_20#_global-snippets) -creare frammenti di codice è possibile utilizzare in tutti i tipi di file.
- [Selezione multipla Esplora](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer) -eseguire azioni su più file in una sola volta.
- [Errori e avvisi in soluzioni](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer) - rapidamente passare gli errori della codebase.
- [Trascinare, copiare e incollare dati tra windows](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support) -spostarli tra finestre aperte Studio operazioni SQL.
- [Supporto di modulo secondario GIT](https://code.visualstudio.com/updates/v1_20#_git-submodules) -Git eseguire operazioni in nidificato repository Git.
- [Supporto per Terminal screen reader](https://code.visualstudio.com/updates/v1_20#_screen-reader-support) -Terminal integrata è ora la modalità "Screen Reader ottimizzato".
- [Editor centrato layout](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout) -ottimizzare il codice visualizzazione area dello schermo.
- [Risultati della ricerca orizzontale (anteprima)](https://code.visualstudio.com/updates/v1_21#_horizontal-search) -è possibile ora Visualizza risultati di ricerca in un pannello orizzontale.

Per ulteriori dettagli, estrarre il [note sulla versione di Visual Studio codice febbraio](https://code.visualstudio.com/updates/v1_21)e il [note sulla versione di Visual Studio codice gennaio](https://code.visualstudio.com/updates/v1_20).

Per ulteriori informazioni, vedere il [log delle modifiche](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md).

## <a name="march-2018-march-public-preview"></a>Marzo 2018 (anteprima pubblica di marzo)

Data di rilascio: 28 marzo 2018  
versione: 0.27.3

L'*anteprima pubblica di marzo* continua a rivolgersi ai principali issue su GitHub e si concentra sul miglioramento dell'estendibilità. In particolare, è stato aggiunto il pannello di gestione delle estensioni, è stata migliorata la gestione delle dashboard e sono stati introdotti il supporto a SQL Agent e le estensioni di insight. Questa versione include i miglioramenti seguenti:

- Migliorato il modello di estendibilità delle dashboard tramite l'aggiunta del supporto di schede per gli insight e riquadri di configurazione.
   - Aggiunto il pannello ESTENSIONI, che consente la semplice acquisizione delle estensioni.
   - Aggiunta un'estensione per sp_whoisactive da [whoisactive.com](http://www.whoisactive.com).
   - Per informazioni dettagliate, vedere [estendere le funzionalità di SQL Studio operazioni](extensions.md).
- Aggiunte ulteriori [API di estendibilità per le connessioni ed Esplora Oggetti](https://github.com/Microsoft/sqlopsstudio/wiki/Extensibility-API).
- Correzioni dei [problemi di GitHub](https://github.com/Microsoft/sqlopsstudio/issues) ad alto impatto sui clienti.


## <a name="february-2018-february-public-preview"></a>Febbraio 2018 (anteprima pubblica di febbraio)

Data di rilascio: 15 febbraio 2018  
versione: 0.26.7

Il *anteprima pubblica di febbraio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Introdotta la funzionalità di aggiornamento automatico, che mostra una notifica quando una nuova versione è disponibile per il download. 
- Il campo 'Database' della finestra di dialogo di connessione è ora un elenco a discesa popolato in modo dinamico dall'elenco dei database presenti nel server specificato.
- Corretto il [problema 6](https://github.com/Microsoft/sqlopsstudio/issues/6): Mantienere la connessione e il database selezionati quando si aprono nuove schede di query.
- Corretto il [problema 22](https://github.com/Microsoft/sqlopsstudio/issues/22): 'Server' e 'Database' - è possibile trasformarli in elenchi a discesa anziché caselle di testo?
- Corretto il [problema 549](https://github.com/Microsoft/sqlopsstudio/issues/549): Le installazioni con il parametro Silent/VerySilent fanno aprire l'applicazione subito dopo la fine del setup.
- Corretto il [problema 481](https://github.com/Microsoft/sqlopsstudio/issues/481): Aggiungere l'opzione "Controlla aggiornamenti".
- Correzioni riguardanti l'editor SQL e il completamento automatico:
   - Corretto il [problema 584](https://github.com/Microsoft/sqlopsstudio/issues/584): La parola chiave 'FULL' non è evidenziata da IntelliSense.
   - Corretto il [problema 345](https://github.com/Microsoft/sqlopsstudio/issues/345): Colorare le funzioni SQL all'interno dell'editor.
   - Corretto il [problema 300](https://github.com/Microsoft/sqlopsstudio/issues/300): In una stringa [#tempData] il carattere finale"]" verrà visualizzato di colore verde.
   - Corretto il [problema 225](https://github.com/Microsoft/sqlopsstudio/issues/225): Mancata corrispondenza di colore su parola chiave.
   - Corretto il [problema 60](https://github.com/Microsoft/sqlopsstudio/issues/60): Colore non valido quando si utilizza una tabella temporanea nella clausola from.
- Introdotta l'API di estensibilità di connessione.
- Aggiunta l'integrazione dell'editor di codice di Visual Studio 1.19.
- Aggiornato il componente JustinPealing/query-plan per ottenere diversi miglioramenti sul visualizzatore dei piani di query.


## <a name="january-2018-january-public-preview"></a>Gennaio 2018 (anteprima pubblica di gennaio)

Data di rilascio: 17 gennaio 2018  
versione: 0.25.4

L'*anteprima pubblica di gennaio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta.  Questa versione include i miglioramenti seguenti:

- Le connessioni server salvate sono disponibili nella finestra di dialogo di connessione.
- Abilitare l'uscita Hot,  disattivata per impostazione predefinita. Per abilitarla vedere [impostazione uscita Hot](settings.md#hot-exit).
- Ogni scheda è ora contraddistinta dal colore del relativo gruppo di server. La colorazione della scheda è disattivata per impostazione predefinita, per abilitare vedere [impostazione del colore di una scheda](settings.md#tab-color).
- Modificata l'etichetta *Nome Server* in *Server* nella finestra di dialogo di connessione.
- Corretto il comando non funzionante *Esegui Query corrente*.
- Corretto il bug dello scripting di interruzione di tracina e rilascia.
- Corretta l'icona del Menu Start bloccata in modo non corretto.
- Aggiunta l'icona mancante dell'Account di Azure.


## <a name="december-2017-december-public-preview"></a>Dicembre 2017 (anteprima pubblica di dicembre)

Data di rilascio: 19 dicembre 2017  
versione: 0.24.1

L'*anteprima pubblica di dicembre* include diverse correzioni di bug in tutte le aree di funzionalità, nonché i miglioramenti seguenti:

- La finestra di dialogo per l'aggiunta automatica della regola del firewall è ora disponibile per consentire la connessione a Database SQL di Azure e Azure SQL Data Warehouse.
- Aggiunta l'installazione di Windows e i pacchetti di installazione Linux DEB e RPM.
- Aggiunto l'editor di layout della dashboard.
- Aggiunti i comandi *Script come ALTER* e *Script come EXECUTE*.
- Aggiunto il comando *Esegui la query corrente con il piano effettivo*.
- Integrato l'editor di codice di Visual Studio 1.18.1.
- Abilitato il caricamento dei file con estensione VSIX.
- Supporta la sintassi di iterazione batch "GO N".


## <a name="november-2017"></a>Novembre 2017

Data di rilascio: 15 novembre 2017  
versione: 0.23.6

- Versione iniziale di [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Passaggi successivi

Seguire una delle guide rapide qui sotto per iniziare:
- [Connettersi ed eseguire query in SQL Server](quickstart-sql-server.md)
- [Connettersi ed eseguire query in Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi ed eseguire query in Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio)
