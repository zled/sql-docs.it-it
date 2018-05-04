---
title: sp_droppullsubscription (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b95a8bbbe4d31a530061a6da0a61aa78bd1aec5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdroppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una sottoscrizione nel database corrente del Sottoscrittore. Questa stored procedure viene eseguita nel database di sottoscrizione pull del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=** ] **'***publisher***'**  
 Nome del server remoto. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito. Se **tutti**, la sottoscrizione viene eliminata in tutti i server di pubblicazione.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db* viene **sysname**, non prevede alcun valore predefinito. **tutti i** indica tutti i database del server di pubblicazione.  
  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito. Se **tutti**, la sottoscrizione viene eliminata in tutte le pubblicazioni.  
  
 [  **@reserved=** ] *riservato*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_droppullsubscription** viene utilizzata nella replica snapshot e transazionale.  
  
 **sp_droppullsubscription** Elimina la riga corrispondente nella [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) tabella e l'agente di distribuzione corrispondente nel Sottoscrittore. Se nessuna riga viene mantenuta nella [MSreplication_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md), viene eliminata anche la tabella.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o l'utente che ha creato la sottoscrizione pull può eseguire **sp_droppullsubscription**. Il **db_owner** ruolo predefinito del database è in grado di eseguire solo **sp_droppullsubscription** se l'utente che ha creato la sottoscrizione pull appartiene a questo ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare una sottoscrizione Pull](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
