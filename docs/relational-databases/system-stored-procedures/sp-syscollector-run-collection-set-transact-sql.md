---
title: sp_syscollector_run_collection_set (Transact-SQL) | Documenti Microsoft
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
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca014293d64b0782d4844794efb5528849d0ecf9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorruncollectionset-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Avvia un set di raccolta se l'agente di raccolta è già abilitato e set di raccolta è configurato per la modalità di raccolta non in cache.  
  
> [!NOTE]  
>  Questa procedura avrà esito negativo se eseguita in un set di raccolta configurato per la modalità di raccolta in modalità memorizzata nella cache.  
  
 sp_syscollector_run_collection_set consente a un utente di acquisire snapshot dei dati su richiesta.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@collection_set_id =** ] *collection_set_id*  
 Identificatore univoco locale del set di raccolta. *collection_set_id* è **int** e deve avere un valore se *nome* è NULL.  
  
 [  **@name =** ] **'***nome***'**  
 Nome del set di raccolta. *nome* è **sysname** e deve avere un valore se *collection_set_id* è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Entrambi *collection_set_id* o *nome* deve avere un valore, non possono essere entrambi NULL.  
  
 Questa procedura verrà avviare la raccolta e caricare i processi per set di raccolta specificata e avvierà immediatamente il processo dell'agente di raccolta se il set di raccolta ha relativo  **@collection_mode**  impostato su non memorizzati nella cache (1). Per ulteriori informazioni, vedere [sp_syscollector_create_collection_set &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 È possibile utilizzare sp_sycollector_run_collection_set anche per eseguire un set di raccolta senza una pianificazione.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **dc_operator** (con autorizzazione EXECUTE) ruolo predefinito del database per eseguire questa procedura.  
  
## <a name="example"></a>Esempio  
 Avviare un set di raccolta utilizzandone l'identificatore.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
