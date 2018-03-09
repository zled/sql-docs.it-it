---
title: sp_reinitpullsubscription (Transact-SQL) | Documenti Microsoft
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
- sp_reinitpullsubscription_TSQL
- sp_reinitpullsubscription
helpviewer_keywords:
- sp_reinitpullsubscription
ms.assetid: 7d9abe49-ce92-47f3-82c9-aea749518c91
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9020182762ac7f74e888e64814cedcae6fedec2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spreinitpullsubscription-transact-sql"></a>sp_reinitpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrassegna una sottoscrizione pull o anonima transazionale per la reinizializzazione alla successiva esecuzione dell'agente di distribuzione. Questa stored procedure viene eseguita nel database di sottoscrizione pull del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_reinitpullsubscription [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, con un valore predefinito è all, che indica che tutte le sottoscrizioni per la reinizializzazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_reinitpullsubscription** viene utilizzata nella replica transazionale.  
  
 **sp_reinitpullsubscription** non è supportato per la replica transazionale peer-to-peer.  
  
 **sp_reinitpullsubscription** può essere chiamato dal sottoscrittore per reinizializzare la sottoscrizione, durante l'esecuzione successiva dell'agente di distribuzione.  
  
 Sottoscrizioni alle pubblicazioni create con un valore di **false** per  **@immediate_sync**  non è possibile reinizializzare dal sottoscrittore.  
  
 È possibile reinizializzare una sottoscrizione pull, eseguire **sp_reinitpullsubscription** nel Sottoscrittore o **sp_reinitsubscription** nel server di pubblicazione.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_reinitpullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitpullsubscriptio_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_reinitpullsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
