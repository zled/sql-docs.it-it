---
title: "Un database secondario non è associato | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6041c31fa2c2e015980c8fc8a7875ddd1e53ac13
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="secondary-database-is-not-joined"></a>Un database secondario non è associato
    
## <a name="introduction"></a>Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Stato di join del database di disponibilità|  
|**Problema**|Il database secondario non è unito in join.|  
|**Category**|**Avviso**|  
|**Facet**|Database di disponibilità|  
  
## <a name="description"></a>Descrizione  
 Questi criteri consentono di controllare lo stato di join del database secondario, anche noto come "replica di database secondaria". I criteri sono in uno stato non integro quando la replica del set di dati non è unita in join. Altrimenti, sono in uno stato integro.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]le informazioni sulle cause e sulle soluzioni possibili sono disponibili in [Secondary database is not joined](http://go.microsoft.com/fwlink/p/?LinkId=220862) (Database secondario non unito in join) in TechNet Wiki.  
  
## <a name="possible-causes"></a>Possibili cause  
 Questo database secondario non è unito in join al gruppo di disponibilità. La configurazione di questo database secondario è incompleta.  
  
## <a name="possible-solution"></a>Possibile soluzione  
 Utilizzare Transact-SQL, PowerShell o SQL Server Management Studio per creare un join della replica secondaria al gruppo di disponibilità. Per altre informazioni sul join delle repliche secondarie ai gruppi di disponibilità, vedere [Creare un join di una replica secondaria a un gruppo di disponibilità (SQL Server)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utilizzare il Dashboard AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

