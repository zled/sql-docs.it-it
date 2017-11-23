---
title: database_scoped_configurations (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords: sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
caps.latest.revision: "13"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 70b0f5c2ecb1f15828d5ac1c219033c337bb3a8f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni configurazione. 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|ID dell'opzione di configurazione.|  
|**name**|**nvarchar(60)**|Il nome dell'opzione di configurazione. Per informazioni sulle possibili configurazioni, vedere [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**valore**|**SQLVARIANT**|Il valore impostato per questa opzione di configurazione per la replica primaria.|  
|**value_for_secondary**|**SQLVARIANT**|Il valore impostato per questa opzione di configurazione per le repliche secondarie.|  
  
##  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene restituito NULL come valore per **value_for_secondary**, ciò significa che il database secondario è impostato su primario.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
