---
title: Configurare i parametri per la raccolta dati (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: data-collection
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 35f12b5199894db04613c963d36442d3ecd993ba
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Configurazione dei parametri per la raccolta dati (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Prima di creare un set di raccolta personalizzato è necessario configurare i parametri della raccolta dati. A tale scopo, utilizzare le stored procedure fornite con l'agente di raccolta dati. Il completamento di questa attività comporta l'utilizzo dell'editor di query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per effettuare la procedura descritta di seguito.  
  
> [!NOTE]  
>  I parametri per la raccolta dati possono essere configurati una volta sola. Dopo la configurazione, tali parametri vengono utilizzati per qualsiasi set di raccolta aggiuntivo creato.  
  
### <a name="configure-data-collection-parameters"></a>Configurazione dei parametri per la raccolta dati  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al database in cui si desidera creare un set di raccolta personalizzato.  
  
2.  Nell'editor di query eseguire le istruzioni indicate di seguito.  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
