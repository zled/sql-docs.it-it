---
title: MSdistribution_status (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistribution_status_TSQL
- MSdistribution_status
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_status view
ms.assetid: 90d447de-3a4a-4f3e-aeab-e8fff6348361
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7851aa5a7fe383d4d97304bbad2731694e59e1a3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msdistributionstatus-transact-sql"></a>MSdistribution_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdistribution_status** visualizzazione espone informazioni aggiuntive sui comandi di stato nel database di distribuzione. Questa vista è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Identifica un articolo.|  
|**agent_id**|**int**|Identificatore dell'agente di replica.|  
|**UndelivCmdsInDistDB**|**int**|Numero di comandi con recapito in sospeso ai Sottoscrittori.|  
|**DelivCmdsInDistDB**|**int**|Numero di comandi recapitati ai Sottoscrittori.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
