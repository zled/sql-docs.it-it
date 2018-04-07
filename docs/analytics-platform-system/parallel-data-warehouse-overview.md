---
title: Panoramica del Data Warehouse parallelo
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: In questo argomento viene illustrato il software di dispositivo e i componenti non strumento software di sistema della piattaforma Analitica.
ms.date: 01/05/2017
ms.topic: article
ms.assetid: db0c4a43-a66d-4c44-ab91-791c5785f71c
caps.latest.revision: 20
ms.openlocfilehash: 42fb92c30c0487603f2ad8e870886f25b4c1655a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="parallel-data-warehouse-overview"></a>Panoramica del Data Warehouse parallelo
In questo argomento viene illustrato il software di dispositivo e i componenti non strumento software di sistema della piattaforma Analitica.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Software di Data Warehouse parallelo](media/parallel-data-warehouse-software.png "software Parallel Data Warehouse")  
  
## <a name="sec1"></a>Software accessorio – eseguire Query di elaborazione e archiviazione dei dati utente  
  
### <a name="control-node"></a>Nodo di controllo  
Motore MPP  
Il motore MPP è il meccanismo alla base del sistema altamente parallelo di elaborazione (MPP). Esegue le operazioni seguenti:  
  
-   Crea piani di query parallele e coordina l'esecuzione parallela di query sui nodi di calcolo.  
  
-   Archivia e coordina i metadati e dati di configurazione per tutti i database.  
  
-   Gestisce l'autorizzazione e autenticazione di database di SQL Server PDW.  
  
-   Tiene traccia dello stato di hardware e software.  
  
### <a name="data-movement-service-dms"></a>Servizio di spostamento di dati (DMS)  
Servizio lo spostamento dei dati (DMS) fa parte del "segreto" di PDW. Esegue le operazioni seguenti:  
  
-   Trasferisce i dati da e verso i nodi di SQL Server PDW.  
  
-   Processi di operazioni che richiedono il trasferimento dei dati tra i nodi di query.  
  
-   Consente di migliorare le prestazioni delle query ottimizzando la velocità di trasferimento dei dati.  
  
### <a name="admin-console"></a>Console di amministrazione  
La Console di amministrazione è un'applicazione web che presenta la stato dello strumento, l'integrità e le informazioni sulle prestazioni.  
  
### <a name="configuration-manager"></a>Gestione configurazione  
Gestione configurazione (dwconfig.exe), è lo strumento che accessorio agli amministratori di configurare il sistema di piattaforma Analitica.  
  
### <a name="control-node-databases"></a>Controllo nodo database  
SQL Server gestisce tutti i database nel nodo di controllo.  
  
-   Lo scheletro di database che gestisce i metadati per tutti i database utente distribuita.  
  
-   TempDB contiene i metadati per tutte le tabelle temporanee di un utente tra il dispositivo.  
  
-   Master è la tabella master di SQL Server nel nodo di controllo.  
  
### <a name="compute-node"></a>Nodo di calcolo  
I nodi di calcolo sono unità di archiviazione e di elaborazione parallela dei dati. Che dispone di archiviazione collegata direttamente e usare SQL Server per gestire i dati utente.  
  
### <a name="data-movement-service-dms"></a>Servizio di spostamento di dati (DMS)  
Servizio lo spostamento dei dati (DMS) viene eseguito in ogni nodo di calcolo per eseguire le operazioni seguenti:  
  
-   Come parte dell'elaborazione di query parallele, DMS trasferire i dati da e verso altri nodi di Computer e il nodo di controllo.  
  
-   DMS, in esecuzione in ogni nodo di calcolo, riceve i caricamenti di dati in parallelo. Caricamento dei dati in parallelo direttamente dal server di caricamento per i nodi di calcolo  
  
-   DMS trasferisce i dati da ogni nodo di calcolo direttamente al server di backup.  
  
-   Usando PolyBase, DMS trasferisce i dati in e da un cluster Hadoop esterno o l'area di HDInsight nel dispositivo.  
  
### <a name="compute-node-databases"></a>Database di nodo di calcolo 
Ogni nodo di calcolo esegue un'istanza di SQL Server per l'elaborazione delle query e gestire i dati utente.  
  
## <a name="appliance-fabric"></a>Infrastruttura di dispositivo  
L'infrastruttura accessorio fornisce il sistema operativo, servizi e l'infrastruttura di rete per l'applicazione.  
  
### <a name="domain-controller"></a>Controller di dominio  
Servizi di dominio Active Directory (AD) (DS)  
Sistema della piattaforma Analitica esegue l'autenticazione tra i nodi del sistema della piattaforma Analitica e gestisce l'autenticazione di accesso con autenticazione di Windows di SQL Server PDW.  
  
Servizio DNS  
Windows servizio DNS (Domain Name) risolve i nomi di dominio in indirizzi IP per il dispositivo di sistema della piattaforma Analitica.  
  
### <a name="windows-deployment-service"></a>Servizi di distribuzione Windows  
Il servizio di distribuzione Windows (WDS) consente di distribuire il sistema operativo Windows Server nel dispositivo. Viene distribuita in ogni host e macchina virtuale tra il dispositivo.  
  
Il servizio DHCP crea gli indirizzi IP in modo che gli host all'interno del dominio applicazione l'accesso alla rete di dispositivo senza un indirizzo IP configurato in precedenza.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Sistema della piattaforma Analitica utilizza la virtualizzazione per ottenere la disponibilità elevata. Virtual Machine Manager ospita System Center per distribuire il sistema operativo negli host fisici.  
  
Windows Server Update Services (WSUS) per applicare o rimuovere gli aggiornamenti di Windows in tutti gli host e macchine virtuali.  
  
### <a name="windows-server"></a>Windows Server  
Tutti gli host e macchine virtuali nel dispositivo di eseguire il sistema operativo Windows Server.  
  
### <a name="failover-clustering"></a>Clustering di failover  
Clustering di Failover di Windows offre la possibilità di riavviare i processi in un host passivo nel caso in cui un host non riesce.  
  
### <a name="storage-spaces"></a>Spazi di archiviazione  
Spazi di archiviazione di Windows gestisce i dati utente come un pool di archiviazione per un piccolo gruppo di nodi di calcolo. Se un nodo di calcolo non riesce, i dati sono ancora accessibili tramite un altro nodo di calcolo nel gruppo.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server offre una soluzione di virtualizzazione affidabile e semplice. Sistema della piattaforma Analitica Usa virtualizzazione: per bilanciare le risorse della CPU e per fornire disponibilità elevata per i nodi PDW e un accessorio componenti dell'infrastruttura.  
  
## <a name="sec2"></a>Dati non relazionali
Tecnologia PolyBase consente di integrare dati di SQL Server PDW con dati Hadoop esterni. I dati di Hadoop possono essere archiviati in uno qualsiasi di queste origini dati Hadoop:  
  
-   Hortonworks per Linux o Windows Server  
  
-   Cloudera su Linux  
  
-   HDInsight in esecuzione sui punti di accesso  
  
-   HDInsight dati archiviati nel Blob di archiviazione di Azure  
  
## <a name="query-tools"></a>Strumenti di query   
  
Le query vengono scritti con Transact\-SQL modificati a seconda della natura MPP delle query. Tutte le query vengono inviate al nodo di controllo che genera un piano di query parallele per eseguire la query tra i nodi di calcolo.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools viene eseguito all'interno di Visual Studio ed è il nostro strumento GUI consigliato per l'invio di query in SQL Server PDW. È simile a SQL Server Management Studio, consentendo di passare tramite Esplora oggetti.  
  
Se si dispone già di Visual Studio, è possibile scaricare gli strumenti che è necessario gratuitamente. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>Strumento di Query della riga di comando SQLCMD  
SQLCMD è lo strumento da riga di comando di SQL Server per l'esecuzione di Transact\-SQL istruzioni e comandi del sistema. Questa funziona con SQL Server PDW ed è consigliato strumenti da riga di comando per l'esecuzione di query SQL Server PDW. Con sqlcmd è possibile eseguire Transact\-istruzioni SQL in modo interattivo dalla riga di comando, come un file batch o da Windows PowerShell.  
  
<!-- MISSING LINKS

If you don’t have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
È possibile utilizzare servizi di integrazione per query SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Server collegato  
Tramite una connessione di server collegato SQL Server, è possibile utilizzare SQL Server per inviare Transact\-istruzioni SQL in SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Strumenti di Business Intelligence
  
Analysis Services  
SQL Server PDW è un'origine dati valida per i modelli di PowerPivot per Excel e database di Analysis Services. Se si utilizza il provider OLE DB, è possibile configurare un cubo di Analysis Services per l'utilizzo di elaborazione analitica in linea multidimensionale (MOLAP) o archiviazione di elaborazione analitica in linea relazionale (ROLAP).  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>Generatore report  
È possibile utilizzare SQL Server PDW come origine dati SQL Server per i report di Reporting Services sviluppate utilizzando Generatore Report di SQL Server. È inoltre possibile utilizzare SQL Server PDW come un'origine di SQL Server per i modelli di report. Utilizzando Gestione Report o l'API del server di report, è possibile generare un modello da un database di SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot per Excel  
È possibile connettersi a SQL Server PDW con PowerPivot per Excel, un download gratuito che consente di espandere in modo significativo le funzionalità di analisi di dati di Excel.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Strumenti di caricamento 
  
### <a name="integration-services"></a>Integration Services  
Installare gli adapter di destinazione PDW specifici che consentono di utilizzare servizi di SQL ServerIntegration per caricare dati in SQL Server PDW.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>dwloader caricatore della riga di comando  
dwloader è uno strumento di caricamento della riga di comando che carica i dati in parallelo dal server di caricamento per i nodi di calcolo di SQL Server PDW. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase per l'integrazione di Hadoop  
Con la tecnologia PolyBase, è possibile caricare i dati non relazionali da un Hadoop Cluster in una tabella relazionale in SQL Server PDW. I dati di Hadoop possono trovarsi in un riferimento esterno Hadoop Cluster, l'area HDI sui punti di accesso o in un Blob di archiviazione di Azure.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Ripristino e Backup del database  
SQL Server PDW utilizza Transact\-SQL backup e ripristino dei database i comandi di backup e ripristino di database utente, in parallelo, in e da un server di backup. SQL Server PDW scrive il backup in una directory in una condivisione di file di Windows e quindi allo stesso modo ripristinare i dati da una condivisione di file di Windows.  
  
Per altre informazioni, vedere [pianificare per il Backup e il caricamento di Hardware](backup-and-loading-hardware.md) e [Panoramica del Backup e ripristino](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>Copia della tabella remota  
La funzionalità di copia della tabella remota consente di copiare tabelle dal database di SQL Server PDW ai database remoti di SMP SQL Server (non accessorio). Questo consente scenari di hub e spoke per SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Monitoraggio  
Sistema della piattaforma Analitica ha diversi modi per monitorare l'attività dello strumento  
  
### <a name="admin-console"></a>Console di amministrazione  
La Console di amministrazione consente di visualizzare lo stato corrente sullo stato dello strumento. Ciò viene eseguito come un'applicazione web nel nodo di controllo ed è accessibile tramite https.  
  
Per altre informazioni, vedere [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Viste di sistema  
La Console di amministrazione è basata sulle query di vista di sistema. È possibile eseguire query di viste di sistema per ottenere la parte specifica di informazioni che necessarie.  

Per altre informazioni, vedere [monitorare l'accessorio dalle viste di sistema usando &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Sono disponibili in System Center Operations Manager (SCOM) Management Pack per SQL Server PDW. 

Per configurare il dispositivo per SCOM, vedere [monitorare l'accessorio by Using System Center Operations Manager &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
