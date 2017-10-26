---
title: "Archivio BLOB remoto (RBS) e gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e6b39d1e5bda9e7426b92611df9f0ac0dfa3a495
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="remote-blob-store-rbs-and-always-on-availability-groups-sql-server"></a>Archivio BLOB remoti (RBS) e gruppi di disponibilità AlwaysOn (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] offre una soluzione di disponibilità elevata e di ripristino di emergenza per gli oggetti BLOB dell'[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][archivio BLOB remoto](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) (RBS, Remote Blob Store). [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] protegge tutti i metadati e gli schemi di RBS archiviati in un database di disponibilità replicandoli nelle repliche secondarie. Questo è il database del contenuto di SharePoint. In generale, tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] questi metadati di RBS vengono archiviati in modo indipendente dal BLOB.  
  
 La protezione dei dati dei BLOB dell'archivio BLOB remoti dipende dal percorso dell'archivio BLOB, come riportato di seguito:  
  
|Percorso dell'archivio BLOB|Possibilità di protezione dei dati BLOB tramite i gruppi di disponibilità|  
|-------------------------|-----------------------------------------------------|  
|Stesso database in cui sono contenuti i metadati di RBS (archiviato utilizzando un provider FILESTREAM remoto di RBS)|Sì|  
|Database diverso nella stessa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (archiviato utilizzando un provider FILESTREAM remoto di RBS)|Sì<br /><br /> È consigliabile inserire questo database nello stesso gruppo di disponibilità del database in cui sono contenuti i metadati di RBS.|  
|Database diverso in un'istanza differente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (archiviato utilizzando un provider FILESTREAM remoto di RBS)|Sì<br /><br /> Questo database deve trovarsi in un gruppo di disponibilità separato.|  
|Archivio BLOB di terze parti|No<br /><br /> Per proteggere questi dati BLOB, utilizzare i meccanismi di disponibilità elevata del provider dell'archivio BLOB.|  
  
##  <a name="Limitations"></a> Limitazioni  
  
-   I gestori RBS devono essere indirizzati alla replica primaria.  
  
##  <a name="Recommendations"></a> Indicazioni  
  
-   Utilizzare un listener del gruppo di disponibilità. Per altre informazioni, vedere [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md).  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   [Maintaining Remote BLOB Store](http://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (Gestione dell'archivio BLOB remoti) in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Documentazione online  
  
-   [Running RBS Maintainer](http://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (Esecuzione di Gestore RBS) (blog)  
  
-   [Configure Remote BLOB Storage (RBS) with the FILESTREAM provider (SharePoint 2010)](http://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (Configurare l'archivio BLOB remoti (RBS) con il provider FILESTREAM (SharePoint 2010)) (blog)  
  
## <a name="see-also"></a>Vedere anche  
 [Connettività client AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)   
 [Archivio BLOB remoto &#40;RBS&#41; &#40;SQL Server&#41;](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  

