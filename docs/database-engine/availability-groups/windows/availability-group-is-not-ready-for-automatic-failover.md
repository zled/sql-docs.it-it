---
title: "Il gruppo di disponibilit&#224; non &#232; pronto per il failover automatico | Microsoft Docs"
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
  - "sql13.swb.agdashboard.agp3autofailover.issues.f1"
helpviewer_keywords: 
  - "Gruppi di disponibilità [SQL Server], criteri"
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# Il gruppo di disponibilit&#224; non &#232; pronto per il failover automatico
    
## Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Conformità del gruppo di disponibilità al failover automatico|  
|**Problema**|Il gruppo di disponibilità non è pronto per il failover automatico.|  
|**Category**|**Critico**|  
|**Facet**|Gruppo di disponibilità|  
  
## Descrizione  
 Con questi criteri è possibile verificare che nel gruppo di disponibilità sia disponibile almeno una replica secondaria pronta per il failover. I criteri si trovano in uno stato non integro e viene generato un avviso quando il failover della replica primaria è automatico, ma nessuna delle repliche secondarie nel gruppo di disponibilità è pronta per il failover.  
  
 I criteri sono in uno stato integro quando almeno una replica secondaria è pronta per il failover automatico.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili nella pagina relativa alla situazione in cui il [gruppo di disponibilità non è pronto per il failover automatico](http://go.microsoft.com/fwlink/p/?LinkId=220851)su Wiki di TechNet.  
  
## Possibili cause  
 Il gruppo di disponibilità non è pronto per il failover automatico. La replica primaria viene configurata per il failover automatico; tuttavia, la replica secondaria non è pronta per il failover automatico. La replica secondaria configurata per il failover automatico potrebbe non essere disponibile o il relativo stato della sincronizzazione dei dati è attualmente NON SINCRONIZZATO.  
  
## Possibili soluzioni  
 Di seguito sono riportate le possibili soluzioni a questo problema:  
  
-   Verificare che almeno una replica secondaria venga configurata come failover automatico. Se non è disponibile alcuna replica secondaria configurata come failover automatico, aggiornare la configurazione di una replica secondaria affinché rappresenti la destinazione del failover automatico con commit sincrono.  
  
-   Utilizzare i criteri per verificare che i dati siano in uno stato di sincronizzazione e che la destinazione del failover automatico sia SINCRONIZZATO, quindi risolvere il problema della replica di disponibilità.  
  
## Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usare il Dashboard AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  