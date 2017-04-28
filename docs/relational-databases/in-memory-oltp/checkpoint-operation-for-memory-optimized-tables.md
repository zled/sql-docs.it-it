---
title: Operazione su checkpoint per le tabelle con ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 04176fec3cc190cba1a89a11780d84561512431a
ms.lasthandoff: 04/11/2017

---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>Operazione su checkpoint per le tabelle con ottimizzazione per la memoria
  Un checkpoint deve essere eseguito periodicamente per consentire l'avanzamento dei dati con ottimizzazione per la memoria nei file di dati e differenziali nella parte attiva del log delle transazioni. Il checkpoint consente il ripristino o il recupero delle tabelle con ottimizzazione per la memoria all'ultimo checkpoint eseguito correttamente, quindi viene applicata la parte attiva del log delle transazioni per aggiornare le tabelle con ottimizzazione per la memoria in modo da completare il recupero. L'operazione di checkpoint per le tabelle basate su disco e quella per le tabelle con ottimizzazione per la memoria sono distinte. Di seguito vengono descritti diversi scenari e viene indicato il comportamento del checkpoint per le tabelle basate su disco e per quelle con ottimizzazione per la memoria:  
  
## <a name="manual-checkpoint"></a>Checkpoint manuale  
 Quando si crea un checkpoint manuale, il checkpoint per le tabelle basate su disco e per quelle con ottimizzazione per la memoria viene chiuso. Il file di dati attivo viene chiuso anche se è riempito parzialmente.  
  
## <a name="automatic-checkpoint"></a>Checkpoint automatico  
 Il checkpoint automatico viene implementato in modo diverso per le tabelle basate su disco e per le tabelle con ottimizzazione per la memoria a causa dei modi diversi in cui i dati sono resi persistenti.  
  
 Per le tabelle basate su disco, viene acquisito un checkpoint automatico in base all'opzione di configurazione dell'intervallo di recupero. Per altre informazioni, vedere [Modificare il tempo di recupero di riferimento di un database &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)).  
  
 Per le tabelle con ottimizzazione per la memoria, viene acquisito un checkpoint automatico quando le dimensioni del file di log delle transazioni superano 1,5 GB dall'ultimo checkpoint. Questa dimensione di 1,5 GB include i record dei log delle transazioni sia per le tabelle basate su disco sia per quelle con ottimizzazione per la memoria.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
