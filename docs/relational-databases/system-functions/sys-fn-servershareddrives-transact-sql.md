---
title: sys.fn_servershareddrives (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_servershareddrives
- fn_servershareddrives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_servershareddrives function
- shared drives [SQL Server]
- names [SQL Server], shared drives
- sys.fn_serversharedrives function
ms.assetid: ff01eff7-8cb6-460c-ba7a-6a52bda6d471
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a9fe23ad67b8a8cc4e687badf8ef6f75d9363e3e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702319"
---
# <a name="sysfnservershareddrives-transact-sql"></a>sys.fn_servershareddrives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce i nomi delle unità condivise utilizzate dal server del cluster.  
  
> [!IMPORTANT]  
>  Questa funzione di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è inclusa per garantire la compatibilità con le versioni precedenti. È consigliabile usare [sys.dm_io_cluster_valid_path_names &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn_servershareddrives()  
```  
  
## <a name="tables-returned"></a>Tabelle restituite  
 Se il server corrente è un server cluster, **fn_servershareddrives** restituisce il nome delle unità condivise.  
  
 Se l'istanza del server corrente non è un server cluster, **fn_servershareddrives** restituisce un set di righe vuoto.  
  
## <a name="remarks"></a>Note  
 La funzione `fn_servershareddrives` restituisce l'elenco delle unità condivise utilizzate dal server del cluster corrente. Tali unità appartengono allo stesso gruppo di cluster di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risorsa. A sua volta, la risorsa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dipende da queste unità.  
  
 Questa funzione risulta utile per l'identificazione delle unità disponibili agli utenti.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre dell'autorizzazione VIEW SERVER STATE per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la funzione `fn_servershareddrives` viene utilizzata per eseguire una query su un'istanza del server del cluster.  
  
```  
SELECT * FROM fn_servershareddrives();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 DriveName  
  
 -------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_io_cluster_valid_path_names &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)  
  
  
