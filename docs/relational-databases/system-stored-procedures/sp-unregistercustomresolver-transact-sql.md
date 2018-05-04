---
title: sp_unregistercustomresolver (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_unregistercustomresolver_TSQL
- sp_unregistercustomresolver
helpviewer_keywords:
- sp_unregistercustomresolver
ms.assetid: 08bd20c8-c6be-4be2-be9f-2b5e1d7bee43
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 92a6cfa9cf51ed0742e19d75abeb5baf7f343b16
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spunregistercustomresolver-transact-sql"></a>sp_unregistercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Annulla la registrazione di un modulo di logica di business precedentemente registrato. La logica di business può essere un componente COM o un assembly [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Questa stored procedure viene eseguita nel server di distribuzione in cui è stata registrata la logica di business personalizzata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_unregistercustomresolver [ @article_resolver = ] 'article_resolver'   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@article_resolver =** ] **'***article_resolver***'**  
 Specifica il nome della logica di business personalizzata di cui annullare la registrazione. *article_resolver* viene **nvarchar(255**, non prevede alcun valore predefinito. Se la logica di business da rimuovere è un componente COM, questo parametro corrisponde al nome descrittivo del componente. Se la logica di business è un assembly .NET Framework, il parametro corrisponde al nome dell'assembly.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_unregistercustomresolver** viene utilizzata nella replica di tipo merge.  
  
 Utilizzare [sp_enumcustomresolvers](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) in qualsiasi server della topologia di replica per restituire l'elenco dei moduli di logica di business personalizzata registrato o sistemi di risoluzione COM disponibili alla topologia.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_unregistercustomresolver**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
