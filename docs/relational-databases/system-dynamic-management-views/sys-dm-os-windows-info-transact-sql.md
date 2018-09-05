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
ms.openlocfilehash: 27896207321b39ef37d4317a6ca8c4e332ccee55
ms.sourcegitcommit: 2a47e66cd6a05789827266f1efa5fea7ab2a84e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43348139"
---
# <a name="sysdmoswindowsinfo-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga in cui sono visualizzate le informazioni sulla versione del sistema operativo Windows.  
  
  Si applica solo a SQL Server in esecuzione su Windows. Per visualizzare informazioni simili per SQL Server in esecuzione in un host non Windows, ad esempio Linux, usare [DM os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Per Windows, restituisce il numero di versione. Per un elenco di valori e descrizioni, vedere [versione del sistema operativo (Windows)](/windows/desktop/SysInfo/operating-system-version). Non può essere NULL.|  
|**windows_service_pack_level**|**nvarchar(256)**| Per Windows, restituisce il numero di service pack. Non può essere NULL. |  
|**windows_sku**|**int**|Per Windows, restituisce l'ID di Windows Stock mantenendo Unit (SKU). Per un elenco degli ID SKU e descrizioni, vedere [funzione GetProductInfo](http://msdn.microsoft.com/library/ms724358.aspx). Sono ammessi valori null. |  
|**os_language_version**|**int**| Per Windows, restituisce l'identificatore di impostazioni locali (LCID) di Windows del sistema operativo. Per un elenco dei valori LCID e delle descrizioni, vedere [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/?LinkId=208080). Non può essere NULL.|  
  
  
## <a name="permissions"></a>Permissions  
Per impostazione predefinita, l'autorizzazione SELECT per sys.dm_os_windows_info viene concessa al ruolo public. Se è stato revocato, richiede l'autorizzazione VIEW SERVER STATE nel server.  

## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni
Per visualizzare informazioni per SQL in esecuzione in un host non Windows, ad esempio Linux, usare [DM os_host_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce tutte le colonne dai **sys.dm_os_windows_info** visualizzazione.  
  
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
  
  

