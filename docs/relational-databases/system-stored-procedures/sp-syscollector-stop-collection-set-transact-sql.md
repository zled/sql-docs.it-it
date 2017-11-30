---
title: sp_syscollector_stop_collection_set (Transact-SQL) | Documenti Microsoft
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
- sp_syscollector_stop_collection_set_TSQL
- sp_syscollector_stop_collection_set
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_stop_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 4668cfb7-462f-40d0-948c-8f740a792a4d
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6f91cbec86a4799a6172525ba2633be9f34dcdd9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spsyscollectorstopcollectionset-transact-sql"></a>sp_syscollector_stop_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Arresta un set di raccolta.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_stop_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @stop_collection_job = ] stop_collection_job ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @collection_set_id =] *collection_set_id*  
 Identificatore univoco locale del set di raccolta. *collection_set_id* è **int** con un valore predefinito null. *collection_set_id* deve avere un valore se *nome* è NULL.  
  
 [ @name =] '*nome*'  
 Nome del set di raccolta. *nome* è **sysname** con un valore predefinito null. *nome* deve avere un valore se *collection_set_id* è NULL.  
  
 [ @stop_collection_job =] *stop_collection_job*  
 Specifica che il processo di raccolta relativo al set di raccolta deve essere arrestato se è in esecuzione. *stop_collection_job* è **bit** con un valore predefinito è 1.  
  
 *stop_collection_job* si applica solo ai set di raccolta con modalità di raccolta cache. Per ulteriori informazioni, vedere [sp_syscollector_create_collection_set &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 È necessario eseguire sp_syscollector_create_collection_set nel contesto del database di sistema msdb.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire questa procedura, è necessaria l'appartenenza al ruolo predefinito del database dc_operator (con autorizzazione EXECUTE).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene arrestato un set di raccolta utilizzando il relativo identificatore.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
