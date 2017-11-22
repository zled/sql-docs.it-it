---
title: Sys.dm_server_memory_dumps (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
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
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs: TSQL
helpviewer_keywords: sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd4af6e42415814c6fc0771346f94a5283a41730
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmservermemorydumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni file di dump della memoria generato dal [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Utilizzare la DMV per risolvere potenziali problemi.  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nome file**|**nvarchar(256)**|Percorso e nome del file di dump della memoria. Non può essere null.|  
|**creation_time**|**DateTimeOffset(7)**|Data e ora di creazione del file. Non può essere null.|  
|**size_in_bytes**|**bigint**|Dimensioni (in byte) del file. Ammette i valori Null.|  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Il dump può essere di tipo minidump, all-thread o completo. I file hanno estensione .mdmp.  
  
## <a name="security"></a>Security  
 I file di dump possono contenere informazioni riservate. Per proteggere tali informazioni, è possibile utilizzare un elenco di controllo di accesso per limitare l'accesso ai file oppure copiare i file in una cartella con accesso limitato. Ad esempio, prima di inviare i file di debug ai servizi di supporto tecnico Microsoft, è consigliato rimuovere qualsiasi informazione sensibile o riservata.  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE.  
  
  
