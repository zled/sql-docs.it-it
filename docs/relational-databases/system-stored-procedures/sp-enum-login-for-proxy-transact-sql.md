---
title: sp_enum_login_for_proxy (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs: TSQL
helpviewer_keywords: sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efb661e0ad7f711654840392425a0ae78f936c3b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spenumloginforproxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza un elenco di associazioni tra le entità di sicurezza e i proxy.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name** =] '*nome*'  
 Il nome di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entità, l'account di accesso, ruolo del server o **msdb** ruolo del database per l'elenco dei proxy. Il nome è **nvarchar (256)**, con un valore predefinito è NULL.  
  
 [  **@proxy_id** =] *id*  
 Numero di identificazione del proxy per cui visualizzare un elenco di informazioni. Il *proxy_id* è **int**, con un valore predefinito è NULL. Entrambi i *id* o *proxy_name* può essere specificato.  
  
 [  **@proxy_name** =] **'***proxy_name***'**  
 Nome del proxy per cui visualizzare un elenco di informazioni. Il *proxy_name* è **sysname**, con un valore predefinito è NULL. Entrambi i *id* o *proxy_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Numero di identificazione del proxy.|  
|**proxy_name**|**sysname**|Nome del proxy.|  
|**name**|**sysname**|Nome dell'entità di sicurezza per l'associazione.|  
|**flag**|**int**|Tipo dell'entità di sicurezza.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso<br /><br /> **1** = ruolo predefinito del sistema<br /><br /> **2** = ruolo del database in **msdb**|  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene specificato alcun parametro, **sp_enum_login_for_proxy** Elenca informazioni su tutti gli account di accesso nell'istanza per ogni proxy.  
  
 Quando viene fornito un id o un nome del proxy, **sp_enum_login_for_proxy** Elenca gli account di accesso che dispongono dell'accesso al proxy. Quando viene fornito un nome di accesso, **sp_enum_login_for_proxy** Elenca l'accesso a proxy con l'account di accesso.  
  
 Quando vengono specificate le informazioni sul proxy e un nome dell'account di accesso, il set di risultati restituisce una riga se l'account di accesso specificato può accedere al proxy specificato.  
  
 Questa stored procedure si trova in **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-associations"></a>A. Visualizzazione di un elenco di tutte le associazioni  
 Nell'esempio seguente viene visualizzato un elenco di tutte le autorizzazioni stabilite tra gli account di accesso e i proxy nell'istanza corrente.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy ;  
GO  
```  
  
### <a name="b-listing-proxies-for-a-specific-login"></a>B. Visualizzazione di un elenco di proxy per un account di accesso specifico  
 Nell'esempio seguente viene visualizzato un elenco di proxy cui può accedere l'account `terrid`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy  
    @name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  