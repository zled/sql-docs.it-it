---
title: sp_polybase_leave_group (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 807b90e460910c7175a867d2c2cc0ecf73549f69
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sppolybaseleavegroup-transact-sql"></a>sp_polybase_leave_group (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Rimuove un'istanza di SQL Server da un gruppo di PolyBase per il calcolo di scalabilità orizzontale. 
 
 L'istanza di SQL Server deve disporre di [Guida a PolyBase](../../relational-databases/polybase/polybase-guide.md) funzionalità installata.  PolyBase consente l'integrazione di origini dati non SQL Server, ad esempio l'archiviazione blob di Hadoop e Azure. Vedere anche [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="remarks"></a>Osservazioni  
 È solo possibile rimuovere un nodo di calcolo da un gruppo.  
  
 Dopo aver eseguito la stored procedure, riavviare il motore PolyBase e PolyBase Data Movement Service nel computer. Per verificare eseguire sulla seguente DMV nel nodo head: **Sys.dm exec_compute_nodes**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio viene rimosso il computer corrente da un gruppo di PolyBase.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
