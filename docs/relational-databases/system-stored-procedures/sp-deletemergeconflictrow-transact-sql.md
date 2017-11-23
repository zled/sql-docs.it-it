---
title: sp_deletemergeconflictrow (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords: sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e085a7010f25f40b95a45d8ddd0c7b455d7266c6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina righe da una tabella dei conflitti o [MSmerge_conflicts_info &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella. Questa stored procedure viene eseguita nella stessa posizione di archiviazione della tabella con conflitti in qualsiasi database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@conflict_table=**] **'***conflict_table***'**  
 Nome della tabella dei conflitti. *conflict_table* è **sysname**, il valore predefinito è  **%** . Se il *conflict_table* è specificato come NULL o  **%** , il conflitto si presuppone che sia un conflitto di eliminazione e la riga corrispondente *rowguid* e *origin_datasource* e *source_object* viene eliminato dal [MSmerge_conflicts_info &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella.  
  
 [  **@source_object=**] **'***source_object***'**  
 Nome della tabella di origine. *source_object* è **nvarchar (386)**, con un valore predefinito è NULL.  
  
 [  **@rowguid =**] **'***rowguid***'**  
 Identificatore di riga per il conflitto di eliminazione. *ROWGUID* è **uniqueidentifier**, non prevede alcun valore predefinito.  
  
 [  **@origin_datasource=**] **'***origin_datasource***'**  
 Origine del conflitto. *origin_datasource* è **varchar (255)**, non prevede alcun valore predefinito.  
  
 [  **@drop_table_if_empty=**] **'***drop_table_if_empty***'**  
 Flag che indica che il *conflict_table* deve essere eliminata se è vuota. *drop_table_if_empty* è **varchar (10)**, con un valore predefinito è FALSE.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_deletemergeconflictrow** viene utilizzata nella replica di tipo merge.  
  
 [MSmerge_conflicts_info &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella è una tabella di sistema e non viene eliminata dal database, anche se è vuota.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
