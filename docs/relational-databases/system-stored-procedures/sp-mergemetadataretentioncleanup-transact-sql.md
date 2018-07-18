---
title: sp_mergemetadataretentioncleanup (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4ac0c7820ab4f336057a3d747409b0e1af09248d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32996088"
---
# <a name="spmergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue una pulizia manuale dei metadati nel [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_ mapping](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), e [MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md) tabelle di sistema. Questa stored procedure viene eseguita in ogni server di pubblicazione e in ogni Sottoscrittore incluso nella topologia.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@num_genhistory_rows=** ] *num_genhistory_rows* OUTPUT  
 Restituisce il numero di righe rimosse dal [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md) tabella. *num_genhistory_rows* viene **int**, il valore predefinito è **0**.  
  
 [  **@num_contents_rows=** ] *num_contents_rows* OUTPUT  
 Restituisce il numero di righe rimosse dal [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) tabella. *num_contents_rows* viene **int**, il valore predefinito è **0**.  
  
 [  **@num_tombstone_rows=** ] *num_tombstone_rows* OUTPUT  
 Restituisce il numero di righe rimosse dal [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) tabella. *num_tombstone_rows* viene **int**, il valore predefinito è **0**.  
  
 [  **@aggressive_cleanup_only=** ] *aggressive_cleanup_only*  
 Solo per uso interno.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
  
> [!IMPORTANT]  
>  Se sono presenti più pubblicazioni in un database, e uno di tali pubblicazioni viene utilizzato un periodo di memorizzazione infinito, in esecuzione **sp_mergemetadataretentioncleanup** non pulizia il rilevamento delle modifiche di tipo merge della replica metadati per il database. È pertanto opportuno utilizzare il periodo di memorizzazione infinito con cautela. Per determinare se una pubblicazione presenta un periodo di memorizzazione indefinito, eseguire [sp_helpmergepublication &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) di pubblicazione e annotare tutte le pubblicazioni nel risultato impostare con il valore **0** per **memorizzazione**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **db_owner** fissa utenti nell'elenco di accesso alla pubblicazione o ruolo del database per un database pubblicato può eseguire **sp_mergemetadataretentioncleanup**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
