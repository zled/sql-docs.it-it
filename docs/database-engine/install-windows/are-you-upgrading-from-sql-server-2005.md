---
title: "Aggiornamento da SQL Server 2005 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
caps.latest.revision: 21
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 21
---
# Aggiornamento da SQL Server 2005
  La fine del supporto esteso per SQL Server 2005 è uno dei motivi per cui si consiglia di aggiornare subito il sistema a una nuova versione di SQL Server e al database SQL di Azure. L'aggiornamento consente di garantire sicurezza e conformità, di raggiungere eccellenti livelli di prestazioni e di ottimizzare l'infrastruttura della piattaforma di dati.  
  
 Per altre informazioni, indicazioni e strumenti per pianificare e automatizzare l'aggiornamento o la migrazione, vedere [SQL Server 2005 end of support](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/) (Fine del supporto per SQL Server 2005).  
  
## Vantaggi dell'aggiornamento  
  
> [!IMPORTANT]  
>  Il supporto esteso per SQL Server 2005 termina il 12 aprile 2016. Se si continua a usare SQL Server 2005 dopo il 12 aprile 2016, non si riceveranno più aggiornamenti della sicurezza.  
  
 Per ottenere un foglio dati in formato PDF che spiega i vantaggi dell'aggiornamento da SQL Server 2005, [fare clic qui](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-Infographic-UpgradeSQL2005Datasheet.pdf) (non sull'immagine di anteprima riportata di seguito).  
  
 ![Data sheet about upgrading from SQL Server 2005](../../database-engine/install-windows/media/sqlserver2005eos.png "Data sheet about upgrading from SQL Server 2005")  
  
## Opzioni di aggiornamento disponibili  
 Se si aggiornano i database relazionali da SQL Server 2005, queste di seguito sono le opzioni per l'archiviazione relazionale nella piattaforma Microsoft.  
  
 Per un'analisi più completa di queste opzioni, [fare clic qui](http://sql05upgrade.azurewebsites.net/).  
  
|Opzione di archiviazione relazionale|Vantaggi|Altri fattori da considerare|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server locale**<br /><br /> Prendere in considerazione questa opzione per le applicazioni di database di qualsiasi tipo, dai sistemi transazionali ai data warehouse.|Si ha un maggiore controllo sulle funzionalità e la scalabilità perché vengono gestiti sia l'hardware che il software.<br /><br /> Se si esegue l'aggiornamento da SQL Server 2005, questo è l'ambiente più simile.|L'investimento iniziale è elevato ed è necessaria una gestione continua perché è necessario acquistare, mantenere e gestire il proprio hardware e software.<br /><br /> Per altre informazioni, vedere [SQL Server 2016](https://www.microsoft.com/EN-US/server-cloud/products/sql-server-2016/).|  
|**SQL Server ospitato in macchine virtuali di Azure**<br /><br /> Prendere in considerazione questa opzione se si hanno le esigenze seguenti:<br /><br /> Vantaggi associati alla migrazione a un ambiente ospitato.<br /><br /> Controllo sull'ambiente operativo.<br /><br /> Set di funzionalità di SQL Server, già noto.|È possibile eseguire rapidamente la distribuzione da una libreria di immagini della macchina virtuale.<br /><br /> Viene fornito il set di funzionalità completo di SQL Server.<br /><br /> Si risparmiano i costi per l'hardware e il software del server. Si paga per ora in base all'utilizzo.|È necessario configurare e gestire sia SQL Server che il software del sistema operativo.<br /><br /> <br /><br /> Per altre informazioni, vedere [Panoramica di SQL Server in Macchine virtuali di Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Per informazioni sulla migrazione, vedere [Eseguire la migrazione di un database di SQL Server a SQL Server in una macchina virtuale di Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|  
|**Servizio di database ospitato nel database SQL di Azure**<br /><br /> Prendere in considerazione questa opzione se si preferisce una soluzione a basso costo che necessita di poca manutenzione.<br /><br /> Questa opzione è particolarmente adatta per le app che non richiedono una capacità costante o che devono fornire un accesso esterno.|La distribuzione è rapida e la scalabilità verticale semplice.<br /><br /> Si paga per ora in base all'utilizzo.<br /><br /> Il costo del servizio include anche la disponibilità elevata e i backup automatici, oltre all'archiviazione.|Il database SQL di Azure non offre alcune delle funzionalità di SQL Server non applicabili a un ambiente cloud ospitato. Per altre informazioni, vedere [Differenze di Transact-SQL del database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Anche le dimensioni massime del database SQL di Azure sono di 500 GB, invece dei 524 PB di SQL Server.<br /><br /> Per altre informazioni, vedere [Database SQL](https://azure.microsoft.com/services/sql-database/).<br /><br /> Per informazioni sulla migrazione, vedere [Migrazione di un database SQL Server nel database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|  
  
 Per alcuni dati e applicazioni si può valutare anche una soluzione non relazionale o NoSQL.  
  
|Soluzione non relazionale|Vantaggi|  
|------------------------------|--------------|  
|**Azure DocumentDB**<br /><br /> Prendere in considerazione questa opzione per applicazioni moderne, scalabili, mobili e Web che usano i dati JSON e richiedono una combinazione affidabile di funzionalità di query e di elaborazione dei dati transazionali.<br /><br /> Per altre informazioni, vedere [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/).<br /><br /> Per informazioni sull'importazione di dati, vedere [Importare dati in DocumentDB](https://azure.microsoft.com/documentation/articles/documentdb-import-data/).|I documenti vengono indicizzati ed è possibile eseguire query usando la sintassi SQL con cui si ha già familiarità.<br /><br /> Il database è senza schema.<br /><br /> È possibile aggiungere proprietà ai documenti senza dover ricompilare gli indici.<br /><br /> Il supporto per JSON e JavaScript viene fornito direttamente all'interno del motore di database.<br /><br /> Il supporto nativo viene fornito per i dati geospaziali e l'integrazione con altri servizi di Azure, inclusi Ricerca di Azure, HDInsight e Data Factory.<br /><br /> Si ottiene un'archiviazione a bassa latenza e ad alte prestazioni con livelli di velocità effettiva riservati.|  
|**Archiviazione tabelle di Azure**<br /><br /> Prendere in considerazione questa opzione per archiviare petabyte di dati semistrutturati in una soluzione conveniente.<br /><br /> Per altre informazioni, vedere [Archivio tabelle](https://azure.microsoft.com/services/storage/tables/).|È possibile sviluppare le app e lo schema della tabella senza disconnettere i dati.<br /><br /> È possibile usare la scalabilità verticale senza partizionamento orizzontale del set di dati.<br /><br /> Si ottiene un'archiviazione con ridondanza geografica che replica i dati in più regioni.|  
  
 Per scaricare il report sulla migrazione da SQL Server 2005 di Directions on Microsoft, contenente altre informazioni sulle opzioni di aggiornamento, [fare clic qui](https://info.microsoft.com/CO-SQL-CNTNT-FY16-09Sep-14-ModernizationDirOnMFST-Register.html) (non sull'immagine di anteprima riportata di seguito).  
  
 ![Report about migrating from SQL Server 2005](../../database-engine/install-windows/media/sqlserver2005migratingdoc.png "Report about migrating from SQL Server 2005")  
  
## Pianificare l'aggiornamento  
  
-   Per informazioni su come pianificare l'aggiornamento, vedere la serie seguente di post di blog del team di SQL Server.  
  
    -   [Pianificazione di un aggiornamento efficiente da SQL Server 2005: Passaggio 1 di 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [Pianificazione di un aggiornamento efficiente da SQL Server 2005: Passaggio 2 di 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [Pianificazione di un aggiornamento efficiente da SQL Server 2005: Passaggio 3 di 3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   Vedere i requisiti e le considerazioni in [Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md), oltre a [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md).  
  
-   Vedere come eseguire l'aggiornamento.  
  
    -   Esaminare i metodi di aggiornamento disponibili e ottenere informazioni sulla pianificazione e sull'esecuzione dei test nell'argomento [Aggiornare il motore di database](../../database-engine/install-windows/upgrade-database-engine.md).  
  
        > [!IMPORTANT]  
        >  Non è possibile eseguire l'aggiornamento di un server SQL Server 2005 a un server SQL Server 2016 sul posto. È necessario installare SQL Server 2016, quindi eseguire la migrazione dei database SQL Server 2005 alla nuova installazione. Per altre informazioni, vedere la sezione relativa a un nuovo aggiornamento dell'installazione nell'argomento [Scegliere un metodo di aggiornamento del motore di database](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
    -   Per ottenere una guida tecnica all'aggiornamento più dettagliata in formato PDF, [fare clic qui](http://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf).  
  
        > [!NOTE]  
        >  Questa è la versione della guida tecnica all'aggiornamento per SQL Server 2014. La versione della guida per SQL Server 2016 non è ancora disponibile.  
  
-   Per altre informazioni, indicazioni e strumenti per pianificare e automatizzare l'aggiornamento o la migrazione, vedere [SQL Server 2005 end of support](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/) (Fine del supporto per SQL Server 2005).  
  
## Ottenere SQL Server 2016  
 Per scaricare una copia di valutazione di SQL Server 2016, [fare clic qui](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016/?wt.mc_id=upgrade2005).  
  
## Vedere anche  
 [SQL Server 2016](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/default.aspx)   
 [Fine del supporto di SQL Server 2005](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)   
 [Aggiornare da SQL Server 2005 a SQL Server 2014](https://msdn.microsoft.com/en-us/library/mt170591\(v=sql.120\).aspx)  
  
  