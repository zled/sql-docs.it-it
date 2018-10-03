---
title: Funzionalità deprecate di Master Data Services in SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 89d2d5d8cee989d6541cdb256b0a7aaf48d00162
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142212"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a>Funzionalità deprecate di Master Data Services in SQL Server 2014
  In questo argomento verranno descritte le funzionalità deprecate di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ancora disponibili in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Tali funzionalità verranno rimosse a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È consigliabile non usare le funzionalità deprecate nelle nuove applicazioni.  
  
## <a name="staging-process"></a>Processo di gestione temporanea  
 Il processo di gestione temporanea utilizzato in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] non è più disponibile nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ; tuttavia è ancora disponibile in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Gli errori di gestione temporanea dal processo di gestione temporanea [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] non sono più visualizzati nell'interfaccia utente. I codici di errore popolati durante il processo di staging sono ancora disponibili nelle tabelle di staging e sono disponibili qui: [ http://msdn.microsoft.com/library/ff487022.aspx ](http://msdn.microsoft.com/library/ff487022.aspx).  
  
 Le tabelle di staging (tblStgMember, tblStgMemberAttribute e tblStgRelationship) ancora sono disponibili nel database. La stored procedure utilizzata per iniziare il processo di gestione temporanea (mdm.udpStagingSweep) è ancora disponibile nel database.  
  
 Sono ancora disponibili i metodi del servizio Web che richiamano il processo di gestione temporanea.  
  
 Il set dell'intervallo di gestione temporanea in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] si applica al processo di gestione temporanea in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] e in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Un nuovo, più elevato processo di gestione temporanea delle prestazioni è stato implementato in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Per altre informazioni, vedere [Importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
## <a name="metadata"></a>Metadati  
 Sebbene il modello di metadati è ancora visualizzato nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , non deve essere utilizzato. Verrà rimosso in una versione futura. Gli Utenti possono visualizzare anche più metadati nell'area funzionale **Esplora** ed è possibile creare più versioni del modello di metadati.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di Master Data Services non più supportate in SQL Server 2014](discontinued-master-data-services-features.md)  
  
  
