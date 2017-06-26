---
title: "Novità di SQL Server 2017 | Documenti Microsoft"
ms.custom: 
ms.date: 06/19/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: aa08b5e7de9bb317fd781a98ee5d829431b92df6
ms.openlocfilehash: 66c9bc4f2cba20076c357d27fdfacbc767a94c5c
ms.contentlocale: it-it
ms.lasthandoff: 06/23/2017

---
# <a name="what39s-new-in-sql-server-2017"></a>Novità di SQL Server 2017
SQL Server 2017 rappresenta un importante passo avanti verso effettua una piattaforma che è disponibili le opzioni di linguaggi di sviluppo, i tipi di dati, in locale e nel cloud e tra i sistemi operativi per la potenza di SQL Server per Linux, contenitori Docker basati su Linux e Windows di SQL Server.

In questo argomento è riportato un riepilogo delle novità nella versione Community Technical Preview (CTP) e collegamenti a più dettagliati per le aree di funzionalità specifiche informazioni sulle novità più recenti.

![info_tip](../sql-server/media/info-tip.png) Eseguire SQL Server in Linux. Per altre informazioni, vedere:
-  [Novità di SQL Server 2017 su Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new)
-  [SQL Server on Linux Documentation](https://docs.microsoft.com/sql/linux/)


**Per provarlo:**    
   -   [![Download da Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  **[scaricare SQL Server 2017 Community Technology Preview](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="whats-new-in-sql-server-2017-ctp-21-may-2017"></a>Novità di SQL Server 2017 CTP 2.1 (maggio 2017)
### <a name="sql-server-database-engine"></a>Motore di database di SQL Server  
- Un nuovo DMF, [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md), è stato introdotto per esporre attributi a livello di riepilogo e le informazioni nei file di log delle transazioni; utile per il monitoraggio dello stato del log delle transazioni.  
- Questa versione CTP include correzioni di bug e miglioramenti delle prestazioni per il motore di Database.
- Per un elenco dettagliato dei 2017 miglioramenti CTP nelle versioni CTP precedenti, vedere [novità di SQL Server 2017 (motore di Database)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- SQL Server Reporting Services non è più disponibile per l'installazione tramite l'installazione di SQL Server a partire dalla versione CTP 2.1.
- I commenti sono ora disponibili per i report. I commenti consentono di aggiungere una prospettiva al contenuto in un report e collaborare con altri utenti nell'organizzazione. È inoltre possibile includere gli allegati con il commento.
- Per informazioni più dettagliate sulle novità di SSRS, compresi i dati relativi a versioni precedenti, vedere [Novità di Reporting Services](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 
- Per informazioni sul Server di Report di Power BI, vedere [Introduzione a Server di Report di Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

### <a name="sql-server-machine-learning-services"></a>Servizi di apprendimento macchina SQL Server
- In questa versione CTP non esistono alcun nuove funzionalità di servizi di Machine Learning.
- Per ulteriori servizi di Machine Learning cosa nuove informazioni, inclusi i dettagli da precedente CTP, vedere [novità di servizi di SQL Server Machine Learning](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).  

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS).
- In questa versione CTP non sono presenti nuove funzionalità di SSAS.  
- Per ulteriori informazioni sui miglioramenti e correzioni di bug in questa versione, vedere [novità di Analysis Services di SQL Server 2017](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
-   È ora possibile usare il **Use32BitRuntime** parametro.
-   Le prestazioni di registrazione sono stata migliorata.
- Per ulteriori SSIS cosa nuove informazioni, inclusi i dettagli da precedente CTP, vedere [novità di servizi di integrazione di SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).  

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="whats-new-in-sql-server-2017-ctp-20-april-2017"></a>Novità di SQL Server 2017 CTP 2.0 (aprile 2017)
### <a name="sql-server-database-engine"></a>Motore di database di SQL Server
- **Ricompilazione dell'indice online può essere ripristinato**. Ricompilazione dell'indice online può essere ripristinato consente di riprendere un'operazione di ricompilazione indice online dal punto di interruzione dopo un errore. Ad esempio, un failover su una replica o di una situazione di spazio su disco insufficiente. È possibile inoltre sospendere e riprendere un'operazione di ricompilazione indice online. È ad esempio, potrebbe essere necessario liberare temporaneamente le risorse di sistemi per l'esecuzione di un'attività ad alta priorità o completare la ricompilazione dell'indice in un'altra finestra miniatous se le finestre di manutenzione disponibile è insufficiente per una tabella di grandi dimensioni. Infine, la ricostruzione dell'indice online può essere ripristinato non richiede spazio di log significative, che consente di eseguire il troncamento del log durante l'esecuzione dell'operazione di ricompilazione può essere ripristinato. Vedere [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) e [linee guida per operazioni sugli indici online](../relational-databases/indexes/guidelines-for-online-index-operations.md).
- **Opzione IDENTITY_CACHE per ALTER DATABASE SCOPED CONFIGURATION**. È stata aggiunta una nuova opzione IDENTITY_CACHE all'istruzione ALTER DATABASE con ambito di configurazione T-SQL. Quando questa opzione è impostata su OFF, è possono evitare gap nei valori delle colonne di identità nel caso in cui un server viene riavviato in modo imprevisto o viene eseguito il failover a un server secondario. Vedere [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).  
- CLR utilizza Strumentazione gestione Windows (CAS, Code Access Security) in .NET Framework, non è più supportato come limite di sicurezza. Un assembly CLR creato con `PERMISSION_SET = SAFE` potrebbe essere in grado di accedere alle risorse di sistema esterne, chiamare codice non gestito e acquisire i privilegi sysadmin. A partire da [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)], un `sp_configure` opzione denominata `clr strict security` viene introdotto per migliorare la sicurezza degli assembly CLR. `clr strict security`è abilitata per impostazione predefinita e considera `SAFE` e `EXTERNAL_ACCESS` assembly come se fossero contrassegnati `UNSAFE`. Il `clr strict security` opzione può essere disabilitata per la compatibilità con le versioni precedenti, ma non è consigliata. Si consiglia di tutti gli assembly di essere firmato da un certificato o chiave asimmetrica con un account di accesso corrispondente è stata concessa `UNSAFE ASSEMBLY` autorizzazione nel database master. Per ulteriori informazioni, vedere [elevata protezione CLR](../database-engine/configure-windows/clr-strict-security.md).  
- Funzionalità di database Graph per modellare relazioni molti-a-molti. Questo include nuovi [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) sintassi per la creazione di tabelle edge e di nodo e la parola chiave [corrispondenza](../t-sql/queries/match-sql-graph.md) per le query. Per ulteriori informazioni, vedere [grafico elaborazione con SQL Server 2017](../relational-databases/graphs/sql-graph-overview.md).   
- L'ottimizzazione automatica è una funzionalità di database che fornisce informazioni dettagliate sulla query potenziali problemi di prestazioni, è possibile suggerire soluzioni e correzione identificate automaticamente i problemi. L'ottimizzazione automatica [!INCLUDE[ssnoversion](../includes/ssnoversion.md)], invia una notifica ogni volta che viene rilevato un potenziale problema di prestazioni e consente di applicare azioni correttive o consente il [!INCLUDE[ssde](../includes/ssde-md.md)] risolvere automaticamente i problemi di prestazioni. Per ulteriori informazioni, vedere [ottimizzazione automatica](../relational-databases/automatic-tuning/automatic-tuning.md).  
-   Batch modalità adattivo Join per migliorare la qualità del piano (in db compatibilità 140).
-   Esecuzione Interleaved di più istruzioni T-SQL TVF migliorare la qualità del piano (in db compatibilità 140).
- Archivio query ora tiene traccia anche le informazioni di riepilogo statistiche attesa. Categorie di statistiche di attesa per ogni query in archivio Query di rilevamento consente i livelli di prestazioni esperienza di risoluzione dei problemi, fornendo, ancora più approfondite sulle prestazioni del carico di lavoro e il relativo colli di bottiglia mantenendo i vantaggi di archivio Query.
- Supporto DTC per gruppi di disponibilità AlwaysOn per tutte le transazioni tra database tra database che fanno parte del gruppo di disponibilità, tra cui database che fanno parte della stessa istanza. Per ulteriori informazioni, vedere [transazioni - gruppi di disponibilità AlwaysOn e mirroring del Database](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)
- Una nuova colonna **modified_extent_page_count** è stato introdotto in [Sys.dm db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) per tenere traccia delle modifiche differenziali in ogni file di database del database.
- [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) ora supporta il caricamento di una tabella in un filegroup diverso da un filegroup predefinito dell'utente utilizzando il **ON** (parola chiave).
- Installazione di SQL Server supporta la specifica di un massimo di dimensioni del file tempdb iniziale **(262.144 MB) a 256 GB** per ogni file con un avviso se le dimensioni del file sono impostata su valore maggiore di **1 GB** e IFI non è abilitata.
- Una nuova gestione vista dinamica (DMV) [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) viene introdotto per tenere traccia dell'utilizzo di archivio versione per ogni database.
- Una nuova DMV [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) viene introdotto per esporre le informazioni di VLF simile a DBCC LOGINFO.
- Le tabelle temporali con controllo delle versioni del sistema supportano ora CASCADE UPDATE e eliminazione a catena.
- Questa versione CTP contiene correzioni di bug per il motore di database.
- Per un elenco dettagliato dei 2017 miglioramenti CTP nelle versioni CTP precedenti, vedere [novità di SQL Server 2017 (motore di Database)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).   

### <a name="sql-server-machine-learning-services"></a>Servizi di apprendimento macchina SQL Server
- SQL Server R Services dispone di un nuovo nome, in modo da riflettere il supporto per il linguaggio Python nella versione CTP 2.0. È ora possibile utilizzare SQL Server Machine Learning Services (In-Database) per eseguire gli script R o Python in SQL Server. In alternativa, installare Microsoft Machine Learning Server (Standalone) per distribuire e utilizzare i modelli R e Python che non richiedono SQL Server. 
- Entrambe le piattaforme includono nuovi algoritmi MicrosoftML per distribuita di machine learning e la versione più recente di Microsoft R (versione 9.1.0).
- Per ulteriori informazioni, vedere [novità per Machine Learning](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-14-march-2017"></a>Novità di SQL Server 2017 CTP 1.4 (marzo 2017)
### <a name="sql-server-database-engine"></a>Motore di database di SQL Server
- Questa versione CTP non include nuove funzionalità del motore di database.
- Questa versione CTP contiene correzioni di bug per il motore di database.
- Per un elenco dettagliato dei 2017 miglioramenti CTP nelle versioni CTP precedenti, vedere [novità di SQL Server 2017 (motore di Database)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

### <a name="sql-server-r-services"></a>SQL Server R Services
- Non sono presenti nuove funzionalità di R Services in questa versione CTP.
- Per informazioni più dettagliate sulle novità di R Services, compresi i dati relativi a versioni CTP precedenti, vedere [Novità di SQL Server R Services](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- In questa versione CTP non sono presenti nuove funzionalità di SSRS.
- Per informazioni più dettagliate sulle novità di SSRS, compresi i dati relativi a versioni precedenti, vedere [Novità di Reporting Services](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS).
- In questa versione CTP non sono presenti nuove funzionalità di SSAS.  
- Per ulteriori informazioni, incluse le novità di Analysis Services in una delle versioni di anteprima più recente di SSDT e SSMS, vedere [novità di Analysis Services 2017](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- In questa versione CTP non sono presenti nuove funzionalità di SSIS.
- Per ulteriori SSIS cosa nuove informazioni, inclusi i dettagli da precedente CTP, vedere [novità di Integration Services 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).  

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-13-february-2017"></a>Novità di SQL Server 2017 CTP 1.3 (febbraio 2017)
### <a name="sql-server-database-engine"></a>Motore di database di SQL Server
- Sono state migliorate le prestazioni dei checkpoint indiretti.
- È stato aggiunto il supporto per i gruppi di disponibilità senza cluster.
- È stata aggiunta l'impostazione relativa ai gruppi di disponibilità che consente di definire il numero minimo di repliche necessarie per il commit.
- I gruppi di disponibilità sono ora supportati negli ambienti Windows e Linux per consentire le migrazioni e i test tra i diversi sistemi operativi.
- Aggiunto il supporto dei criteri di conservazione di tabelle temporale. Per ulteriori informazioni, vedere [gestire conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni del sistema](../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md#using-temporal-history-retention-policy-approach).
- È stata introdotta la nuova vista a gestione dinamica SYS.DM_DB_STATS_HISTOGRAM.
- Columnstore non cluster in linea compilazione di indice e ricompila aggiunto il supporto
- Sono state incluse cinque nuove viste a gestione dinamica per restituire informazioni sul processo Linux. Per altre informazioni, vedere [Viste a gestione dinamica del processo Linux](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- È stata aggiunta[sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) per l'analisi delle statistiche.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- Hint di codifica: una funzionalità avanzata che viene usata per ottimizzare l'elaborazione (aggiornamento dei dati) di modelli tabulari di grandi dimensioni in memoria. Per ulteriori informazioni, vedere [novità di Analysis Services 2017](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md). 


![horizontal_bar](../sql-server/media/horizontal-bar.png)

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Coinvolgimento del team di progettazione di SQL Server 
- [Stack Overflow (tag sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Forum di MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - report bugs and request features](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - general discussion about R](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>Vedere anche    
- ![Note sulla versione](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) [le note sulla versione SQL Server 2017](../sql-server/sql-server-2017-release-notes.md). 
- [Edizioni e funzionalità supportate](https://msdn.microsoft.com/library/cc645993.aspx)
- [Requisiti hardware e software per l'installazione](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
- [Installazione guidata di SQL Server](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
- [Installare gli aggiornamenti dei servizi di SQL Server](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

