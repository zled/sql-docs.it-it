---
title: masked_columns (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: be64d748a3bd1a283c917490bc1a916118834b82
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysmaskedcolumns-transact-sql"></a>masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Utilizzare il **masked_columns** vista per eseguire query per tabelle e colonne che dispongono di una funzione applicata di maschera dati dinamici. Questa vista viene ereditata dalla vista **sys.columns** , che restituisce tutte le colonne della vista **sys.columns** , in aggiunta alle colonne **is_masked** e **masking_function** , che indicano se la colonna è nascosta e, in tal caso, quale funzione di maschera viene definita. Questa vista mostra solo le colonne su cui è applicata una funzione di maschera.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto a cui appartiene la colonna.|  
|name|**sysname**|Nome della colonna. Valore univoco all'interno dell'oggetto.|  
|column_id|**int**|ID della colonna. Valore univoco all'interno dell'oggetto.<br /><br /> È possibile che gli ID di colonna non siano sequenziali.|  
|**Sys. masked_columns** restituisce molte altre colonne ereditate da **Sys. Columns**.|vari|Vedere [Sys. Columns &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) per altre definizioni di colonna.|  
|is_masked|**bit**|Indica se la colonna è nascosta. 1 indica mascherato.|  
|masking_function|**nvarchar(4000)**|Funzione di maschera per la colonna.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista restituisce informazioni sulle tabelle in cui l'utente disponga di autorizzazioni per la tabella o se l'utente dispone dell'autorizzazione VIEW ANY DEFINITION.  
  
## <a name="example"></a>Esempio  
 La query seguente join **masked_columns** a **Sys. Tables** per restituire informazioni su tutti i colonne mascherate.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Maschera dati dinamica](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
