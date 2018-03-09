---
title: sp_addmergepullsubscription (Transact-SQL) | Documenti Microsoft
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
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords:
- sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64af301fda7ee871c30611698b1385fa8bd318f0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge una sottoscrizione pull a una pubblicazione di tipo merge. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addmergepullsubscription [ @publication= ] 'publication'   
    [ , [ @publisher= ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @subscriber_type= ] 'subscriber_type' ]   
    [ , [ @subscription_priority= ] subscription_priority ]   
    [ , [ @sync_type= ] 'sync_type' ]   
    [ , [ @description= ] 'description' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *Server di pubblicazione* è **sysname**, con valore predefinito è il nome del server locale. Il server di pubblicazione deve essere un server valido.  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_type=**] **'***subscriber_type***'**  
 Tipo di Sottoscrittore. *subscriber_type* è **nvarchar (15)**e può essere **globale**, **locale** o **anonimo**. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive le sottoscrizioni locali vengono dette sottoscrizioni client e le sottoscrizioni globali vengono dette sottoscrizioni server.  
  
 [  **@subscription_priority=**] *subscription_priority*  
 Priorità della sottoscrizione. *subscription_priority*è **reale**, con un valore predefinito è NULL. Per le sottoscrizioni locali e anonime, la priorità è **0,0**. La priorità viene utilizzata dal sistema di risoluzione predefinito per eseguire una selezione in caso di conflitti. Per i Sottoscrittori globali, la priorità della sottoscrizione deve essere minore di 100, che corrisponde al livello di priorità del server di pubblicazione.  
  
 [  **@sync_type=**] **'***sync_type***'**  
 Tipo di sincronizzazione per la sottoscrizione. *sync_type*è **nvarchar (15)**, il valore predefinito è **automatica**. Può essere **automatica** o **Nessuno**. Se **automatico**, lo schema e i dati iniziali per le tabelle pubblicate vengono trasferiti nel Sottoscrittore prima. Se **Nessuno**, si presuppone il sottoscrittore includa già lo schema e i dati iniziali per le tabelle pubblicate. Le tabelle e i dati di sistema vengono sempre trasferiti.  
  
> [!NOTE]  
>  Non è consigliabile specificare un valore di **Nessuno**.  
  
 [  **@description=**] **'***descrizione***'**  
 Breve descrizione della sottoscrizione pull. *Descrizione*è **nvarchar (255)**, con un valore predefinito è NULL. Questo valore viene visualizzato da Monitoraggio replica nel **nome descrittivo** colonna, che può essere utilizzato per ordinare le sottoscrizioni per una pubblicazione monitorata.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addmergepullsubscription** usato per la replica di tipo merge.  
  
 Se si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente per sincronizzare la sottoscrizione, il [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) stored procedure deve essere eseguita nel Sottoscrittore per creare un agente e il processo per la sincronizzazione con la pubblicazione.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addmergepullsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
