---
title: sp_srvrolepermission (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: db6b3367b1d1a048bb47e4d30b96970557f48939
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261510"
---
# <a name="spsrvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le autorizzazioni di un ruolo predefinito del server.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@srvrolename =** ] **'***ruolo***'**  
 Nome del ruolo predefinito del server di cui vengono restituite autorizzazioni. *ruolo* viene **sysname**, con un valore predefinito è NULL. Se il ruolo viene omesso, vengono restituite le autorizzazioni di tutti i ruoli predefiniti del server. *ruolo* può avere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**sysadmin**|Amministratori di sistema|  
|**securityadmin**|Amministratori di sicurezza|  
|**serveradmin**|Amministratori di server|  
|**setupadmin**|Amministratori di installazione|  
|**processadmin**|Amministratori di processi|  
|**diskadmin**|Amministratori di dischi|  
|**dbcreator**|Creatori di database|  
|**bulkadmin**|Può eseguire le istruzioni BULK INSERT|  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**sysname**|Nome di un ruolo predefinito del server.|  
|**Autorizzazione**|**sysname**|Autorizzazione associata **ServerRole**|  
  
## <a name="remarks"></a>Osservazioni  
 Le autorizzazioni visualizzate includono le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] e altre attività speciali che possono essere eseguite dai membri del ruolo predefinito del server. Per visualizzare un elenco dei ruoli predefiniti del server, eseguire **sp_helpsrvrole**.  
  
 Il **sysadmin** ruolo predefinito del server disponga delle autorizzazioni di tutti gli altri ruoli predefiniti del server.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nella query seguente vengono restituite le autorizzazioni associate al ruolo predefinito del server `sysadmin`.  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
