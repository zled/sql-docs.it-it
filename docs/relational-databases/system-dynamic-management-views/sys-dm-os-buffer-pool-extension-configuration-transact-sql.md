---
title: sys.dm_os_buffer_pool_extension_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_buffer_pool_extension_configuration
- sys.dm_os_buffer_pool_extension_configuration_TSQL
- dm_os_buffer_pool_extension_configuration_TSQL
- sys.dm_os_buffer_pool_extension_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_pool_extension_configuration dynamic management view
ms.assetid: d52cc481-4d29-4f33-b63d-231ec35d092f
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ecc569a1f112bba0ec49c46da77c1dbc29fcddab
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020019"
---
# <a name="sysdmosbufferpoolextensionconfiguration-transact-sql"></a>sys.dm_os_buffer_pool_extension_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni di configurazione sull'estensione del pool di buffer in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Restituisce una riga per ogni file di estensione del pool di buffer.  
  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|percorso|**nvarchar**(256)|Percorso e nome del file della cache di estensione del pool di buffer. Ammette valori Null.|  
|file_id|**int**|ID del file di estensione del pool di buffer. Non ammette i valori Null.|  
|state|**int**|Stato della funzionalità di estensione del pool di buffer. Non ammette i valori Null.<br /><br /> 0 - Estensione pool di buffer disabilitata<br /><br /> 1 - Disabilitazione estensione pool di buffer<br /><br /> 2: riservato per utilizzi futuri<br /><br /> 3 - Abilitazione estensione pool di buffer<br /><br /> 4 - Riservato per utilizzi futuri<br /><br /> 5 - Estensione pool di buffer abilitata|  
|state_description|**nvarchar**(60)|Descrive lo stato della funzionalità di estensione del pool di buffer. Ammette i valori Null.<br /><br /> 0 = BUFFER POOL EXTENSION DISABLED<br /><br /> 1 = BUFFER POOL EXTENSION ENABLED|  
|current_size_in_kb|**bigint**|Dimensione corrente del file di estensione del pool di buffer. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-configuration-buffer-pool-extension-information"></a>A. Restituzione delle informazioni di configurazione sull'estensione del pool di buffer  
 Nell'esempio seguente vengono restituite tutte le colonne dalla DMV sys.dm_os_buffer_pool_extension_configuration.  
  
```sql  
SELECT path, file_id, state, state_description, current_size_in_kb  
FROM sys.dm_os_buffer_pool_extension_configuration;  
```  
  
### <a name="b-returning-the-number-of-cached-pages-in-the-buffer-pool-extension-file"></a>B. Restituzione del numero di pagine memorizzate nella cache di estensione del pool di buffer  
 Nell'esempio seguente viene restituito il numero delle pagine memorizzate nella cache di ogni file di estensione del pool di buffer.  
  
```sql  
SELECT COUNT(*) AS cached_pages_count  
FROM sys.dm_os_buffer_descriptors  
WHERE is_in_bpool_extension <> 0  
;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del Pool di buffer](../../database-engine/configure-windows/buffer-pool-extension.md)   
 [sys.dm_os_buffer_descriptors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-descriptors-transact-sql.md)  
  
  
