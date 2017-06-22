---
title: Includere valori in JSON - Opzione INCLUDE_NULL_VALUES | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- INCLUDE_NULL_VALUES (FOR JSON)
ms.assetid: 06873768-3778-4ed8-a1db-61758726bda0
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 2cdb047169569041e3a8f7890d8215fd87284959
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="include-null-values-in-json---includenullvalues-option"></a>Includere valori in JSON - Opzione INCLUDE_NULL_VALUES
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Per includere valori Null nell'output JSON della clausola **FOR JSON** , specificare l'opzione **INCLUDE_NULL_VALUES** .  
  
 Se non si specifica l'opzione **INCLUDE_NULL_VALUES** , l'output JSON non includerà le proprietà per i valori Null presenti nei risultati della query.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente illustra l'output della clausola **FOR JSON** con e senza l'opzione **INCLUDE_NULL_VALUES**  
  
|Senza l'opzione **INCLUDE_NULL_VALUES**|Con l'opzione **INCLUDE_NULL_VALUES**|  
|--------------------------------------------------|-----------------------------------------------|  
|`{    "name": "John",    "surname": "Doe" }`|`{    "name": "John",    "surname": "Doe",    "age": null,    "phone": null }`|  
  
 Ecco un altro esempio di clausola **FOR JSON** con l'opzione **INCLUDE_NULL_VALUES** .  
  
 **Query**  
  
```sql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO, INCLUDE_NULL_VALUES    
```  
  
 **Risultato**  
  
```json  
[{
    "name": "John",
    "surname": null
}, {
    "name": "Jane",
    "surname": "Doe"
}] 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Acquisire familiarità con il supporto JSON integrato in SQL Server  
Per un numero elevato di soluzioni specifiche, casi di utilizzo e indicazioni, vedere il [post di blog sul supporto JSON predefinito](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e Database SQL di Azure per Microsoft Program Manager Jovan Popovic.  

## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

