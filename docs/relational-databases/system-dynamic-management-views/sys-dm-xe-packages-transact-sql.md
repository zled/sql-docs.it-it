---
title: Sys.dm xe_packages (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_xe_packages_TSQL
- sys.dm_xe_packages_TSQL
- dm_xe_packages
- sys.dm_xe_packages
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_xe_packages dynamic management view
- extended events [SQL Server], views
ms.assetid: 2e5ecbe9-3ea8-45e6-a161-e31671a03e1d
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d44f313bcb4f199d43305cd9752dda71db5da980
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmxepackages-transact-sql"></a>sys.dm_xe_packages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca tutti i pacchetti registrati con il motore degli eventi estesi.  
  
 
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(60)**|Nome del pacchetto. La descrizione viene esposta dal pacchetto stesso. Non ammette i valori Null.|  
|guid|**uniqueidentifier**|GUID che identifica il pacchetto. Non ammette i valori Null.|  
|description|**nvarchar(256)**|Descrizione del pacchetto. descriptionis impostata dall'autore del pacchetto e non ammette valori null.|  
|capabilities|**int**|Bitmap che descrive le funzionalità di questo pacchetto. Ammette i valori Null.|  
|capabilities_desc|**nvarchar(256)**|Elenco di tutte le funzionalità possibili per questo pacchetto. Ammette i valori Null.|  
|module_guid|**uniqueidentifier**|GUID del modulo che espone questo pacchetto. Non ammette i valori Null.|  
|module_address|**varbinary (8)**|Indirizzo di base in cui viene caricato il modulo contenente il pacchetto. Un solo modulo può esporre molti pacchetti. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="remarks"></a>Osservazioni  
 I pacchetti registrati con il motore degli eventi estesi espongono gli eventi, le azioni che possono essere eseguite al momento della generazione dell'evento e le destinazioni per l'elaborazione sincrona e asincrona di dati degli eventi.  
  
 Questi pacchetti possono essere caricati dinamicamente in uno spazio di indirizzi di processo. Al momento del caricamento del pacchetto vengono registrati tutti gli oggetti esposti con il motore degli eventi esteso.  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
||||  
|-|-|-|  
|Da|Per|Relazione|  
|sys.dm_xe_packages.module_address|sys.dm_os_loaded_modules.base_address|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

