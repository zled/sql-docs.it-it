---
title: Note sulla versione di Azure Data Studio | Microsoft Docs
description: Note sulla versione di Azure Data Studio
ms.custom: tools|sos
ms.date: 11/06/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9723a51154d0098271f8d3206c7f7a7470598422
ms.sourcegitcommit: 8cc38f14ec72f6f420479dc1b15eba64b1a58041
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2018
ms.locfileid: "51289921"
---
# <a name="azure-data-studio-release-notes"></a>Note sulla versione di Azure Data Studio

**[Scaricare la versione di novembre.](download.md)**

## <a name="november-2018-november-release"></a>Novembre 2018 (versione di novembre)

Data di rilascio: 6 novembre 2018  
versione: 1.2.4

- Aggiornare il [estensione di anteprima di SQL Server 2019](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)
- Introduzione a incollare l'estensione di piano
- Introduzione a estensione query High Color, incluso il tema dell'editor SSMS
- Consente di correggere le estensioni di importazione, Profiler e SQL Server Agent
- Correggere.NET Core che causa problema Socket KeepAlive eliminate le connessioni inattive in macOS
- Aggiornamento servizio di strumenti di SQL per.NET Core versione 2.2 Preview 3 (per il supporto AAD finale)

### <a name="bug-fixes"></a>Correzioni di bug
- Correggere [problema #2933](https://github.com/Microsoft/azuredatastudio/issues/2933): connessione persa a database SQL di Azure
- Correggere [problema #2914](https://github.com/Microsoft/azuredatastudio/issues/2914): eccezione di "argomento non valido" espansione OE database nodo
- Correggere [problema #2935](https://github.com/Microsoft/azuredatastudio/pull/2935): visualizzare correttamente i messaggi a più righe nei risultati della query
- Correggere [problema #2906](https://github.com/Microsoft/azuredatastudio/pull/2906): nome del documento correggere la modifica dei dati quando il nome di tabella contiene caratteri speciali
- Correggere [problema #2929](https://github.com/Microsoft/azuredatastudio/issues/2929): compilato nell'estensione changelog afferma controllare le note sulla versione di Visual Studio code per le modifiche
- Correggere [problema #2719](https://github.com/Microsoft/azuredatastudio/issues/2719): tema a contrasto elevato. valori Double/Triple icone
- Correggere [problema #3047](https://github.com/Microsoft/azuredatastudio/pull/3047): aggiungere un'interfaccia della riga di comando per la connessione a SQL Server
- Correggere [problema #3031](https://github.com/Microsoft/azuredatastudio/pull/3031): aggiungere il supporto di tema piano di query
- ...

Per informazioni dettagliate, vedere la [Log delle modifiche](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), e [versioni](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="october-2018-october-release"></a>Ottobre 2018 (versione di ottobre)

Data di rilascio: 29 ottobre 2018  
versione: 1.1.4

- Introduzione a Esplora risorse di Azure per esplorare database SQL di Azure
- Migliorare l'affidabilità di connettività di Esplora oggetti ed Editor di Query
- Miglioramenti di estensioni SQL Agent
- Aggiornare il [estensione di anteprima di SQL Server 2019](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)

### <a name="bug-fixes"></a>Correzioni di bug
- Correggere [problema #2717](https://github.com/Microsoft/azuredatastudio/issues/2717): il risultato di colonne XML su formattazione
- Correggere [problema #2993](https://github.com/Microsoft/azuredatastudio/issues/2993): finestre dei risultati della larghezza è incompleta
- Correggere [problema #2999](https://github.com/Microsoft/azuredatastudio/issues/2999): Impossibile caricare il file Tracing in computer Mac quando ci si connette al database
- Correggere [problema #2851](https://github.com/Microsoft/azuredatastudio/issues/2851): grafico delle serie temporali non esegue il rendering correttamente
- Correggere [problema #2996](https://github.com/Microsoft/azuredatastudio/issues/2996): Temp perdita di tabella a causa di modifiche improvvise sessione
- ...

Per informazioni dettagliate, vedere la [Log delle modifiche](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), e [versioni](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="september-2018-september-ga-release"></a>Settembre 2018 (versione di settembre a livello generale)

Data di rilascio: 24 settembre 2018  
versione: 1,0

Versione di disponibilità generale di Studio dei dati di Azure (precedentemente SQL Operations Studio).

- Annuncio dell'estensione di anteprima di SQL Server 2019.
  - Supporto per le funzionalità di anteprima di SQL Server 2019 compresi [cluster di big data](../big-data-cluster/big-data-cluster-overview.md) supportano.
    - Connettersi al Gateway HDFS/Spark forniti con l'anteprima di SQL Server 2019.
    - Sfoglia HDFS, caricare i file, salvare i file e avviare azioni utili, ad esempio analizza in blocco note per i file CSV.
    - Inviare processi Spark nel dashboard o fare clic su una connessione di Spark o HDFS in Esplora oggetti.
  - Notebook di Studio dei dati di Azure
    - Creare o aprire notebook utilizzando un Visualizzatore integrato Notebook. In questa versione il Notebook viewer supporta la connessione a kernel locale e solo il cluster di big data di SQL Server 2019.
    - Per informazioni su tipi di dati e formato di file per la preparazione dei dati veloce, usare le librerie di tasti di scelta rapida codice PROSE nel Notebook.
  - Esplora risorse di Azure
    - La visualizzazione di Esplora risorse di Azure consente di esplorare gli endpoint relativi ai dati per gli account Azure e creare connessioni a essi in Esplora oggetti. In questa versione sono supportati server e database SQL di Azure.
  - PolyBase di SQL Server Creazione guidata tabella esterna
    - Creare una tabella esterna e le relative strutture di metadati di supporto con una procedura guidata di facile utilizzo. In questa versione, i server remoti di SQL Server e Oracle sono supportati.
- Miglioramenti dell'esperienza utente per un numero elevato di set di risultati e le prestazioni di griglia di risultati di query.
- Codice sorgente di Visual Studio Code Aggiorna da 1,23 per 1.26.1 con griglia di Layout e migliorato impostazioni Editor (anteprima).
- Miglioramenti all'accessibilità per la lettura dello schermo, la navigazione da tastiera e a contrasto elevato.
- Aggiunto `Connection name` opzione per specificare un nome alternativo visualizzato nel consentono di visualizzare i server.

### <a name="bug-fixes"></a>Correzioni di bug

- Correggere [problema #2647](https://github.com/Microsoft/azuredatastudio/issues/143): I grafici ha richiesto un grosso passo con le versioni precedenti.
- Correggere [problema #2648](https://github.com/Microsoft/azuredatastudio/issues/143): SELECT che restituisce l'intera colonna collegamenti ipertestuali JSON.
- ...

Per informazioni dettagliate, vedere la [Log delle modifiche](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), e [versioni](https://github.com/Microsoft/azuredatastudio/releases).


## <a name="august-2018-august-public-preview"></a>Agosto 2018 (anteprima pubblica di agosto)

Data di rilascio: 30 agosto 2018  
versione: 0.32.8

*0.32.8 contiene correzioni per un paio delle regressioni trovate in 0.32.7 ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971), [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372)*)

Il *versione di anteprima pubblica di agosto* è incentrato sulle correzioni di bug, stabilizzazione del prodotto e colmando i vuoti nella scenari esistenti.  

- Annuncio dell'estensione di importazione SQL Server
- Gestione delle sessioni di SQL Server Profiler
- Supporto del modello di sessione di SQL Server Profiler
- Miglioramenti di SQL Server Agent
- Nuova estensione della community: primo kit risponditore
- Miglioramenti della qualità della vita: le stringhe di connessione

### <a name="bug-fixes"></a>Correzioni di bug

- Analizzare in una finestra dell'Editor di Query SQL usando il `Parse Syntax` comando.
- Correggere [problema #143](https://github.com/Microsoft/azuredatastudio/issues/143): fare doppio clic su se non si seleziona nel nome della variabile.
- Correggere [problema #387](https://github.com/Microsoft/azuredatastudio/issues/387): SQL scheda DB icona è rossa.
- Correggere [problema #825](https://github.com/Microsoft/azuredatastudio/issues/825): richiesta: connessione automatica al server corrente dopo lo Script come... 
- Correggere [problema #1278](https://github.com/Microsoft/azuredatastudio/issues/1278): sqlops.desktop [voce Desktop] - valore ridondanti per nome & commento.
- Correggere [problema #1285](https://github.com/Microsoft/azuredatastudio/issues/1285): l'aggiornamento causa l'icona dell'applicazione essere rimosso o sostituito in Windows.
- Correggere [problema #1317](https://github.com/Microsoft/azuredatastudio/issues/1317): correggere il separatore decimale.
- Correggere [problema #1474](https://github.com/Microsoft/azuredatastudio/issues/1474): Annulla Modifica connessione disconnette la connessione corrente.
- Correggere [problema #1497](https://github.com/Microsoft/azuredatastudio/issues/1497): visualizzazione sotto forma di grafico le opzioni sono tagliate nella parte inferiore.
- Correggere [problema #1524](https://github.com/Microsoft/azuredatastudio/issues/1524): Shell/Dashboard: Main viewlet icone sono trascinabile e causare un arresto anomalo dell'app.
- Correggere [problema #1578](https://github.com/Microsoft/azuredatastudio/issues/1578): non è possibile espandere/comprimere cartella browser file remoto facendo clic sul nome.
- Correggere [problema #1620](https://github.com/Microsoft/azuredatastudio/issues/1620): suggerimento di funzionalità: introduzione di stringa di connessione per la connessione esistente.
- Correggere [problema #1624](https://github.com/Microsoft/azuredatastudio/issues/1624): SelectBox non cambia colore quando disabilitata.
- Correggere [problema #1728](https://github.com/Microsoft/azuredatastudio/issues/1728): Salva con nome JSON/EXCEL/CSV non funzionano.
- Correggere [problema #1744](https://github.com/Microsoft/azuredatastudio/issues/1744): riquadro risultati perde le posizioni di scorrimento quando si passa tra le schede.
- Correggere [problema #1748](https://github.com/Microsoft/azuredatastudio/issues/1748): messaggio di errore durante il salvataggio ora file seconde (e successive) di Excel.
- Correggere [problema #1782](https://github.com/Microsoft/azuredatastudio/issues/1782): modificare i dati: cella non viene ripristinato al valore originale sul premendo ESC.
- Correggere [problema #1836](https://github.com/Microsoft/azuredatastudio/issues/1836): file con estensione SQL non associati di SQL Operations Studio.
- Correggere [problema #1850](https://github.com/Microsoft/azuredatastudio/issues/1850): N digitando ' durante la digitazione a N ' '.
- Correggere [problema #1985](https://github.com/Microsoft/azuredatastudio/issues/1985): copia da griglia di risultati della query è disattivata per 1 colonna.
- Correggere [problema #1998](htpts://github.com/Microsoft/azuredatastudio/pull/1998): versione aggiungere Visual Studio Code sulla finestra di dialogo.
- Correggere [problema #2042](https://github.com/Microsoft/azuredatastudio/pull/2042): Agent: pulsante attivato importare query da file sql.
- Correggere [problema #2091](https://github.com/Microsoft/azuredatastudio/issues/2091): non è possibile usare scelta rapida Ctrl + C per copiare dal riquadro dei risultati.
- Correggere [problema #2099](https://github.com/Microsoft/azuredatastudio/pull/2099): aggiunta di altre opzioni saveAsCsv.
- Correggere [problema #2107](https://github.com/Microsoft/azuredatastudio/issues/2107): icona del documento Update per i documenti di Dashboard e Profiler.
- Correggere [problema #2129](https://github.com/Microsoft/azuredatastudio/pull/2129): salvare i dati di modifica quando si cambia scheda posizione di scorrimento.
- Correggere [problema #2152](https://github.com/Microsoft/azuredatastudio/issues/2152): in base Zero indicatore di risultati della griglia righe.

## <a name="known-issues"></a>Problemi noti

- [Problema #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) Salva con nome solo Salva prima riga di dati di Excel
- [Problema #2150](https://github.com/Microsoft/azuredatastudio/issues/2150): non è possibile connettersi in Ubuntu 16.04 per SQL in un contenitore


## <a name="july-2018-july-public-preview"></a>Luglio 2018 (luglio anteprima pubblica)

Data di rilascio: 19 luglio 2018  
versione: 0.31.4

Il *versione di anteprima pubblica di luglio* è incentrato sul rilascio iniziale degli scenari di configurazione di SQL Server Agent, miglioramenti di modello della sessione e visualizzazione di SQL Server Profiler e continuare correzioni di bug per problemi di GitHub segnalati dai clienti. Questa versione include le caratteristiche principali seguenti:  

- [SQL Server Agent per l'estensione di SQL Operations Studio](sql-server-agent-extension.md) miglioramenti
 - Visualizzazione aggiunta di avvisi, operatori e proxy e le icone nel riquadro a sinistra
 - Finestre di dialogo aggiunta per nuovo processo, nuovo passaggio di processo, nuovo avviso e operatore New
 - Aggiunto il processo di eliminazione, Elimina avviso e Delete-operatore (pulsante destro del mouse)
 - Aggiunta la visualizzazione esecuzioni precedenti
 - Aggiunta di filtri per ogni nome di colonna
- [SQL Server Profiler per l'estensione di SQL Operations Studio](sql-server-profiler-extension.md) miglioramenti
 - Aggiunti i tasti di scelta rapida per avviare e rapidamente avvio/arresto Profiler
 - Aggiungere 5 modelli predefiniti per visualizzare gli eventi estesi
 - Nome della connessione Server/Database aggiunto
 - Aggiunta del supporto per le istanze del Database SQL di Azure
 - Suggerimento aggiunta per uscire dal Profiler quando scheda è chiusa quando il Profiler è ancora in esecuzione
- Versione dell'estensione di script di combinazione
- Punti di estensibilità di finestra di dialogo e procedura guidata aggiunti per gli autori delle estensioni
- Risolvere i problemi di GitHub:
 - Correggere [emettere 728](https://github.com/Microsoft/azuredatastudio/issues/728): nessuna risposta al Aggiungi connessione in macOS
 - Correggere [emettere 1612](https://github.com/Microsoft/azuredatastudio/issues/1612): visualizzazione di testo della griglia di risultati è un disastro per caratteri internazionali
 - Correggere [emettere 1693](https://github.com/Microsoft/azuredatastudio/issues/1693): finestra di dialogo Backup: il browser File dell'interfaccia utente viene interrotto
 - Correggere [emettere 1713](https://github.com/Microsoft/azuredatastudio/issues/1713): numero di righe interessate
 - Correggere [emettere 1718](https://github.com/Microsoft/azuredatastudio/issues/1718): Impossibile connettersi a qualsiasi origine dati
 - Correggere [emettere 1719](https://github.com/Microsoft/azuredatastudio/issues/1719): TypeError quando ci si connette al Server
 - Correggere [emettere 1724](https://github.com/Microsoft/azuredatastudio/issues/1724): le finestre di dialogo di estensione hanno smesso di funzionare
 - Correggere [emettere 1749](https://github.com/Microsoft/azuredatastudio/issues/1749): BUG: interpretazione dei dati HTML in una colonna
 - Correggere [emettere 1789](https://github.com/Microsoft/azuredatastudio/issues/1789): estendibilità: se si aggiunge un provider di connessione disinstallazione non verrà mai rimosso dall'elenco
 - Correggere [emettere 1791](https://github.com/Microsoft/azuredatastudio/issues/1791): Sqlops estensioni: queryeditor.connect() si connette al database di destinazione, ma dell'interfaccia utente non viene visualizzato l'editor è connesso
 - Correggere [emettere 1799](https://github.com/Microsoft/azuredatastudio/issues/1799): grafico Top 10 DB dimensioni non funziona nelle istanze di maiuscole / minuscole
 - Correggere [emettere 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): definizione del tipo di errore di digitazione sqlops.d.ts causa implicita 'any'
 - Correggere [emettere 1817](https://github.com/Microsoft/azuredatastudio/issues/1817): errore de Ortografia
 - Correggere [emettere 1830](https://github.com/Microsoft/azuredatastudio/issues/1830): l'impostazione iconPath in ButtonComponent dopo la chiamata di component() non modifica icona
 - Correggere [emettere 1843](https://github.com/Microsoft/azuredatastudio/issues/1843): organizzazione di tabelle migliori


## <a name="june-2018-june-public-preview"></a>Giugno 2018 (anteprima pubblica del giugno)

Data di rilascio: 20 giugno 2018  
versione: 0.30.6

Il *versione di anteprima pubblica di giugno* contiene le caratteristiche principali seguenti:  

- **SQL Server Profiler per SQL Operations Studio *Preview***  versione iniziale di estensione.
- Il nuovo **SQL Data Warehouse** estensione include i widget di dashboard personalizzabili avanzato esporre informazioni dettagliate nel tuo data warehouse. Ciò consente di sbloccare gli scenari principali per la gestione e ottimizzazione del data warehouse per assicurarti che è ottimizzato per prestazioni coerenti.
- **Modificare "applicazione di filtri e l'ordinamento dei dati"** supportano.
- **SQL Server Agent per SQL Operations Studio *Preview***  miglioramenti dell'estensione per i processi e la cronologia processo viste.
- Migliorato **guidata & finestra di dialogo dell'interfaccia utente generatore Framework** API di estendibilità.
- Aggiornare l'integrazione di Visual Studio Code piattaforma origine codice [mese di marzo 2018 (1.22)](https://code.visualstudio.com/updates/v1_22) e [aprile 2018 (1.23)](https://code.visualstudio.com/updates/v1_23) rilascia.
- Risolvere i problemi di GitHub:
  - Richiesta di funzionalità ([emettere 1204](https://github.com/Microsoft/azuredatastudio/issues/1204)):. verificare i risultati della larghezza della colonna di adattamento della griglia ai dati e/o ricordare le modifiche manuali se la stessa query viene rieseguita.
  - Correggere [emettere 1398](https://github.com/Microsoft/azuredatastudio/issues/1398): necessario show aggiungere dei messaggi e pulsante Aggiungi account account quando l'account collegato è vuota.
  - Correggere [emettere 1399](https://github.com/Microsoft/azuredatastudio/issues/1399): scheda account collegato viene interrotta quando la visualizzazione è compressa.
  - Correggere [emettere 1374](https://github.com/Microsoft/azuredatastudio/issues/1374): arresti anomali del servizio di strumenti di SQL all'apertura di file con estensione SQL dal disco.
  - Correggere [emettere 1372](https://github.com/Microsoft/azuredatastudio/issues/1372): la parola chiave SQL manca "BETWEEN".
  - Correggere [emettere 1395](https://github.com/Microsoft/azuredatastudio/issues/1395): parola chiave 'MATCH' di arresto anomalo del servizio di strumenti SQL.
  - Correggere [emettere 1496](https://github.com/Microsoft/azuredatastudio/issues/1496): opzione del menu di scelta rapida "Nuovo Profiler" in Esplora oggetti non esegue alcuna operazione.
  - Correggere [emettere 1495](https://github.com/Microsoft/azuredatastudio/issues/1495): piano di query "Spiegazione" editor di Query viene interrotta.


## <a name="may-2018-may-public-preview"></a>Mese di maggio 2018 (maggio di anteprima pubblica)

Data di rilascio: 7 marzo 2018  
versione: 0.29.3

Il *potrebbe Public Preview* è incentrato su stabilizzazione e correzioni di bug. Questa build contiene le caratteristiche principali seguenti:  

- Annuncio relativo all'estensione di Redgate SQL Search disponibile in Gestione estensioni.
- Localizzazione della community disponibile per 10 lingue: tedesco, spagnolo, francese, italiano, giapponese, coreano, portoghese, russo, cinese semplificato e cinese tradizionale.
- Raccolta dati di telemetria ridotta, esperienza migliorata per rifiutare esplicitamente e nel prodotto collegamenti all'informativa sulla Privacy.
- Gestione estensioni ha Marketplace migliorata esperienza per individuare facilmente le estensioni della community.
- Processi di estensione di SQL Agent e la cronologia processo visualizzare analisi utilizzo software.
- Aggiornamenti per whoisactive ed estensioni di rapporti del Server.
- Migliorare la gestione proprietà Dashboard lo scorrimento.
- Risolvere i problemi di GitHub:
   - Correggere [emettere 703](https://github.com/Microsoft/azuredatastudio/issues/703): immissione di testo simile a HTML nei dati di modifica provoca valore da visualizzare in modo non corretto finché l'aggiornamento
   - Correggere [emettere 821](https://github.com/Microsoft/azuredatastudio/issues/821): azuredatastudio.deb dipendenza del pacchetto
   - Correggere [emettere 1260](https://github.com/Microsoft/azuredatastudio/issues/1260): parola chiave 'distinct' non è evidenziata
   - Correggere [emettere 1332](https://github.com/Microsoft/azuredatastudio/issues/1332): ripristino i dati di modifica riga non funziona
   - Correggere [emettere 1215](https://github.com/Microsoft/azuredatastudio/issues/1215): estensione di SQL Agent e la barra di stato
   - Correggere [emettere 1316](https://github.com/Microsoft/azuredatastudio/issues/1316): SQL Agent non ridimensionare dopo la modifica delle dimensioni di windows




## <a name="april-2018-april-public-preview"></a>Aprile 2018 (anteprima pubblica del mese di aprile)

Data di rilascio: 25 aprile 2018  
versione: 0.28.6

Il *versione di anteprima pubblica di aprile* include miglioramenti e correzioni di bug. 

- Miglioramenti per l'estensione di anteprima di SQL Agent.
- Migliorato il supporto di file di grandi dimensioni e protetto per il salvataggio di amministratore protetto e > 256M file all'interno di SQL Operations Studio.
- Terminale integrato di suddivisione per lavorare con più terminali aperti in una sola volta.
- Consente di stampare piede conteggio file su disco di installazione ridotti per le installazioni più veloce e tempi di avvio.
- Continuare a correggere i problemi di GitHub:
   - Correggere [emettere 37](https://github.com/Microsoft/azuredatastudio/issues/37): quando il Visualizzatore grafico genera un errore, si verifica un comportamento imprevisto.
   - Correggere [emettere 462](https://github.com/Microsoft/azuredatastudio/issues/462): funzionalità richiesta: opzione per i gruppi di Server per essere espanso per impostazione predefinita.
   - Correggere [emettere 606](https://github.com/Microsoft/azuredatastudio/issues/606): intellisense - suggerimento non valido per 'update' comando.
   - Correggere [emettere 967](https://github.com/Microsoft/azuredatastudio/issues/967): prevede che il piano di query quando seleziona showplan XML nella griglia di risultati.
   - Correggere [emettere 1023](https://github.com/Microsoft/azuredatastudio/issues/1023): aggiungere le parentesi quadre per ms_foreachdb chiamata dalla flyfishingdba.
   - Correggere [emettere 1048](https://github.com/Microsoft/azuredatastudio/issues/1048): errore di handshake SSL/TLS di pre-login.
   - Correggere [emettere 1050](https://github.com/Microsoft/azuredatastudio/issues/1050): Cancella insights visualizzare prima di visualizzare l'errore.
   - Correggere [emettere 1057](https://github.com/Microsoft/azuredatastudio/issues/1057): nuove azioni di query in Esplora-widget e ripristino vengono interrotte.
   - Correggere [emettere 1068](https://github.com/Microsoft/azuredatastudio/issues/1068): Output Dashboard windows pop-up con il messaggio di errore per il Database SQL di Azure.
   - Correggere [emettere 1069](https://github.com/Microsoft/azuredatastudio/issues/1069): finestra di dialogo connessione Mostra errore è necessario un Server alla visualizzazione iniziale.
   - Correggere [emettere 1070](https://github.com/Microsoft/azuredatastudio/issues/1070): gruppi di Server è ora necessario un doppio clic per espandere.
   - Correggere [emettere 1072](https://github.com/Microsoft/azuredatastudio/issues/1072): sfondo del controllo di selezione è semi-trasparente.
   - Correggere [emettere 1115](https://github.com/Microsoft/azuredatastudio/issues/1115): risolvere i problemi di accessibilità di tutti a contrasto elevato in SQL Operations Studio.
   - Correggere [emettere 1101](https://github.com/Microsoft/azuredatastudio/issues/1101): ha esito negativo di estensione per il collegamento di aggiornamento "scaricare manualmente" passa a una posizione non valida.
   - Correggere [emettere 1103](https://github.com/Microsoft/azuredatastudio/issues/1103): V scorrimento non funziona nella scheda Home.
   - Correggere [emettere 1104](https://github.com/Microsoft/azuredatastudio/issues/1104): schede dell'estensione SQL ha smesso di funzionare.


Un'evidenziazione significativa per l'anteprima pubblica di aprile è l'aggiornamento di codice sorgente di piattaforma pari a 1,21 codice di Visual Studio. In questo modo diversi aggiornamenti per l'editor principale e workbench dal punto di 1.19 sincronizzazione precedente. Alcuni esempi includono quanto segue:

- [Nuova interfaccia utente delle notifiche](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui) : facilmente gestire e controllare le notifiche di SQL Operations Studio.
- [Integrato suddivisione Terminal](https://code.visualstudio.com/updates/v1_21#_split-terminals) -lavorare contemporaneamente con più terminali open.
- [Salvare i file di grandi dimensioni e protetti](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges) : consente di salvare amministratore protetto e > 256M file all'interno di SQL Operations Studio.
- [Migliorato il supporto di file di grandi dimensioni](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements) -ottimizzazioni di buffer di testo per file di grandi dimensioni.
- [Funzionalità di ricerca migliorata impostazioni](https://code.visualstudio.com/updates/v1_20#_settings-search) - facilmente individuare la corretta impostazione con la ricerca del linguaggio naturale.
- [Frammenti di codice globale](https://code.visualstudio.com/updates/v1_20#_global-snippets) -creare frammenti di codice è possibile usare in tutti i tipi di file.
- [Selezione multipla Esplora](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer) -eseguire azioni su più file contemporaneamente.
- [Errori e avvisi in Esplora](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer) - rapidamente passare agli errori nella base di codice.
- [Trascinare e rilasciare, copiare e incollare dati tra windows](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support) -spostarli tra finestre aperte di SQL Operations Studio.
- [Supporto di modulo secondario GIT](https://code.visualstudio.com/updates/v1_20#_git-submodules) -Git eseguire operazioni nei repository Git annidati.
- [Supporto di lettura dello schermo terminal](https://code.visualstudio.com/updates/v1_20#_screen-reader-support) -terminale integrato è ora la modalità "Schermata lettore con ottimizzazione per la".
- [Layout centrato editor](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout) -ottimizzare il codice visualizza sullo schermo.
- [I risultati della ricerca orizzontale (anteprima)](https://code.visualstudio.com/updates/v1_21#_horizontal-search) -è possibile ora Visualizza risultati di ricerca in un pannello orizzontale.

Per altri dettagli, estrarre il [note sulla versione di Visual Studio Code febbraio](https://code.visualstudio.com/updates/v1_21)e il [note sulla versione di Visual Studio Code gennaio](https://code.visualstudio.com/updates/v1_20).

Per ulteriori informazioni, vedere il [log delle modifiche](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).

## <a name="march-2018-march-public-preview"></a>Marzo 2018 (anteprima pubblica di marzo)

Data di rilascio: 28 marzo 2018  
versione: 0.27.3

L'*anteprima pubblica di marzo* continua a rivolgersi ai principali issue su GitHub e si concentra sul miglioramento dell'estendibilità. In particolare, è stato aggiunto il pannello di gestione delle estensioni, è stata migliorata la gestione delle dashboard e sono stati introdotti il supporto a SQL Agent e le estensioni di insight. Questa versione include i miglioramenti seguenti:

- Migliorato il modello di estendibilità delle dashboard tramite l'aggiunta del supporto di schede per gli insight e riquadri di configurazione.
   - Aggiunto il pannello ESTENSIONI, che consente la semplice acquisizione delle estensioni.
   - Aggiunta un'estensione per sp_whoisactive da [whoisactive.com](http://www.whoisactive.com).
   - Per informazioni dettagliate, vedere [estendono le funzionalità di SQL Operations Studio](extensions.md).
- Aggiunte ulteriori [API di estendibilità per le connessioni ed Esplora Oggetti](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API).
- Correzioni dei [problemi di GitHub](https://github.com/Microsoft/azuredatastudio/issues) ad alto impatto sui clienti.


## <a name="february-2018-february-public-preview"></a>Febbraio 2018 (anteprima pubblica di febbraio)

Data di rilascio: 15 febbraio 2018  
versione: 0.26.7

Il *anteprima pubblica di febbraio* include alcuni suggerimenti sulle funzionalità e correzioni di bug con priorità alta. Questa versione include i miglioramenti seguenti:

- Introdotta la funzionalità di aggiornamento automatico, che mostra una notifica quando una nuova versione è disponibile per il download. 
- Il campo 'Database' della finestra di dialogo di connessione è ora un elenco a discesa popolato in modo dinamico dall'elenco dei database presenti nel server specificato.
- Corretto il [problema 6](https://github.com/Microsoft/azuredatastudio/issues/6): Mantienere la connessione e il database selezionati quando si aprono nuove schede di query.
- Corretto il [problema 22](https://github.com/Microsoft/azuredatastudio/issues/22): 'Server' e 'Database' - è possibile trasformarli in elenchi a discesa anziché caselle di testo?
- Corretto il [problema 549](https://github.com/Microsoft/azuredatastudio/issues/549): Le installazioni con il parametro Silent/VerySilent fanno aprire l'applicazione subito dopo la fine del setup.
- Corretto il [problema 481](https://github.com/Microsoft/azuredatastudio/issues/481): Aggiungere l'opzione "Controlla aggiornamenti".
- Correzioni riguardanti l'editor SQL e il completamento automatico:
   - Corretto il [problema 584](https://github.com/Microsoft/azuredatastudio/issues/584): La parola chiave 'FULL' non è evidenziata da IntelliSense.
   - Corretto il [problema 345](https://github.com/Microsoft/azuredatastudio/issues/345): Colorare le funzioni SQL all'interno dell'editor.
   - Corretto il [problema 300](https://github.com/Microsoft/azuredatastudio/issues/300): In una stringa [#tempData] il carattere finale"]" verrà visualizzato di colore verde.
   - Corretto il [problema 225](https://github.com/Microsoft/azuredatastudio/issues/225): Mancata corrispondenza di colore su parola chiave.
   - Corretto il [problema 60](https://github.com/Microsoft/azuredatastudio/issues/60): Colore non valido quando si utilizza una tabella temporanea nella clausola from.
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
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
