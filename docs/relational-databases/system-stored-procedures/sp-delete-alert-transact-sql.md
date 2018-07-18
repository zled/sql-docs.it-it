---
title: sp_delete_alert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_alert_TSQL
- sp_delete_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_alert
ms.assetid: a831315e-793d-41c4-8333-b324bb2bc614
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8babe7d632f43a490a123470a8dc8d7cc5c07b4f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243847"
---
# <a name="spdeletealert-transact-sql"></a>sp_delete_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un avviso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_alert [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@name=** ] **'***name***'**  
 Nome dell'avviso. *nome* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Quando si rimuove un avviso, vengono rimosse anche le notifiche associate.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso l'avviso denominato `Test Alert`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_alert  
   @name = N'Test Alert' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
