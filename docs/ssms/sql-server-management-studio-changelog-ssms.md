---
title: SQL Server Management Studio - Log delle modifiche (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fd9e5b79aaf16454e74eb1e63325f95bf5f45a40
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703989"
---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Questo articolo fornisce informazioni dettagliate sugli aggiornamenti, i miglioramenti e le correzioni di bug per le versioni correnti e precedenti di SSMS. Scaricare le [versioni precedenti di SSMS](#previous-ssms-releases).

## <a name="ssms-180-preview-5download-sql-server-management-studio-ssmsmd"></a>[SSMS 18.0 (anteprima 5)](download-sql-server-management-studio-ssms.md)

Numero di build: 15.0.18068.0<br>
Data di rilascio: 15 novembre 2018

Anteprima 5 è la seconda anteprima pubblica di SSMS 18.0. Per la versione GA (General Availability) più recente di SSMS, [scaricare e installare SSMS 17.9](#ssms-179-latest-ga-release).

### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

- Dimensioni massime dei file di log degli errori incluse in "Configura log degli errori di SQL Server". Per informazioni dettagliate, vedere [Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035/suggestions/33624115) (Impostare le dimensioni massime dei log degli errori in SQL Server).  

Esplora oggetti:

- Estensione della logica per richiedere una conferma quando si rinomina un database per tutti gli oggetti dello schema (l'impostazione può essere configurata e questa opzione disabilitata).

Scripting per gli oggetti:

- Aggiunte nuove voci di menu per "CREATE OR ALTER" quando si esegue lo scripting per gli oggetti.

Aggiornamento del livello di compatibilità del database:

-  Aggiunta una nuova opzione in <Database name> > **Attività** > **Aggiornamento database**. Questa opzione consente di avviare il nuovo *Assistente ottimizzazione query* per guidare gli utenti attraverso il processo di:
   - Raccolta di baseline delle prestazioni prima dell'aggiornamento del livello di compatibilità del database.  
   - Aggiornamento al livello di compatibilità del database desiderato.
   - Raccolta di un secondo passaggio di dati sulle prestazioni nel corso dello stesso carico di lavoro.
   - Rilevamento delle regressioni del carico di lavoro e specifica di elementi consigliati testati per migliorare le prestazioni del carico di lavoro.

Questa funzionalità è simile al processo di aggiornamento del database documentato in [Mantenere la stabilità delle prestazioni durante l'aggiornamento alla nuova versione di SQL Server](https://docs.microsoft.com/sql/relational-databases/performance/query-store-usage-scenarios#CEUpgrade), tranne nell'ultimo passaggio in cui l'Assistente ottimizzazione query non si basa su uno stato valido noto in precedenza per generare elementi consigliati.

Query Store:

- Migliorata l'usabilità di alcuni report (Consumo complessivo risorse) grazie all'aggiunta di migliaia di separatori per i numeri visualizzati sull'asse Y dei grafici.
- Aggiunto un nuovo report Statistiche di attesa query.

Valutazione della vulnerabilità:

- Abilitato il menu delle attività Valutazione della vulnerabilità in Azure SQL Data Warehouse.

Maschera dati:

- Aggiunta maschera dati statica. La maschera dati statica è uno strumento di protezione dei dati che consente agli utenti di creare una copia del database per mascherare i propri dati sensibili nella copia. Questa funzionalità si rivela utile per chi condivide il database di produzione con utenti non di produzione, ad esempio il team di sviluppo/test o di analisi. Per altre informazioni, vedere [Static Data Masking for Azure SQL Database and SQL Server](https://azure.microsoft.com/blog/static-data-masking-preview/) (Maschera dati statica per database SQL di Azure e SQL Server).

SMO:

- Nuova proprietà ProductUpdateLevel inclusa nell'oggetto Server, che esegue il mapping al livello di servizio per la versione di SQL in uso (ad esempio, CU12 RTM, e così via).
- Nuova proprietà LastGoodCheckDbTime inclusa in un oggetto Database, che esegue il mapping alla proprietà del database "lastgoodcheckdbtime". Se tale proprietà non è disponibile, viene restituito il valore predefinito 1/1/1900 12:00:00 AM.

Supporto di Istanza gestita:

- Supporto aggiunto per la logica di replica.

Integrazione di Azure Data Studio:

- Aggiunta la voce di menu **Start Azure Data Studio** (Avvia Azure Data Studio) in Esplora oggetti.

SSIS:

- Aggiunta del supporto per consentire ai clienti di pianificare in Azure-SSIS Integration Runtime i pacchetti SSIS che si trovano nel cloud di Azure per enti pubblici.

### <a name="bug-fixes"></a>Correzioni di bug

Arresto anomalo/blocco:

- Risolto il problema dell'arresto anomalo del sistema in SSMS quando si tenta di usare il server di gestione centrale e i server di database SQL di Azure. Per altre informazioni, vedere [crash when using Central Management Server](https://feedback.azure.com/forums/908035/suggestions/33374884) (Arresto anomalo del sistema con il server di gestione centrale).  
- Risolto un blocco in Esplora oggetti mediante l'ottimizzazione del modo in cui viene recuperata la proprietà IsFullTextEnabled.
- Risolto un blocco in "Copia guidata database" evitando la compilazione di query non necessarie per recuperare le proprietà del database.

Opzioni SSMS:

- Ripristinata la scelta rapida da tastiera CTRL+D, presente nella versione precedente di SSMS. Per altre informazioni, vedere [Restore CTRL-D shortcut for ResultsToGrid in SSMS](https://feedback.azure.com/forums/908035/suggestions/35544754) (Ripristinare la scelta rapida da tastiera CTRL-D per ResultsToGrid in SSMS).

Esplora oggetti:

- Risolto un problema per cui la finestra di dialogo "Nuova pianificazione processo" non eseguiva il rendering correttamente nei monitori a risoluzione elevata.
- Risolta/migliorata la modalità di visualizzazione delle dimensioni del database ("Dimensioni (MB)") in Esplora oggetti. Con il separatore delle migliaia vengono formattate solo 2 cifre decimali. Per altre informazioni, vedere [Too Many Decimal-places in Size (MB) property](https://feedback.azure.com/forums/908035/suggestions/34379308) (Troppi decimali nella proprietà Dimensioni (MB)).
- Risolto un problema che impediva la creazione di un "Indice spaziale" con un errore simile a "Per eseguire questa azione, impostare la proprietà PartitionScheme".
- Miglioramenti delle prestazioni minori in Esplora oggetti per evitare di eseguire query aggiuntive, quando possibile.

Analysis Services (AS):

- Risolto un problema per cui l'analisi DAX generava l'eccezione File non trovato.
- Aggiunto nuovamente il collegamento "Distribuzione guidata" al menu Start.

Integration Services:

- Risolto un problema side-by-side per cui la distribuzione guidata non riusciva a connettersi a SQL Server se nello stesso computer erano installati sia SQL Server 2019 che SSMS 18.0.
- Risolto un problema per cui l'attività di pianificazione della manutenzione non poteva essere modifica al momento della progettazione della pianificazione della manutenzione.
- Risolto un problema per cui la distribuzione guidata si bloccava quando il progetto in distribuzione veniva rinominato.
- Abilitata l'impostazione dell'ambiente nella funzionalità di pianificazione di Azure-SSIS IR.


HADR/Gruppi di disponibilità:

- Risolto un problema per cui i ruoli nella procedura guidata Failover gruppo di disponibilità erano sempre visualizzati come "Risoluzione".
- Risolto un problema per cui SSMS visualizzava avvisi troncati nel dashboard del gruppo di disponibilità.

Backup/ripristino/collegamento/scollegamento del database:

- Risolto un problema per cui nella procedura guidata "Collega Database" non venivano visualizzati file secondari rinominati. Ora tali file vengono visualizzati con un commento aggiunto, ad esempio, "Non trovato". Per altre informazioni, vedere [database attach not displaying secondary files](https://feedback.azure.com/forums/908035/suggestions/32897434) (File secondari non visualizzati in collegamento database).


Supporto di Istanza gestita:

- Supporto migliorato per l'accesso di AAD (in SSMS Explorer).
- Scripting degli oggetti filegroup di SMO migliorato.
- Interfaccia utente migliorata per le credenziali e i controlli.


Importazione guidata applicazione livello dati:

- Risolto un problema per cui la procedura guidata di importazione applicazione livello dati non funzionava se si era connessi tramite Azure Active Directory.

Visualizzatore XEvent:

- Risolto un problema per cui il visualizzatore XEvent si arrestava in modo anomalo quando si tentava di raggruppare gli eventi usando le *opzioni della barra degli strumenti Eventi estesi*.

Valutazione della vulnerabilità:

- Risolto un problema per cui i risultati dell'analisi non venivano caricati correttamente.




## <a name="ssms-180-preview-4"></a>SSMS 18.0 (anteprima 4)

Numero di build: 15.0.18040.0<br>
Data di rilascio: 24 settembre 2018

Anteprima 4 è la prima anteprima pubblica di SSMS 18.0. Per la versione GA (General Availability) più recente di SSMS, [scaricare e installare SSMS 17.9](#ssms-179-latest-ga-release).

### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

File di download di dimensioni più piccole:

- Le dimensioni correnti del bundle sono inferiori alla metà di quelle di SSMS 17.x (circa 400 MB). Le dimensioni aumenteranno quando verranno di nuovo aggiunti i componenti Integration Services, ma non raggiungeranno quelle delle versioni precedenti.

SSMS 18.x è basato sul nuovo prodotto Visual Studio 2017 Isolated Shell:

- Si tratta di una shell moderna (è stato scelto Visual Studio 2017 15.6.4). La nuova shell sblocca tutte le correzioni di accessibilità integrate in SSMS e in Visual Studio.

Miglioramenti dell'accessibilità:

- È stata dedicata un'attenzione particolare ai problemi di accessibilità in tutti gli strumenti (SSMS, DTA e Profiler).

SSMS può essere installato in una cartella personalizzata:

- Attualmente questa opzione è disponibile solo nell'installazione dalla riga di comando. Passare il seguente argomento aggiuntivo a SSMS-Setup-ENU.exe:

  `SSMSInstallRoot=C:\MySSMS18`

  Per impostazione predefinita il nuovo percorso di installazione per SQL Server Management Studio è: `%ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`
  
  > [!NOTE]
  > Questo non significa che SSMS sia multi-istanza.

SSMS non condivide più componenti con il motore SQL:

- È stata dedicata un'attenzione particolare a evitare la condivisione di componenti con il motore SQL. Questa condivisione generava spesso problemi di funzionalità quando i programmi di installazione di SQL o di SSMS sovrascrivevano file installati dall'altro programma.

SSMS ora richiede NetFx 4.7.2 o versioni successive:

- Il requisito minimo è passato da NetFx4.6.1 a NetFx4.7.2: in tal modo è possibile trarre vantaggio dalle nuove funzionalità incluse nel nuovo framework.

SSMS non è supportato in Windows 8. Per Windows 10/Windows Server 2016 è richiesta la versione 1607 (10.0.14393) o versioni successive:
  
- A causa della nuova dipendenza da NetFx 4.7.2, SSMS 18.0 non viene installato in Windows 8, nelle versioni meno recenti di Windows 10 e in Windows Server 2016. In questi sistemi operativi il programma di installazione di SSMS si blocca. Windows 8.1 è ancora supportato.

SSMS non viene aggiunto alla variabile di ambiente PATH:

- Il percorso di SSMS.EXE (e degli strumenti in generale) non viene più aggiunto alla variabile PATH. Gli utenti possono aggiungerlo direttamente o tramite il menu Start se usano una versione recente di Windows.

Supporto per [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]

- Questa è la prima versione di SSMS che *supporta completamente* [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] (compatLevel 150 e così via).
- Supporto di "BATCH_STARTED_GROUP" e "BATCH_COMPLETED_GROUP" nella [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] e in Istanza gestita in SSMS.
- GraphDB: è stato aggiunto un flag nello showplan per la sequenza Graph TC.
- Always Encrypted: è stato aggiunto il supporto di [Always Encrypted con enclave sicuri](../relational-databases/security/encryption/always-encrypted-enclaves.md).
  - La finestra di dialogo Connessione ha una nuova scheda "Always Encrypted" quando l'utente fa clic sul pulsante "Opzioni" per abilitare e configurare il supporto degli enclave.

Gli ID pacchetto non sono più necessari per sviluppare le estensioni di SQL Server Management Studio:

- SSMS caricava in modo selettivo solo i pacchetti noti e gli sviluppatori dovevano registrare i propri pacchetti. Questo non si verifica più.

Supporto di Azure SQL migliorato:

- Le proprietà del database SLO/Edition/MaxSize ora accettano nomi personalizzati, facilitando il supporto delle edizioni future del database SQL di Azure.
- Aggiunto il supporto per gli SKU vCore (uUtilizzo generico e business critical): Gen4_24 e tutti gli SKU Gen5.

SMO:

- Supporto SMO esteso per la creazione di indici ripristinabili.
- Aggiunto un nuovo evento per gli oggetti SMO ("PropertyMissing") che aiuta gli autori di applicazioni a rilevare i problemi di prestazioni SMO in tempi più rapidi.
- Aggiunta la nuova proprietà *DefaultBackupChecksum* sull'oggetto Configuration con mappatura sulla configurazione server "backup checksum default".

SSMS:

- Opzione di configurazione AUTOGROW_ALL_FILES disponibile per i filegroup in SSMS
- Rimosse le opzioni a rischio "lightweight pooling" e "priority boost" dalla GUI SSMS (https://blogs.msdn.microsoft.com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended).
- L'editor SQL supporta la combinazione di tasti **CTRL+D** per duplicare le righe (https://feedback.azure.com/forums/908035-sql-server/suggestions/32896594).
- Nuovo menu e sequenza di tasti per la creazione di file: **CTRL+ALT+N**. **CTRL+N** continua a funzionare per creare una nuova query.
- La finestra di dialogo **Nuova regola del firewall** ora consente di specificare un nome di regola anziché generarne uno automaticamente (https://feedback.azure.com/forums/908035-sql-server/suggestions/32902039).
- Classificazione dei dati: gli elementi consigliati sono stati aggiornati.
- Funzionalità IntelliSense migliorata nell'editor, in particolare per T-SQL v140.
- Supporto di tutte le lingue di livello 1.
- Aggiunta del supporto UTF-8 nella finestra di dialogo delle regole di confronto dell'interfaccia utente di SSMS.
- Passaggio a "Gestione credenziali di Windows" per le password MRU della finestra di dialogo Connessione. Risolve un problema esistente da tempo per cui la persistenza delle password non era sempre affidabile (https://feedback.azure.com/forums/908035-sql-server/suggestions/32896486).
- Il supporto dei valori DPI alti è abilitato per impostazione predefinita.
- Supporto migliorato per i sistemi con più monitor, con un numero crescente di finestre e più finestre di dialogo ora visualizzate sul monitor previsto.
- Viene visualizzata la configurazione server "backup checksum default" nella nuova pagina Impostazioni database della finestra di dialogo Proprietà server. (https://feedback.azure.com/forums/908035-sql-server/suggestions/34634974).


SSMS/ShowPlan:

- Aggiunti il tempo trascorso reale e le righe effettive rispetto alle righe stimate (se disponibili) sotto il nodo dell'operatore ShowPlan. Questa modifica fa sì che il piano effettivo sia coerente con il piano Statistiche query dinamiche.
- Modificata la descrizione comando e aggiunto un commento quando si fa clic sul pulsante Modifica query per un elemento ShowPlan, per indicare all'utente che l'elemento ShowPlan potrebbe essere troncato dal motore SQL se la query supera i 4000 caratteri.
- Aggiunto codice per visualizzare "Materializer Operator (External Select)".
- Aggiunto un nuovo attributo showplan BatchModeOnRowStoreUsed per identificare facilmente le query che usano la funzionalità "batch-mode scan on rowstores". Ogni volta che una query esegue "batch mode scan on rowstores" (analisi in modalità batch su rowstore) viene aggiunto un nuovo attributo (BatchModeOnRowStoreUsed="true") all'elemento StmtSimple.

Always On:

- Rigenerazione hash per RTO (Tempo di recupero stimato) e RPO (Perdita di dati stimata) nel dashboard SSMS Always On. Per informazioni dettagliate, vedere [Monitorare le prestazioni di Gruppi di disponibilità Always On](../database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups.md).

File di controllo:

- Metodo di autenticazione cambiato dal metodo basato sulla Chiave account di archiviazione all'autenticazione basata su Azure AD.

Always Encrypted:

- Aggiunta una scheda Always Encrypted con una casella di controllo *Abilita Always Encrypted* nella finestra di dialogo *Connetti al server* che offre un metodo facile per abilitare o disabilitare Always Encrypted per una connessione di database.
- Sono stati apportati diversi miglioramenti per il supporto di Always Encrypted con enclave sicuri:
  - Un campo di testo per specificare l'URL di attestazione dell'enclave nella finestra di dialogo Connetti al server (la nuova scheda Always Encrypted).
  - La nuova casella di controllo nella finestra di dialogo Nuova chiave master della colonna per controllare se una nuova chiave master della colonna consente i calcoli dell'enclave.
  - Altre finestre di dialogo di gestione delle chiavi Always Encrypted ora visualizzano informazioni su quali chiavi master della colonna consentono i calcoli dell'enclave.
  - Per informazioni dettagliate, vedere [Always Encrypted con enclave sicuri](../relational-databases/security/encryption/always-encrypted-enclaves.md).

        
### <a name="bug-fixes"></a>Correzioni di bug

Arresto anomalo/blocco:

- Correzione di un'origine di arresti anomali SSMS comuni associati agli oggetti GDI
- Correzione di un'origine comune di blocchi del sistema e prestazioni insufficienti quando si seleziona "Script come Crea/Aggiorna/Rilascia" (rimosse operazioni inutili di recupero di oggetti SMO)
- Correzione di un blocco durante la connessione a un database SQL di Azure con MFA mentre sono abilitate le tracce ADAL
- Correzione di un blocco (o un blocco percepito) in Statistiche query dinamiche chiamato da Monitor attività (il problema si manifesta quando si usa l'autenticazione di SQL Server senza nessuna impostazione "Mantieni informazioni di sicurezza").
- Risolto un blocco che si verificava quando si selezionava "Report" in Esplora oggetti e si rilevavano connessioni con latenza elevata o impossibilità temporanea di accesso alle risorse.

Finestra di dialogo della connessione:

- Abilitata la rimozione di nomi utente dall'elenco nomi utente precedenti premendo CANC (https://feedback.azure.com/forums/908035/suggestions/32897632).

XEvent:

- Aggiunte due colonne "action_name" e "class_type_desc" che visualizzano i campi ID azione e tipo classe come stringhe leggibili.
- Rimosso il limite massimo di 1.000.000 di eventi per il visualizzatore XEvent.

Tabelle esterne:

- Aggiunta del supporto per `Rejected_Row_Location` in modelli, SMO, IntelliSense e nella griglia delle proprietà.

Opzioni SSMS:

- Correzione di un problema per cui la pagina **Strumenti > Opzioni > Esplora oggetti di SQL Server > Comandi** non viene ridimensionata correttamente.


Editor SSMS:

- Risolto un problema in "Tabella di sistema SQL" per cui il ripristino dei colori predefiniti impostava il colore verde limone anziché il verde predefinito, rendendo difficile la lettura su uno sfondo bianco (https://feedback.azure.com/forums/908035-sql-server/suggestions/32896906).
- Correzione di un problema per cui IntelliSense non funziona quando si è connessi ad Azure SQL DW usando l'autenticazione AAD.
- Correzione di un problema di IntelliSense in Azure quando l'utente non dispone di credenziali per l'accesso master.
- Corretti frammenti di codice per la creazione di "tabelle temporanee" che venivano interrotti quando le regole di confronto del database di destinazione facevano distinzione tra maiuscole e minuscole.

Esplora oggetti:

- Correzione di un problema per cui SSMS genera un'eccezione, ad esempio perché non è possibile eseguire il cast dell'oggetto da DBNull ad altri tipi, quando si prova a espandere il nodo "Gestione" in Esplora oggetti (errore di configurazione di DataCollector)
- Correzione di un problema per cui CANC non funziona quando si rinomina un nodo (https://feedback.azure.com/forums/908035/suggestions/32910247 e altri duplicati).
- Correzione di un problema per cui Esplora oggetti non applica escape alle virgolette prima di chiamare "Modifica le prime n righe" e rende confusa la struttura
- Correzione di un problema per cui la procedura guidata "Importare un'applicazione livello dati" non viene avviata dalla struttura di Archiviazione di Azure.
- Correzione di un problema per cui in "Configurazione guidata Posta elettronica database" lo stato della casella di controllo SSL non viene mantenuto (https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541).
- Risolto un problema per cui in SSMS l'opzione Chiudi connessioni esistenti veniva disattivata quando si provava a ripristinare il database con is_auto_update_stats_async_on
- Risolto un problema per cui quando si faceva clic con il pulsante destro del mouse sui nodi in Esplora oggetti, ad esempio "Tabelle", e si voleva eseguire un'azione come ad esempio filtrare le tabelle selezionando **Filtro > Impostazioni filtro**, le impostazioni filtro potevano essere visualizzate in un altro schermo rispetto a quello in cui SSMS era attivo. (https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106).
- Correzione di un problema rilevato da tempo per cui CANC non funziona in Esplora oggetti quando si prova a rinominare un oggetto (https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510).
- Quando si visualizzano le proprietà di file di database esistenti, le dimensioni vengono visualizzate in una colonna "Dimensioni (MB)" anziché "Dimensioni iniziali (MB)", che è la colonna visualizzata quando si crea un nuovo database (https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024).
- Disattivazione dell'elemento del menu sensibile al contesto "Progettazione" in "Tabelle grafi" perché questo tipo di tabella non è supportato nella versione corrente di SSMS.

        
Visualizzatore della Guida:

- Miglioramento della logica associata al supporto delle modalità online/offline.
- Correzione di "Visualizza Guida" per rispettare le impostazioni online/offline (https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791).
    
Scripting per gli oggetti:

- Miglioramento delle prestazioni generali: la generazione di script WideWorldImporters viene eseguita in metà tempo rispetto a SSMS 17.7.
- Quando si aggiungono oggetti allo script, la configurazione con ambito database che include valori predefiniti viene omessa.
- Evitare di generare T-SQL dinamico durante lo scripting (https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391).
- Omettere le sintassi dei grafi "as edge" e "as node" per lo scripting di una tabella in SQL Server 2016 e versioni precedenti.


Progettazione tabelle:

- Correzione di un arresto anomalo in "Modifica 200 righe".
- Correzione di un problema per cui la finestra di progettazione consente l'aggiunta di una tabella durante la connessione a un database Azure SQL.

SMO:

- Correzione di un problema per cui SMO/ServerConnection non gestisce correttamente le connessioni basate su SqlCredential (https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941).

AS:

- Correzione di un problema per cui "Impostazioni avanzate" per l'interfaccia utente AS Xevent viene troncata

Procedura guidata Importa file flat:

- Correzione di un problema per cui la procedura guidata "Importa file flat" non gestisce correttamente le virgolette doppie (escape).
- Correzione di un problema di gestione errata dei tipi a virgola mobile (per impostazioni locali che usano un delimitatore diverso dal punto)
- Correzione di un problema associato all'importaizone di bit quando i valori sono 0 o 1 (https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535).
- Correzione di un problema per cui i valori float vengono immessi come null.
        
Classificazione dei dati:

- Correzione di un problema per cui la parte di raccomandazione della classificazione dei dati non funziona con una nuova installazione.

Backup/ripristino/collegamento/scollegamento del database:

- Correzione di un problema per cui l'utente non è in grado di associare un database quando il nome file fisico del file con estensione mdf non corrisponde al nome file originale.
- Risolto un problema per cui SSMS non trovava un piano di ripristino valido o ne trovava uno non ottimale (https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752).
- Correzione di un arresto anomalo di SSMS durante il tentativo di ripristinare un backup su URL.

Monitoraggio attività processi:

- Correzione di un arresto anomalo quando si usa Monitoraggio attività processi (con filtri).
        
Supporto di istanze gestite in SSMS:

- Miglioramento del supporto di istanze gestite: disabilitazione delle opzioni non supportate nell'interfaccia utente e risoluzione di un problema di Visualizza log di controllo per la gestione della destinazione di controllo URL.
- La procedura guidata "Genera e pubblica script" include clausole CREATE DATABASE non supportate.
- Statistiche sulle query dinamiche è stata disabilitata per le istanze di CL.
- Proprietà database -> File generava codice script errato per ALTER DB ADD FILE.
- Correzione della regressione con l'utilità di pianificazione di SQL Agent in cui la pianificazione ONIDLE veniva scelta anche quando era stato scelto un altro tipo di pianificazione.
- Regolazione di MAXTRANSFERRATE, MAXBLOCKSIZE per i backup in Archiviazione di Azure.
- Problema per cui il backup della parte finale del log viene aggiunto allo script prima dell'operazione RESTORE (operazione non supportata in CL).
- La procedura guidata Crea database non esegue correttamente lo scripting dell'istruzione CREATE DATABASE.
- Correzione di un problema per cui veniva visualizzato un errore quando si provava a usare "Monitor attività" durante la connessione a istanze gestite.


Database SQL di Azure:

- Correzione di un problema per cui l'elenco di database non veniva compilato correttamente per la finestra delle query di Azure SQL DB se la connessione veniva eseguita a un database utente in Azure SQL DB anziché a un database master.
- Correzione di un problema per cui non è possibile aggiungere "Tabella temporale" a un database SQL di Azure.


Supporto generico di Azure SQL:

- Correzione di problemi in un controllo comune dell'interfaccia utente di Azure UI che impedisce all'utente di visualizzare le sottoscrizioni di Azure (se il loro numero è maggiore di 50). Impostazione dell'ordinamento in base al nome anziché in base all'ID sottoscrizione. L'utente poteva trovare questa impostazione ad esempio quando provava a ripristinare un backup da un URL.
- Risolto un problema nel controllo interfaccia utente di Azure comune per cui l'enumerazione di sottoscrizioni poteva generare un errore "L'indice non è compreso nell'intervallo. Deve essere non negativo e inferiore al numero di colonne." quando l'utente non aveva sottoscrizioni in alcuni tenant. L'utente poteva trovare questa impostazione ad esempio quando provava a ripristinare un backup da un URL.

Griglia dei risultati:

- Correzione di un problema in modalità Contrasto elevato (i numeri di riga selezionati non erano visibili).

Profiler XEvent:

- Correzione di un problema per cui il profiler XEvent non veniva avviato se connesso a un server SQL Server a 96 nuclei.


### <a name="deprecated-features"></a>Caratteristiche deprecate

Le funzionalità seguenti non sono più disponibili in SSMS:

- Debugger Transact-SQL
- Diagrammi di database
- OSQL.EXE
- Interfaccia utente di amministrazione Dreplay
- Strumenti di Configuration Manager:
  - Gestione configurazione SQL Server e Gestione configurazione server di report non sono più inclusi nell'installazione di SSMS.

- Criteri standard DMF
  - I criteri non vengono più installati con SSMS. Vengono spostati in Git. Gli utenti possono contribuire a svilupparli e scaricarli/installarli in base alle esigenze.

- Opzione della riga di comando -P di SSMS rimossa
  - A causa di problemi di sicurezza, l'opzione per specificare password non crittografate nella riga di comando è stata rimossa.

- Genera script | Pubblica su servizio Web è stato rimosso. Questa funzionalità (deprecata) è stata rimossa dall'interfaccia utente di SSMS.

- Il nodo "Manutenzione | Legacy" di Esplora oggetto è stato rimosso. L'opzione Genera e pubblica script | Pubblica su servizio Web è stata rimossa. I nodi *obsoleti* "Piani di manutenzione del database" e "SQL Mail" non saranno più accessibili. I nodi recenti "Posta elettronica database" e "Piani di manutenzione" funzionano come di consueto.

### <a name="known-issues"></a>Problemi noti

Di seguito sono illustrati i problemi noti riscontrati nella versione corrente:

> [!IMPORTANT]
> Quando si usa l'autenticazione *Active Directory - Universale con supporto MFA* con l'editor di query SQL, è possibile che la connessione degli utenti venga chiusa e riaperta ogni volta che viene chiamata una query. Gli effetti collaterali di tale chiusura includono il rilascio imprevisto delle tabelle temporanee e talvolta l'assegnazione di un nuovo SPID alla connessione. Questa chiusura non si verifica se è presente una transazione aperta sulla connessione. Per risolvere questo problema, gli utenti possono impostare `persist security info=true` nei parametri di connessione.

SSMS

- Se si fa doppio clic su un file con estensione sql viene avviato SSMS, ma non viene aperto lo script.
  - Soluzione alternativa: trascinare e rilasciare il file con estensione sql nell'editor di SSMS.

SSIS

- Il pacchetto non può essere distribuito o eseguito correttamente quando è destinato a una versione meno recente di SQL Server e nel contempo include Attività script o il componente script.
- SSMS non può connettersi a Integration Services remoto.

## <a name="ssms-179-latest-ga-release"></a>SSMS 17.9 (release GA più recente)

![Scaricare](../ssdt/media/download.png) [SSMS 17.9](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)

Numero di build: 14.0.17285.0<br>
Data di rilascio: 04 settembre 2018

> [!NOTE]
> Le versioni di SSMS 17.x localizzate in lingue diverse dall'inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/kb/2862966).

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40a)


### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**


Showplan:

- Lo showplan grafico mostra ora i nuovi attributi per il feedback delle concessioni di memoria in modalità riga quando la funzionalità è attivata per un piano specifico: IsMemoryGrantFeedbackAdjusted e LastRequestedMemory, che vengono aggiunti all'elemento XML per i piani di query MemoryGrantInfo. Per altre informazioni sul feedback delle concessioni di memoria in modalità riga, vedere [Elaborazione di query adattive nei database SQL](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing).

Azure SQL: 

- Aggiunta del supporto per SKU vCore nella creazione di database di Azure. Per altre informazioni, vedere il [modello di acquisto basato su vCore](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers#vcore-based-purchasing-model).
 

### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale**
    
Monitoraggio replica:

- Risoluzione di un problema che impediva l'avvio di Monitoraggio replica (SqlMonitor.exe) (elemento User Voice: https://feedback.azure.com/forums/908035-sql-server/suggestions/34791079).

Procedura guidata Importa file flat:

- Correzione del collegamento alla pagina della Guida per la finestra di dialogo della procedura guidata "Importa file flat" 
- Risolto il problema a causa del quale la procedura guidata non consentiva la modifica della tabella di destinazione quando la tabella esisteva già: ciò consente agli utenti di ritentare l'operazione senza dover uscire dalla procedura guidata, eliminare la tabella in errore e quindi immettere nuovamente le informazioni nella procedura guidata (elemento User Voice: https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186).

Importa/Esporta l'applicazione livello dati:

- Correzione di un problema (in DacFx) a causa del quale l'importazione di un file bacpac potrebbe non riuscire con un messaggio di tipo "Errore SQL72014: provider dati di .NET SqlClient: Msg 9108, Livello 16, Stato 10, Riga 1 Questo tipo di statistiche non può essere incrementale. " quando si lavora con tabelle con partizioni definite e senza indici.

Intellisense:

- Correzione di un problema a causa del quale il completamento IntelliSense non funzionava quando si usava AAD con MFA.

Esplora oggetti:

- Correzione di un problema a causa del quale la "finestra di dialogo Filtro" veniva visualizzata in monitor casuali invece che nel monitor in cui era in esecuzione SSMS (sistemi con più monitor).

Azure SQL:

- Correzione di un problema correlato all'enumerazione dei database in "Database disponibili" a causa del quale il database "master" non veniva visualizzato nell'elenco a discesa in presenza di una connessione a un database specifico.
- Correzione di un problema a causa del quale il tentativo di generare uno script ("Dati" o "Schema e dati") non riusciva in caso di connessione al database SQL Azure con AAD e MFA.
- Correzione di un problema in Progettazione viste (Viste) a causa del quale non era possibile selezionare "Aggiungi tabelle" dall'interfaccia utente in presenza di una connessione a un database di SQL Azure.
- Correzione di un problema a causa del quale l'editor di query di SQL Server Management Studio chiudeva e riapriva automaticamente le connessioni durante il rinnovo del token MFA. Questa correzione consente di evitare effetti collaterali all'insaputa dell'utente, come la chiusura di una transazione senza che venga mai riaperta. La modifica aggiunge la scadenza del token nella finestra delle proprietà. 
- Correzione di un problema a causa del quale SQL Server Management Studio non applicava le richieste di password per gli account MSA importati per AAD con accesso MFA. 

Monitoraggio attività: 

- Correzione di un problema a causa del quale "Statistiche query dinamiche" si bloccava in caso di avvio da Monitoraggio attività con l'uso dell'autenticazione di SQL. 

Integrazione di Microsoft Azure: 

- Correzione di un problema a causa del quale SQL Server Management Studio mostra solo le prime 50 sottoscrizioni (finestre di dialogo Always Encrypted, finestre di dialogo per il backup/ripristino d URL e così via). 
- Risolto un problema a causa del quale SSMS generava un'eccezione ("L'indice non è compreso nell'intervallo") durante il tentativo di accedere a un account di Microsoft Azure senza account di archiviazione (nella finestra di dialogo per il ripristino del backup da URL). 

Scripting per gli oggetti: 

- Durante lo scripting "DROP e CREATE", SSMS ora evita la generazione di T-SQL dinamico.
- Durante lo scripting di un oggetto di database, SQL Server Management Studio ora non genera script per impostare le configurazioni con ambito database, se sono impostate sui valori predefiniti.

Help:

- Correzione di un problema esistente da tempo, a causa del quale per "Uso della Guida" non veniva rispettata la modalità online/offline.
- Quando si fa clic su "Guida | Progetti ed esempi della community" SQL Server Management Studio ora apre il browser predefinito che punta a una pagina Git e non visualizza errori/avvisi relativi all'uso di browser meno recenti.

### <a name="known-issues"></a>Problemi noti


> [!IMPORTANT]
> Quando si usa l'autenticazione *Active Directory - Universale con supporto MFA* con l'editor di query SQL, è possibile che la connessione degli utenti venga chiusa e riaperta ogni volta che viene chiamata una query. Gli effetti collaterali di tale chiusura includono il rilascio imprevisto delle tabelle temporanee e talvolta l'assegnazione di un nuovo SPID alla connessione. Questa chiusura non si verifica se è presente una transazione aperta sulla connessione. Per risolvere questo problema, gli utenti possono impostare `persist security info=true` nei parametri di connessione.




## <a name="previous-ssms-releases"></a>Versioni precedenti di SSMS

Scaricare le versioni precedenti di SSMS facendo clic sui collegamenti dei titoli nelle sezioni seguenti:

## <a name="downloadssdtmediadownloadpng-ssms-1781httpsgomicrosoftcomfwlinklinkid875802"></a>![download](../ssdt/media/download.png) [SSMS 17.8.1](https://go.microsoft.com/fwlink/?linkid=875802)
*È stato rilevato un bug nella versione 17.8 correlato al provisioning dei database SQL, quindi SSMS 17.8.1 sostituisce 17.8.*

Numero di build: 14.0.17277.0<br>
Data di rilascio: 26 giugno 2018

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40a)


### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

Proprietà database:

- Questo miglioramento espone l'opzione di configurazione **AUTOGROW_ALL_FILES** per i filegroup. Questa nuova opzione di configurazione viene aggiunta nella finestra Proprietà database > Filegroup sotto forma di nuova colonna (Aumento automatico di tutti i file) di caselle di controllo per ogni filegroup disponibile (tranne che per Filestream e i filegroup ottimizzati per la memoria). L'utente può abilitare/disabilitare AUTOGROW_ALL_FILES per un determinato filegroup attivando o disattivando la corrispondente casella di controllo Autogrow_All_Files. In maniera corrispondente, lo script dell'opzione **AUTOGROW_ALL_FILES** viene correttamente generato quando si genera lo script del database per creare/generare gli script per il database (SQL 2016 e versioni successive).
    
Editor SQL:

- Esperienza migliorata con IntelliSense nel database SQL di Azure quando l'utente non ha l'accesso master.

Scripting:

- Miglioramenti delle prestazioni generali, soprattutto nelle connessioni a latenza elevata.
    
**Analysis Services (AS)**

- Provider di dati e librerie client di Analysis Services aggiornati alla versione più recente, con aggiunta del supporto per la nuova autorità AAD di Azure per enti pubblici (login.microsoftonline.us).



### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale**
    
Piani di manutenzione:

- Risoluzione di un problema durante la modifica dei piani di manutenzione con autenticazione SQL a causa del quale "Attività Notifica operatori" genera errori quando si usa l'autenticazione SQL.
    
Scripting:

- Risoluzione di un problema a causa del quale le azioni PostProcess in SMO causano esaurimento delle risorse ed errori di accesso SQL
    
SMO:

- Risoluzione di un problema a causa del quale Table.Alter() ha esito negativo se si aggiungere una colonna con un vincolo predefinito e la tabella contiene già dati. Per informazioni dettagliate, vedere [sql server smo generating inline default constraint when adding a column to a table containing data](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895625) (SQL Server SMO: generazione di vincolo predefinito inline quando si aggiunge una colonna a una tabella contenente dati).
    
Always Encrypted:

- Risoluzione di un problema (in DacFx) che causava un errore di timeout di blocco quando si abilita Always Encrypted in una tabella partizionata
    

**Analysis Services (AS)**

- Risoluzione di un problema che verificava durante la modifica di un'origine dati OAuth in un modello tabulare con livello di compatibilità 1400 per Analysis Services, a causa del quale le modifiche nei token OAuth non venivano aggiornate nell'origine dati.
- Risoluzione di un arresto anomalo in SSMS che poteva verificarsi durante l'uso di alcune credenziali dell'origine dati non valide o la modifica di origini dati che non supportano la migrazione Modifica origine dati in Power Query (ad esempio, Oracle) nei modelli tabulari con livello di compatibilità 1400 di Analysis Services.


### <a name="known-issues"></a>Problemi noti

- Facendo clic sul pulsante *Script* dopo avere modificato una proprietà del filegroup nella finestra *Proprietà*, vengono generati due script: uno script con un'istruzione *USE <database>* e un secondo script con un'istruzione *USE master*.  Lo script con *USE master* viene generato per errore e deve essere rimosso. Eseguire lo script contenente l'istruzione *USE <database>*.
- Alcune finestre di dialogo visualizzano un errore di edizione non valida quando si lavora con nuove edizioni del database SQL di Azure *Utilizzo generico* oppure *Business Critical*.
- È possibile osservare latenza nel visualizzatore XEvents. Si tratta di un [problema noto in .NET Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net472/dotnet472-changes.md#sql). Considerare l'aggiornamento a NetFx 4.7.2.




## <a name="downloadssdtmediadownloadpng-ssms-177httpsgomicrosoftcomfwlinklinkid873126"></a>![download](../ssdt/media/download.png) [SSMS 17.7](https://go.microsoft.com/fwlink/?linkid=873126)

Numero di build: 14.0.17254.0<br>
Data di rilascio: 09 maggio 2018

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40a)


### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

Monitoraggio replica:   
- Monitoraggio replica supporta ora la registrazione di un listener per gli scenari in cui il database del server di pubblicazione e/o il database del server di distribuzione fa parte del gruppo di disponibilità. È ora possibile monitorare gli ambienti di replica in cui il database del server di pubblicazione e/o il database del server di distribuzione fa parte di Always On. 
 
Azure SQL Data Warehouse: 
- Aggiunto il supporto del percorso righe rifiutate per Tabelle esterne in Azure SQL Data Warehouse. 

**Integration Services (IS)**

- Aggiunta una funzionalità di pianificazione per i pacchetti SSIS distribuiti al database SQL di Azure. A differenza di SQL Server locale e di Istanza gestita di database SQL, che dispongono di SQL Server Agent come pianificatore di processi di prima classe, il database SQL non dispone di un pianificatore integrato. Questa nuova funzionalità SSMS offre un'interfaccia utente familiare e simile a SQL Server Agent per la pianificazione dei pacchetti distribuiti al database SQL. Se si usa il database SQL per ospitare il database del catalogo SSIS, SSIDB, è possibile usare questa funzionalità SSMS per generare le pipeline, le attività e i trigger Data Factory necessari per la pianificazione dei pacchetti SSIS. Quindi è possibile modificare ed estendere tali oggetti in Data Factory. Per altre informazioni, vedere [Schedule SSIS package execution on Azure SQL Database with SSMS](../integration-services/lift-shift/ssis-azure-schedule-packages-ssms.md) (Pianificare l'esecuzione del pacchetto SSIS nel database SQL di Azure con SSMS). Per altre informazioni sulla pipeline, le attività e i trigger di Azure Data Factory, vedere [Pipeline e attività in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities) e [Esecuzione e trigger di pipeline in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers).
- Supporto per la pianificazione dei pacchetti SSIS in SQL Agent nell'istanza gestita di SQL. È ora possibile creare processi di SQL Agent per eseguire pacchetti SSIS nell'istanza gestita. 

### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale** 

Piano di manutenzione:   
- Risolto un problema per cui durante il tentativo di modificare la pianificazione di un piano di manutenzione esistente veniva generata un'eccezione. Per informazioni dettagliate, vedere [SSMS 17.6 crashes when clicking on a schedule in a maintenance plan](https://feedback.azure.com/forums/908035-sql-server/suggestions/33712924) (Arresto anomalo di SSMS 17.6 se si seleziona una pianificazione in un piano di manutenzione).

Always On: 
- Risolto un problema per cui il dashboard della latenza di Always On latenza non funzionava con SQL Server 2012.
 
Scripting: 
- Risolto un problema per cui la creazione dello script per la stored procedure in Azure SQL Data Warehouse non funziona con utenti non amministratori.
- Risolto un problema per cui la creazione dello script per un database nel database SQL di Azure non creava lo script delle proprietà *SCOPED CONFIGURATION*.
 
Telemetria: 
- Risolto il problema per cui SSMS si arresta in modo anomalo nel tentativo di connettersi a un server, dopo il rifiuto esplicito dell'invio dei dati di telemetria.
 
Database SQL di Azure: 
- Risolto un problema per cui l'utente non poteva impostare o modificare il livello di compatibilità (menu a discesa vuoto). Nota: per impostare il livello di compatibilità su 150, l'utente deve comunque usare il pulsante *Script* e modificare manualmente lo script. 
 
SMO: 
- Esposta l'impostazione delle dimensioni del log degli errori in SMO. Per informazioni dettagliate, vedere [Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035-sql-server/suggestions/33624115) (Impostare le dimensioni massime dei log degli errori in SQL Server).  
- Corretta la creazione dello script per l'avanzamento riga in SMO in Linux.
- Vari miglioramenti delle prestazioni durante il recupero di proprietà usate raramente.  

Intellisense: 
- Miglioramento delle prestazioni: ridotto il volume delle query Intellisense per i dati di colonna. Questo miglioramento è particolarmente utile se si usano tabelle con un numero elevato di colonne. 

Impostazioni utente SSMS:
- Risolto un problema per cui la pagina delle opzioni non veniva ridimensionata correttamente.

Varie:  
- Migliorata la visualizzazione del testo nella pagina *Statistics details* (Dettagli statistiche). 

**Integration Services (IS)**

- Migliore supporto per Istanza gestita di database SQL di Azure.
- Risolto un problema per cui l'utente non poteva creare un catalogo per SQL Server 2014 o versione precedente.
- Sono stati risolti due problemi con i report:
   - Rimosso il nome del computer per i server di Azure.
   - Migliorata la gestione del nome di oggetto localizzato.


### <a name="known-issues"></a>Problemi noti

Alcune finestre di dialogo visualizzano un errore di edizione non valida quando si lavora con nuove edizioni del database SQL di Azure *Utilizzo generico* oppure *Business Critical*.

## <a name="downloadssdtmediadownloadpng-ssms-176httpsgomicrosoftcomfwlinklinkid870039"></a>![Download](../ssdt/media/download.png) [SSMS 17.6](https://go.microsoft.com/fwlink/?linkid=870039)

Numero di build: 14.0.17230.0<br>
Data di rilascio: 20 marzo 2018

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40a)

### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

Istanza gestita di database SQL di Azure:

- Aggiunto un supporto per [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Istanza gestita di database SQL di Azure offre una compatibilità prossima al 100% con SQL Server in locale, un'implementazione nativa della [rete virtuale (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) che risolve i problemi di sicurezza più comuni e un [modello di business](https://azure.microsoft.com/pricing/details/sql-database/) ideale per i clienti di SQL Server locale.
- Supporto per scenari di gestione comuni, ad esempio:
   - Creazione e modifica dei database.
   - Eseguire il backup e il ripristino di database.
   - Importazione, esportazione, estrazione e pubblicazione di applicazioni livello dati.
   - Visualizzazione e modifica delle proprietà server.
   - Supporto completo di Esplora oggetti.
   - Generazione di script per oggetti di database.
   - Supporto per i processi di SQL Agent.
   - Supporto per i server collegati.
- Altre informazioni sulle istanze gestite sono disponibili [qui](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/).

Esplora oggetti:
- Aggiunte impostazioni che consentono di non racchiudere i nomi tra parentesi quadre quando si trascinano e rilasciano elementi da Esplora oggetti alla finestra di query (suggerimenti utente [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) e [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051)).

Classificazione dei dati:
- Miglioramenti generali e correzioni di bug.

**Integration Services (IS)**

- Aggiunto il supporto per la distribuzione dei pacchetti a un'[istanza gestita del database SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).

### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale**

Classificazione dei dati:

- Risolto un problema di *classificazione dei dati che causava la visualizzazione delle classificazioni appena aggiunte con *Tipo di informazioni* ed *Etichetta di riservatezza* non aggiornati.
- Risolto un problema per cui la *classificazione dei dati* non funziona quando la destinazione è un server impostato su regole di confronto con distinzione tra maiuscole e minuscole.
        
Always On:

- Risolto un problema nel gruppo di disponibilità Mostra dashboard per cui fare clic su *Raccogli dati di latenza* può causare un errore se il server è impostato su regole di confronto con distinzione tra maiuscole e minuscole.
- Risolto un problema per cui SSMS segnala erroneamente un gruppo di disponibilità come *distribuito* quando si arresta il Servizio cluster.
- Risolto un problema per cui durante la creazione di gruppi di disponibilità nella finestra di dialogo *Crea gruppo di disponibilità* *ReadOnlyRoutingUrl* è obbligatorio.
- Risolto un problema per cui se il database primario non era attivo e si eseguiva il failover manuale al database secondario, veniva generata un'eccezione NullReferenceException.
- Risolto un problema per cui durante la creazione di un gruppo di disponibilità usando il backup o il ripristino per inizializzare un database, nelle repliche secondarie i file di database venivano creati nella directory predefinita. La correzione include:
   - Aggiungere la convalida della directory di dati o di log.
   - Effettuare la rilocazione di file solo quando la replica si trova in un sistema operativo diverso da quello della replica primaria.
- Risolto un problema per cui la procedura guidata di SSMS non genera l'opzione *CLUSTER_TYPE*, causando l'esito negativo del join secondario.

Installazione:
- Risolto il problema per cui non è possibile aggiornare SSMS installando il "pacchetto di aggiornamento" se SSMS è installato in un percorso non predefinito.

SMO:
- Risolto un problema di prestazioni per cui lo scripting di tabelle in SQL Server 2016 e versioni successive può richiedere fino a 30 secondi (il tempo si è ridotto a meno di 1 secondo).

Esplora oggetti:
- Risolto un problema per cui SSMS può generare un'eccezione, ad esempio perché non è possibile eseguire il cast dell'oggetto da DBNull ad altri tipi, quando si tenta di espandere il nodo *Gestione* in Esplora oggetti.
- Risolto un problema in cui *Avvia PowerShell* non rileva il modulo SQLServer quando il profilo PS definito dall'utente genera output.
- Corretto un blocco intermittente che potrebbe verificarsi quando si fa clic con il pulsante destro del mouse su un nodo Tabella o Indice in Esplora oggetti.

Posta elettronica database:
- Risolto un problema per cui la *configurazione guidata della posta elettronica del database* genera un'eccezione quando si tenta di visualizzare o gestire più di 16 profili.


**Analysis Services (AS)**

- Risolto come problema in cui le modifiche apportate a un'origine dati per un modello con livello di compatibilità 1400 in SSMS non vengono salvate nel server.

**Integration Services (IS)**

- Risolto un problema per cui SSMS non visualizza il nodo del catalogo SSIS e i report quando si è connessi all'istanza gestita di database SQL

### <a name="known-issues"></a>Problemi noti

> [!WARNING]
> Si verifica il problema noto in cui SSMS 17.6 diventa instabile e si blocca quando si usano [piani di manutenzione](../relational-databases/maintenance-plans/maintenance-plans.md). Se si usano piani di manutenzione, non installare SSMS 17.6. Effettuare il downgrade a SSMS 17.5 se è già installata la versione 17.6 e si è riscontrato questo problema. 



## <a name="downloadssdtmediadownloadpng-ssms-175httpsgomicrosoftcomfwlinklinkid867670"></a>![Download](../ssdt/media/download.png) [SSMS 17.5](https://go.microsoft.com/fwlink/?linkid=867670)
Disponibile per il pubblico | Numero di build: 14.0.17224.0

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40a)

### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

Individuazione dati e classificazione:

- È stata aggiunta una nuova funzionalità SQL di individuazione e classificazione dei dati per l'individuazione, la classificazione, l'assegnazione di etichette e la creazione di report per i dati sensibili presenti nei database. 
- L'individuazione automatica e la classificazione dei dati più sensibili, come ad esempio i dati aziendali, finanziari, medici, personali e così via, possono avere un ruolo fondamentale nella protezione delle informazioni dell'organizzazione.
- Altre informazioni sono disponibili in [Individuazione dati e classificazione SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

Editor query:

- È stato aggiunto il supporto dell'opzione SkipRows al formato di file esterno di testo delimitato per Azure SQL DW. Questa funzionalità consente agli utenti di ignorare un numero di righe specificato durante il caricamento di file di testo delimitato in SQL DW. È stato aggiunto anche il supporto di intellisense/SMO corrispondente per la parola chiave FIRST_ROW. 

Showplan:

- È stata abilitata la visualizzazione del pulsante del piano stimato per SQL Data Warehouse
- È stato aggiunto il nuovo attributo showplan *EstimateRowsWithoutRowGoal* e i nuovi attributi showplan a *QueryTimeStats*: *UdfCpuTime* e *UdfElapsedTime*. Per altre informazioni, vedere [Optimizer row goal information in query execution plan added in SQL Server 2017 CU3](https://support.microsoft.com/help/4051361) (Informazioni sull'obiettivo di righe di Query Optimizer nel piano di esecuzione query aggiunto in SQL Server 2017 CU3).



### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale**

Showplan:

- È stato risolto il problema del tempo trascorso di Statistiche query dinamiche in modo che visualizzi il tempo di esecuzione del motore invece del tempo trascorso per la connessione di Statistiche query dinamiche.
- È stato risolto un problema per cui showplan non riusciva a riconoscere gli operatori logici Apply come GbApply e InnerApply.
- È stato risolto un problema correlato a ExchangeSpill.

Editor query:

- È stato risolto un problema correlato agli SPID per cui SSMS poteva generare un errore simile a "Il formato della stringa di input non è corretto. (mscorlib) " all'esecuzione di una query semplice preceduta da"SET SHOWPLAN_ALL ON". 


SMO:

- È stato risolto un problema in cui SMO non riusciva a recuperare le proprietà AvailabilityReplica nel caso in cui le regole di confronto del server distinguessero tra maiuscole/minuscole. Di conseguenza, in SSMS veniva visualizzato un messaggio di errore simile a "Impossibile associare l'identificatore in più parti "a.delimited"."
- Risolto un problema nella classe DatabaseScopedConfigurationCollection, dovuto alla gestione errata delle regole di confronto. In conseguenza di tale problema, SSMS in esecuzione in un computer MA con impostazioni locali in turco visualizzava l'errore "legacy cardinality estimation is not valid scoped configuration"(la stima di cardinalità legacy non è valida nell'ambito di configurazione) quando si faceva clic con il pulsante destro del mouse su un database in esecuzione in un server con regole di confronto con distinzione tra maiuscole e minuscole.
- È stato risolto un problema nella classe JobServer, per cui SMO non riusciva a recuperare le proprietà di SQL Agent in un server SQL 2005. Di conseguenza, SSMS generava un errore "Impossibile assegnare un valore predefinito a una variabile locale. Dichiarare la variabile scalare "\@ServiceStartMode" e infine il nodo SQL Agent in Esplora oggetti non veniva visualizzato.

Modelli: 

- "Posta elettronica database": corretti un paio di errori di digitazione [ (https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512).  

Esplora oggetti:
- Risolto un problema per cui la compressione gestita non riesce per gli indici (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o).

Controllo:
- È stato risolto un problema con la funzionalità *Unisci file di controllo*.
<br>

### <a name="known-issues"></a>Problemi noti

Classificazione dei dati:
- Se si rimuove una classificazione e si aggiunge manualmente una nuova classificazione per la stessa colonna, il tipo di informazioni e l'etichetta di riservatezza precedenti vengono assegnati alla colonna nella visualizzazione principale.<br>
*Soluzione alternativa*: assegnare il nuovo tipo di informazioni e la nuova etichetta di riservatezza dopo che la classificazione è stata aggiunta nuovamente alla visualizzazione principale e prima di salvare.


## <a name="downloadssdtmediadownloadpng-ssms-174httpsgomicrosoftcomfwlinklinkid864329"></a>![download](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
Disponibile a livello generale | Numero di build: 14.0.17213.0

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### <a name="whats-new"></a>Novità

**SQL Server Management Studio (SSMS) - Generale**

Valutazione della vulnerabilità:
- Aggiunta di un nuovo servizio di valutazione della vulnerabilità SQL per l'analisi dei database per rilevare eventuali vulnerabilità e deviazioni dalle procedure consigliate, ad esempio configurazioni errate, autorizzazioni eccessive ed esposizione di dati sensibili. 
- I risultati della valutazione includono le azioni applicabili per risolvere ogni problema, oltre a script di correzione personalizzati, ove applicabile. I report di valutazione possono essere personalizzati per ogni ambiente e adattati a specifici requisiti. Per altre informazioni, vedere [Valutazione della vulnerabilità SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Risolto il problema per cui *HasMemoryOptimizedObjects generava un'eccezione in Azure.
- Aggiunta del supporto per la funzionalità CATALOG_COLLATION.

Dashboard Always On:
- Miglioramenti dell'analisi della latenza nei gruppi di disponibilità.
- Aggiunta di due nuovi report: *AlwaysOn\_Latency\_Primary* e *AlwaysOn\_Latency\_Secondary*.

Showplan:
- Aggiornamento dei collegamenti che ora puntano alla documentazione corretta.
- Possibilità di eseguire l'analisi di un singolo piano direttamente dal piano effettivo generato.
- Nuovo set di icone.
- Aggiunta del supporto per riconoscere l'applicazione di operatori logici, ad esempio GbApply e InnerApply.
        
Profiler XE:
- Rinominato in Profiler XEvent.
- I comandi di menu Arresta/Avvia ora arrestano/avviano la sessione per impostazione predefinita.
- Abilitazione dei tasti di scelta rapida (ad esempio, CTRL+F per la ricerca).
- Aggiunta delle azioni database\_name e client\_hostname agli eventi appropriati nelle sessioni di Profiler XEvent. Per applicare la modifica, potrebbe essere necessario eliminare le istanze della sessione QuickSessionStandard o QuickSessionTSQL sui server - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

Riga di comando:
- Aggiunta una nuova opzione della riga di comando ("-G") che può essere usata per la connessione automatica di SSMS a un server/database usando l'autenticazione di Active Directory (integrata o della password). Per altre informazioni, vedere [Utilità Ssms](ssms-utility.md).

Procedura guidata Importa file flat:
- Possibilità di selezionare un nome di schema diverso da quello predefinito ("dbo") quando si crea la tabella.

Query Store:
- Ripristino del report "Query regredite" quando si espande l'elenco di report disponibili di Query Store.

**Integration Services (IS)**
- Aggiunta della funzione di convalida dei pacchetti in Distribuzione guidata, che consente all'utente di determinare i componenti nei pacchetti SSIS non supportati nel runtime di integrazione SSIS di Azure.

### <a name="bug-fixes"></a>Correzioni di bug

**SQL Server Management Studio (SSMS) - Generale**

- Esplora oggetti: risolto un problema per cui il nodo Funzione con valori di tabella non viene visualizzato per gli snapshot del database - [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161).
Miglioramento delle prestazioni quando si espande il nodo *Database* quando il server ha database a chiusura automatica.
- Editor di query: risoluzione di un problema per cui IntelliSense ha esito negativo per gli utenti che non hanno accesso al database master.
Risoluzione di un problema che in alcuni casi causa l'arresto anomalo di SSMS quando la connessione a un computer remoto viene chiusa - [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557).
- Visualizzatore XEvent: riabilitazione della funzionalità di esportazione in XEL.
Risoluzione dei problemi per cui in alcuni casi l'utente non riesce a caricare un intero file XEL.
- Profiler XEvent: risoluzione di un problema che causa l'arresto anomalo di SSMS quando l'utente non ha autorizzazioni *VISUALIZZAZIONE STATO DEL SERVER*.
Risoluzione di un problema per cui la chiusura della finestra dei dati dinamici di Profiler XE non arresta la sessione sottostante.
- Server registrati: risoluzione di un problema a causa del quale il comando "Sposta in" smetteva di funzionare - [Connect 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) e [Connect 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/).
- SMO: risoluzione di un problema per cui il metodo TransferData sull'oggetto Transfer non funziona.
Risoluzione di un problema per cui i database del server generano un'eccezione per i database di SQL DW in pausa.
Risoluzione di un problema per cui lo script del database SQL in SQL DW genera valori di parametri T-SQL non corretti.
Risoluzione di un problema per cui lo script di un database con estensione crea erroneamente l'opzione *DATA\_COMPRESSION*.
- Monitoraggio attività processi: risoluzione di un problema per cui l'utente visualizza l'errore "L'indice non è compreso nell'intervallo. Richiesto valore non negativo e minore della dimensione della raccolta. 
      Nome parametro: index (System.Windows.Forms)" quando prova ad applicare il filtro per categoria - [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691).
- Finestra di dialogo Connessione: risolto un problema per cui gli utenti di un dominio senza accesso a un controller di dominio in lettura/scrittura non potevano accedere a un'istanza di SQL Server usando l'autenticazione SQL - [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381).
- Replica: risoluzione di un problema per cui viene visualizzato un errore simile a "Non è possibile applicare il valore 'null' alla proprietà ServerInstance" quando si esaminano le proprietà di una sottoscrizione pull in SQL Server.
- Installazione di SSMS: risoluzione di un problema per cui l'installazione di SSMS causa erroneamente la riconfigurazione di tutti i prodotti installati nel computer.
- Impostazioni utente:
   - Con questa correzione, gli utenti del cloud sovrano US Government avranno accesso senza interruzione alle risorse del database SQL di Azure e di Azure Resource Manager con SSMS tramite l'autenticazione universale e l'accesso ad Azure Active Directory.  Gli utenti delle versioni precedenti di SSMS devono aprire Strumenti|Opzioni|Servizi di Azure e in Gestione risorse impostare la configurazione della proprietà "Autorità di Active Directory" su https://login.microsoftonline.us.

**Analysis Services (AS)**

- Profiler: risoluzione di un problema quando si prova a connettersi usando l'autenticazione di Windows in Azure AS.
- Risoluzione di un problema che può causare un arresto anomalo del sistema quando si annullano i dettagli della connessione in un modello 1400.
- Quando si imposta una chiave BLOB di Azure nella finestra di dialogo Proprietà connessione quando si aggiornano le credenziali, ora risulta mascherata.
- Risoluzione di un problema per cui nella finestra di dialogo Selezione utenti di Azure Analysis Services viene visualizzato il GUID ID applicazione invece dell'ID oggetto durante una ricerca.
- Risoluzione di un problema della barra degli strumenti Progettazione query MDX/Browse Database (Esplora database) che causa il mapping non corretto delle icone per alcuni pulsanti.
- Risoluzione di un problema che impedisce la connessione a SSAS tramite indirizzi http/https di IIS di tipo msmdpump.
- Diverse stringhe nella finestra di dialogo Selezione utenti di Azure Analysis Services sono state convertite per altri linguaggi.
- La proprietà MaxConnections è ora visibile per le origini dati nei modelli tabulari.
- La Distribuzione guidata genera ora le definizioni JSON corrette per i membri del ruolo di Azure AS.
- Risoluzione di un problema in SQL Profiler per cui, selezionando l'autenticazione di Windows in Azure AS, viene ancora richiesto l'accesso.



## <a name="downloadssdtmediadownloadpng-ssms-173httpsgomicrosoftcomfwlinklinkid858904"></a>![download](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
Disponibile a livello generale | Numero di build: 14.0.17199.0

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


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
- Always On: è stato risolto un problema per cui il backup del ripristino dei log restituiva l'errore "The sign in this backup set terminates at LSN x, which is too early to apply to the database" (L'ultimo LSN del log in questo set di backup è LSN x, che corrisponde a un punto troppo indietro nel tempo per l'applicazione al database).
- Monitor attività processi: sono state risolte incoerenze tra le icone - [Argomento Connect 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100).
- Query Store: è stato risolto un problema per il quale l'utente non poteva scegliere l'intervallo di date personalizzato per i report di Query Store. Collegato ai seguenti argomenti Connect.
   - [Argomento Connect 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Argomento Connect 3139399](https://connect.microsoft.com/SQLServer/feedback/details/3139399)
- È stato risolto un problema per il quale la finestra di dialogo di connessione non cancellava l'ultimo database usato quando le informazioni salvate includevano un database con nome e l'utente selezionava <default>.
- Scripting per gli oggetti: risolto un problema in cui "Generazione script del database" non funzionava e restituiva un errore quando l'utente aveva un database Data Warehouse in pausa nel server, ma aveva selezionato un altro database non DW e stava provando a eseguire uno script.
È stato risolto un problema per cui l'intestazione delle stored procedure con script non corrispondeva alle impostazioni di script, restituendo uno script fuorviante - [Argomento Connect 3139784](https://connect.microsoft.com/SQLServer/feedback/details/3139784).
È stato riabilitato il pulsante "Script" per gli oggetti SQL Azure.
  È stato risolto un problema per cui SSMS non consentiva lo scripting per "Modifica" o "Esegui" su determinati oggetti (UDF, View, SP, Trigger) se connesso a un database SQL di Azure - [Argomento Connect 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386).
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
   - È stata abilitata una query multiserver per i server agente utente che usa lo stesso token per tutti i server agente utente del gruppo.
- Autenticazione universale AD:
   - È stato risolto un problema per cui l'autenticazione Azure Active Directory non era supportata.
   - È stato risolto un problema per cui la finestra di progettazione tabella/vista non funzionava.
   - È stato risolto un problema per cui "Select Top 1000 rows" (Seleziona le prime 1000 righe) e "Edit Top 200 rows" (Modifica le prime 200 righe) non funzionavano.
- Ripristino del database: è stato risolto un problema per cui il ripristino ometteva l'ultima cartella del percorso durante lo spostamento di file in un percorso alternativo.
- Compressione guidata:
   - È stato risolto un problema con la gestione della compressione guidata per gli indici; è stato risolto un problema per il quale la compressione guidata dati non funzionava per SQL 2016 e versioni precedenti.
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
   - La procedura Ottimizzazione guidata motore di database non è supportata per l'autenticazione di Azure AD: esiste un problema noto a causa del quale il messaggio di errore visualizzato all'utente è poco chiaro: "Impossibile caricare il file o l'assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…", invece del previsto "Ottimizzazione guidata motore di database non supporta database SQL di Microsoft Azure." (DTAClient)".
- Il tentativo di analizzare una query in DTA restituisce un errore: "L'oggetto deve implementare IConvertible. (mscorlib)".
- *Query regredite* non è disponibile nell'elenco di report Query Store in Esplora oggetti.
   - Soluzione alternativa: fare clic con il pulsante destro del mouse sul nodo **Query Store** e selezionare **View Regressed Queries** (Visualizza le query regredite).

**Integration Services (IS)**

- [execution_path] in [catalog].[event_messagea] non è corretto per le esecuzioni dei pacchetti in Scale Out. [execution_path] inizia con "\Package" anziché con il nome oggetto dell'eseguibile del pacchetto. Quando si visualizza il report panoramica delle esecuzioni dei pacchetti in SSMS, il collegamento "Percorso di esecuzione" in Panoramica sulle esecuzioni non funziona. La soluzione alternativa consiste nel fare clic su "Visualizzazione messaggi" nel report panoramica per controllare tutti i messaggi di evento.


## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![download](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
Disponibile a livello generale | Numero di build: 14.0.17177.0

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

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
- È stata aggiunta anche una nuova interfaccia della riga di comando che supporta l'impostazione di amministrazione di Azure AD per il database SQL e SQL Data Warehouse.

 Per altre informazioni sui metodi di autenticazione di Active Directory, vedere [Autenticazione universale con database SQL e SQL Data Warehouse (supporto SSMS per MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) e [Configurare Multi-Factor Authentication per SQL Server Management Studio e Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La finestra di output include voci per le query eseguite durante l'espansione dei nodi di Esplora oggetti.
- Progettazione viste abilitato per i database SQL di Azure.
- Sono state modificate le opzioni di scripting predefinite per l'inserimento di oggetti nello script da Esplora oggetti in SSMS:
  - Per impostazione predefinita, in precedenza lo script generato in una nuova installazione era destinato all'ultima versione di SQL Server, attualmente SQL Server 2017.
  - In SSMS 17.2 è stata aggiunta una nuova opzione: *Corrispondenza delle impostazioni dello script con l'origine*. Se impostata su *True*, lo script generato è destinato alla stessa versione e allo stesso tipo ed edizione del motore del server da cui viene eseguito l'inserimento dell'oggetto nello script.
  - Per l'opzione *Corrispondenza delle impostazioni dello script con l'origine*, *True* è l'impostazione predefinita. Le nuove installazioni di SSMS, quindi, eseguono sempre lo scripting di oggetti nella stessa destinazione del server originale.
  - Quando il valore dell'opzione *Corrispondenza delle impostazioni dello script con l'origine* è impostato su *False*, vengono abilitate le normali opzioni di destinazione di scripting e ripristinato il funzionamento precedente.
Tutte le opzioni di scripting sono state spostate nella relativa sezione, *Opzioni versione*, e non si trovano più in *Opzioni generali di scripting*.

- Aggiunto il supporto per i cloud nazionali nel ripristino dall'URL.
- I report QueryStoreUI ora supportano metriche aggiuntive, come RowCount, DOP, CLR Time e così via, da sys.query_store_runtime_stats.
- IntelliSense è ora supportato per il database SQL di Azure https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
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
- Risolto un problema per cui in alcuni casi SSMS genera un errore "Riferimento oggetto non impostato su un'istanza di un oggetto" all'avvio. https://connect.microsoft.com/SQLServer/feedback/details/3134698
- Risolto un problema in "Compressione guidata dati" che provocava l'arresto anomalo di SSMS quando si premeva "Calcola" nella Tabella grafici.
- Risolto un problema di prestazioni generato facendo clic sull'indice di una tabella con una connessione a Internet lenta. https://connect.microsoft.com/SQLServer/feedback/details/3120783
- Risolto un problema per cui SSMS non riusciva a enumerare i file di backup nei server con regole di confronto con distinzione tra maiuscole e minuscole. https://connect.microsoft.com/SQLServer/feedback/details/3134787 e https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Correzioni varie relative a showplan e al confronto showplan.
- Risolto un problema per cui la finestra di dialogo di connessione non consentiva all'utente di specificare il protocollo di rete da usare per la connessione, a meno che SQL Server non fosse installato nel computer con SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3134997
- Migliorato il supporto per le configurazioni a più monitor in cui alcune finestre di dialogo di SSMS venivano visualizzate in posizioni "casuali". Aggiunta una nuova opzione "Finestre di dialogo attività" in "Esplora oggetti di SQL Server | Comandi" per consentire di ricordare la posizione di una finestra di dialogo attività o di una finestra delle proprietà quando questa si chiude. https://connect.microsoft.com/SQLServer/feedback/details/889169, https://connect.microsoft.com/SQLServer/feedback/details/1158271, https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- Risolto un problema per cui SSMS non riusciva a modificare le proprietà di database per i database SQL di Azure crittografati.
- Migliorata l'opzione "Elimina risultati dopo l'esecuzione". https://connect.microsoft.com/SQLServer/feedback/details/1196581
- Migliorato/risolto un problema per cui gli utenti non possono accedere alle sottoscrizioni di Azure di cui non sono amministratori.
- Migliorata la procedura guidata "Ripristino database" per mantenere il database di destinazione selezionato in OE indipendentemente dalla selezione del database di origine. https://connect.microsoft.com/SQLServer/feedback/details/3118581
- Risolto un problema per cui Esplora oggetti non ordinava correttamente le "stored procedure compilate in modo nativo" appena aggiunte. https://connect.microsoft.com/SQLServer/feedback/details/3133365
- Risolto un problema per cui "Seleziona le prime n righe" non includeva la clausola "prime" per Azure SQLDW. https://connect.microsoft.com/SQLServer/feedback/details/3133551 e https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI: risolto un problema per cui gli intervalli di tempo non personalizzati non funzionavano correttamente per tutti i report.
- Always Encrypted: Miglioramento della messaggistica per lo stato autorizzazione AKV nella finestra di dialogo New CMK (Nuovo CMK). Aggiunta di descrizioni comando all'elenco a discesa CEK per facilitare la distinzione di CEK con nomi lunghi. Correzione di un problema per cui i provider degli archivi delle chiavi CNG non venivano visualizzati nella finestra di dialogo Nuova chiave master della colonna per Always Encrypted
- Corretto il "Nome applicazione" non coerente per le connessioni di SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3135115
- Risolto un problema per cui SSMS non generava script corretti per SQL Azure (tabelle e indici con l'opzione DATA_COMPRESSIONS). https://connect.microsoft.com/SQLServer/feedback/details/3133148
- Risolto un problema per cui l'utente non poteva usare i tasti di scelta rapida CTRL+Q per l'Avvio veloce. Nota: i nuovi tasti di scelta rapida per attivare o disattivare l'opzione "IntelliSense abilitato" nell'Editor di Query sono CTRL+B e CTRL+I. https://connect.microsoft.com/SQLServer/feedback/details/3131968
- Risolto un problema in "Ripristina database" per cui SSMS generava un'eccezione durante il tentativo di selezionare un account di archiviazione da una sottoscrizione che include account con domini personalizzati definiti.
- Risolto un problema in "Diagramma di database" per cui SSMS generava un errore "Indice oltre i limiti della matrice" e l'utente non poteva impostare la "Vista tabella" su un'opzione diversa da quella standard. https://connect.microsoft.com/SQLServer/feedback/details/3133792 e https://connect.microsoft.com/SQLServer/feedback/details/3135326
- Risolto un problema in "Backup/Ripristino su URL" per cui SSMS non riusciva a enumerare gli account di archiviazione della versione classica.
- Risolto un problema per cui veniva generata un'eccezione durante il tentativo di aggiungere entità a protezione diretta associate allo schema ai ruoli di database. https://connect.microsoft.com/SQLServer/feedback/details/3118143
- Risolto un problema per cui SSMS restituiva saltuariamente il messaggio di errore "I dati hanno valore Null. Impossibile chiamare il metodo o la proprietà su valori Null" quando si espande un nodo di tabella https://connect.microsoft.com/SQLServer/feedback/details/3136283
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

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

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

## <a name="downloadssdtmediadownloadpng-ssms-170httpsgomicrosoftcomfwlinklinkid847722"></a>![Download](../ssdt/media/download.png) [SSMS 17.0](https://go.microsoft.com/fwlink/?LinkID=847722)
Disponibile a livello generale | Numero di build: 14.0.17099.0

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40a)

### <a name="enhancements"></a>Miglioramenti 

- Il pacchetto di aggiornamento e le versioni Windows Software Update Services (WSUS) 17.X future includono un pacchetto di aggiornamento cumulativo più piccolo 
  - Il pacchetto di aggiornamento verrà pubblicato anche nel catalogo WSUS  
- Aggiornamento icone: Icone aggiornate per la coerenza con le icone fornite dalla shell VS e il supporto di risoluzioni DPI elevate. Nuove icone dei programmi SSMS e Profiler per differenziare tra le versioni 16.X e 17.X
- Modulo SQL PowerShell
  - Modulo SQL Server PowerShell rimosso da SSMS e attualmente incluso mediante la raccolta di PowerShell (per PowerShell 5.0 è richiesto il supporto delle versioni del modulo)
  - Sono stati introdotti miglioramenti di vario tipo alla "presentazione" (formattazione) di alcuni oggetti SMO (ad esempio per i database vengono ora indicati le dimensioni e lo spazio disponibile e per le tabelle il numero di righe e lo spazio occupato)
  - È stata aggiunta la colorazione quando viene richiamato il prompt dei comandi di PowerShell dal menu "Avvia PowerShell" in OE
  - Sono stati aggiunti i parametri -ClusterType e -RequiredCopiesToCommit ai cmdlet di Gruppi di disponibilità (cmdlet New-SqlAvailabilityGroup, Join-SqlAvailabilityGroup e Set-SqlAvailabilityGroup)
  - Sono stati aggiunti i parametri -ActiveDirectoryAuthority e -AzureKeyVaultResourceId al cmdlet Add-SqlAzureAuthenticationContext
  - Sono stati aggiunti   Revoke-SqlAvailabilityGroupCreateAnyDatabase, Grant-SqlAvailabilityGroupCreateAnyDatabase e Set-SqlAvailabilityReplicaRoleToSecondary cmdlets
  - È stato aggiunto il parametro -SeedingMode a Set-SqlAvailabilityReplica e New-SqlAvailabilityReplica cmdlets
  - È stato aggiunto il parametro - ConnectionString a Get-SqlDatabase
- Miglioramenti generali e correzioni per il log shipping di SQL Server in Linux
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
- Showplan: Viene visualizzato il valore max anziché il valore somma nella finestra proprietà per il tempo trascorso. Vengono visualizzate le proprietà del nuovo operatore di concessione memoria. È attivato il pulsante "Modifica query" in Statistiche query dinamiche. È supportata l'esecuzione interleaved
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
  - Aggiunto il supporto per nuovi tipi di cluster: EXTERNAL e NONE. Aggiunto il supporto di SQL Server su Linux. Aggiunto il seeding automatico come opzione per la sincronizzazione dei dati iniziale. Correzione di alcuni bug, ad esempio nella gestione degli URL di endpoint, nell'aggiornamento del database e nel layout dell'interfaccia utente. Rimozione delle funzionalità associate alla replica di Azure
  - Migliorato IntelliSense per diverse parole chiave del gruppo di disponibilità
- Monitoraggio attività
  - Aggiunto il nuovo riquadro "Monitoraggio attività" alla finestra di output di SSMS
  - Modificato errore di connessione/messaggio di timeout per registrare informazioni nella finestra di output anziché in un messaggio popup
  - Rimosso grafico vuoto (quinto grafico) nella sezione Panoramica
  - Aggiunto "(in pausa)" al titolo della Panoramica se la raccolta di dati Monitoraggio attività viene messa in pausa
  - Estensioni grafiche per SQL Server: Nuove icone per il nodo grafico e le tabelle bordi. Il nodo grafico e le tabelle edge verranno visualizzate nella cartella Tabelle grafi. Modelli disponibili per creare il nodo grafico e le tabelle bordi.
- Modalità presentazione: Tre nuove attività disponibili tramite Avvio veloce (CTRL+Q) PresentOn: attiva la modalità presentazione PresentEdit: modifica la dimensione del tipo di carattere per la modalità presentazione.  "Tipo di carattere Editor di testo" per Editor di query.  "Tipo di carattere ambiente" per altri componenti.
RestoreDefaultFonts: ripristina le impostazioni predefinite.
*Nota: non è attualmente disponibile un comando PresentOff.  Per disattivare la modalità presentazione è possibile usare l'opzione RestoreDefaultFonts*

### <a name="bug-fixes"></a>Correzioni di bug

- È stato risolto un problema per il quale SSMS si arrestava in modo anomalo quando si eseguiva lo scorrimento sullo showplan nel touchpad
- È stato risolto un problema a causa del quale SSMS rimane in sospensione per lungo tempo mentre ottiene le proprietà di un database in corso di ripristino o offline 
- È stato risolto un problema a causa del quale non è stato possibile aprire "Help viewer" nei build RC
- È stato risolto un problema a causa del quale in SSMS potrebbero mancare gli elementi della "Casella degli strumenti delle attività dei piani di manutenzione".
- È stato risolto un problema in SSMS a causa del quale l'utente non era in grado di comprimere un database quando il nome del database conteneva parentesi graffe. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- È stato risolto un problema a causa del quale SSMS cercava di eseguire lo script di eliminazione di un database di Azure; in realtà provocava l'eliminazione dello stesso database. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- È stato risolto un problema a causa del quale i valori predefiniti non venivano inseriti negli script per i tipi di tabella definiti dagli utenti. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- È stata introdotta un'altra serie di miglioramenti delle prestazioni nel menu di scelta rapida degli indici. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- È stato risolto un problema che provocava un eccessivo sfarfallio durante il passaggio del mouse su un indice mancante nel piano di esecuzione. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- È stato risolto un problema per cui SSMS impostava il database offline durante lo scripting [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118550)
- Sono state apportate varie correzioni all'interfaccia utente delle versioni localizzate (non in lingua inglese) di SSMS.
- È stato risolto un problema a causa del quale mancava il nodo "Chiavi Always Encrypted" quando la destinazione era SQL 2016 SP1 Standard Edition.
- Always Encrypted: Il menu "Always Encrypted" era abilitato erroneamente per SQL 2016 RTM Standard Edition o i server SQL 2014 (o precedenti). Correzione di un problema per cui IntelliSense segnalava un errore quando si usava la sintassi CREATE OR ALTER. Correzione di un problema per cui la crittografia non riusciva se CMK/CEK contenevano caratteri che richiedono escape, ovvero racchiusi tra parentesi. Quando si verifica un'eccezione Memoria insufficiente in SSMS viene visualizzato un messaggio di errore che suggerisce come alternativa l'uso di PowerShell nativo (a 64 bit).
È stato risolto un problema a causa del quale la procedura guidata AE non riusciva se l'utente usava sottoscrizioni Resource Group Manager (Gestore gruppo di risorse) anziché sottoscrizioni Azure classiche. È stato risolto un problema a causa del quale la procedura guidata AE visualizzava un errore non pertinente quando l'utente non aveva autorizzazioni in nessuna sottoscrizione o non aveva Azure Key Vault in nessuna sottoscrizione.
È stato risolto un problema nella procedura guidata AE per cui la pagina di accesso di Azure Key Vault non visualizza le sottoscrizioni di Azure se sono presenti più AAD. È stato risolto un problema nella procedura guidata AE per cui la pagina di accesso di Azure Key Vault non visualizza le sottoscrizioni di Azure per le quali l'utente dispone di autorizzazioni di lettura
  - È stato risolto un problema a causa del quale i file di risorse non potevano essere caricati correttamente, con conseguenti messaggi di errore non accurati
- È stato migliorato il contrasto dei collegamenti ipertestuali nella pagina di installazione di SSMS
- È stato risolto un problema a causa del quale i nodi PolyBase non venivano visualizzati se connessi a SQL Server Express (2016 SP1)
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
https://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- Le icone dei server registrati non vengono visualizzate dopo l'aggiornamento del nodo radice.
- Il pulsante Script per Crea database nei server v12 di Azure esegue lo script e quindi visualizza il messaggio "Nessuna azione per cui generare uno script".
- La finestra di dialogo Connetti al server di SSMS non cancella la scheda "Proprietà aggiuntive" per ogni nuova connessione.
- Lo script per generare attività non genera script CREATE DATABASE per un database SQL di Azure.
- La barra di scorrimento in Progettazione viste è disabilitata.
- I percorsi delle chiavi AVK di Always Encrypted non includono gli ID di versione.
- È stato ridotto il numero di query dell'edizione del motore nella finestra di query. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3113387)
- Gli errori di Always Encrypted derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.
- Modificato il timeout di connessione predefinito per OLTP e OLAP da 15 a 30 secondi per risolvere una serie di errori di connessione ignorati. 
- Risolto un arresto anomalo in SSMS all'avvio di un report personalizzato. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118856)
- Risoluzione di un problema a causa del quale "Genera script" ha esito negativo per i database SQL di Azure.
- Correzione di "Script come" e della procedura guidata "Genera script" per evitare l'aggiunta di nuove righe superflue durante la creazione di script per oggetti, come le stored procedure. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3115850)
- Provider PowerShell SQLAS: aggiunta della proprietà LastProcessed alle cartelle Dimension e MeasureGroup. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3111879)
- Statistiche query dinamiche: risolto un problema a causa del quale veniva visualizzata solo la prima query in un batch. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- Showplan: visualizzazione del massimo invece della somma per i thread nella finestra delle proprietà.
- Archivio query: aggiunta di un nuovo report per le query con variazioni di esecuzione notevoli.
- Problemi relativi alle prestazioni di Esplora oggetti: il menu a comparsa [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3114074) (Connetti elemento) per le tabelle si blocca. SSMS è lento quando si fa clic con il pulsante destro del mouse su un indice per una tabella su una connessione remota (tramite Internet). Evitare di eseguire query di tabella che eseguono ordinamenti nel server
- Rimozione della distribuzione guidata in Azure (Distribuisci database in una macchina virtuale Azure) da SSMS
- Risolto un problema a causa del quale gli indici mancanti non venivano visualizzati nei piani di esecuzione in SSMS [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3114194)
- Risolto un problema comune di arresto anomalo in fase di chiusura in SSMS
- Risolto un problema in Esplora oggetti a causa del quale si verificava un errore in seguito alla visualizzazione del menu di scelta rapida nei nodi PolyBase|Gruppo con scalabilità orizzontale [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3115128)
- Risolto un problema a causa del quale può verificarsi un arresto anomalo di SSMS durante il tentativo di visualizzare le autorizzazioni per un database
- Archivio query: miglioramenti generali nelle voci del menu di scelta rapida per le griglie dei risultati del report dell'archivio query
- La configurazione di Always Encrypted per una tabella esistente ha esito negativo con errori per gli oggetti correlati. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3103181)
- La configurazione di Always Encrypted per un database esistente con più schemi non funziona. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3109591)
- La procedura guidata Always Encrypted, Colonna crittografata ha esito negativo a causa del database che contiene viste che fanno riferimento a viste di sistema. [Argomento Connect](https://connect.microsoft.com/SQLServer/feedback/details/3111925)
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


## <a name="downloadssdtmediadownloadpng-ssms-1653httpsgomicrosoftcomfwlinklinkid840946"></a>![Download](../ssdt/media/download.png) [SSMS 16.5.3](https://go.microsoft.com/fwlink/?LinkID=840946)
Disponibile a livello generale | Numero di build: 13.0.16106.4

[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

In questa versione sono stati risolti i problemi seguenti:

* Risolto un problema introdotto in SSMS 16.5.2 che causava l'espansione del nodo 'Tabella' quando la tabella aveva più di una colonna di tipo sparse.

* Gli utenti possono distribuire pacchetti SSIS contenenti Gestione connessione OData per connettere una risorsa Microsoft Dynamics AX/CRM Online al catalogo SSIS. Per altre informazioni, vedere [Gestione connessione OData](../integration-services/connection-manager/odata-connection-manager.md).

* La configurazione di Always Encrypted per una tabella esistente ha esito negativo con errori per gli oggetti correlati. [ID Connect 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configurazione di Always Encrypted per un database esistente con più schemi non funziona. [ID Connect 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* La procedura guidata Always Encrypted, Colonna crittografata ha esito negativo a causa del database che contiene viste che fanno riferimento a viste di sistema. [ID Connect 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Durante la crittografia con Always Encrypted, gli errori derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.

* Il menu *Apri recenti* non mostra i file salvati di recente. [ID Connect 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS è lento quando si fa clic con il pulsante destro del mouse su un indice per una tabella (tramite una connessione Internet remota). [ID Connect 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Risolto un problema con la barra di scorrimento di SQL Designer. [ID Connect 3114856](https://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Il menu di scelta rapida per le tabelle si blocca momentaneamente 
 
* SSMS in alcuni casi genera eccezioni in Monitoraggio attività e subisce un arresto anomalo. [ID Connect 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* Si verifica un arresto anomalo di SSMS 2016 con l'errore "Il processo è stato terminato a causa di un errore interno del runtime .NET in IP 71AF8579 (71AE0000) con codice di uscita 80131506"


## <a name="uninstall-and-reinstall-ssms-17x"></a>Disinstallare e reinstallare SSMS 17.x

Se si verificano problemi durante l'installazione di SSMS che non vengono risolti con una disinstallazione e reinstallazione standard, è possibile provare a [ripristinare](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs) Visual Studio 2015 Isolated Shell. Se il ripristino di Visual Studio 2015 Isolated Shell non risolve il problema, la procedura seguente consente di risolvere molti problemi casuali:

1.  Disinstallare SSMS nello stesso modo in cui si disinstalla un'applicazione qualsiasi, usando *Programmi*, *Programmi e funzionalità* e così via, a seconda della versione di Windows.

2.  Disinstallare Visual Studio 2015 Isolated Shell **da un prompt dei comandi con privilegi elevati**:
   
    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```

    ```vs_isoshell.exe /Uninstall /Force /PromptRestart```

3.  Disinstallare Microsoft Visual C++ 2015 Redistributable nello stesso modo in cui si disinstalla un'applicazione qualsiasi. Disinstallare sia la versione x86 che la x64 se sono entrambe presenti nel computer.

4.  Reinstallare Visual Studio 2015 Isolated Shell **da un prompt dei comandi con privilegi elevati**:  

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```  
 
    ```vs_isoshell.exe /PromptRestart```

5.  Reinstallare SSMS.

6.  Eseguire l'aggiornamento alla [versione più recente di Visual C++ 2015 Redistributable](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) se non è già stato fatto.


## <a name="additional-downloads"></a>Download aggiuntivi  
Per un elenco di tutti i download di SQL Server Management Studio, vedere [Area download Microsoft](https://www.microsoft.com/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Per la versione più recente di SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
