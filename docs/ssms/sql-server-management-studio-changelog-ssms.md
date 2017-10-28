---
title: SQL Server Management Studio - Log delle modifiche (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 10/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 9b477c4c755e98d5aaae6ba92f4a67ff4d02d190
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)

Questo articolo fornisce informazioni dettagliate sugli aggiornamenti, i miglioramenti e le correzioni di bug per le versioni correnti e precedenti di SSMS. Scaricare le [versioni precedenti di SSMS indicate di seguito](#previous-ssms-releases).


## <a name="ssms-173download-sql-server-management-studio-ssmsmd"></a>[SSMS 17.3](download-sql-server-management-studio-ssms.md)
Disponibile a livello generale | Numero di build: 14.0.17199.0

### <a name="enhancements"></a>Miglioramenti

- È stata aggiunta la nuova procedura guidata "Importa file flat" per semplificare l'importazione di file con estensione CSV mediante un framework intelligente, che richiede livelli minimi di intervento dell'utente o conoscenza specifica dell'argomento. Per informazioni dettagliate, vedere [Import Flat File to SQL Wizard](../relational-databases/import-export/import-flat-file-wizard.md) (Procedura guidata Importa file flat in SQL).
- Nodo "XEvent Profiler" aggiunto a Esplora oggetti. Per altre informazioni, vedere [Usare il profiler XEvent di SQL Server Management Studio](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Aggiornamento del filtro e della categorizzazione delle attese nel report cronologico attese di Performance Dashboard.
- È stato aggiunto il controllo della sintassi della funzione "Stima".
- È stato aggiunto il controllo della sintassi delle query di gestione librerie esterne.
- È stato aggiunto il supporto SMO per la gestione librerie esterne.
- È stato aggiunto il supporto di "Avvia PowerShell" alla finestra "Server registrati" (è necessario un nuovo modulo SQL PowerShell).
- Always On: è stato aggiunto il [supporto del routing in sola lettura](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) per i gruppi di disponibilità.
- È stata aggiunta un'opzione per l'invio dei dettagli di traccia alla finestra di output per gli accessi "Active Directory - Universale con supporto MFA" (disattivata per impostazione predefinita; deve essere attivata nelle impostazioni utente in "Strumenti > Opzioni > Servizi di Azure > Cloud di Azure > Livello di traccia della finestra di output di ADAL"). 
- Query Store: 
  - L'interfaccia utente di Query Store è accessibile anche quando QDS è OFF, a condizione che abbia registrato dei dati.
  - L'interfaccia utente di Query Store ora visualizza categorie per le attese in tutti i report esistenti. In questo modo i clienti possono sbloccare gli scenari delle prime query in attesa e molto altro ancora.
- L'inclusione delle intestazioni dei parametri di scripting è ora facoltativa (disattivata per impostazione predefinita; può essere attivata nelle impostazioni utente in"Strumenti > Opzioni > Esplora oggetti di SQL Server > Script > Includere l'intestazione dei parametri di scripting") - [Argomento Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- La denominazione "RC" è stata rimossa.

### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale**

- XEvent: 
   - È stato risolto un problema per il quale SSMS apriva solo una parte degli eventi del file con estensione XEL.
   - È stata migliorata la funzionalità "Controlla i dati dinamici" quando il database predefinito non è "master" - [Argomento Connect 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582).
- Always On: è stato risolto un problema per cui il backup del ripristino dei log restituiva l'errore "L'ultimo LSN del log in questo set di backup è LSN x, che corrisponde a un punto troppo indietro nel tempo per l'applicazione al database".
- Monitor attività processi: sono state risolte incoerenze tra le icone - [Argomento Connect 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100).
- Query Store: è stato risolto un problema per il quale l'utente non poteva scegliere l'intervallo di date personalizzato per i report di Query Store. Collegato ai seguenti argomenti Connect.
   - [Argomento Connect 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Argomento Connect 3139399](http://connect.microsoft.com/SQLServer/feedback/details/3139399)
- È stato risolto un problema per il quale la finestra di dialogo di connessione non cancellava l'ultimo database usato quando le informazioni salvate includevano un database con nome e l'utente selezionava <default>.
- Scripting per gli oggetti:
    - È stato risolto un problema in cui "Generate database script" (Genera script del database) non funzionava e restituiva un errore quando l'utente aveva un database Data Warehouse in pausa nel server, ma aveva selezionato un altro database non DW e stava provando a eseguire uno script.
    - È stato risolto un problema per cui l'intestazione delle stored procedure con script non corrispondeva alle impostazioni di script, restituendo uno script  fuorviante - [Argomento Connect 3139784](http://connect.microsoft.com/SQLServer/feedback/details/3139784).
    - È stato riabilitato il pulsante "Script" per gli oggetti SQL Azure.
    - È stato risolto un problema per cui SSMS non consentiva lo scripting per "Modifica" o "Esegui" su determinati oggetti (UDF, View, SP, Trigger) se connesso a un database SQL di Azure - [Argomento Connect 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386).
- Editor query:
  - Miglioramento di IntelliSense nell'interazione con i database SQL di Azure.
  - È stato risolto un problema per il quale le query non andavano a buon fine a causa di un token di autenticazione scaduto (Autenticazione universale).
  - È stata migliorata l'interazione di IntelliSense con i database SQL di Azure. In particolare, per la connessione a un database SQL di Azure viene usata la grammatica T-SQL più aggiornata (140).
  - È stato risolto un problema per cui in seguito all'apertura di una finestra query con una connessione a un database non DataWarehouse in un server, le finestre di query successive per database DataWarehouse nel server restituivano vari errori per tipi/opzioni non supportate.
- Always On:
   - È stata aggiunta la colonna Modalità seeding al dashboard Always On e alla pagina delle proprietà del gruppo di disponibilità.
   - È stato risolto un problema per cui non era possibile creare un gruppo di disponibilità Linux quando il gruppo primario era in Windows - [Argomento Connect 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856).
- Sono stati risolti vari problemi "Memoria insufficiente" in SSMS durante l'esecuzione di query - [Argomento Connect 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190), [Argomento Connect 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864).
- Profiler: 
   - È stato risolto un problema per cui Profiler non funzionava con SQL 2005.
   - È stato risolto un problema per cui Profiler non implementava l'opzione di connessione "Considera attendibile certificato server".
- Monitor attività: è stato risolto un problema per cui Monitor attività non funzionava con SQL Server in esecuzione su Linux.
- È stato risolto un problema per cui nella classe SMO Transfer non venivano trasferiti gli oggetti Origine dati esterna o Formato di file esterno. Questi tipi di oggetti ora vengono inclusi correttamente nel trasferimento.
- Server registrati:
   - È stata abilitata una query multiserver per i server agente utente (che userà lo stesso token per tutti i server agente utente del gruppo).
- Autenticazione universale AD:
   - È stato risolto un problema per cui l'autenticazione Azure Active Directory non era supportata.
   - È stato risolto un problema per cui la finestra di progettazione tabella/vista non funzionava.
   - È stato risolto un problema per cui "Select Top 1000 rows" (Seleziona le prime 1000 righe) e "Edit Top 200 rows" (Modifica le prime 200 righe) non funzionavano.
- Ripristino del database: è stato risolto un problema per cui il ripristino ometteva l'ultima cartella del percorso durante lo spostamento di file in un percorso alternativo.
- Compressione guidata:
   - È stato risolto un problema con la gestione della compressione guidata per gli indici; è stato risolto un problema per il quale Compressione guidata dati non funzionava per SQL 2016 e versioni precedenti.
        https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - Compressione guidata è stata aggiunta alle tabelle e agli indici di Azure.
- Showplan: 
   - È stato risolto un problema per cui gli operatori PDW non venivano riconosciuti.
- Proprietà del server:
   - È stato risolto un problema per cui non era possibile modificare l'affinità processori server.


**Analysis Services (AS)**

- Sono stati risolti vari problemi di Distribuzione guidata per il supporto dei modelli di livello compatibilità 1400 tabulari e le origini dati Power Query.
- Ora Distribuzione guidata può eseguire la distribuzione ad Azure AS durante l'esecuzione dalla riga di comando.
- Quando si usa l'autenticazione di Windows in Azure AS l'utente ora visualizza correttamente il nome dell'account utente in Esplora oggetti.


### <a name="known-issues-in-this-173-release"></a>Problemi noti in questa versione 17.3:

**SQL Server Management Studio (SSMS) - Generale**

- Le funzionalità di SSMS riportate di seguito non sono supportate per l'autenticazione di Azure AD tramite agente utente con MFA:
   - La procedura Ottimizzazione guidata motore di database non è supportata per l'autenticazione di Azure AD: è stato rilevato un problema per cui l'utente visualizza un messaggio di errore poco chiaro: "Impossibile caricare il file o l'assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…" mentre dovrebbe visualizzare il messaggio "Ottimizzazione guidata motore di database non supporta il database SQL di Microsoft Azure. (DTAClient)".
- Il tentativo di analizzare una query in DTA restituisce un errore: "L'oggetto deve implementare IConvertible. (mscorlib)".
- *Query regredite* non è disponibile nell'elenco di report Query Store in Esplora oggetti.
   - Soluzione alternativa: fare clic con il pulsante destro del mouse sul nodo **Query Store** e selezionare **View Regressed Queries** (Visualizza le query regredite).

**Integration Services (IS)**

- [execution_path] in [catalog].[event_messagea] non è corretto per le esecuzioni dei pacchetti in Scale Out. [execution_path] inizia con "\Package" anziché con il nome oggetto dell'eseguibile del pacchetto. Quando si visualizza il report panoramica delle esecuzioni dei pacchetti in SSMS, il collegamento "Percorso di esecuzione" in Panoramica sulle esecuzioni non funziona. La soluzione alternativa consiste nel fare clic su "Visualizzazione messaggi" nel report panoramica per controllare tutti i messaggi di evento.


## <a name="previous-ssms-releases"></a>Versioni precedenti di SSMS

Scaricare le versioni precedenti di SSMS facendo clic sui collegamenti ai titoli nelle sezioni seguenti.

## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![download](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
Disponibile a livello generale | Numero di build: 14.0.17177.0

### <a name="enhancements"></a>Miglioramenti

- Multi-Factor Authentication (MFA).
  - Autenticazione multiutente di Azure AD per l'autenticazione universale con Multi-Factor Authentication (agente utente con MFA).
  - Aggiunto un nuovo campo di input delle credenziali utente per l'autenticazione universale con MFA per supportare l'autenticazione multiutente.
- La finestra di dialogo di connessione supporta ora i cinque metodi di autenticazione seguenti:
  - Autenticazione di Windows
  - autenticazione di SQL Server
  - Active Directory - Universale con supporto MFA
  - Active Directory - Password
  - Active Directory - Integrata

- Esportazione/importazione di database per la procedura guidata di DacFx tramite l'autenticazione universale con MFA.
- Per il supporto API, vedere l'articolo relativo all'[interfaccia IUniversalAuthProvider](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- La libreria gestita ADAL usata dall'autenticazione universale di Azure AD con MFA è stata aggiornata alla versione 3.13.9.
- È stata aggiunta anche una nuova interfaccia CLI che supporta l'impostazione di amministrazione di Azure AD per il database SQL e SQL Data Warehouse.

 Per altre informazioni sui metodi di autenticazione di Active Directory, vedere [Autenticazione universale con database SQL e SQL Data Warehouse (supporto SSMS per MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) e [Configurare Multi-Factor Authentication per SQL Server Management Studio e Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La finestra di output include voci per le query eseguite durante l'espansione dei nodi di Esplora oggetti.
- Progettazione viste abilitato per i database SQL di Azure.
- Sono state modificate le opzioni di scripting predefinite per l'inserimento di oggetti nello script da Esplora oggetti in SSMS:
  - Per impostazione predefinita, in precedenza lo script generato in una nuova installazione era destinato all'ultima versione di SQL Server, attualmente SQL Server 2017.
  - In SSMS 17.2 è stata aggiunta una nuova opzione: *Corrispondenza delle impostazioni dello script con l'origine*. Se impostata su *True*, lo script generato è destinato alla stessa versione e allo stesso tipo ed edizione del motore del server da cui viene eseguito l'inserimento dell'oggetto nello script.
  - Per l'opzione *Corrispondenza delle impostazioni dello script con l'origine*, *True* è l'impostazione predefinita. Le nuove installazioni di SSMS, quindi, eseguono sempre lo scripting di oggetti nella stessa destinazione del server originale.
  - Quando il valore dell'opzione *Corrispondenza delle impostazioni dello script con l'origine* è impostato su *False*, vengono abilitate le normali opzioni di destinazione di scripting e ripristinato il funzionamento precedente.
    - Tutte le opzioni di scripting sono state spostate nella relativa sezione, *Opzioni versione*, e non si trovano più in *Opzioni generali di scripting*.

- Aggiunto il supporto per i cloud nazionali nel ripristino dall'URL.
- I report QueryStoreUI ora supportano metriche aggiuntive, come RowCount, DOP, CLR Time e così via, da sys.query_store_runtime_stats.
- IntelliSense è ora supportato per il database SQL di Azure.
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Sicurezza: per impostazione predefinita, la finestra di dialogo di connessione non riterrà attendibili i certificati del server e richiederà la crittografia per le connessioni del database SQL di Azure.
- Miglioramenti generali del supporto per SQL Server in Linux:
 - Il nodo Posta elettronica database è nuovamente disponibile.
 - Sono stati risolti vari problemi relativi ai percorsi.
 - Monitoraggio attività è più stabile.
 - La finestra di dialogo Proprietà connessione consente di visualizzare la piattaforma corretta.
- Il report del server di Performance Dashboard è ora disponibile come report predefinito:
  - Connessione a SQL Server 2008 e versioni successive.
  - Il sottoreport sugli indici mancanti usa l'assegnazione di punteggi per consentire l'identificazione degli indici più utili.
  - Il sottoreport sulle statistiche di attesa cronologiche ora aggrega le attese per categoria. Le attese per inattività e sospensione vengono escluse dal filtro per impostazione predefinita.
  - Nuovo sottoreport sui latch cronologici.
- La ricerca nel nodo showplan permette di cercare tra le proprietà del piano. È possibile cercare facilmente qualsiasi proprietà operatore, come il nome della tabella. Per usare questa opzione quando si visualizza un piano:
  - Fare clic con il pulsante destro del mouse sul piano e scegliere l'opzione Trova nodo nel menu di scelta rapida.
  - Usare CTRL+F.


**Analysis Services (AS)**

- Nuova selezione di membri del ruolo AAD per gli utenti senza indirizzi di posta elettronica nei modelli di Azure Analysis Services in SSMS.

**Integration Services (IS)**

- Nuova colonna "Numero di query eseguite" aggiunta al report di esecuzione per SSIS.

### <a name="known-issues-in-this-release"></a>Problemi noti di questa versione:

- Le finestre di query che usano l'autenticazione "Active Directory - Universale con supporto MFA" potrebbero restituire un errore simile al seguente, quando si prova a eseguire una query dopo un'ora dall'apertura:

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   La riesecuzione della query dovrebbe consentire di superare l'errore e dare esito positivo.

- Le funzionalità di SSMS riportate di seguito non sono supportate per l'autenticazione di Azure AD tramite l'autenticazione universale con MFA:
  - La finestra di progettazione **Nuova tabella/vista** mostra il prompt di accesso obsoleto e non funziona per l'autenticazione di Azure AD.
  - La funzionalità **Modifica le prime 200 righe** non supporta l'autenticazione di Azure AD.
  - Il componente **Server registrato** non supporta l'autenticazione di Azure AD.
  - L'**Ottimizzazione guidata motore di database** non è supportata per l'autenticazione di Azure AD. C'è un problema noto in cui il messaggio di errore mostrato all'utente non è molto utile: *Impossibile caricare il file o l'assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory…*, anziché il messaggio previsto *Ottimizzazione guidata motore di database non supporta il database SQL di Microsoft Azure*  (DTAClient).

**Analysis Services (AS)**

- Esplora oggetti in SSAS non visualizza il nome utente dell'autenticazione di Windows nelle proprietà di connessione di Azure Analysis Services.

### <a name="bug-fixes"></a>Correzioni di bug

- Risolto un problema che si presentava durante il tentativo di stampare i risultati di una query come testo.  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- Risolto un problema per cui SSMS eliminava erroneamente tabelle e altri oggetti durante lo scripting dell'eliminazione di tali oggetti in un database SQL di Azure.
- Risolto un problema per cui in alcuni casi SSMS non si avvia e restituisce un messaggio di errore simile a: "Impossibile trovare uno o più componenti. Reinstallare l'applicazione".
- Risolto un problema per cui lo SPID nell'interfaccia utente di SSMS non viene aggiornato né sincronizzato. https://connect.microsoft.com/SQLServer/feedback/details/1898875
- Risolto un problema nell'installazione invisibile all'utente di SSMS in cui l'argomento /passive veniva considerato come /quiet.
- Risolto un problema per cui in alcuni casi SSMS genera un errore "Riferimento oggetto non impostato su un'istanza di un oggetto" all'avvio. http://connect.microsoft.com/SQLServer/feedback/details/3134698
- Risolto un problema in "Compressione guidata dati" che provocava l'arresto anomalo di SSMS quando si premeva "Calcola" nella Tabella grafici.
- Risolto un problema di prestazioni generato facendo clic sull'indice di una tabella con una connessione a Internet lenta. https://connect.microsoft.com/SQLServer/feedback/details/3120783
- Risolto un problema per cui SSMS non riusciva a enumerare i file di backup nei server con regole di confronto con distinzione tra maiuscole e minuscole. http://connect.microsoft.com/SQLServer/feedback/details/3134787 e https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Correzioni varie relative a showplan e al confronto showplan.
- Risolto un problema per cui la finestra di dialogo di connessione non consentiva all'utente di specificare il protocollo di rete da usare per la connessione, a meno che SQL Server non fosse installato nel computer con SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3134997
- Migliorato il supporto per le configurazioni a più monitor in cui alcune finestre di dialogo di SSMS venivano visualizzate in posizioni "casuali". Aggiunta una nuova opzione "Finestre di dialogo attività" in "Esplora oggetti di SQL Server | Comandi" per consentire di ricordare la posizione di una finestra di dialogo attività o di una finestra delle proprietà quando questa si chiude. https://connect.microsoft.com/SQLServer/feedback/details/889169, https://connect.microsoft.com/SQLServer/feedback/details/1158271, https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- Risolto un problema per cui SSMS non riusciva a modificare le proprietà di database per i database SQL di Azure crittografati.
- Migliorata l'opzione "Elimina risultati dopo l'esecuzione". https://connect.microsoft.com/SQLServer/feedback/details/1196581
- Migliorato/risolto un problema per cui gli utenti non possono accedere alle sottoscrizioni di Azure di cui non sono amministratori.
- Migliorata la procedura guidata "Ripristino database" per mantenere il database di destinazione selezionato in OE indipendentemente dalla selezione del database di origine. https://connect.microsoft.com/SQLServer/feedback/details/3118581
- Risolto un problema per cui Esplora oggetti non ordinava correttamente le "stored procedure compilate in modo nativo" appena aggiunte. http://connect.microsoft.com/SQLServer/feedback/details/3133365
- Risolto un problema per cui "Seleziona le prime n righe" non includeva la clausola "prime" per Azure SQLDW. https://connect.microsoft.com/SQLServer/feedback/details/3133551 e https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI: risolto un problema per cui gli intervalli di tempo non personalizzati non funzionavano correttamente per tutti i report.
- Always Encrypted:
    - Migliorata la messaggistica per lo stato di autorizzazione di AKV nella finestra di dialogo Nuovo CMK.
    - Aggiunte descrizioni comandi all'elenco a discesa CEK per agevolare la distinzione dei CEK con nomi lunghi.
    - Risolto un problema per cui alcuni provider dell'archivio chiavi CNG non venivano visualizzati nella finestra di dialogo Nuova chiave master della colonna per Always Encrypted.
- Corretto il "Nome applicazione" non coerente per le connessioni di SSMS. http://connect.microsoft.com/SQLServer/feedback/details/3135115
- Risolto un problema per cui SSMS non generava script corretti per SQL Azure (tabelle e indici con l'opzione DATA_COMPRESSIONS). https://connect.microsoft.com/SQLServer/feedback/details/3133148
- Risolto un problema per cui l'utente non poteva usare i tasti di scelta rapida CTRL+Q per l'Avvio veloce. Nota: i nuovi tasti di scelta rapida per attivare o disattivare l'opzione "IntelliSense abilitato" nell'Editor di Query sono CTRL+B e CTRL+I. https://connect.microsoft.com/SQLServer/feedback/details/3131968
- Risolto un problema in "Ripristina database" per cui SSMS generava un'eccezione durante il tentativo di selezionare un account di archiviazione da una sottoscrizione che include account con domini personalizzati definiti.
- Risolto un problema in "Diagramma di database" per cui SSMS generava un errore "Indice oltre i limiti della matrice" e l'utente non poteva impostare la "Vista tabella" su un'opzione diversa da quella standard. https://connect.microsoft.com/SQLServer/feedback/details/3133792 e http://connect.microsoft.com/SQLServer/feedback/details/3135326
- Risolto un problema in "Backup/Ripristino su URL" per cui SSMS non riusciva a enumerare gli account di archiviazione della versione classica.
- Risolto un problema per cui veniva generata un'eccezione durante il tentativo di aggiungere entità a protezione diretta associate allo schema ai ruoli di database. https://connect.microsoft.com/SQLServer/feedback/details/3118143
- Risolto un problema per cui SSMS restituiva saltuariamente il messaggio di errore "I dati hanno valore Null. Impossibile chiamare il metodo o la proprietà su valori Null" durante l'espansione di un nodo di tabella. http://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA: risolto un problema per cui DTAEngine.exe terminava con la corruzione dell'heap durante la valutazione della funzione di partizione con determinati valori limite.


**Analysis Services (AS)**

- Risolto un problema per cui Ripristina database di Analysis Services non riusciva con errore se il database aveva un nome diverso dall'ID.
- Risolto un problema per cui la finestra di query DAX ignorava l'opzione di menu per l'attivazione/la disattivazione dell'opzione IntelliSense abilitato.
- Risolto un problema che impediva la connessione a SSAS tramite indirizzi http/https di IIS di tipo msmdpump.
- È consentita la connessione ad Azure Analysis Services con una password contenente un punto e virgola.
- L'inserimento nello script del comando Ripristina database di Analysis Services con l'opzione "Ignora appartenenza" includerà la nuova opzione JSON corrispondente, se usato con SQL Server 2017 Analysis Services o Azure Analysis Services.
- Risolto un problema estremamente raro per cui la finestra di dialogo Elimina database poteva generare un errore durante il caricamento.
- Risolto un problema che poteva verificarsi durante il tentativo di visualizzare le partizioni nel modello con livello di compatibilità 1400 contenente una combinazione di query SQL e definizioni di partizioni M.

**Integration Services (IS)**
- Risolto il problema che impediva la visualizzazione dei report sulle informazioni di esecuzione del catalogo SSISDB.
- Risolti i problemi di prestazioni non ottimali in SSMS correlati a un numero elevato di progetti/pacchetti.

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid849819"></a>![Download](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
Disponibile a livello generale | Numero di build: 14.0.17119.0

### <a name="enhancements"></a>Miglioramenti

- Profiler: Guida > Informazioni su visualizza il numero di versione (ad esempio, 17.1)
- Gli utenti del servizio di analisi possono aggiornare le credenziali per le origini dati per i modelli TM 1200 e versioni successive dal menu di scelta rapida nell'origine dati
- I report SSIS integrati visualizzano ora i log dell'esecuzione di scalabilità orizzontale SSIS in CTP 2.1
- Applicazione di gestione della scalabilità orizzontale SSIS
  - Visualizza le informazioni di base relative al master di scalabilità orizzontale.
  - Consente di aggiungere facilmente un ruolo di lavoro alla distribuzione con scalabilità orizzontale.
  - Visualizza tutti i processi di lavoro di scalabilità orizzontale e le relative informazioni di base e può anche abilitarle o disabilitarle facilmente.

### <a name="bug-fixes"></a>Correzioni di bug
- Always On:
  - È stato risolto un problema a causa del quale le proprietà di una replica di disponibilità erano sempre visualizzate come modalità di "failover automatico" per gruppi di disponibilità di WSFC.
  - È stato risolto un problema in cui veniva sovrascritto l'elenco di routing di sola lettura durante l'aggiornamento del gruppo di disponibilità
- Always Encrypted: è stato risolto un problema a causa del quale nel file di log generato mancavano le informazioni generate da DacFx.
- ShowPlan: è stato risolto un problema a causa del quale nell'interfaccia utente era sempre visualizzato l'attributo Tipo di join effettivo per gli operatori di unione non adattivi.
- Installazione:
  - È stato risolto un problema a causa del quale SSMS 17.0 causava l'interruzione di SSDT in Visual Studio 2013 [Argomento Connect 3133479]
  - È stato risolto un problema a causa del quale facendo clic su "Riavvia" al termine dell'installazione il computer non veniva riavviato
- Scripting: impedisce temporaneamente a SSMS di eliminare accidentalmente oggetti di database di Azure durante il tentativo di eseguire lo script dell'eliminazione disabilitando tale opzione.  In una versione futura di SSMS sarà disponibile una correzione adeguata.
- Esplora oggetti: è stato risolto un problema a causa del quale il nodo "database" non era stato espanso durante il collegamento a un database di Azure creato mediante il comando "AS COPY"

## <a name="downloadssdtmediadownloadpng-ssms-170httpgomicrosoftcomfwlinklinkid847722"></a>![Download](../ssdt/media/download.png) [SSMS 17.0](http://go.microsoft.com/fwlink/?LinkID=847722)
Disponibile a livello generale | Numero di build: 14.0.17099.0

### <a name="enhancements"></a>Miglioramenti 

- Pacchetto di aggiornamento e Windows Software Update Services (WSUS) 
    - Le versioni 17.X future includono un pacchetto di aggiornamento cumulativo più piccolo 
  - Il pacchetto di aggiornamento verrà pubblicato anche nel catalogo WSUS  
- Aggiornamenti delle icone
    - Le icone sono state aggiornate per essere compatibili con le icone di VS Shell e supportano risoluzioni DPI elevate
    - Nuove icone di SSMS e del programma Profiler per distinguere le versioni 16.X e 17.X
- Modulo SQL PowerShell
  - Modulo SQL Server PowerShell rimosso da SSMS e attualmente incluso mediante la raccolta di PowerShell (per PowerShell 5.0 è richiesto il supporto delle versioni del modulo)
  - Sono stati introdotti miglioramenti di vario tipo alla "presentazione" (formattazione) di alcuni oggetti SMO (ad esempio per i database vengono ora indicati le dimensioni e lo spazio disponibile e per le tabelle il numero di righe e lo spazio occupato)
  - È stata aggiunta la colorazione quando viene richiamato il prompt dei comandi di PowerShell dal menu "Avvia PowerShell" in OE
  - Sono stati aggiunti i parametri -ClusterType e -RequiredCopiesToCommit ai cmdlet di Gruppi di disponibilità (cmdlet New-SqlAvailabilityGroup, Join-SqlAvailabilityGroup e Set-SqlAvailabilityGroup)
  - Sono stati aggiunti i parametri -ActiveDirectoryAuthority e -AzureKeyVaultResourceId al cmdlet Add-SqlAzureAuthenticationContext
  - Sono stati aggiunti   Revoke-SqlAvailabilityGroupCreateAnyDatabase, Grant-SqlAvailabilityGroupCreateAnyDatabase e Set-SqlAvailabilityReplicaRoleToSecondary cmdlets
  - È stato aggiunto il parametro -SeedingMode a Set-SqlAvailabilityReplica e New-SqlAvailabilityReplica cmdlets
  - È stato aggiunto il parametro - ConnectionString a Get-SqlDatabase
- SQL Server in Linux
    - Miglioramenti generali e correzioni per il log shipping
  - È stato aggiunto il supporto dei percorsi nativi di Linux Allega, Ripristino e database di backup
  - È stato aggiunto il supporto dei percorsi nativi di Linux per la cartella di destinazione del log di controllo
- Analysis Services
  - Finestra di Query DAX:
    - Parentesi corrispondenti nell'editor
    - Supporto della sintassi DEFINE MEASURE e DEFINE VAR
    - Vari miglioramenti di Intellisense
  - Autenticazione universale
    - Consente agli utenti di specificare un nome utente e nessuna password e la finestra di dialogo di accesso di Azure gestisce la connessione
  - Integrazione PQ in SSMS: 
    - Creazione di script del funzionamento delle origini dati strutturate 
    - Visualizzazione e modifica delle origini dati strutturate nell'interfaccia utente PQ
- Nuovo modello "Aggiungi vincolo univoco"
- Showplan
    - Viene visualizzato il valore massimo anziché la somma per i thread nella finestra delle proprietà per il tempo trascorso
    - Vengono esposte nuove proprietà per gli operatori che richiedono la concessione di memoria
    - È stato abilitato il pulsante "Modifica query" in Statistiche query dinamiche
    - È stato incluso il supporto per l'esecuzione interleaved
  - Nuova opzione per "Analizza piano di esecuzione effettivo"
  - Miglioramenti generali per il confronto di showplan
  - Sono state introdotte funzionalità in Confronto showplan per individuare differenze significative nella stima della cardinalità tra i nodi corrispondenti di due piani di query ed eseguire un'analisi di base delle possibili cause principali
- È stato rimosso Configuration Manager dalla finestra di esplorazione dei server registrati
- È stata abilitata la lettura dei log di controllo dal BLOB del servizio di archiviazione di Azure
- È stata aggiunta la parametrizzazione per Always Encrypted. Per altre informazioni, vedere [questa pagina](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) 
- La connessione con autenticazione universale di AAD al database SQL di Azure supporta un ID tenant personalizzato 
- Quando si generano script per il database SQL di Azure, negli script vengono ora inclusi full-text, regole e database
- Correzioni della personalizzazione nelle schermate iniziali per SSMS e Profiler
- Rimozione dell'interfaccia utente per il punto di controllo dell'utilità da SSMS
- SSMS può creare i database di SQL Azure edizione "PremiumRS"
- Gruppi di disponibilità AlwaysOn
  - Aggiunto il supporto di nuovi tipi di cluster: ESTERNO e NESSUNO
    - Aggiunto il supporto per SQL Server su Linux
    - Aggiunto il seeding automatico come opzione per la sincronizzazione iniziale dei dati
    - Corretti alcuni difetti, ad esempio la gestione dell'endpoint URL, l'aggiornamento del DB e il layout dell'interfaccia utente
    - Rimosse le funzionalità correlate alla replica di Azure
  - Migliorato IntelliSense per diverse parole chiave del gruppo di disponibilità
- Monitoraggio attività
  - Aggiunto il nuovo riquadro "Monitoraggio attività" alla finestra di output di SSMS
  - Modificato errore di connessione/messaggio di timeout per registrare informazioni nella finestra di output anziché in un messaggio popup
  - Rimosso grafico vuoto (quinto grafico) nella sezione Panoramica
  - Aggiunto "(in pausa)" al titolo della Panoramica se la raccolta di dati Monitoraggio attività viene messa in pausa
  - Estensioni dei grafici per SQL Server 
    - Nuove icone per il nodo del grafico e le tabelle bordi
    - Il nodo del grafico e le tabelle bordi verranno visualizzati nella cartella Tabelle grafi
    - Modelli disponibili per la creazione del nodo del grafico e delle tabelle bordi
- Modalità presentazione
    - Tre nuove attività disponibili tramite Avvio veloce (CTRL-Q)
    - PresentOn: attiva la modalità presentazione
    - PresentEdit: modifica la dimensione del tipo di carattere per la modalità presentazione.  "Tipo di carattere Editor di testo" per Editor di query.  "Tipo di carattere ambiente" per altri componenti.
    - RestoreDefaultFonts: ripristina le impostazioni predefinite.
    - *Nota: non è attualmente disponibile un comando PresentOff.  Per disattivare la modalità presentazione è possibile usare l'opzione RestoreDefaultFonts*

### <a name="bug-fixes"></a>Correzioni di bug

- È stato risolto un problema a causa del quale SSMS si arrestava in modo anomalo scorrendo sullo showplan per mezzo del touchpad
- È stato risolto un problema a causa del quale SSMS rimane in sospensione per lungo tempo mentre ottiene le proprietà di un database in corso di ripristino o offline 
- È stato risolto un problema a causa del quale non è stato possibile aprire "Help viewer" nei build RC
- È stato risolto un problema a causa del quale in SSMS potrebbero mancare gli elementi della "Casella degli strumenti delle attività dei piani di manutenzione".
- È stato risolto un problema in SSMS a causa del quale l'utente non era in grado di comprimere un database quando il nome del database conteneva parentesi graffe. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- È stato risolto un problema a causa del quale SSMS cercava di eseguire lo script di eliminazione di un database di Azure; in realtà provocava l'eliminazione dello stesso database. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- È stato risolto un problema a causa del quale i valori predefiniti non venivano inseriti negli script per i tipi di tabella definiti dagli utenti. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- È stata introdotta un'altra serie di miglioramenti delle prestazioni nel menu di scelta rapida degli indici. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- È stato risolto un problema che provocava un eccessivo sfarfallio durante il passaggio del mouse su un indice mancante nel piano di esecuzione. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- È stato risolto un problema per cui SSMS impostava il database offline durante lo scripting [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118550)
- Sono state apportate varie correzioni all'interfaccia utente delle versioni localizzate (non in lingua inglese) di SSMS.
- È stato risolto un problema a causa del quale mancava il nodo "Chiavi Always Encrypted" quando la destinazione era SQL 2016 SP1 Standard Edition.
- Always Encrypted
    - Il menu "Always Encrypted" veniva erroneamente abilitato quando la destinazione era SQL 2016 RTM Standard Edition o un server SQL 2014 (o versioni precedenti)
    - È stato risolto un problema per cui IntelliSense segnalava un errore quando veniva usata la sintassi CREATE o ALTER
    - È stato risolto un problema a causa del quale la crittografia non riusciva quando CMK/CEK conteneva caratteri che avrebbero dovuto essere usati con caratteri di escape, ad esempio racchiusi tra parentesi
    - Quando viene generata un'eccezione di memoria insufficiente in SSMS, viene visualizzato un errore che suggerisce all'utente di usare PowerShell nativo (64 bit).
    - È stato risolto un problema a causa del quale la procedura guidata di Always Encrypted aveva esito negativo se venivano usate sottoscrizioni di Resource Group Manager anziché sottoscrizioni di Azure classico
    - È stato risolto un problema a causa del quale la procedura guidata di Always Encrypted visualizzava un errore non corretto se l'utente non aveva autorizzazioni o Azure Key Vault in nessuna sottoscrizione.
    - È stato risolto un problema nella procedura guidata di Always Encrypted per cui la pagina di accesso ad Azure Key Vault non visualizzava le sottoscrizioni di Azure in presenza di più AAD
    - È stato risolto un problema nella procedura guidata di Always Encrypted per cui la pagina di accesso ad Azure Key Vault non visualizzava le sottoscrizioni di Azure per le quali l'utente disponeva dell'autorizzazione di lettura
  - È stato risolto un problema a causa del quale i file di risorse non potevano essere caricati correttamente, con conseguenti messaggi di errore non accurati
- È stato migliorato il contrasto dei collegamenti ipertestuali nella pagina di installazione di SSMS
- È stato risolto un problema a causa del quale i nodi Polybase non venivano visualizzati se connessi a SQL Server Express (2016 SP1)
- È stato risolto un problema a causa del quale SSMS non era in grado di modificare il livello di compatibilità di un database di Azure con v140
- Sono state migliorate le prestazioni di Esplora oggetti durante l'espansione dell'elenco dei database di Azure [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3100675)
- È stato risolto un problema a causa del quale la voce del menu di scelta rapida "Visualizza log di SQL Server" non veniva visualizzata correttamente per i tipi di server non relazionali (AS\RS\IS) 
- È stato risolto un problema a causa del quale il controllo della sintassi di una query di partizione di Analysis Services con autenticazione SQL poteva restituire un messaggio di accesso non riuscito
- È stato risolto un problema per cui la ridenominazione di un modello tabulare AS di anteprima con livello di compatibilità 1400 non poteva essere eseguita in SSMS
- È stato risolto un problema di tipo "operazione non riuscita nel modello" che può verificarsi in rare circostanze dopo che si è provato a eseguire un'operazione non valida nel server AS, ripristinando le modifiche locali dopo un salvataggio non riuscito nel modello
- È stato risolto un errore di digitazione nella finestra di dialogo popup di sincronizzazione del database in Analysis Services
- Le finestre di dialogo del contenitore di backup/ripristino vengono visualizzate fuori schermo in più configurazioni di monitor. 
- La creazione di criteri di sicurezza ha esito negativo se l'oggetto di destinazione include ] nel nome.
- Il menu "Apri recenti" di SSMS 2016 non mostra i file salvati di recente. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)
- Rimossa la reimpostazione delle impostazioni utente quando viene aggiornata la shell di Visual Studio.
- Risolto un problema che impediva all'utente di modificare il livello di compatibilità di un database in SQL Server 2017.
- Le finestre di query che usano l'autenticazione universale di AAD non possono aggiornare la query dopo un'ora.
- Rimozione dell'interfaccia utente per il punto di controllo dell'utilità da SSMS.
- Le connessioni con autenticazione universale di AD non consentono di eseguire query sui dati dopo la scadenza del token iniziale.
- Non è possibile creare script per le regole dal database di SQL Azure al database di SQL Azure.
- Risolto un problema a causa del quale SQL PowerShell non consentiva la connessione a istanze SQL legacy (2014 e precedenti). [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)
- Risolto un problema che causava l'arresto anomalo di SSMS in caso di errori durante l'importazione dei server registrati.
- Risolto un problema che causava l'arresto anomalo di SSMS in presenza di un utente con particolari autorizzazioni per un database. 
- Le tabelle di SSMS scompaiono dall'area di progettazione durante la revisione delle viste. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views) 
- La barra di scorrimento della tabella non consente all'utente di scorrere il contenuto della tabella ed è possibile usare solo le frecce su/giù a questo scopo. È anche possibile scorrere il contenuto della tabella dopo il tentativo di scorrerla con la barra di scorrimento, e questo è un bug. [Argomento Connect](
http://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- Le icone dei server registrati non vengono visualizzate dopo l'aggiornamento del nodo radice.
- Il pulsante Script per Crea database nei server v12 di Azure esegue lo script e quindi visualizza il messaggio "Nessuna azione per cui generare uno script".
- La finestra di dialogo Connetti al server di SSMS non cancella la scheda "Proprietà aggiuntive" per ogni nuova connessione.
- Lo script per generare attività non genera script CREATE DATABASE per un database SQL di Azure.
- La barra di scorrimento in Progettazione viste è disabilitata.
- I percorsi delle chiavi AVK di Always Encrypted non includono gli ID di versione.
- È stato ridotto il numero di query dell'edizione del motore nella finestra di query. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3113387)
- Gli errori di Always Encrypted derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.
- Modificato il timeout di connessione predefinito per OLTP e OLAP da 15 a 30 secondi per risolvere una serie di errori di connessione ignorati. 
- Risolto un arresto anomalo in SSMS all'avvio di un report personalizzato. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3118856)
- Risolto un problema a causa del quale "Genera script..." ha esito negativo per i database SQL di Azure.
- Correzione di "Script come" e della procedura guidata "Genera script" per evitare l'aggiunta di nuove righe superflue durante la creazione di script per oggetti, come le stored procedure. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3115850)
- Provider PowerShell SQLAS: aggiunta della proprietà LastProcessed alle cartelle Dimension e MeasureGroup. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3111879)
- Statistiche query dinamiche: risolto un problema a causa del quale veniva visualizzata solo la prima query in un batch. [Argomento Connect] (http://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- Showplan: visualizzazione del massimo invece della somma per i thread nella finestra delle proprietà.
- Archivio query: aggiunta di un nuovo report per le query con variazioni di esecuzione notevoli.
- Problemi di prestazioni di Esplora oggetti: [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3114074)
    - Il menu di scelta rapida per le tabelle si blocca momentaneamente
    - SSMS è lento quando si fa clic con il pulsante destro del mouse su un indice per una tabella (tramite una connessione Internet remota). 
    - Evitare di eseguire query di tabella che eseguono ordinamenti nel server
- Rimozione della distribuzione guidata in Azure (Distribuisci database in una macchina virtuale Azure) da SSMS
- Risolto un problema a causa del quale gli indici mancanti non venivano visualizzati nei piani di esecuzione in SSMS [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3114194)
- Risolto un problema comune di arresto anomalo in fase di chiusura in SSMS
- Risolto un problema in Esplora oggetti a causa del quale si verificava un errore in seguito alla visualizzazione del menu di scelta rapida nei nodi Polybase|Gruppo con scalabilità orizzontale [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3115128)
- Risolto un problema a causa del quale può verificarsi un arresto anomalo di SSMS durante il tentativo di visualizzare le autorizzazioni per un database
- Archivio query: miglioramenti generali nelle voci del menu di scelta rapida per le griglie dei risultati del report dell'archivio query
- La configurazione di Always Encrypted per una tabella esistente ha esito negativo con errori per gli oggetti correlati. [Argomento Connect](http://connect.microsoft.com/SQLServer/feedback/details/3103181)
- La configurazione di Always Encrypted per un database esistente con più schemi non funziona. [Argomento Connect] (http://connect.microsoft.com/SQLServer/feedback/details/3109591)
- La procedura guidata Always Encrypted, Colonna crittografata ha esito negativo a causa del database che contiene viste che fanno riferimento a viste di sistema. [Argomento Connect] (http://connect.microsoft.com/SQLServer/feedback/details/3111925)
- Durante la crittografia con Always Encrypted, gli errori derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.
- Risolto un problema di troncamento dell'interfaccia utente nella finestra di dialogo "Nuova registrazione server"
- Risolto un problema dell'interfaccia utente delle condizioni DMF a causa del quale le espressioni che contengono valori costanti stringa con virgolette vengono aggiornate in modo non corretto
- Risolto un problema che potrebbe causare l'arresto anomalo di SSMS durante l'esecuzione di report personalizzati
- Aggiunta della voce di menu per l'esecuzione con scalabilità orizzontale al nodo della cartella
- Risolto un problema con la funzionalità di elenco di IP consentiti dal firewall di database Azure SQL
- Risolto un problema in SSMS che ha causato un'eccezione di tipo Riferimento all'oggetto non impostato durante la modifica dell'origine della partizione multidimensionale
- Risolto un problema in SSMS che ha causato un'eccezione di tipo Riferimento all'oggetto non impostato durante l'eliminazione di un assembly cliente dal server AS multidimensionale
- Risolto un problema a causa del quale non è riuscita la rinomina di un database 1400 tabulare AS
- Risolto un problema di elaborazione di un'origine dati tabulare con livello di compatibilità 1400 prodotto dalla finestra di dialogo delle proprietà di connessione
- Rimossa l'assunzione secondo cui le tabelle nel modello tabulare con livello di compatibilità AS 1400 hanno almeno una partizione
- Ctrl-R alterna il riquadro dei risultati nell'editor di query SSMS DAX


## <a name="downloadssdtmediadownloadpng-ssms-1653httpgomicrosoftcomfwlinklinkid840946"></a>![Download](../ssdt/media/download.png) [SSMS 16.5.3](http://go.microsoft.com/fwlink/?LinkID=840946)
Disponibile a livello generale | Numero di build: 13.0.16106.4

In questa versione sono stati risolti i problemi seguenti:

* Risolto un problema introdotto in SSMS 16.5.2 che causava l'espansione del nodo 'Tabella' quando la tabella aveva più di una colonna di tipo sparse.

* Gli utenti possono distribuire pacchetti SSIS contenenti Gestione connessione OData per connettere una risorsa Microsoft Dynamics AX/CRM Online al catalogo SSIS. Per altre informazioni, vedere [Gestione connessione OData](../integration-services/connection-manager/odata-connection-manager.md).

* La configurazione di Always Encrypted per una tabella esistente ha esito negativo con errori per gli oggetti correlati. [ID Connect 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configurazione di Always Encrypted per un database esistente con più schemi non funziona. [ID Connect 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* La procedura guidata Always Encrypted, Colonna crittografata ha esito negativo a causa del database che contiene viste che fanno riferimento a viste di sistema. [ID Connect 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Durante la crittografia con Always Encrypted, gli errori derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.

* Il menu *Apri recenti* non mostra i file salvati di recente. [ID Connect 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS è lento quando si fa clic con il pulsante destro del mouse su un indice per una tabella (tramite una connessione Internet remota). [ID Connect 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Risolto un problema con la barra di scorrimento di SQL Designer. [ID Connect 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Il menu di scelta rapida per le tabelle si blocca momentaneamente 
 
* SSMS in alcuni casi genera eccezioni in Monitoraggio attività e subisce un arresto anomalo. [ID Connect 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* Si verifica un arresto anomalo di SSMS 2016 con l'errore "Il processo è stato terminato a causa di un errore interno del runtime .NET in IP 71AF8579 (71AE0000) con codice di uscita 80131506"


## <a name="ssms-1651"></a>SSMS 16.5.1
Disponibile a livello generale | Numero di build: 13.0.16100.1

* Risolto un problema per cui Invoke-Sqlcmd inserisce erroneamente più righe quando si verifica il vincolo CHECK. [Argomento Microsoft Connect: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* Risolto un problema in cui le versioni localizzate non ITA non funzionano completamente durante la creazione di gruppi di disponibilità.

* Risolto un problema in cui facendo clic sul'XML del piano di query non viene aperta l'interfaccia utente SSMS corretta.


## <a name="downloadssdtmediadownloadpng-ssms-165httpgomicrosoftcomfwlinklinkid832812"></a>![Download](../ssdt/media/download.png) [SSMS 16.5](http://go.microsoft.com/fwlink/?LinkID=832812)
Disponibile a livello generale | Numero di build: 13.0.16000.28

* È stato risolto il problema per cui potrebbe verificarsi un arresto anomalo quando è stato fatto clic su un database con nome della tabella contenente ";:".
* È stato risolto il problema per cui le modifiche apportate alla pagina Modello nella finestra delle proprietà del database tabulare AS devono creare uno script della definizione originale. 
[Argomento Microsoft Connect: 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* È stato risolto il problema per cui i file temporanei vengono aggiunti all'elenco "File recenti".  
[Argomento Microsoft Connect: 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* È stato risolto il problema per cui la voce del menu di gestione della compressione è disabilitata per i nodi della tabella utente nell'albero Esplora oggetti.  
[Argomento Microsoft Connect: 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* È stato risolto il problema per cui l'utente non è in grado di impostare le dimensioni del carattere per Esplora oggetti, Esplora server registrati, Esplora modelli, nonché per i dettagli di Esplora oggetto. Il carattere per le finestre di esplorazione usato sarà il tipo di carattere Ambiente.  
[Argomento Microsoft Connect: 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* È stato risolto il problema per cui SSMS si riconnette sempre al database predefinito quando la connessione viene interrotta.  
[Argomento Microsoft Connect: 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* Sono stati risolti numerosi problemi relativi ai valori DPI alti nella gestione dei criteri e nella finestra di modifica delle query, tra cui le icone del piano di esecuzione.

* È stato risolto il problema della mancanza dell'opzione per la configurazione del carattere e dei colori degli eventi estesi.

* È stato risolto il problema degli arresti anomali di SSMS che si verificano durante la chiusura dell'applicazione o quando si tenta di visualizzare la finestra di dialogo degli errori.


## <a name="downloadssdtmediadownloadpng-ssms-1641-september-2016httpgomicrosoftcomfwlinklinkid828615"></a>![Download](../ssdt/media/download.png) [SSMS 16.4.1 (settembre 2016)](http://go.microsoft.com/fwlink/?LinkID=828615)
Disponibile a livello generale | Numero di build: 13.0.15900.1

*  È stato corretto un problema per cui veniva generato un errore durante il tentativo di modifica di una stored procedure:  
[Argomento Microsoft Connect N. 3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* Nuovi cmdlet 'Read-SqlTableData', 'Read-SqlViewData' e 'Write-SqlTableData' per visualizzare e scrivere dati tramite PowerShell.  
[Scheda Read-SqlTableData di Trello](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Argomento Microsoft Connect N. 2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* Nuovo cmdlet 'Add-SqlLogin' per abilitare nuovi scenari di gestione degli account di accesso tramite PowerShell.  
[Argomento Microsoft Connect N. 2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  Supporto migliorato e facilità d'uso per la connessione a vari cloud nazionali da parte degli utenti.
    
    
*  È stato corretto un problema per cui veniva generata un'eccezione di tipo memoria insufficiente.  
[Argomento Microsoft Connect N. 3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Argomento Microsoft Connect N. 3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  È stato corretto un problema per cui l'opzione di filtro in base allo schema non era considerata valida.  
[Argomento Microsoft Connect N. 3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Argomento Microsoft Connect N. 3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  È stato corretto un problema per cui la finestra Monitoraggio per un database con estensione non risultava accessibile.
    
*  È stato corretto un problema per cui la Guida apriva sempre contenuto online. Gli utenti possono ora decidere se preferiscono la guida online oppure offline tramite "Imposta preferenza Guida" nel menu della guida.   
[Argomento Microsoft Connect N. 2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  È stato corretto un problema per cui l'inserimento nello script di un modello tabulare di Analysis Services di livello 1200 non rimuoveva la password per gli script, anche se la versione del server aveva [l'oggetto modello client sincronizzato prima dell'esecuzione dello script].
    
*  È stato corretto un problema per cui l'opzione 'SELEZIONA LE PRIME N RIGHE' generava sintassi deprecata per l'operatore TOP.  
[Argomento Microsoft Connect N. 3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  Sono stati corretti vari problemi di layout tramite SSMS, tra cui la pagina Proprietà account di accesso e le opzioni avanzate di esecuzione query.   
[Argomento Microsoft Connect N. 3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Argomento Microsoft Connect N. 3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Argomento Microsoft Connect N. 3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  È stato corretto un problema per cui una soluzione veniva creata automaticamente ogni volta che un utente apriva una nuova finestra di query.   
[Argomento Microsoft Connect N. 2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Argomento Microsoft Connect N. 2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Argomento Microsoft Connect N. 2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  È stato corretto un problema per cui le tabelle temporali non potevano essere espanse in Esplora oggetti nei database di sistema.  
[Argomento Microsoft Connect N. 2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  Correzione di un problema per cui SSMS esegue una query per SELECT @@trancount dopo l'esecuzione di un batch.    
[Argomento Microsoft Connect N. 3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  È stato corretto un problema in Analysis Services per cui la creazione di uno script dalla pagina delle proprietà di un server generava una finestra di dialogo di connessione nascosta.
    
*  È stato corretto un problema per cui CTRL+Q non selezionava la barra degli strumenti Avvio veloce.
    
*  È stato corretto un problema per cui la modifica del valore MaxSize di un database tramite la finestra di dialogo Proprietà server è stata interrotta per i database > 2 TB.  
[Argomento Microsoft Connect N. 1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  È stato corretto un problema per cui la procedura guidata Ripristina database non accettava nomi di file con spazio vuoto iniziale:   
[Argomento Microsoft Connect N. 2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="downloadssdtmediadownloadpng-ssms-163-august-2016httpgomicrosoftcomfwlinklinkid824938"></a>![Download](../ssdt/media/download.png) [SSMS 16.3 (agosto 2016)](http://go.microsoft.com/fwlink/?LinkID=824938)
Disponibile a livello generale | Numero di versione: 13.0.15700.28

* Le versioni mensili di SSMS sono ora contrassegnate numericamente.

* [Nuova opzione di autenticazione **'Autenticazione universale di Active Directory'**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Si tratta di un meccanismo di autenticazione basato su token di Azure Active Directory che supporta autenticazione a più fattori, password e meccanismi di autenticazione integrati.

* Nuovi modelli di eventi estesi corrispondenti alla funzionalità dei modelli di SQL Server Profiler [(Argomento Microsoft Connect N. 2543925)](../tools/sql-server-profiler/sql-server-profiler-templates.md).

* Nuove finestre di dialogo Crea database e Proprietà database per i database SQL di Azure.

* Nuovi cmdlet 'Get-SqlLogin' e 'Remove-SqlLogin' per la gestione degli account di accesso di SQL Server tramite PowerShell.  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect n. 2588952.](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* Nuovo cmdlet di PowerShell 'New-SqlColumnMasterKeySettings' che aggiunge il supporto per la creazione di chiavi master della colonna per i provider arbitrari e i percorsi delle chiavi.

* Nuova finestra di dialogo 'Crea database' per semplificare la creazione di database di SQL di Azure in SSMS>

* Supporto per la funzionalità di filtro nel nodo 'Database' di Esplora oggetti di SSMS. Passare al nodo 'Database' in Esplora oggetti e fare clic sull'icona del filtro nella barra degli strumenti di Esplora oggetti per filtrare l'elenco dei database.

* Supporto per gli account di archiviazione di tipo Azure Resource Manager (ARM) nelle procedure guidate di backup e ripristino.

* [Supporto beta iniziale per schermi ad alta risoluzione](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/).  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect N. 1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display), [Argomento Microsoft Connect N. 1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/), [Argomento Microsoft Connect N. 1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/), [Argomento Microsoft Connect N. 1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/),  [Argomento Microsoft Connect N. 1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/), [Argomento Microsoft Connect N. 2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/), [Argomento Microsoft Connect N. 1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/), [Argomento Microsoft Connect N. 1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/), [Argomento Microsoft Connect N. 2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/), [Argomento Microsoft Connect N. 1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/), [Argomento Microsoft Connect N. 2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/), [Argomento Microsoft Connect N. 2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/), [Argomento Microsoft Connect N. 2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/), [Argomento Microsoft Connect N. 2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/), [Argomento Microsoft Connect N. 1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/), [Argomento Microsoft Connect N. 2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/), [Argomento Microsoft Connect N. 2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/), [Argomento Microsoft Connect N. 2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* Miglioramenti apportati a Ottimizzazione guidata motore di database per supportare la lettura automatica di un carico di lavoro dall'archivio di query di SQL Server.

* Miglioramenti apportati a Ottimizzazione guidata motore di database per la visualizzazione delle indicazioni relative agli indici per indici columnstore cluster, indici columnstore non cluster e indici rowstore.

* Supporto per l'invio di comandi DBCC (Database Console Command) tramite i cmdlet di PowerShell per SQL Server Analysis Services.

* Correzione di bug per visualizzare testo non crittografato di colonne LOB (large object) di AlwaysEncrypted decrittografate in SSMS.  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect n. 2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Correzione di bug nella finestra di dialogo 	Crittografia sempre attiva per correggere l'arresto anomalo quando gli stili visivi di Windows non sono abilitati (ad esempio, abilitazione della visualizzazione con contrasto elevato).

* Correzione di bug per l'errore "Impossibile trovare il metodo" che impedisce la connessione alle istanze di SQL Server.

* Correzione di bug per l'arresto anomalo di SSMS durante la creazione di una funzione di partizione con offset di datetime.

* Correzione di bug per aggiungere o rimuovere il requisito di Microsoft .NET 3.5 per l'avvio dello strumento di amministrazione Riesecuzione distribuita (DReplay.exe).

* Correzione di bug in Creazione guidata di distribuzione di Analysis Services per supportare i nomi dei server completi.

* Correzione di bug in SSMS per visualizzare le partizioni nei modelli tabulari di Analysis Services con un modello di compatibilità 2016.  
*Richieste collegate a bug segnalati dai clienti:*   
[Argomento Microsoft Connect n. 2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Miglioramenti apportati alle prestazioni e correzioni di bug in modelli tabulari di Analysis Services e SQL Server Shared Management Objects (SMO). 


---
## <a name="downloadssdtmediadownloadpng-ssms-july-2016-hotfix-updatehttpgomicrosoftcomfwlinklinkid822301"></a>![Download](../ssdt/media/download.png) [SSMS - Aggiornamento hotfix luglio 2016](http://go.microsoft.com/fwlink/?LinkID=822301)
Disponibile a livello generale | Numero di versione: 13.0.15600.2

* **Correzione di bug in SSMS per abilitare le voci di menu selezionabili con il pulsate destro del mouse mancanti**.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect n. 2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Argomento Microsoft Connect n. 2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Argomento Microsoft Connect n. 2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016"></a>SSMS (luglio 2016) 
Disponibile a livello generale | Numero di versione: 13.0.15500.91

* *Modifica, 5 luglio:* è stato migliorato il supporto per i database tabulari SQL Server 2016 (livello di compatibilità 1200) nella finestra di dialogo di elaborazione Analysis Services e nella Distribuzione guidata Analysis Services.

* *Modifica, 5 luglio:* è disponibile una nuova opzione nella finestra di dialogo Query Execution Options (Opzioni di esecuzione query) per l'impostazione di "XACT_ABORT". Questa opzione, abilitata per impostazione predefinita in questa versione di SSMS, indica a SQL Server di eseguire il rollback dell'intera transazione e di interrompere il batch se si verifica un errore di run-time.

* Supporto per Azure SQL Data Warehouse in SSMS.

* Aggiornamenti significativi al modulo SQL Server PowerShell. Sono inclusi un nuovo [modulo SQL PowerShell e nuovi cmdlet per Crittografia sempre attiva, SQL Agent e i log degli errori di SQL](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update).

* Supporto per la generazione di script PowerShell nella procedura guidata Crittografia sempre attiva.

* Tempi di connessione ai database SQL di Azure significativamente migliorati.

* La nuova finestra di dialogo "Backup to URL" (Backup su URL) supporta la creazione di credenziali di archiviazione di Azure per i backup dei database di SQL Server 2016. Questa finestra di dialogo offre un'esperienza semplificata per l'archiviazione dei backup dei database in un account di archiviazione di Azure.
 
* Nuova finestra di dialogo Ripristino per semplificare il ripristino di un backup del database SQL Server 2016 dal servizio di archiviazione di Microsoft Azure.
 
* Correzione di bug nella finestra di progettazione query di SSMS per consentire l'aggiunta di tabelle a tale finestra nel caso in cui un utente non disponga delle necessarie autorizzazioni SELECT.

* Correzione di bug per l'aggiunta del supporto IntelliSense per le funzioni 'TRY_CAST()' e 'TRY_CONVERT()'.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).

* Correzione di bug nel modulo PowerShell per abilitare il caricamento dell'estensione 'SQLAS' di Analysis Services.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension).

* Correzione di bug nella finestra dell'editor SSMS per consentire l'apertura dei file SQL mediante trascinamento della selezione.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).

* Correzione di bug nel profiler per correggere l'arresto anomalo di quest'ultimo durante le modifiche  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped).  
[Argomento Microsoft Connect N. 2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968).

* Correzione di bug in SSMS per evitare l'arresto anomalo del sistema quando si modifica un collegamento di join in Progettazione tabelle di SSMS.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).

* Correzione di bug in SSMS per abilitare la generazione di script di database per i membri del ruolo db_owner  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june).

* Correzione di bug nell'editor di SSMS per rimuovere il ritardo nella chiusura di una scheda di query nel caso in cui il server sia offline.  
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline).

* Correzione di bug per abilitare l'opzione Backup nei database di SQL Server Express. 
*Richieste collegate a bug segnalati dai clienti:*  
[Argomento Microsoft Connect N. 2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks).  
[Argomento Microsoft Connect N. 2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance).

* Correzione di bug in Analysis Services per visualizzare correttamente il provider di feed di dati per modelli Analysis Services multidimensionali.

----
## <a name="downloadssdtmediadownloadpng-ssms-june-2016httpgomicrosoftcomfwlinklinkid799832"></a>![Download](../ssdt/media/download.png) [SSMS (giugno 2016)](http://go.microsoft.com/fwlink/?LinkID=799832)
Disponibile a livello generale | Numero di versione: 13.0.15000.23

* SSMS è disponibile a livello generale a partire dalla versione di giugno 2016.

* Nuova finestra di dialogo Ricerca veloce in SSMS meglio integrata nel documento corrente che consente la ricerca tramite espressioni regolari. 
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* Miglioramenti apportati al programma di installazione di SSMS per consentire di tenere traccia dello stato dell'installazione ed eseguire codici di uscita per installazioni automatiche tramite script.

* Correzione di bug nella Guida sensibile al contesto di SSMS per visualizzare correttamente i documenti e gli articoli della Guida.

* Correzione del bug nella vista Query regredite di Archivio dati query che provocava l'arresto anomalo di SSMS durante lo scorrimento.

* Correzione di bug nel connettore OLEDB per Excel e Analysis Services per consentire le connessioni da Excel 2016 a SQL Server Analysis Services.

* Correzione di bug nella finestra di dialogo Connessione di SSMS per visualizzare la finestra di dialogo di connessione sullo stesso monitor come finestra principale di SSMS in sistemi con più monitor.  
*Richieste collegate a bug segnalati dai clienti:*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* Correzioni di bug in Always Encrypted. Bug corretto dove l'opzione di menu Crittografia sempre attiva non risultava abilitata correttamente per l'estensione database. Bug corretto anche nella procedura guidata Crittografia sempre attiva dove non veniva eseguita correttamente tramite il provider HSM SafeNet (Luna SA).


## <a name="additional-downloads"></a>Download aggiuntivi  
Per un elenco di tutti i download di SQL Server Management Studio, vedere [Area download Microsoft](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Per la versione più recente di SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  

