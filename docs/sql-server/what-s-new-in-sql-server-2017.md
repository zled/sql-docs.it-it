---
title: "Novità di SQL Server 2017 | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 731d53110d9dc47de5a44dd7f65190e029e120dc
ms.contentlocale: it-it
ms.lasthandoff: 07/19/2017

---
# <a name="whats-new-in-sql-server-2017"></a>Novità di SQL Server 2017
SQL Server 2017 rappresenta un importante passo avanti verso una piattaforma che offre opzioni di linguaggi di sviluppo, tipi di dati, memorizzazione in locale e nel cloud e sistemi operativi rendendo disponibili le funzionalità di SQL Server in Linux, nei contenitori Docker basati su Linux e in Windows. Questo argomento include un riepilogo delle novità di specifiche aree funzionali delle ultime versioni di SQL Server 2017 Release Candidate (RC1, luglio 2017) e Community Technical Preview (CTP).

**Per provarlo:** [Scaricare SQL Server 2017 Release Candidate (RC)](http://go.microsoft.com/fwlink/?LinkID=829477)

>[!TIP]
>**Eseguire SQL Server in Linux.** Per altre informazioni, vedere [SQL Server on Linux Documentation](https://docs.microsoft.com/sql/linux/) (Documentazione di SQL in Linux) e [What's new for SQL Server 2017 on Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new) (Novità di SQL Server 2017 in Linux).

## <a name="latest-release-sql-server-2017-release-candidate-rc1-july-2017"></a>Ultima versione: SQL Server 2017 Release Candidate (RC1, luglio 2017)

### <a name="sql-server-database-engine"></a>Motore di database di SQL Server    
- Gli assembly CLR possono ora essere aggiunti a un elenco elementi consentiti come soluzione alternativa per la funzionalità `clr strict security` descritta in CTP 2.0. [sp_add_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md), [sp_drop_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) e [sys.trusted_asssemblies](../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md) sono aggiunti per supportare l'elenco elementi consentiti di assembly attendibili.  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- La nuova funzionalità **Scalabilità orizzontale** di SSIS include nella versione RC1 le seguenti funzionalità nuove e modificate. Per altre informazioni, vedere [What's New in Integration Services in SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md) (Novità di Integration Services in SQL Server 2017).
    -   Il master di scalabilità orizzontale supporta ora la disponibilità elevata.
    -   La gestione del failover dei log di esecuzione dai ruoli di lavoro di scalabilità orizzontale è stata migliorata.
    -   Il parametro *runincluster* della stored procedure **[catalog].[create_execution]** è stato rinominato in *runinscaleout* per coerenza e leggibilità.
    -   Il catalogo SSIS include una nuova proprietà globale che consente di specificare la modalità predefinita per l'esecuzione dei pacchetti SSIS.

## <a name="sql-server-database-engine"></a>Motore di database di SQL Server  
SQL Server 2017 include numerose nuove funzionalità del motore di database, miglioramenti e aumenti delle prestazioni. 
- La **ricompilazione dell'indice online ripristinabile** consente di ripristinare un'operazione di ricompilazione dell'indice online dal punto in cui è stata arrestata a causa di un errore, ad esempio un failover in una replica o lo spazio su disco insufficiente, o di sospendere e successivamente ripristinare l'operazione. Vedere [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) e [linee guida per operazioni sugli indici online](../relational-databases/indexes/guidelines-for-online-index-operations.md). (CTP 2.0)
- L'opzione **IDENTITY_CACHE** per ALTER DATABASE SCOPED CONFIGURATION consente di evitare gap nei valori delle colonne Identity nel caso in cui un server viene riavviato in modo imprevisto o esegue un failover in un server secondario. Vedere [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). (CTP 2.0)
- L'**ottimizzazione di database automatica** offre informazioni su potenziali problemi di prestazioni delle query, suggerisce soluzioni e consente di correggere automaticamente i problemi rilevati. Vedere [Automatic tuning](../relational-databases/automatic-tuning/automatic-tuning.md) (Ottimizzazione automatica). (CTP 2.0)
- Le nuove **funzionalità dei database dei grafici** per la modellazione delle relazioni molti-a-molti include la nuova sintassi [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) per la creazione di nodi e tabelle bordi e la parola chiave [MATCH](../t-sql/queries/match-sql-graph.md) per le query. Vedere [Graph Processing with SQL Server 2017](../relational-databases/graphs/sql-graph-overview.md) (Elaborazione di grafici con SQL Server 2017). (CTP 2.0)
- Un'opzione sp_configure denominata `clr strict security` è abilitata per impostazione predefinita per migliorare la sicurezza degli assembly CLR. Vedere [CLR strict security](../database-engine/configure-windows/clr-strict-security.md). (CTP 2.0)
- Il programma di installazione consente ora di specificare una dimensione del file tempdb iniziale massima di **256 GB** (262,144 MB) per singolo file con un avviso se viene impostata una dimensione del file maggiore di 1 GB con l'inizializzazione immediata dei file non abilitata. (CTP 2.0)
- La colonna **modified_extent_page_count** in [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) tiene traccia delle modifiche differenziali in ogni file di database abilitando soluzioni di backup intelligente che eseguono un backup differenziale o un backup completo in base alla percentuale di pagine modificate nel database. (CTP 2.0)
- La sintassi T-SQL [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) supporta ora il caricamento di una tabella in un filegroup diverso da quello predefinito dell'utente usando la parola chiave **ON**. (CTP 2.0)
- Le transazioni tra database sono ora supportate in tutti i database che appartengono a un **gruppo di disponibilità Always On**, inclusi i database che appartengono alla stessa istanza. Vedere [Transactions - Always On Availability Groups and Database Mirroring](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md) (Transazioni: gruppi di disponibilità Always On e mirroring del database) (CTP 2.0)
- La nuova funzionalità **Gruppi di disponibilità** include il supporto senza cluster, l'impostazione Minimum Replica Commit Availability Groups (Gruppi di disponibilità con commit di un numero minimo di repliche), le migrazioni tra sistemi operativi Windows e Linux e i test. (CTP 1.3)
- Nuove viste di gestione dinamiche:
    - [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) espone attributi a livello di riepilogo e informazioni sui file di log delle transazioni utili per il monitoraggio dello stato dei log delle transazioni. (CTP 2.1)
    - [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) tiene traccia dell'utilizzo dell'archivio versioni per ogni database e consente di pianificare in modo proattivo la dimensione del file tempdb in base all'utilizzo dell'archivio versioni di ogni singolo database. (CTP 2.0)
    - [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) espone le informazioni VLF per monitorare, segnalare ed evitare problemi potenziali dei log delle transazioni. (CTP 2.0)
    - [sys.dm_db_stats_histogram](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) è una nuova vista di gestione dinamica per l'esame delle statistiche. (CTP 1.3)
    - **sys.dm_os_host_info** offre informazioni sul sistema operativo per Windows e Linux. (CTP 1.0)
- L'**Ottimizzazione guidata motore di database (DTA)** include opzioni aggiuntive e prestazioni migliorate. (CTP 1.2)
- I **miglioramenti in memoria** includono il supporto per le colonne calcolate nelle tabelle ottimizzate per la memoria, il supporto completo delle funzioni JSON nei moduli compilati in modo nativo e l'operatore CROSS APPLY nei moduli compilati in modo nativo. (CTP 1.1)
- Le nuove **funzioni di stringa** sono CONCAT_WS, TRANSLATE e TRIM e WITHIN GROUP è ora supportata per la funzione STRING_AGG. (CTP 1.1)
- Sono disponibili nuove **opzioni di accesso in blocco** (BULK INSERT e OPENROWSET(BULK...) ) per i file con estensione csv e i file del BLOB di Azure. (CTP 1.1)
- I **miglioramenti degli oggetti con ottimizzazione per la memoria** includono sp_spaceused e l'eliminazione del limite di 8 indici per le tabelle ottimizzate per la memoria, sp_rename per le tabelle ottimizzate per la memoria e i moduli T-SQL compilati in modo nativo e CASE e TOP (N) WITH TIES per i moduli T-SQL compilati in modo nativo. I file di filegroup con ottimizzazione per la memoria possono ora essere archiviati ed è possibile eseguirne il backup e il ripristino nell'archiviazione di Azure. (CTP 1.0)
- **DATABASE SCOPED CREDENTIAL** è una nuova classe di autorizzazioni a protezione diretta che supportano CONTROL, ALTER, REFERENCES, TAKE OWNERSHIP e VIEW DEFINITION. ADMINISTER DATABASE BULK OPERATIONS è ora visibile in sys.fn_builtin_permissions. (CTP 1.0)
- È stata aggiunto il livello **COMPATIBILITY_LEVEL 140** del database. (CTP 1.0).  

Per altre informazioni, vedere [What's new in SQL Server 2017 Database Engine](~/database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md) (Novità del motore di database di SQL Server 2017).

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- La nuova funzionalità **Scalabilità orizzontale** di SSIS include le seguenti funzionalità nuove e modificate. Per altre informazioni, vedere [What's New in Integration Services in SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md) (Novità di Integration Services in SQL Server 2017). (RC1)
    -   Il master di scalabilità orizzontale supporta ora la disponibilità elevata.
    -   La gestione del failover dei log di esecuzione dai ruoli di lavoro di scalabilità orizzontale è stata migliorata.
    -   Il parametro *runincluster* della stored procedure **[catalog].[create_execution]** è stato rinominato in *runinscaleout* per coerenza e leggibilità.
    -   Il catalogo SSIS include una nuova proprietà globale che consente di specificare la modalità predefinita per l'esecuzione dei pacchetti SSIS.
- Nella nuova funzionalità **Scalabilità orizzontale di SSIS** è ora possibile usare il parametro **Use32BitRuntime** quando si attiva l'esecuzione. (CTP 2.1)
- SQL Server 2017 Integration Services (SSIS) supporta ora **SQL Server in Linux** e un nuovo pacchetto consente di eseguire i pacchetti SSIS in Linux dalla riga di comando. Per altre informazioni, vedere il [post del blog che annuncia il supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). (CTP 2.1)
- La nuova funzionalità **Scalabilità orizzontale di SSIS** semplifica l'esecuzione di SSIS su più computer. Vedere [Integration Services Scale Out](~/integration-services/integration-services-ssis-scale-out.md) (Scalabilità orizzontale di Integration Services). (CTP 1.0)
- L'origine OData e la gestione connessione OData supportano ora la connessione ai feed OData di Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online. (CTP 1.0)

Per altre informazioni, vedere [What's New in Integration Services in SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md) (Novità di Integration Services in SQL Server 2017).

## <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS). 
SQL Server Analysis Services 2017 include numerosi miglioramenti per i modelli tabulari. tra cui:
- Modalità tabulare come opzione di installazione predefinita per Analysis Services. (CTP 2.0)
- Sicurezza a livello di oggetto per la protezione dei metadati dei modelli tabulari. (CTP 2.0)
- Relazioni di date per creare facilmente relazioni basate sui campi data. (CTP 2.0)
- Supporto delle nuove origini dati **Get Data** (Power Query) e delle origini dati DirectQuery esistenti per query M. (CTP 2.0) 
- Editor DAX per SSDT. (CTP 2.0)
- Suggerimenti di codifica, una funzione avanzata per l'ottimizzazione dell'aggiornamento dei dati di modelli tabulari in memoria di grandi dimensioni. (CTP 1.3)
- Supporto del **livello di compatibilità 1400** per i modelli tabulari. Per creare nuovi progetti di modelli tabulari o aggiornare quelli esistenti con il livello di compatibilità 1400, scaricare e installare [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). (CTP 1.1)
- Una nuova funzione **Recupera dati** per modelli tabulari al livello di compatibilità 1400. Vedere il [blog del team di Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-2017-on-windows-ctp-1-1-for-analysis-services/). (CTP 1.1)
- Proprietà **Nascondi membri** per nascondere i membri vuoti nelle gerarchie incomplete. (CTP 1.1)
- Nuova azione dell'utente finale **Righe di dettaglio** in **Mostra dettagli** per informazioni aggregate. Funzioni [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) e **DETAILROWS** per la creazione di espressioni Righe di dettaglio. (CTP 1.1)
- Operatore **IN** DAX per la specifica di più valori. (CTP 1.1)

Per altre informazioni, vedere [What's new in SQL Server Analysis Services 2017](~/analysis-services/what-s-new-in-sql-server-analysis-services-2017.md) (Novità di Analysis Services di SQL Server 2017).

## <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
A partire dalla versione CTP 2.1, SSRS non può più essere installato tramite l'installazione di SQL Server. Passare all'Area download Microsoft per [scaricare l'anteprima di maggio 2017 del server di report di Power BI e Power BI Desktop ottimizzato per il server di report di Power BI](https://www.microsoft.com/download/details.aspx?id=55253). Per informazioni sul Server di Report di Power BI, vedere [Introduzione a Server di Report di Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).
- I commenti sono ora disponibili per i report per una maggior prospettiva e collaborazione con altri utenti. È anche possibile includere allegati nei commenti. (CTP 2.1)
- Nelle versioni più recenti di Generatore Report e SQL Server Data Tools è possibile creare query DAX native nei modelli di dati tabulari di SQL Server Analysis Services supportati trascinando i campi desiderati nelle finestre di progettazione delle query. Vedere il [blog di Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

Per altre informazioni, vedere [Novità di SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

## <a name="sql-server-machine-learning-services"></a>Servizi di apprendimento macchina SQL Server
SQL Server R Services è stato rinominato **SQL Server Machine Learning Services** per indicare il nuovo supporto per Python in aggiunta ai linguaggi R. È possibile usare Machine Learning Services (In-Database) per eseguire script R o Python in SQL Server o installare Microsoft Machine Learning Server (Standalone) per distribuire e usare modelli R e Python che non richiedono SQL Server. Entrambe le piattaforme includono nuovi algoritmi MicrosoftML per distribuita di machine learning e la versione più recente di Microsoft R (versione 9.1.0). (CTP 2.0)
- Machine Learning con Python include il modulo **revoscalepy** che supporta un subset di algoritmi distribuiti e contesti di calcolo inclusi in RevoScaleR. 
- È possibile creare facilmente più modelli in parallelo da R usando la nuova funzione **rxExecBy**. I contesti di calcolo supportati includono RxSpark e RxInSQLServer. (CTP 2.0)

Per altre informazioni, vedere [What's new in SQL Server Machine Learning Services](~/advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) (Novità di SQL Server Machine Learning Services).

## <a name="next-steps"></a>Passaggi successivi
- Vedere [Note sulla versione di SQL Server 2017](sql-server-2017-release-notes.md).
- Vedere [Novità di SQL Server 2016](what-s-new-in-sql-server-2016.md).

