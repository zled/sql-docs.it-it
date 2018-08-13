---
title: masked_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 64461261b624ace154376250419ec2e9a2f6ac89
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39558931"
---
# <a name="sysmaskedcolumns-transact-sql"></a>masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Usare la **masked_columns** vista alla query per tabelle e colonne che hanno una funzione applicata di maschera dati dinamici. Questa vista viene ereditata dalla vista **sys.columns** , che restituisce tutte le colonne della vista **sys.columns** , in aggiunta alle colonne **is_masked** e **masking_function** , che indicano se la colonna è nascosta e, in tal caso, quale funzione di maschera viene definita. Questa vista mostra solo le colonne su cui è applicata una funzione di maschera.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID dell'oggetto a cui appartiene la colonna.|  
|NAME|**sysname**|Nome della colonna. Valore univoco all'interno dell'oggetto.|  
|column_id|**int**|ID della colonna. Valore univoco all'interno dell'oggetto.<br /><br /> È possibile che gli ID di colonna non siano sequenziali.|  
|**masked_columns** restituisce troppe colonne ereditate da **Sys. Columns**.|vari|Visualizzare [Sys. Columns &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) per altre definizioni di colonna.|  
|is_masked|**bit**|Indica se la colonna è nascosta. 1 indica mascherato.|  
|masking_function|**nvarchar(4000)**|La funzione di maschera della colonna.|  
  
## <a name="remarks"></a>Note  
  
## <a name="permissions"></a>Permissions  
 Questa vista restituisce informazioni sulle tabelle in cui l'utente ha una sorta di autorizzazione per la tabella o se l'utente ha l'autorizzazione VIEW ANY DEFINITION.  
  
## <a name="example"></a>Esempio  
 La query seguente join **masked_columns** al **Sys. Tables** per restituire le informazioni relative a tutte le colonne mascherate.  
  
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
  
  
