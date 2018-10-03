---
title: MSagentparameterlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSagentparameterlist_TSQL
- MSagentparameterlist
dev_langs:
- TSQL
helpviewer_keywords:
- Msagentparameterlist system table
ms.assetid: 4ea571a0-078d-4e13-95ee-f3d4bbd4dfb2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a765732f4d44ef31ed947a10d3b9449e261d1a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760929"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSagentparameterlist** tabella contiene le informazioni sui parametri dell'agente di replica e viene usata per specificare i parametri che è possibile impostare per un tipo di agente specificato. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Tipo di agente:<br /><br /> **1** = agente snapshot.<br /><br /> **2** = agente di lettura log.<br /><br /> **3** = agente di distribuzione.<br /><br /> **4** = agente di merge.<br /><br /> **9** = agente di lettura coda.|  
|**parameter_name**|**sysname**|Nome di un parametro valido dell'agente.|  
|**default_value**|**nvarchar(4000)**|Valore predefinito del parametro dell'agente, dove NULL indica che non esiste alcun valore predefinito.|  
|**MIN_VALUE**|**int**|Imposta il limite inferiore per il parametro dell'agente, dove NULL indica che non esiste alcun limite inferiore.|  
|**MAX_VALUE**|**int**|Imposta il limite superiore per il parametro dell'agente, dove NULL indica che non esiste alcun limite superiore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
