---
title: MSsub_identity_range (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 01008e8cd5bd740c333b483703ca5f27ab499c94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mssubidentityrange-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSsub_identity_range** tabella fornisce il supporto di gestione di identità intervallo per le sottoscrizioni. Questa tabella è archiviata nel database di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|ID della tabella la cui colonna Identity è gestita dalla replica.|  
|**intervallo**|**bigint**|Controlla le dimensioni dell'intervallo di valori Identity consecutivi che verrebbe assegnato nella sottoscrizione durante un intervento di regolazione.|  
|**last_seed**|**bigint**|Limite inferiore dell'intervallo corrente.|  
|**Soglia**|**int**|Valore percentuale che controlla quando l'agente di distribuzione assegna un nuovo intervallo di valori Identity. Quando la percentuale di valori specificato in *soglia* è utilizzato, l'agente di distribuzione crea un nuovo intervallo di valori identity.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
