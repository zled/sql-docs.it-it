---
title: sys.dm_os_windows_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6f6669704242a780d947dc271cb81724429992a
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmoswindowsinfo-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga in cui sono visualizzate le informazioni sulla versione del sistema operativo Windows.  
  
  Si applica solo a SQL Server in esecuzione su Windows. Per visualizzare informazioni relative al simili per SQL Server in esecuzione in un host non Windows, ad esempio Linux, usare [sys.dm_os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Per Windows, restituisce il numero di versione. Per un elenco di valori e descrizioni, vedere [versione del sistema operativo (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx). Non può essere NULL.|  
|**windows_service_pack_level**|**nvarchar(256)**| Per Windows, restituisce il numero di service pack. Non può essere NULL. |  
|**windows_sku**|**int**|Per Windows, viene restituito l'ID di unità mantenendo Stock Windows (SKU). Per un elenco degli ID SKU e descrizioni, vedere [funzione GetProductInfo](http://msdn.microsoft.com/library/ms724358.aspx). È NULLable. |  
|**os_language_version**|**int**| Per Windows, restituisce l'identificatore di impostazioni locali (LCID) di Windows del sistema operativo. Per un elenco di valori LCID e descrizioni, vedere [ID impostazioni locali assegnati da Microsoft](http://go.microsoft.com/fwlink/?LinkId=208080). Non può essere NULL.|  
  
  
## <a name="permissions"></a>Autorizzazioni  
Per impostazione predefinita, l'autorizzazione SELECT per Sys.dm os_sys_info viene concessa al ruolo public. Se è stato revocato, richiede l'autorizzazione VIEW SERVER STATE nel server.  

## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni
Per visualizzare informazioni relative per SQL in esecuzione in un host non Windows, ad esempio Linux, usare [sys.dm_os_host_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce tutte le colonne di **Sys.dm os_sys_info** visualizzazione.  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 Set di risultati di esempio:  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  

