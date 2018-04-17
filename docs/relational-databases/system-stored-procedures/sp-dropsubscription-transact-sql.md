---
title: sp_dropsubscription (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords:
- sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 85d2d9188f84d4d2dac6167180013d1e659de3de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina le sottoscrizioni di un determinato articolo, pubblicazione o set di sottoscrizioni nel server di pubblicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione associata. *pubblicazione* viene **sysname**, con un valore predefinito è NULL. Se **tutti**, vengono annullate tutte le sottoscrizioni per tutte le pubblicazioni del Sottoscrittore specificato. *pubblicazione* è un parametro obbligatorio.  
  
 [  **@article=** ] **'***articolo***'**  
 Nome dell'articolo. *articolo* viene **sysname**, con valore predefinito è NULL. Se **tutti**, specificato di sottoscrizioni a tutti gli articoli per ogni pubblicazione e nel Sottoscrittore vengono eliminati. Utilizzare **tutti** per le pubblicazioni che consentono immediatamente l'aggiornamento.  
  
 [  **@subscriber=** ] **' * **sottoscrizione*r**' * *  
 Nome del Sottoscrittore da cui si desidera eliminare le sottoscrizioni. *Sottoscrittore* viene **sysname**, non prevede alcun valore predefinito. Se **tutti**, vengono eliminate tutte le sottoscrizioni per tutti i sottoscrittori.  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 Nome del database di destinazione. *destination_db* viene **sysname**, con un valore predefinito è NULL. con cui vengono eliminate tutte le sottoscrizioni dal Sottoscrittore specificato.  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@reserved=** ] **'***riservato***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropsubscription** viene utilizzata nella replica snapshot e transazionale.  
  
 Se si elimina la sottoscrizione di un articolo in una pubblicazione a sincronizzazione immediata, non è possibile aggiungerla nuovamente, a meno che le sottoscrizioni di tutti gli articoli della pubblicazione non vengano eliminate e aggiunte nuovamente in una sola operazione.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database o l'utente che ha creato la sottoscrizione può eseguire **sp_dropsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare una sottoscrizione Push](../../relational-databases/replication/delete-a-push-subscription.md)   
 [stored procedure sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
