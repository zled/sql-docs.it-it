---
title: sp_deletetracertokenhistory (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9e130ffe0853d899bcacd63c35d7987c9981329
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove i record dei token di traccia dal [MStracer_tokens &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) e [MStracer_history &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) tabelle di sistema. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_deletetracertokenhistory [ @publication = ] 'publication'   
    [ , [ @tracer_id = ] tracer_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione in cui è stato inserito il token di traccia. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@tracer_id=** ] *tracer_id*  
 ID del token di traccia da eliminare. *tracer_id* è **int**, con un valore predefinito null. Se **null**, quindi vengono eliminati tutti i token di traccia appartenenti alla pubblicazione.  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 Specifica un valore di cambio data in modo che tutti i token di traccia inseriti nella pubblicazione prima di tale data vengano rimossi. *cutoff_date* è di tipo datetime con un valore predefinito null.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro deve essere specificato solo per non[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito null. Questo parametro viene ignorato se la stored procedure viene eseguita nel server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_deletetracertokenhistory** viene utilizzata nella replica transazionale.  
  
 Quando si esegue **sp_deletetracertokenhistory**, è possibile specificare solo uno dei *tracer_id* o *cutoff_date*. Se si specificano entrambi i parametri, viene generato un errore.  
  
 Se non si esegue **sp_deletetracertokenhistory** per rimuovere i metadati di token di traccia, le informazioni vengono rimosse quando si verifica la pulizia della cronologia regolarmente pianificate.  
  
 ID di token di traccia, è possibile determinare eseguendo [sp_helptracertokens &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) oppure eseguendo una query di [MStracer_tokens &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) tabella di sistema.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database nel database di pubblicazione o **db_owner** predefiniti del database o  **replmonitor** ruoli nel database di distribuzione possono eseguire **sp_deletetracertokenhistory**.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurare la latenza e convalidare le connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_helptracertokenhistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)  
  
  
