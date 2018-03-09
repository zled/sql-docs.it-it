---
title: masked_columns (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7855e2d4ccf46977138cff813d27266d90e0fa86
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysmaskedcolumns-transact-sql"></a>masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Utilizzare il **masked_columns** vista per eseguire query per tabelle e colonne che dispongono di una funzione applicata di maschera dati dinamici. Questa vista viene ereditata dalla vista **sys.columns** , che restituisce tutte le colonne della vista **sys.columns** , in aggiunta alle colonne **is_masked** e **masking_function** , che indicano se la colonna è nascosta e, in tal caso, quale funzione di maschera viene definita. Questa vista mostra solo le colonne su cui è applicata una funzione di maschera.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto a cui appartiene la colonna.|  
|name|**sysname**|Nome della colonna. Valore univoco all'interno dell'oggetto.|  
|column_id|**int**|ID della colonna. Valore univoco all'interno dell'oggetto.<br /><br /> È possibile che gli ID di colonna non siano sequenziali.|  
|**masked_columns** restituisce colonne ereditate da **Columns**.|vari|Vedere [Columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) per più definizioni di colonna.|  
|is_masked|**bit**|Indica se la colonna è nascosta. 1 indica mascherato.|  
|masking_function|**nvarchar(4000)**|Funzione di maschera per la colonna.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="permissions"></a>Permissions  
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
  
  
