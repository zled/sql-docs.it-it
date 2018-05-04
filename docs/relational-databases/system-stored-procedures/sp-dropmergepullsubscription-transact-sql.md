---
title: sp_dropmergepullsubscription (Transact-SQL) | Documenti Microsoft
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
- sp_dropmergepullsubscription
- sp_dropmergepullsubscription_TSQL
helpviewer_keywords:
- sp_dropmergepullsubscription
ms.assetid: 9301dd80-72f7-4adb-9b13-87e7f9114248
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f9de9b1a2460b7621f87aba4be333a26dd02a6ae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdropmergepullsubscription-transact-sql"></a>sp_dropmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una sottoscrizione pull di tipo merge. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropmergepullsubscription [ @publication= ] 'publication'   
        , [ @publisher= ] 'publisher'   
        , [ @publisher_db= ] 'publisher_db'   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, con un valore predefinito è NULL. Questo parametro è obbligatorio. Specificare un valore di **tutti** per rimuovere le sottoscrizioni a tutte le pubblicazioni  
  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione*viene **sysname**, con un valore predefinito è NULL. Questo parametro è obbligatorio.  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db*viene **sysname**, con un valore predefinito è NULL. Questo parametro è obbligatorio.  
  
 [  **@reserved=**] **'***riservato***'**  
 Riservato per utilizzi futuri. *riservata* viene **bit**, il valore predefinito è **0**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropmergepullsubscription** viene utilizzata nella replica di tipo merge.  
  
 **sp_dropmergepullsubscription** Elimina l'agente di Merge per la sottoscrizione pull di tipo merge, anche se l'agente di Merge non viene creata nel **sp_addmergepullsubscription**.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepullsubscrip_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o l'utente che ha creato la sottoscrizione pull di tipo merge può eseguire **sp_dropmergepullsubscription**. Il **db_owner** ruolo predefinito del database è in grado di eseguire solo **sp_dropmergepullsubscription** se l'utente che ha creato la sottoscrizione pull di tipo merge appartiene a questo ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare una sottoscrizione Pull](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)  
  
  
