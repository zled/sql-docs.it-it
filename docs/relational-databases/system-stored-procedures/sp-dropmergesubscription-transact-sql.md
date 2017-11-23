---
title: sp_dropmergesubscription (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_dropmergesubscription_TSQL
- sp_dropmergesubscription
helpviewer_keywords: sp_dropmergesubscription
ms.assetid: 34244ae6-bd98-4a6a-bbd3-85f50edfcdc0
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5c3158dc51b7a54202b9897532e4ee8506cc64d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdropmergesubscription-transact-sql"></a>sp_dropmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una sottoscrizione di una pubblicazione di tipo merge e l'agente di merge corrispondente. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropmergesubscription [ [ @publication= ] 'publication' ]   
    [ , [ @subscriber= ] 'subscriber'    
    [ , [ @subscriber_db= ] 'subscriber_db' ]   
    [ , [ @subscription_type= ] 'subscription_type' ]   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, con un valore predefinito è NULL. È necessario che la pubblicazione esista già e che sia conforme alle regole per gli identificatori.  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_db=** ] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscription_database*è **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscription_type=** ] **'***subscription_type***'**  
 Tipo di sottoscrizione. *subscription_type*è **nvarchar (15)**, i possibili valori sono i seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**tutti i**|Sottoscrizioni push, pull e anonime.|  
|**anonimo**|Sottoscrizione anonima.|  
|**push**|Sottoscrizione push.|  
|**pull**|Sottoscrizione pull.|  
|**entrambi** (impostazione predefinita)|Sottoscrizione sia push che pull.|  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 Indica se questa stored procedure viene eseguita senza stabilire la connessione al server di distribuzione. *ignore_distributor* è **bit**, il valore predefinito è **0**. È possibile utilizzare questo parametro per eliminare una sottoscrizione senza eseguire attività di pulizia dei dati nel server di distribuzione. Risulta inoltre utile se è stato necessario reinstallare il server di distribuzione.  
  
 [  **@reserved=** ] *riservato*  
 Riservato per utilizzi futuri. *riservato* è **bit**, il valore predefinito è **0**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropmergesubscription** viene utilizzata nella replica di tipo merge.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergesubscription_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_dropmergesubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare una sottoscrizione Push](../../relational-databases/replication/delete-a-push-subscription.md)   
 [Eliminare una sottoscrizione Pull](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
