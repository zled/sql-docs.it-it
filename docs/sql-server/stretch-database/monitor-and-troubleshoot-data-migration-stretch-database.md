---
title: Monitorare e risolvere i problemi relativi alla migrazione dei dati (Stretch Database) | Microsoft Docs
ms.custom: 
ms.date: 06/14/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: stretch-database
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, monitoring
- monitoring Stretch Database
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a81763ab7207da8fa21b61c9f853ad51439ed6e
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="monitor-and-troubleshoot-data-migration-stretch-database"></a>Monitorare e risolvere i problemi relativi alla migrazione dei dati (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Per monitorare la migrazione dei dati in Monitoraggio di Stretch Database, selezionare **Attività | Stretch | Monitoraggio** per un database in SQL Server Management Studio.  
  
## <a name="check-the-status-of-data-migration-in-the-stretch-database-monitor"></a>Controllare lo stato della migrazione dei dati in Stretch Database Monitor  
 Selezionare **Attività | Stretch | Monitoraggio** per un database in SQL Server Management Studio per aprire Monitoraggio di Stretch Database e monitorare la migrazione dei dati.  
  
-   Nella parte superiore della finestra di monitoraggio vengono visualizzate informazioni generali sul database SQL Server abilitato per l'estensione e sul database Azure remoto.  
  
-   Nella parte inferiore viene visualizzato lo stato della migrazione dei dati per ogni tabella abilitata per l'estensione nel database.  
  
 ![Monitoraggio di Stretch Database](../../sql-server/stretch-database/media/stretch-monitor.PNG "Monitoraggio di Stretch Database")  
  
##  <a name="Migration"></a> Controllare lo stato della migrazione dei dati in una DMV  
 Aprire la DMV **sys.dm_db_rda_migration_status** per visualizzare il numero di batch e righe di dati di cui è stata eseguita la migrazione. Per altre informazioni, vedere [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
##  <a name="Firewall"></a> Risolvere i problemi relativi alla migrazione dei dati  
 **Non viene eseguita la migrazione in Azure delle righe dalla tabella abilitata per l'estensione. Qual è il problema?**  
 Esistono diversi problemi che possono influire sulla migrazione. Verificare quanto segue.  
  
-   Verificare la connettività di rete per il computer SQL Server.  
  
-   Verificare che il firewall di Azure non impedisca a SQL Server di connettersi all'endpoint remoto.  
  
-   Verificare lo stato dell'ultimo batch nella DMV **sys.dm_db_rda_migration_status** . Se si è verificato un errore, controllare i valori error_number, error_state, ed error_severity per il batch.  
  
    -   Per altre informazioni sulla vista, vedere [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
    -   Per altre informazioni sul contenuto di un messaggio di errore di SQL Server, vedere [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md).  
  
 **Il firewall di Azure blocca le connessioni dal server locale.**  
 Può essere necessario aggiungere una regola nelle impostazioni del firewall di Azure del server di Azure per consentire a SQL Server di comunicare con il server remoto di Azure.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione e risoluzione dei problemi di Stretch Database](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
  
