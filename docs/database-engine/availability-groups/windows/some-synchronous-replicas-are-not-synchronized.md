---
title: Alcune repliche sincrone non sono sincronizzate | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: availability-groups
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c303ef171fecf9d6aac2c6e9462129ffc65606f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Alcune repliche sincrone non sono sincronizzate
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Stato di sincronizzazione dei dati delle repliche sincrone|  
|**Problema**|Alcune repliche sincrone non sono sincronizzate.|  
|**Category**|**Avviso**|  
|**Facet**|gruppo di disponibilità|  
  
## <a name="description"></a>Description  
 Questi criteri consentono di eseguire il rollup dello stato di sincronizzazione dei dati di tutte le repliche di disponibilità e di verificare tutte le repliche di disponibilità che non sono nello stato di sincronizzazione previsto. I criteri sono in uno stato non integro se una replica asincrona è in uno stato NON IN SINCRONIZZAZIONE e una replica sincrona è in uno stato NON SINCRONIZZATO. Altrimenti, i criteri sono in uno stato integro.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili nella pagina relativa ad [alcune repliche sincrone non sono sincronizzate](http://go.microsoft.com/fwlink/p/?LinkId=220853) su Wiki di TechNet.  
  
## <a name="possible-causes"></a>Possibili cause  
 In questo gruppo di disponibilità, almeno una replica sincrona non è attualmente sincronizzata. Lo stato di sincronizzazione della replica potrebbe essere SINCRONIZZAZIONE IN CORSO o NON IN SINCRONIZZAZIONE.  
  
## <a name="possible-solution"></a>Possibile soluzione  
 Utilizzare lo stato dei criteri della replica di disponibilità per trovare quella con lo stato di sincronizzazione non corretto e risolvere il problema.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usare il dashboard Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
