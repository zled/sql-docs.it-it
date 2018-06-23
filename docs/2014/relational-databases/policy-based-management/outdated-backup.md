---
title: Backup obsoleto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 702d49974dc77aad02b9cf79a1ebeff2ed03dc25
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156440"
---
# <a name="outdated-backup"></a>Backup obsoleto
  Questa regola consente di controllare se per un database siano disponibili backup recenti. La pianificazione di backup frequenti è importante per la protezione dei database dalla perdita di dati dovuta a errori diversi. La frequenza più appropriata per il backup dei dati dipende dal modello di recupero del database, dalle esigenze aziendali relative alla possibile perdita di dati e dalla frequenza con cui viene aggiornato il database. In un database aggiornato di frequente, l'esposizione alla perdita di dati aumenta piuttosto rapidamente tra i backup.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 È consigliabile eseguire backup sufficientemente frequenti per proteggere i database dalla perdita di dati.  
  
 Il modello di recupero con registrazione minima e il modello di recupero con registrazione completa richiedono entrambi il backup dei dati. Per entrambi i modelli, è possibile aggiungere ai backup completi backup differenziali per ridurre in modo efficiente il rischio di perdita di dati.  
  
 Per un database che utilizza il modello di recupero con registrazione completa, è consigliabile eseguire frequenti backup del log. Per un database di produzione che contiene dati molto importanti, è in genere consigliabile eseguire backup del log ogni quindici minuti.  
  
> [!NOTE]  
>  Il metodo consigliato per la pianificazione dei backup è un piano di manutenzione del database.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Backup e ripristino di database di sistema &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Modelli di recupero &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)  
  
 [Creare un backup differenziale del database &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [Creazione di un backup completo del database &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [Piani di manutenzione](../maintenance-plans/maintenance-plans.md)  
  
 [Backup di log delle transazioni &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  