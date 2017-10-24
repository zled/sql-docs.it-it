---
title: DROP SEARCH PROPERTY LIST (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_SEARCH_PROPERTY_LIST_TSQL
- DROP SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- DROP SEARCH PROPERTY LIST statement
- search property lists [SQL Server], dropping
- search property lists [SQL Server], deleting
ms.assetid: 7c7ce52a-6b77-4a1c-9abf-d5feb664bea8
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 970fd636239f6de212d667ef6ec22edfa182859c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-search-property-list-transact-sql"></a>DROP SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Elimina un elenco di proprietà dal database corrente se l'elenco delle proprietà di ricerca non è attualmente associato a un indice full-text nel database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP SEARCH PROPERTY LIST property_list_name  
;  
```  
  
## <a name="arguments"></a>Argomenti  
 *property_list_name*  
 Nome dell'elenco delle proprietà di ricerca da eliminare. *property_list_name* è un identificatore.  
  
 Per visualizzare i nomi degli elenchi di proprietà esistenti, utilizzare il [registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) vista del catalogo come indicato di seguito:  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
## <a name="remarks"></a>Osservazioni  
 Non è possibile eliminare un elenco di proprietà di ricerca da un database se l'elenco è associato a un indice full-text e i relativi tentativi avranno esito negativo. Per eliminare un elenco di proprietà di ricerca da un determinato indice full-text, utilizzare il [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) istruzione e specificare la clausola SET SEARCH PROPERTY LIST con off o il nome di un altro elenco di proprietà di ricerca.  
  
 **Per visualizzare le proprietà sono elencate in un'istanza del server**  
  
-   [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 **Per visualizzare la proprietà elenchi associati agli indici full-text**  
  
-   [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
 **Per rimuovere un elenco di proprietà da un indice full-text**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione CONTROL per l'elenco delle proprietà di ricerca.  
  
> [!NOTE]  
>  Le autorizzazioni CONTROL possono essere concesse per l'elenco dal proprietario dell'elenco di proprietà. Per impostazione predefinita, l'utente che crea un elenco di proprietà di ricerca è il proprietario. Il proprietario può essere modificato utilizzando il [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato l'elenco di proprietà `JobCandidateProperties` dal database `AdventureWorks2012`.  
  
```  
DROP SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Sys. registered_search_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [registered_search_property_lists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
  

