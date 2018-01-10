---
title: Ospitare un database del server di report in un cluster di failover di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: "5"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: e3ae4f8b7a1abe9950ce2110da6914cc2b401438
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Ospitare un database del server di report in un cluster di failover di SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre supporto per il clustering di failover, per consentire l'utilizzo di più dischi per una o più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il clustering di failover è supportato solo per il database del server di report e non è possibile eseguire il servizio Windows ReportServer o il servizio Web come parte di un cluster di failover.  
  
 Per ospitare un database del server di report in un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario che il cluster sia già installato e configurato. È quindi possibile selezionare il cluster di failover come nome del server quando si crea il database del server di report nella pagina Impostazione database dello strumento Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Sebbene il servizio Windows ReportServer non possa essere eseguito come parte di un cluster di failover, è possibile installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in un computer in cui è installato un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il server di report viene eseguito indipendentemente dal cluster di failover. Se si installa un server di report in un computer che fa parte di un'istanza di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , non è necessario utilizzare il cluster di failover per il database del server di report, ma, per ospitare il database, è possibile utilizzare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diversa.  
  
## <a name="see-also"></a>Vedere anche  
 [Database del server di report &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Creare un database del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)  
  
  
