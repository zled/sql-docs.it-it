---
title: sp_notify_operator (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs: TSQL
helpviewer_keywords: sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2ff7b50b5eef5d5ff753039bf4dd7ab501160eda
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Invia un messaggio di posta elettronica a un operatore tramite Posta elettronica database.  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_name=** ] **'***profilename***'**  
 Nome del profilo di Posta elettronica database da utilizzare per inviare il messaggio. *ProfileName* è **nvarchar (128)**. Se *profilename* viene omesso, viene utilizzato il profilo di posta elettronica Database predefinito.  
  
 [  **@id=** ] *id*  
 Identificatore dell'operatore a cui inviare il messaggio. *ID* è **int**, con un valore predefinito è NULL. Uno dei *id* o *nome* deve essere specificato.  
  
 [  **@name=** ] **'***nome***'**  
 Nome dell'operatore a cui inviare il messaggio. *nome* è **nvarchar (128)**, con un valore predefinito è NULL. Uno dei *id* o *nome* deve essere specificato.  
  
> **Nota:** indirizzo di posta elettronica deve essere definito per l'operatore per poter ricevere i messaggi.  
  
 [  **@subject=** ] **'***soggetto***'**  
 Oggetto del messaggio di posta elettronica. *oggetto* è **nvarchar (256)** prevede alcun valore predefinito.  
  
 [  **@body=** ] **'***messaggio***'**  
 Corpo del messaggio di posta elettronica. *messaggio* è **nvarchar (max)** prevede alcun valore predefinito.  
  
 [  **@file_attachments=** ] **'***allegato***'**  
 Nome del file da allegare al messaggio di posta elettronica. *allegato* è **nvarchar (512)**, non prevede alcun valore predefinito.  
  
 [  **@mail_database=** ] **'***mail_host_database***'**  
 Specifica il nome del computer host. *mail_host_database* è **nvarchar (128)**. Se non *mail_host_database* è specificato, il **msdb** database viene utilizzato per impostazione predefinita.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Invia il messaggio specificato all'indirizzo di posta elettronica dell'operatore. Se non è stato configurato un indirizzo di posta elettronica per l'operatore, viene restituito un errore.  
  
 Per poter inviare una notifica a un operatore, è necessario innanzitutto configurare Posta elettronica database e un database host della posta elettronica.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene inviato un messaggio di notifica all'operatore `François Ajenstat` tramite il profilo `AdventureWorks Administrator` di Posta elettronica database. L'oggetto del messaggio di posta elettronica è `Test Notification`. The e-mail message contains the sentence, "This is a test of notification via e-mail."  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
