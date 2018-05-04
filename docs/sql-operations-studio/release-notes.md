---
title: Note sulla versione di Microsoft SQL operazioni Studio (anteprima) | Documenti Microsoft
description: Note sulla versione di Microsoft SQL operazioni Studio (anteprima)
ms.custom: tools|sos
ms.date: 04/25/2018
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3e13f0604ebbfc616a70768d7382b0e044055ec6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-operations-studio-preview-release-notes"></a>Note sulla versione Studio operazioni SQL (anteprima)

**[Scaricare l'anteprima pubblica di aprile](download.md)**


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

Per ulteriori informazioni, vedere il [registro delle modifiche](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md).

## <a name="march-2018-march-public-preview"></a>2018 marzo (marzo in anteprima pubblica)

Data di rilascio: il 28 marzo 2018  
versione: 0.27.3

Il *anteprima pubblica di marzo* continua a risolvere i problemi principali GitHub e si concentra sul miglioramento della nostra storia di estendibilità. In particolare l'abilitazione estensione Manager, il miglioramento della gestione di dashboard e fornire SQL Agent e le estensioni di insights. Questa versione include i miglioramenti seguenti:

- Migliorare il modello di estendibilità del dashboard per supportare insights a schede e riquadri di configurazione.
   - Gestore estensioni del attiva semplice acquisizione delle estensioni.
   - Le estensioni del dashboard per sp_whoisactive dal [whoisactive.com](http://www.whoisactive.com).
   - Per informazioni dettagliate, vedere [estendere le funzionalità di SQL Studio operazioni](extensions.md).
- Aggiungere ulteriori [API di estendibilità per la connessione e oggetto explorer](https://github.com/Microsoft/sqlopsstudio/wiki/Extensibility-API) management.
- Continuare a correggere i clienti che hanno un impatto [problemi GitHub](https://github.com/Microsoft/sqlopsstudio/issues).


## <a name="february-2018-february-public-preview"></a>2018 febbraio (febbraio in anteprima pubblica)

Data di rilascio: 15 febbraio 2018  
versione: 0.26.7

Il *anteprima pubblica di febbraio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Che l'introduzione di installazione di aggiornamento automatico, fornisce una notifica quando una nuova versione è disponibile per il download 
- Il campo di finestra di dialogo di connessione 'Database' è un elenco di riepilogo a discesa popolato in modo dinamico contenenti un elenco di database popolato dal server specificato.
- Correggere [emettere 6](https://github.com/Microsoft/sqlopsstudio/issues/6): Mantieni connessione e il database selezionato quando si apre nuove schede di query.
- Correggere [emettere 22](https://github.com/Microsoft/sqlopsstudio/issues/22): "Nome Server" e 'Nome di Database -' possono questi essere elenchi a discesa anziché le caselle di testo?
- Correggere [emettere 549](https://github.com/Microsoft/sqlopsstudio/issues/549): installazione invisibile all'utente invisibile all'utente/molto comporterà l'applicazione che apre dopo l'installazione.
- Correggere [emettere 481](https://github.com/Microsoft/sqlopsstudio/issues/481): aggiungere l'opzione "Controlla aggiornamenti".
- Editor SQL colorazione e correzioni di completamento automatico:
   - Correggere [emettere 584](https://github.com/Microsoft/sqlopsstudio/issues/584): parola chiave "Completa" non è evidenziata da IntelliSense.
   - Correggere [emettere 345](https://github.com/Microsoft/sqlopsstudio/issues/345): funzioni colorare SQL all'interno dell'editor.
   - Correggere [emettere 300](https://github.com/Microsoft/sqlopsstudio/issues/300): [#tempData] più recente "]" verrà visualizzato di colore verde.
   - Correggere [emettere 225](https://github.com/Microsoft/sqlopsstudio/issues/225): mancata corrispondenza di colore (parola chiave).
   - Correggere [emettere 60](https://github.com/Microsoft/sqlopsstudio/issues/60): sql non valido Colore evidenziazione della sintassi quando si utilizza la tabella temporanea nella clausola from.
- Introdurre API di estensibilità di connessione.
- Integrazione di Visual Studio 1.19 Editor di codice.
- Aggiornare il componente JustinPealing/html-piano di query al ritiro diversi miglioramenti di Visualizzatore di piano di Query.


## <a name="january-2018-january-public-preview"></a>2018 gennaio (anteprima pubblica di gennaio)

Data di rilascio: 17 gennaio 2018  
versione: 0.25.4

Il *anteprima pubblica di gennaio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Connessioni Server salvate sono disponibili nella finestra di dialogo di connessione.
- Abilitare l'uscita a caldo. Uscita frequente è disattivata per impostazione predefinita, per abilitare vedere [impostazione uscita Hot](settings.md#hot-exit).
- Scheda contraddistinta dal colore in base a gruppo di Server. La colorazione della scheda è disattivata per impostazione predefinita, per abilitare vedere [scheda impostazione del colore](settings.md#tab-color).
- Modifica *nome Server* a *Server* nella finestra di dialogo di connessione.
- Correzione suddiviso *Esegui Query corrente* comando.
- Correggere l'interruzione di trascinamento e rilascio bug di scripting.
- Correggere icona Menu Start aggiunto non corretta.
- Correggere l'icona di branding mancante Account di Azure.


## <a name="december-2017-december-public-preview"></a>Dicembre 2017 (anteprima pubblica di dicembre)

Data di rilascio: 19 dicembre 2017  
versione: 0.24.1

Il *anteprima pubblica di dicembre* include diverse correzioni di bug in tutte le aree di funzionalità, nonché i miglioramenti seguenti:

- Creare finestra di dialogo regola Firewall è ora disponibile per consentire la connessione a Database SQL di Azure e Azure SQL Data Warehouse.
- Aggiunto l'installazione di Windows e Linux DEB e RPM pacchetti di installazione.
- Gestire l'editor di layout visivo del Dashboard.
- *Script di modifica come* e *Script come eseguire* comandi.
- *Eseguire la Query corrente con il piano effettivo* comando.
- Integrare il codice di Visual Studio 1.18.1 editor platform.
- Abilitare i file di trasferimento locale di estensione VSIX.
- Supporta la sintassi di iterazione batch "Vai N".


## <a name="november-2017"></a>2017 novembre

Data di rilascio: 15 novembre 2017  
versione: 0.23.6

- Versione di iniziale [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Passaggi successivi

Vedere una delle Guide rapide seguenti per iniziare:
- [Connettersi ed eseguire query in SQL Server](quickstart-sql-server.md)
- [Connettersi ed eseguire query di Database SQL di Azure](quickstart-sql-database.md)
- [Connettersi ed eseguire query in Azure Data Warehouse](quickstart-sql-dw.md)

Contribuire a [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio)
