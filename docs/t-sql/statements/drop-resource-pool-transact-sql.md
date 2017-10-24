---
title: ELIMINARE il POOL di risorse (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP RESOURCE POOL
- DROP_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP RESOURCE POOL
ms.assetid: 18cd6dd9-7a6d-4a08-b9d5-649af23583d5
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 72d609a56d8d0327d72a74f173445f666b78f09c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-resource-pool-transact-sql"></a>DROP RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina un pool di risorse di Resource Governor definito dall'utente.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP RESOURCE POOL pool_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *pool_name*  
 Il nome di un pool di risorse esistente definito dall'utente.  
  
## <a name="remarks"></a>Osservazioni  
 Non è possibile eliminare un pool di risorse contenente gruppi del carico di lavoro.  
  
 Non è possibile eliminare pool predefiniti o interni di Resource Governor.  
  
 Per l'esecuzione di istruzioni DDL, è consigliabile avere familiarità con gli stati di Resource Governor. Per ulteriori informazioni, vedere [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il pool di risorse denominato `big_pool`.  
  
```  
DROP RESOURCE POOL big_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

