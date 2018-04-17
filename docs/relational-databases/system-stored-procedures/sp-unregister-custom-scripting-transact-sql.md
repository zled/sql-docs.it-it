---
title: sp_unregister_custom_scripting (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d2d1e9e081984645fcad82d59d6229f30225502
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure rimuove una definita dall'utente stored procedure personalizzata o [!INCLUDE[tsql](../../includes/tsql-md.md)] file di script che è stato registrato tramite l'esecuzione di [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@type** =] **'***tipo***'**  
 Tipo della stored procedure o dello script personalizzato da rimuovere. *tipo di* viene **varchar(16)**e non prevede alcun valore predefinito può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**insert**|La stored procedure o lo script personalizzato registrato viene eseguito quando viene replicata un'istruzione INSERT.|  
|**Aggiornamento**|La stored procedure o lo script personalizzato registrato viene eseguito quando viene replicata un'istruzione UPDATE.|  
|**delete**|La stored procedure o lo script personalizzato registrato viene eseguito quando viene replicata un'istruzione DELETE.|  
|**custom_script**|La stored procedure o lo script personalizzato registrato viene eseguito al termine del trigger DDL (Data Definition Language).|  
  
 [ **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione per cui si desidera rimuovere la stored procedure o lo script personalizzato. *pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@article** =] **'***articolo***'**  
 Nome dell'articolo per cui si desidera rimuovere la stored procedure o lo script personalizzato. *articolo* viene **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_unregister_custom_scripting** viene utilizzata nella replica snapshot e transazionale.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database, o **db_ddladmin** ruolo predefinito del database possono eseguire **sp _ unregister_custom_scripting**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
