---
title: sp_dropmergepublication (Transact-SQL) | Documenti Microsoft
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
- sp_dropmergepublication
- sp_dropmergepublication_TSQL
helpviewer_keywords:
- sp_dropmergepublication
ms.assetid: 9e1cb96e-5889-4f97-88cd-f60cf313ce68
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5eac5a3f606a2a8ed3fabe5146f47d1c04aa7185
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdropmergepublication-transact-sql"></a>sp_dropmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una pubblicazione di tipo merge e l'agente snapshot associato. Prima di eliminare una pubblicazione di tipo merge, è necessario eliminare tutte le sottoscrizioni. Gli articoli della pubblicazione vengono eliminati automaticamente. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropmergepublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione da eliminare. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito. Se **tutti**, vengono rimosse tutte le pubblicazioni di tipo merge esistenti nonché il processo dell'agente Snapshot associato. Se si specifica un valore particolare per *pubblicazione*, vengono eliminati solo tale pubblicazione e il processo dell'agente Snapshot associato.  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 Utilizzato per eliminare una pubblicazione senza eseguire attività di pulizia nel server di distribuzione. *ignore_distributor* viene **bit**, il valore predefinito è **0**. Questo parametro viene utilizzato anche quando si reinstalla il server di distribuzione.  
  
 [  **@reserved=**] *riservato*  
 Riservato per utilizzi futuri. *riservata* viene **bit**, il valore predefinito è **0**.  
  
 [  **@ignore_merge_metadata=** ] *ignore_merge_metadata*  
 Solo per uso interno.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropmergepublication** viene utilizzata nella replica di tipo merge.  
  
 **sp_dropmergepublication** in modo ricorsivo Elimina tutti gli articoli che sono associati a una pubblicazione e quindi elimina la pubblicazione stessa. Non è possibile rimuovere una pubblicazione per cui esistono una o più sottoscrizioni. Per informazioni su come rimuovere le sottoscrizioni, vedere [eliminare una sottoscrizione Push](../../relational-databases/replication/delete-a-push-subscription.md) e [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 L'esecuzione di **sp_dropmergepublication** per eliminare una pubblicazione non rimuove gli oggetti pubblicati dal database di pubblicazione o degli oggetti corrispondenti dal database di sottoscrizione. Utilizzare DROP \<oggetto > per rimuovere questi oggetti manualmente, se necessario.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_dropmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepublication-_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_dropmergepublication**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminazione di una pubblicazione](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
