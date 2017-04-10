---
title: "Replica di disponibilit&#224; non unita in join | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.arp4joined.issues.f1"
helpviewer_keywords: 
  - "Gruppi di disponibilità [SQL Server], criteri"
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# Replica di disponibilit&#224; non unita in join
    
## Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Stato di join della replica di disponibilità|  
|**Problema**|La replica di disponibilità non è unita in join.|  
|**Category**|**Avviso**|  
|**Facet**|Replica di disponibilità|  
  
## Descrizione  
 Tramite questi criteri viene controllato lo stato del join della replica di disponibilità. Lo stato dei criteri non è integro quando la replica di disponibilità viene aggiunta al gruppo di disponibilità, ma non ne viene creato il join correttamente. Altrimenti, sono in uno stato integro.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili nella pagina relativa alla situazione in cui [la replica di disponibilità non è unita in join](http://go.microsoft.com/fwlink/p/?LinkId=220859) su Wiki di TechNet.  
  
## Possibili cause  
 La replica secondaria non è unita in join al gruppo di disponibilità. Affinché una replica di disponibilità venga correttamente unita in join al gruppo di disponibilità, lo stato del join deve essere Istanza autonoma unita in join (1) o Cluster di failover unito in join (2).  
  
## Possibile soluzione  
 Utilizzare Transact-SQL, PowerShell o SQL Server Management Studio per creare un join della replica secondaria al gruppo di disponibilità. Per altre informazioni sul join delle repliche secondarie ai gruppi di disponibilità, vedere [Creare un join di una replica secondaria a un gruppo di disponibilità (SQL Server)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx).  
  
## Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utilizzare il Dashboard AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  