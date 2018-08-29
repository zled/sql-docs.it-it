---
title: sp_deletemergeconflictrow (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4290c07ddb9e7f352c6fe6177205ce6add03ead
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017394"
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono eliminate righe da una tabella dei conflitti o la [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella. Questa stored procedure viene eseguita nella stessa posizione di archiviazione della tabella con conflitti in qualsiasi database.  
  
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
 Nome della tabella dei conflitti. *conflict_table* viene **sysname**, il valore predefinito è **%**. Se il *conflict_table* è specificato come NULL oppure **%**, il conflitto si presuppone che sia un conflitto di eliminazione e la riga corrispondente *rowguid* e*origin_datasource* e *source_object* viene eliminato dal [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella.  
  
 [  **@source_object=**] **'***source_object***'**  
 Nome della tabella di origine. *source_object* viene **nvarchar(386)**, con un valore predefinito è NULL.  
  
 [  **@rowguid =**] **'***rowguid***'**  
 Identificatore di riga per il conflitto di eliminazione. *ROWGUID* viene **uniqueidentifier**, non prevede alcun valore predefinito.  
  
 [  **@origin_datasource=**] **'***origin_datasource***'**  
 Origine del conflitto. *origin_datasource* viene **nvarchar (255)**, non prevede alcun valore predefinito.  
  
 [  **@drop_table_if_empty=**] **'***drop_table_if_empty***'**  
 Flag che indica che il *conflict_table* è deve essere eliminata se risulta vuota. *drop_table_if_empty* viene **varchar (10)**, con un valore predefinito è FALSE.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_deletemergeconflictrow** viene utilizzata nella replica di tipo merge.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella è una tabella di sistema e non viene eliminata dal database, anche se è vuota.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
