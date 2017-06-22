---
title: Eseguire la pulizia dei metadati di merge (programmazione Transact-SQL della replica) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 847a42192c396dcda29ed214e279f00d991a4eb0
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>Pulizia dei metadati di merge (programmazione Transact-SQL della replica)
  La rimozione dei metadati della replica di tipo merge viene eseguita periodicamente dall'agente di merge in base all'impostazione di memorizzazione per la pubblicazione. Nel server di pubblicazione e nel Sottoscrittore ciò avviene nelle tabelle di sistema [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)e [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) . È inoltre possibile rimuovere i dati in tali tabelle a livello di programmazione utilizzando le stored procedure di replica.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Per pulire manualmente i metadati di merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md).  
  
2.  (Facoltativo) Tenere presente il numero di righe rimosse nel passaggio 1 dalle tabelle di sistema [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)e [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) . Tali valori sono restituiti rispettivamente nei parametri di output **@num_genhistory_rows**, **@num_contents_rows**e **@num_tombstone_rows** .  
  
3.  Ripetere i passaggi 1 e 2 nel Sottoscrittore per eseguire la pulizia dei metadati nel database di sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Scadenza e disattivazione delle sottoscrizioni](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
