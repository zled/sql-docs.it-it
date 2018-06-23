---
title: Ripristinare un database e associarlo a un pool di risorse | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: d2aea0f1006790a8fb86805a37ca39188cc6e14c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171025"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a>Ripristinare un database e associarlo a un pool di risorse
  Anche se si dispone di memoria sufficiente per ripristinare un database con tabelle ottimizzate per la memoria, è possibile seguire le procedure consigliate e associare il database a un pool di risorse denominato. Poiché il database deve essere già presente per poter essere associato al pool, il ripristino del database è un processo costituito da più passaggi. In questo argomento viene illustrato tale processo.  
  
## <a name="restoring-a-database-with-memory-optimized-tables"></a>Ripristino di un database con tabelle ottimizzate per la memoria  
 I passaggi seguenti consentono di ripristinare completamente il database IMOLTP_DB e di associarlo al pool Pool_IMOLTP.  
  
1.  [Ripristino con NORECOVERY](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_norecovery)  
  
2.  [Creazione del pool di risorse](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_createpool)  
  
3.  [Associazione del database e del pool di risorse](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_bind)  
  
4.  [Ripristino con RECOVERY](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_recovery)  
  
5.  [Monitoraggio delle prestazioni del pool di risorse](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_monitor)  
  
###  <a name="bkmk_NORECOVERY"></a> Ripristino con NORECOVERY  
 Il ripristino di un database con NORECOVERY comporta la creazione del database e il ripristino dell'immagine disco senza l'uso di memoria.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
###  <a name="bkmk_createPool"></a> Creazione del pool di risorse  
 Il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente consente di creare un pool di risorse denominato Pool_IMOLTP con il 50% della memoria disponibile per l'uso.  Dopo la creazione del pool, Resource Governor viene riconfigurato in modo da includere Pool_IMOLTP.  
  
```tsql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
###  <a name="bkmk_bind"></a> Associazione del database e del pool di risorse  
 Usare la funzione di sistema `sp_xtp_bind_db_resource_pool` per associare il database al pool di risorse. La funzione accetta due parametri: il nome del database seguito dal nome del pool di risorse.  
  
 Con l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente viene definita un'associazione del database IMOLTP_DB al pool di risorse Pool_IMOLTP. L'associazione non diventa effettiva finché non viene completato il passaggio successivo.  
  
```tsql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
###  <a name="bkmk_RECOVERY"></a> Ripristino con RECOVERY  
 Quando si ripristina il database con recupero, il database viene portato online e vengono ripristinati tutti i dati.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
###  <a name="bkmk_Monitor"></a> Monitoraggio delle prestazioni del pool di risorse  
 Dopo l'associazione del database al pool di risorse denominato e il ripristino con RECOVERY, monitorare l'oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Statistiche del pool di risorse. Per ulteriori informazioni, vedere [SQL Server - Oggetto Statistiche del pool di risorse](../performance-monitor/sql-server-resource-pool-stats-object.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di un database con tabelle con ottimizzazione per la memoria a un pool di risorse](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)   
 [SQL Server - Oggetto Statistiche del pool di risorse](../performance-monitor/sql-server-resource-pool-stats-object.md)   
 [sys.dm_resource_governor_resource_pools](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
