---
title: sp_altermessage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_altermessage_TSQL
- sp_altermessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_altermessage
ms.assetid: 1b28f280-8ef9-48e9-bd99-ec14d79abaca
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c254a5ac8837b8e631e2ef688c35bf217a35da7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaltermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica lo stato dei messaggi di sistema o definiti dall'utente in un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. È possibile visualizzare i messaggi definiti dall'utente utilizzando il **Sys. Messages** vista del catalogo.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@message_id =** ] *message_number*  
 Numero di errore del messaggio da modificare, recuperato da **Sys. Messages**. *message_number* viene **int** non prevede alcun valore predefinito.  
  
 [  **@parameter =** ] **' * * * write_to_log*'  
 Viene utilizzato con **@parameter_value** per indicare che il messaggio in cui scrivere il [!INCLUDE[msCoName](../../includes/msconame-md.md)] registro applicazioni di Windows. *write_to_log* viene **sysname** non prevede alcun valore predefinito. *write_to_log* deve essere impostato su WITH_LOG o NULL. Se *write_to_log* è impostato su WITH_LOG o NULL e il valore di **@parameter_value** è **true**, il messaggio viene scritto nel registro applicazioni di Windows. Se *write_to_log* è impostato su WITH_LOG o NULL e il valore di **@parameter_value** è **false**, il messaggio viene scritto nel registro applicazioni di Windows, ma può essere scritta in base al modo in cui è stato generato l'errore. Se *write_to_log* è specificato, il valore per **@parameter_value** deve anche essere specificato.  
  
> [!NOTE]  
>  Se un messaggio viene scritto nel registro applicazioni di Windows, viene registrato inoltre nel file di log degli errori di [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 [  **@parameter_value =** ] **' * * * valore*'  
 Viene utilizzato con **@parameter** per indicare che l'errore è necessario scrivere il [!INCLUDE[msCoName](../../includes/msconame-md.md)] registro applicazioni di Windows. *valore* viene **varchar (5)**, senza alcun valore predefinito. Se **true**, l'errore viene sempre scritto nel registro applicazioni di Windows. Se **false**, l'errore viene scritto nel registro applicazioni di Windows, ma può essere scritta in base al modo in cui è stato generato l'errore. Se *valore* è specificato, *write_to_log* per **@parameter** deve anche essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 L'effetto di **sp_altermessage** con il WITH_LOG è simile a quello del parametro RAISERROR WITH LOG, con la differenza che l'opzione **sp_altermessage** modifica il comportamento di registrazione di un messaggio esistente. I messaggi modificati con l'opzione WITH_LOG vengono sempre scritti nel registro applicazioni di Windows, indipendentemente dalla modalità con cui sono stati generati. Gli errori vengono infatti scritti nel registro applicazioni di Windows anche se RAISERROR viene eseguito senza l'opzione WITH_LOG.  
  
 I messaggi di sistema possono essere modificati mediante **sp_altermessage**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **serveradmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene registrato il messaggio `55001` esistente nel registro applicazioni di Windows.  
  
```  
EXECUTE sp_altermessage 55001, 'WITH_LOG', 'true';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
