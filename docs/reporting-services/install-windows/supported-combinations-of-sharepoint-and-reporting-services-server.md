---
title: Combinazioni supportate di SharePoint e Reporting Services Server | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 10/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
- rsSharePoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2e66cac836de44e8d2a9f23d88a600daaa26c0d1
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>Combinazioni supportate di SharePoint e Server di Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  Un server di report [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installato in modalità SharePoint richiede una versione di SharePoint e il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsSharePoint.msi) per i prodotti SharePoint, da installare nei server SharePoint.  In questo argomento vengono riepilogate le combinazioni supportate.  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Combinazioni supportate di componenti SharePoint e Reporting Services  
 Nella tabella seguente sono riepilogate le combinazioni supportate di server di report, componente aggiuntivo Reporting Services per prodotti SharePoint e prodotti SharePoint. Le combinazioni non elencate nella tabella seguente non sono supportate.  
  
### <a name="supported-combinations"></a>Combinazioni supportate  
  
||Server di report|Componente aggiuntivo|Versione di SharePoint|  
|-|-------------------|-------------|------------------------|  
|1|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2016|  
|2|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2013|  
|3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|  
|4|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|5|SQL Server 2012 SP3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e SQL Server 2012 SP3|SharePoint 2013|  
|6|SQL Server 2012 SP2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e SQL Server 2012 SP2|SharePoint 2013|  
|7|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|  
|8|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]*|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|9|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|  
|10|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|11|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|  
|12|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|  
|13|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|  
|14|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|  
|15|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|  
  
 *Eccezione: l'integrazione di Power View non è supportata.  
  
 Per i collegamenti alle pagine di download del componente aggiuntivo, vedere [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
 **Note aggiuntive:**  

- Assicurarsi di aggiornare tutti i server SharePoint all'interno della farm. Sono inclusi i server front-end Web e i server applicazioni.

-   Per il supporto di SharePoint 2016, inclusa l'integrazione di Power View, sono necessari il server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e la versione del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] di SQL Server 2016 o versione successiva.  

-   Per il supporto di SharePoint 2013, inclusa l'integrazione di Power View, sono necessari il server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e la versione del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] di SQL Server 2012 SP1 o versione successiva.  
  
-   Power View è stato introdotto in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Pertanto, per l'integrazione di Power View con SharePoint 2010 è necessario [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o le versioni successive del componente aggiuntivo.  
  
-   Il componente aggiuntivo di SQL Server 2008 R2 non è supportato dai server di report SQL Server 2012 o versione successiva. Tramite il programma di installazione essenziale di SharePoint 2010 viene installato automaticamente il componente aggiuntivo di SQL Server 2008 R2. È necessario disinstallarlo prima di installare le versioni più recenti del componente aggiuntivo. L'aggiornamento sul posto del componente aggiuntivo non è supportato.  
  
-   **Aggiornamento:** non è possibile eseguire l'aggiornamento sul posto di SharePoint 2010 con il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a SharePoint 2013. Per SharePoint 2013 è necessario [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] o versioni successive del componente aggiuntivo e del server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per altre informazioni sull'aggiornamento, vedere [Eseguire l'aggiornamento e la migrazione di Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  


