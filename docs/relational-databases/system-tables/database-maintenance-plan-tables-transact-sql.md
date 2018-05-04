---
title: Database delle tabelle di piano di manutenzione (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database maintenance plans [SQL Server]
- maintenance plans [SQL Server], system tables
- system tables [SQL Server], database maintenance plans
ms.assetid: f264554c-5514-4df2-aadb-6dcdc2dfcfea
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fc5339d116584589400327e0e5173c47d6274099
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="database-maintenance-plan-tables-transact-sql"></a>Tabelle dei piani di manutenzione dei database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gli argomenti riportati in questa sezione descrivono le tabelle di sistema in cui sono archiviate le informazioni utilizzate dai piani di manutenzione dei database. In queste tabelle sono incluse le informazioni relative alle istanze aggiornate da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)  
 Include una o più righe per ogni database a cui è associato un piano di manutenzione del database aggiornato.  
  
 [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)  
 Contiene una riga per ogni azione eseguita del piano di manutenzione del database aggiornato.  
  
 [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)  
 Include una riga per ogni processo del piano di manutenzione del database aggiornato.  
  
 [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)  
 Include una riga per ogni piano di manutenzione del database aggiornato.  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
