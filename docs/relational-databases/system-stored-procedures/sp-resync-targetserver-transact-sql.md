---
title: sp_resync_targetserver (Transact-SQL) | Microsoft Docs
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
- sp_resync_targetserver
- sp_resync_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resync_targetserver
ms.assetid: 40e44df7-d3e3-44ee-b149-08aba629a21f
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d91ef10c7f1e98c4ad65d014f90fc42b0317ec5
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "33252460"
---
# <a name="spresynctargetserver-transact-sql"></a>sp_resync_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Risincronizza tutti i processi multiserver nel server di destinazione specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_resync_targetserver  
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@server_name =**] **'***server***'**  
 Nome del server da risincronizzare. *server* è di tipo **sysname**e non prevede alcun valore predefinito. Se **tutti** viene specificato, vengono risincronizzati tutti i server di destinazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Segnala il risultato di **sp_post_msx_operation** azioni.  
  
## <a name="remarks"></a>Remarks  
 **sp_resync_targetserver** Elimina il set corrente di istruzioni per il server di destinazione e invia un nuovo set per il server di destinazione per il download. Le nuove istruzioni prevedono l'eliminazione di tutti i processi multiserver e l'inserimento dei vari processi indirizzati al server.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene risincronizzato il server di destinazione `SEATTLE1`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_resync_targetserver  
    N'SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_downloadlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)   
 [sp_post_msx_operation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
