---
title: sp_enum_login_for_proxy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7faec16e49bb2776babb126a5f4d314889b70c2b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036273"
---
# <a name="spenumloginforproxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza un elenco di associazioni tra le entità di sicurezza e i proxy.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@name**=] '*nome*'  
 Il nome di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] principale, account di accesso, ruolo del server, oppure **msdb** ruolo del database per l'elenco dei proxy. Il nome è **nvarchar(256)**, con un valore predefinito è NULL.  
  
 [ **@proxy_id**=] *id*  
 Numero di identificazione del proxy per cui visualizzare un elenco di informazioni. Il *proxy_id* viene **int**, con un valore predefinito è NULL. Entrambi i *id* o nella *proxy_name* può essere specificato.  
  
 [ **@proxy_name**=] **'***proxy_name***'**  
 Nome del proxy per cui visualizzare un elenco di informazioni. Il *nome_proxy* viene **sysname**, con un valore predefinito è NULL. Entrambi i *id* o nella *proxy_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|Numero di identificazione del proxy.|  
|**proxy_name**|**sysname**|Nome del proxy.|  
|**name**|**sysname**|Nome dell'entità di sicurezza per l'associazione.|  
|**flags**|**int**|Tipo dell'entità di sicurezza.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso<br /><br /> **1** = ruolo predefinito del sistema<br /><br /> **2** = ruolo del database in **msdb**|  
  
## <a name="remarks"></a>Note  
 Quando viene specificato alcun parametro, **sp_enum_login_for_proxy** Elenca le informazioni su tutti gli account di accesso nell'istanza per ogni proxy.  
  
 Quando viene specificato il nome del proxy o un id del proxy, **sp_enum_login_for_proxy** Elenca gli account di accesso che dispongono dell'accesso al proxy. Quando viene specificato un nome di account di accesso, **sp_enum_login_for_proxy** i proxy che l'account di accesso ha accesso a elenchi.  
  
 Quando vengono specificate le informazioni sul proxy e un nome dell'account di accesso, il set di risultati restituisce una riga se l'account di accesso specificato può accedere al proxy specificato.  
  
 Questa stored procedure si trova nella **msdb**.  
  
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
 [sp_help_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
