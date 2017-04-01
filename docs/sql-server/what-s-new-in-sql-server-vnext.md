---
title: "Novit&#224; di SQL Server vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: "craigg-msft"
ms.author: "craigg"
manager: "jhubbard"
caps.handback.revision: 65
---
# Novit&#224; di SQL Server vNext
SQL Server vNext rappresenta un importante passo avanti per rendere SQL Server una piattaforma in grado di offrire un'ampia scelta di linguaggi di sviluppo, tipi di dati, in locale e nel cloud, e sistemi operativi, consentendo di sfruttare le potenzialità di SQL Server in Linux, nei contenitori Docker basati su Linux e in Windows.

Questo argomento è un riepilogo delle novità della versione CTP (Community Technology Preview) più recente e include collegamenti a informazioni più dettagliate sulle novità relative ad aree funzionali specifiche.

![info_tip](../sql-server/media/info-tip.png) Eseguire SQL Server in Linux. Per altre informazioni, vedere:
-  [What's new for SQL Server vNext on Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-whats-new) (Novità di SQL Server vNext in Linux)
-  [SQL Server on Linux Documentation](https://docs.microsoft.com/en-us/sql/linux/) (Documentazione di SQL Server in Linux)


**Per provarlo:**    
   -   [![Download da Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Scaricare SQL Server vNext CTP](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="whats-new-in-sql-server-vnext-ctp-13-february-2017"></a>Novità di SQL Server vNext CTP 1.3 (febbraio 2017)
### <a name="sql-server-database-engine"></a>Motore di database di SQL Server
- Sono state migliorate le prestazioni dei checkpoint indiretti.
- È stato aggiunto il supporto per i gruppi di disponibilità senza cluster.
- È stata aggiunta l'impostazione relativa ai gruppi di disponibilità che consente di definire il numero minimo di repliche necessarie per il commit.
- I gruppi di disponibilità sono ora supportati negli ambienti Windows e Linux per consentire le migrazioni e i test tra i diversi sistemi operativi.
- È stato aggiunto il supporto per i criteri di conservazione delle tabelle temporali.
- È stata introdotta la nuova vista a gestione dinamica SYS.DM_DB_STATS_HISTOGRAM.
- È stato aggiunto il supporto per la compilazione e la ricompilazione degli indici online columnstore non cluster.
- Sono state incluse cinque nuove viste a gestione dinamica per restituire informazioni sul processo Linux. Per altre informazioni, vedere [Viste a gestione dinamica del processo Linux](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- È stata aggiunta [sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) per l'analisi delle statistiche.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- Hint di codifica: una funzionalità avanzata che viene usata per ottimizzare l'elaborazione (aggiornamento dei dati) di modelli tabulari di grandi dimensioni in memoria. Per altre informazioni, vedere [Novità di Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md). 

## <a name="whats-new-in-sql-server-vnext-ctp-12-january-2017"></a>Novità di SQL Server vNext CTP 1.2 (gennaio 2017)
### <a name="sql-server-database-engine"></a>Motore di database di SQL Server
- È stato aggiunto il supporto per la compilazione e la ricompilazione degli indici online columnstore non cluster.
- Questa versione CTP contiene anche correzioni di bug per il motore di database.
- Per un elenco dettagliato dei miglioramenti di vNext CTP nelle versioni CPT precedenti, vedere [Novità di SQL Server vNext (motore di database)](../database-engine/configure-windows/what-s-new-in-sql-server-vnext-database-engine.md).

### <a name="sql-server-r-services"></a>SQL Server R Services
- Non sono presenti nuove funzionalità di R Services in questa versione CTP.
- Per informazioni più dettagliate sulle novità di R Services, compresi i dati relativi a versioni CTP precedenti, vedere [Novità di SQL Server R Services](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- In questa versione CTP non sono presenti nuove funzionalità di SSRS.
- Per informazioni più dettagliate sulle novità di SSRS, compresi i dati relativi a versioni precedenti, vedere [Novità di Reporting Services](../reporting-services/novità-di-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS).
- In questa versione CTP non sono presenti nuove funzionalità di SSAS.  
- Per informazioni più dettagliate, vedere [Novità di Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- In questa versione CTP non sono presenti nuove funzionalità di SSIS.
- Per informazioni più dettagliate sulle novità di SSIS, compresi i dati relativi a versioni CTP precedenti, vedere [Novità di Integration Services in SQL Server vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md).  

### <a name="master-data-services-mds"></a>Master Data Services (MDS)
- In questa versione CTP non sono presenti nuove funzionalità di Master Data Services.

##  <a name="infotipimageshiproominfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Coinvolgimento del team di progettazione di SQL Server 
- [Stack Overflow (tag sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Forum di MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - report bugs and request features](https://connect.microsoft.com/SQLServer/Feedback) (Segnalazione di bug e richiesta di funzionalità di Microsoft Connect)
- [Reddit - general discussion about R](https://www.reddit.com/r/SQLServer/) (Discussione generale su R in Reddit)

## <a name="see-also"></a>Vedere anche    
 + [![Note sulla versione](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png)](SQL%20Server%20vNext%20Release%20Notes.md)[ Note sulla versione di SQL Server vNext](../sql-server/sql-server-vnext-release-notes.md). 
+ [Edizioni e funzionalità supportate](https://msdn.microsoft.com/library/cc645993.aspx)
 + [[Requisiti hardware e software per l'installazione](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)](Hardware%20and%20Software%20Requirements%20for%20Installing%20SQL%20Server%202016.md)
 + [Installazione guidata](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)
 
 + [Installazione dei servizi e configurazione](Setup%20and%20Servicing%20Installation.md)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)