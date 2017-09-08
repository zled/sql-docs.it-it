---
title: GetRoot (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4de7e4010400cbf3d192efb3dd6709792d734ba
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="getroot-database-engine"></a>GetRoot (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce la radice dell'albero gerarchico. GetRoot () è un metodo statico.
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  
  
## <a name="return-types"></a>Tipi restituiti  
**Tipo: hierarchyid restituito SQL Server**
  
**Tipo CLR restituito: SqlHierarchyId**
  
## <a name="remarks"></a>Osservazioni  
Utilizzato per determinare il nodo radice in un albero gerarchico.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-transact-sql-example"></a>A. Esempio Transact-SQL  
Nell'esempio seguente viene restituita la radice dell'albero gerarchico:
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>B. Esempio CLR  
Frammento di codice seguente chiama il metodo getRoot ():
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>Vedere anche
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

