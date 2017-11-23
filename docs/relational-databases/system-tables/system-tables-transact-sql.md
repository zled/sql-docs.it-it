---
title: Tabelle di sistema (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- status information [SQL Server]
- tables [SQL Server], system tables
- information retrieval [SQL Server]
- status information [SQL Server], system tables
- system information [SQL Server]
- system tables [SQL Server]
- system tables [SQL Server], about system tables
- system tables [SQL Server], retrieving information from
- retrieving system table information
ms.assetid: 56b8ad51-930c-4e5c-8d99-8c939d5b70ac
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7d2fe1cedb18dd3b2cfd5b6375a61a328178d6f7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="system-tables-transact-sql"></a>Tabelle di sistema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Negli argomenti di questa sezione vengono descritte le tabelle di sistema disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Gli utenti non devono modificare direttamente le tabelle di sistema, ad esempio con istruzioni DELETE, UPDATE o INSERT oppure con trigger definiti dall'utente.  
  
 È consentito fare riferimento alle colonne documentate delle tabelle di sistema. Molte colonne tuttavia non sono documentate. È pertanto consigliabile non creare applicazioni che eseguono query dirette nelle colonne non documentate. Per recuperare informazioni archiviate nelle tabelle di sistema, è necessario che le applicazioni utilizzino i componenti seguenti:  
  
-   Stored procedure di sistema  
  
-   Istruzioni e funzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   Oggetti SMO ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects)  
  
-   Oggetti RMO (Replication Management Objects)  
  
-   Funzioni del catalogo delle API per i database  
  
 Questi componenti compongono un'API pubblicata per il recupero delle informazioni sul sistema da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La compatibilità di tali componenti viene mantenuta nelle diverse versioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Il formato delle tabelle di sistema dipende dalla struttura interna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e può variare nelle diverse versioni. Può pertanto essere necessario apportare modifiche alle applicazioni che hanno accesso diretto a colonne non documentate delle tabelle di sistema in modo che possano accedere alle versioni successive di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Gli argomenti relativi alle tabelle di sistema sono organizzati in base alle aree funzionali riportate di seguito.  
  
|||  
|-|-|  
|[Backup e ripristino tabelle &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)|[Tabelle di log shipping &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)|  
|[Change Data Capture tabelle &#40; Transact-SQL &#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)|[Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)|  
|[Tabelle di piano di manutenzione di database &#40; Transact-SQL &#41;](../../relational-databases/system-tables/database-maintenance-plan-tables-transact-sql.md)|[Tabelle di SQL Server Agent &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)|  
|[Estesi eventi tabelle &#40; SQL Server Transact-SQL &#41;](http://msdn.microsoft.com/library/6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)|[Sys. sysoledbusers &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-sysoledbusers-transact-sql.md)|  
|[Tabelle &#40; di Integration Services Transact-SQL &#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)|[systranschemas &#40; Transact-SQL &#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di compatibilità &#40; Transact-SQL &#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
