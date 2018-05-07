---
title: sp_delete_targetserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_targetserver
- sp_delete_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetserver
ms.assetid: cc438701-ad91-419d-9f23-ebc4c548c700
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b67e059a70c7edfda838d325928a95a8f4b43ab0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spdeletetargetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove il server specificato dall'elenco dei server di destinazione disponibili.  
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@server_name=** ] **'***server***'**  
 Nome del server da rimuovere come server di destinazione disponibile. *server* viene **nvarchar(30)**, non prevede alcun valore predefinito.  
  
 [  **@clear_downloadlist=** ] *clear_downloadlist*  
 Specifica se cancellare l'elenco di download per il server di destinazione. *clear_downloadlist* è di tipo **bit**, il valore predefinito è **1**. Quando *clear_downloadlist* è **1**, la procedura cancella l'elenco di download per il server prima di eliminare il server. Quando *clear_downloadlist* è **0**, l'elenco di download non viene cancellata.  
  
 [  **@post_defection=** ] *post_defection*  
 Viene specificato se inviare un'istruzione di esclusione al server di destinazione. *post_defection* è di tipo **bit**, con un valore predefinito è 1. Quando *post_defection* è **1**, la procedura invia un'istruzione di esclusione al server di destinazione prima di eliminare il server. Quando *post_defection* è **0**, la procedura non invia un'istruzione di esclusione al server di destinazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Il normale per eliminare un server di destinazione consiste nel chiamare **sp_msx_defect** nel server di destinazione. Utilizzare **sp_delete_targetserver** solo quando è necessaria un'esclusione manuale.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa stored procedure, è necessario consentire agli utenti di **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il server `LONDON1` viene rimosso dall'elenco dei server di processo disponibili.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_targetserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
