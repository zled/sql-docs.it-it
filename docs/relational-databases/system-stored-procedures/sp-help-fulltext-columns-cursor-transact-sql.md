---
title: sp_help_fulltext_columns_cursor (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns_cursor
- sp_help_fulltext_columns_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_columns_cursor
ms.assetid: 26054e76-53b7-4004-8d48-92ba3435e9d7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce3850391a0bfe07e228b9f7c57984fdbeb0f886
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpfulltextcolumnscursor-transact-sql"></a>sp_help_fulltext_columns_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilizza un cursore per restituire le colonne impostate per l'indicizzazione full-text.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilizzare il [fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) vista del catalogo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_fulltext_columns_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@cursor_return =**]  *@cursor_variable*  OUTPUT  
 Variabile di output di tipo **cursore**. Il cursore restituito è di tipo scorrevole, dinamico e di sola lettura.  
  
 [  **@table_name =**] **'***table_name***'**  
 Nome della tabella composto da una o due parti su cui si desidera ottenere informazioni relative all'indice full-text. *TABLE_NAME* è **nvarchar (517)**, con un valore predefinito null. Se *table_name* viene omesso, vengono recuperate informazioni di colonna di indice full-text per ogni tabella indicizzata full-text.  
  
 [  **@column_name =**] **'***column_name***'**  
 Nome della colonna per cui vengono richiesti metadati di indice full-text. *column_name* è **sysname** con un valore predefinito null. Se *column_name* viene omesso oppure è NULL, vengono restituite informazioni di colonna full-text per ogni colonna indicizzata full-text per *table_name*. Se *table_name* anche viene omesso oppure è NULL, vengono restituite informazioni di colonna di indice full-text per ogni colonna indicizzata full-text per tutte le tabelle nel database.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Proprietario della tabella. Corrisponde al nome dell'utente del database che ha creato la tabella.|  
|**TABLE_ID**|**int**|ID della tabella.|  
|**TABLE_NAME**|**sysname**|Nome della tabella.|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|Colonna impostata per l'indicizzazione in una tabella indicizzata full-text.|  
|**FULLTEXT_COLID**|**int**|ID della colonna indicizzata full-text.|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|Colonna di una tabella indicizzata full-text che specifica il tipo di documento della colonna indicizzata full-text. Questo valore è applicabile solo quando la colonna indicizzata full-text è un **varbinary (max)** o **immagine** colonna.|  
|**FULLTEXT_BLOBTP_COLID**|**int**|ID della colonna per il tipo di documento. Questo valore è applicabile solo quando la colonna indicizzata full-text è un **varbinary (max)** o **immagine** colonna.|  
|**FULLTEXT_LANGUAGE**|**sysname**|Lingua utilizzata per la ricerca full-text nella colonna.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione vengono assegnate per impostazione predefinita ai membri del ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sulle colonne impostate per l'indicizzazione full-text in tutte le tabelle del database.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_columns_cursor @mycursor OUTPUT  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Vedere anche  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
