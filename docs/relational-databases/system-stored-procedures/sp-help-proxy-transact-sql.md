---
title: sp_help_proxy (Transact-SQL) | Documenti Microsoft
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
- sp_help_proxy
- sp_help_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_proxy
ms.assetid: a2fce164-2b64-40c2-8f35-6eeb7844abf1
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a64cf35c51d4857b666798debb633828b6c66b8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259801"
---
# <a name="sphelpproxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le informazioni per uno o più proxy.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @subsystem_name = ] 'subsystem_name' ,  
    [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@proxy_id** =] *id*  
 Numero di identificazione del proxy per cui visualizzare un elenco di informazioni. Il *proxy_id* è **int**, con un valore predefinito è NULL. Entrambi i *id* o *proxy_name* può essere specificato.  
  
 [ **@proxy_name** =] **'***proxy_name***'**  
 Nome del proxy per cui visualizzare un elenco di informazioni. Il *proxy_name* è **sysname**, con un valore predefinito è NULL. Entrambi i *id* o *proxy_name* può essere specificato.  
  
 [ **@subsystem_name** =] '*subsystem_name*'  
 Il nome del sottosistema per cui visualizzare un elenco dei proxy. Il *subsystem_name* è **sysname**, con un valore predefinito è NULL. Quando *subsystem_name* è specificato, *nome* deve anche essere specificato.  
  
 Nella tabella seguente vengono elencati i valori disponibili per ogni sottosistema.  
  
|Value|Description|  
|-----------|-----------------|  
|ActiveScripting|Script ActiveX|  
|CmdExec|Sistema operativo (CmdExec)|  
|Snapshot|Agente snapshot repliche|  
|LogReader|Agente lettura log repliche|  
|Distribuzione|Agente distribuzione repliche|  
|Merge|Agente merge repliche|  
|QueueReader|Agente di lettura coda repliche|  
|ANALYSISQUERY|Comando di Analysis Services|  
|ANALYSISCOMMAND|Query di Analysis Services|  
|Dts|Esecuzione pacchetti SSIS|  
|PowerShell|Script di PowerShell|  
  
 [ **@name** =] '*nome*'  
 Il nome di un accesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per cui visualizzare un elenco dei proxy. Il nome è **nvarchar (256)**, con un valore predefinito è NULL. Quando *nome* è specificato, *subsystem_name* deve anche essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Numero di identificazione del proxy.|  
|**name**|**sysname**|Nome del proxy.|  
|**credential_identity**|**sysname**|Nome utente e del dominio Microsoft Windows per le credenziali associate al proxy.|  
|**enabled**|**tinyint**|Indica se il proxy è attivato. { **0** = non abilitata, **1** = attivato}|  
|**description**|**nvarchar(1024)**|Descrizione del proxy.|  
|**user_sid**|**varbinary(85)**|ID di sicurezza (SID) di Windows dell'utente di Windows per questo proxy.|  
|**credential_id**|**int**|Identificatore per le credenziali associate a questo proxy.|  
|**credential_identity_exists**|**int**|Indica se credential_identity esiste. { 0 = non esiste, 1 = esiste }|  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene specificato alcun parametro, **sp_help_proxy** Elenca le informazioni per tutti i proxy nell'istanza.  
  
 Per determinare quali proxy un account di accesso è possibile utilizzare per un determinato sottosistema, specificare *nome* e *subsystem_name*. Se vengono specificati questi argomenti, **sp_help_proxy** elenco di proxy che l'account di accesso specificato può accesso e che possono essere utilizzati per il sottosistema specificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono appartenere al ruolo predefinito del database **SQLAgentOperatorRole** nel database **msdb** .  
  
 Per informazioni dettagliate su **SQLAgentOperatorRole**, vedere [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
> [!NOTE]  
>  Il **credential_identity** e **user_sid** colonne vengono restituite solo nel set di risultati quando i membri del **sysadmin** eseguire questa stored procedure.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-information-for-all-proxies"></a>A. Visualizzazione di un elenco di informazioni per tutti i proxy  
 Nell'esempio seguente viene visualizzato un elenco di informazioni per tutti i proxy nell'istanza.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-proxy"></a>B. Visualizzazione di un elenco di informazioni per un proxy specifico  
 Nell'esempio seguente viene visualizzato un elenco di informazioni per il proxy denominato `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
