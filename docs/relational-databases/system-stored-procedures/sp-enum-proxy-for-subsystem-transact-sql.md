---
title: sp_enum_proxy_for_subsystem (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_enum_proxy_for_subsystem_TSQL
- sp_enum_proxy_for_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_proxy_for_subsystems
ms.assetid: 580cc3be-1068-4a96-8d15-78ca3a5bb719
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8551a807fd916c80909e281c8ddd6bc785315573
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
 Numero di identificazione del proxy per cui visualizzare un elenco di informazioni. Il *proxy_id* è **int**, con un valore predefinito è NULL. Entrambi i *id* o *proxy_name* può essere specificato.  
  
 [ **@proxy_name** =] **'***proxy_name***'**  
 Nome del proxy per cui visualizzare un elenco di informazioni. Il *proxy_name* è **sysname**, con un valore predefinito è NULL. Entrambi i *id* o *proxy_name* può essere specificato.  
  
 [ **@subsystem_id** = ] *subsystem_id*  
 Numero di identificazione del sottosistema per cui visualizzare un elenco di informazioni. Il *subsystem_id* è **int**, con un valore predefinito è NULL. Entrambi i *subsystem_id* o *subsystem_name* può essere specificato.  
  
 [ **@subsystem_name** =] **'***subsystem_name***'**  
 Nome del sottosistema per cui visualizzare un elenco di informazioni. Il *subsystem_name* è **sysname**, con un valore predefinito è NULL. Entrambi i *subsystem_id* o *subsystem_name* può essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|Numero di identificazione del sottosistema.|  
|**subsystem_name**|**sysname**|Nome del sottosistema.|  
|**proxy_id**|**int**|Numero di identificazione del proxy.|  
|**proxy_name**|**sysname**|Nome del proxy.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene specificato alcun parametro, **sp_enum_proxy_for_subsystem** Elenca le informazioni su tutti i proxy nell'istanza per ogni sottosistema.  
  
 Quando viene fornito un id o un nome del proxy, **sp_enum_proxy_for_subsystem** l'accesso all'elenco di sottosistemi con il proxy. Quando viene fornito un id o un nome di sottosistema, **sp_enum_proxy_for_subsystem** Elenca proxy che hanno accesso al sottosistema.  
  
 Quando vengono specificate sia le informazioni sul proxy che sul sottosistema, il set di risultati restituisce una riga se il proxy specificato può accedere al sottosistema specificato.  
  
 Questa stored procedure si trova in **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
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
  
  
