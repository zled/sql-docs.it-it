---
title: sp_enum_proxy_for_subsystem (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_proxy_for_subsystem_TSQL
- sp_enum_proxy_for_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_proxy_for_subsystems
ms.assetid: 580cc3be-1068-4a96-8d15-78ca3a5bb719
ms.author: vanto
manager: craigg
ms.openlocfilehash: cc983f79dfa1eafd0f0175448467c3a8d9a69aa0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736865"
---
# <a name="spenumproxyforsubsystem-transact-sql"></a>sp_enum_proxy_for_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza un elenco delle autorizzazioni per i proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per accedere ai sottosistemi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_enum_proxy_for_subsystem  
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@proxy_id** = ] *proxy_id*  
 Numero di identificazione del proxy per cui visualizzare un elenco di informazioni. Il *proxy_id* viene **int**, con un valore predefinito è NULL. Entrambi i *id* o nella *proxy_name* può essere specificato.  
  
 [ **@proxy_name** =] **'***proxy_name***'**  
 Nome del proxy per cui visualizzare un elenco di informazioni. Il *nome_proxy* viene **sysname**, con un valore predefinito è NULL. Entrambi i *id* o nella *proxy_name* può essere specificato.  
  
 [ **@subsystem_id** = ] *subsystem_id*  
 Numero di identificazione del sottosistema per cui visualizzare un elenco di informazioni. Il *subsystem_id* viene **int**, con un valore predefinito è NULL. Entrambi i *subsystem_id* o nella *subsystem_name* può essere specificato.  
  
 [ **@subsystem_name** =] **'***subsystem_name***'**  
 Nome del sottosistema per cui visualizzare un elenco di informazioni. Il *subsystem_name* viene **sysname**, con un valore predefinito è NULL. Entrambi i *subsystem_id* o nella *subsystem_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Numero di identificazione del sottosistema.|  
|**subsystem_name**|**sysname**|Nome del sottosistema.|  
|**proxy_id**|**int**|Numero di identificazione del proxy.|  
|**proxy_name**|**sysname**|Nome del proxy.|  
  
## <a name="remarks"></a>Note  
 Quando viene specificato alcun parametro, **sp_enum_proxy_for_subsystem** Elenca le informazioni su tutti i proxy nell'istanza di ogni sottosistema.  
  
 Quando viene specificato il nome del proxy o un id del proxy, **sp_enum_proxy_for_subsystem** sottosistemi a cui il proxy ha accesso a. Quando viene fornito un id o un nome del sottosistema, **sp_enum_proxy_for_subsystem** proxy che hanno accesso al sottosistema.  
  
 Quando vengono specificate sia le informazioni sul proxy che sul sottosistema, il set di risultati restituisce una riga se il proxy specificato può accedere al sottosistema specificato.  
  
 Questa stored procedure si trova nella **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-associations"></a>A. Visualizzazione di un elenco di tutte le associazioni  
 Nell'esempio seguente viene visualizzato un elenco di tutte le autorizzazioni stabilite tra proxy e sottosistemi nell'istanza corrente.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem ;  
GO  
```  
  
### <a name="b-determining-if-a-proxy-has-access-to-a-specific-subsystem"></a>B. Stabilire se un proxy ha accesso a un sottosistema specificato  
 Nell'esempio seguente viene restituita una riga se il proxy `Catalog application proxy` ha accesso al sottosistema `ActiveScripting`. In caso contrario, viene restituito un set di risultati vuoto.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_proxy_for_subsystem  
    @subsystem_name = 'ActiveScripting',  
    @proxy_name = 'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
