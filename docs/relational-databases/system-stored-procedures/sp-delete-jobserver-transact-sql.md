---
title: sp_delete_jobserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobserver
- sp_delete_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobserver
ms.assetid: 6d63ed32-68cf-4d8f-aa40-05a3826e05b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 886f63ad94921451ca7136064f2148b46eeaba17
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729724"
---
# <a name="spdeletejobserver-transact-sql"></a>sp_delete_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove il server di destinazione specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_jobserver { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id=** ] *job_id*  
 Numero di identificazione del processo da cui si desidera rimuovere il server di destinazione specificato. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Nome del processo da cui si desidera rimuovere il server di destinazione specificato. *nome_processo* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* oppure *job_name* deve essere specificato; non è possibile specificarli entrambi.  
  
 [ **@server_name=** ] **'***server***'**  
 Nome del server di destinazione da cui rimuovere il processo specificato. *server* viene **nvarchar(30)**, non prevede alcun valore predefinito. *server* può essere **(locale)** o il nome di un server di destinazione remoto.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="permissions"></a>Permissions  
 Per eseguire questa stored procedure, gli utenti devono essere membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente rimuove il server `SEATTLE2` dall'elaborazione di `Weekly Sales Backups`processo.  
  
> [!NOTE]  
>  In questo esempio si presuppone che il processo `Weekly Sales Backups` sia stato creato in precedenza.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_jobserver  
    @job_name = N'Weekly Sales Backups',  
    @server_name = N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_help_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
