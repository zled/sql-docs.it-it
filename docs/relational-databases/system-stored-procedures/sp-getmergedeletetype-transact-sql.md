---
title: sp_getmergedeletetype (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a517b90bd59f22c6851403b8928e903eecca7c55
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spgetmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il tipo di eliminazione di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@source_object =**] **'***source_object***'**  
 Nome dell'oggetto di origine. *source_object* è **nvarchar (386)**, non prevede alcun valore predefinito.  
  
 [  **@rowguid=**] **'***rowguid***'**  
 Identificatore di riga per il tipo di eliminazione. *ROWGUID* è **uniqueidentifier**, non prevede alcun valore predefinito.  
  
 [  **@delete_type=**] *delete_type* **OUTPUT**  
 Codice che indica il tipo di eliminazione. *delete_type* è **int**, non prevede alcun valore predefinito. *delete_type* è anche un parametro di OUTPUT e può essere uno dei valori seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Eliminazione eseguita dall'utente|  
|**5**|Eliminazione parziale|  
|**6**|Eliminazione eseguita dal sistema|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_getmergedeletetype** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_getmergedeletetype**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
