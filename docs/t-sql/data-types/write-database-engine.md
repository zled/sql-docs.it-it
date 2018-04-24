---
title: Write (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 984f54540aa43c238a2139ca4d40c7ee1f9b76b2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="write-database-engine"></a>Write (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Write scrive una rappresentazione binaria di **SqlHierarchyId** nell'oggetto **BinaryWriter** passato. Write non può essere chiamato usando [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilizzare invece CAST o CONVERT.
  
## <a name="syntax"></a>Sintassi  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Argomenti  
*w*  
Oggetto **BinaryWriter** su cui verrà scritta la rappresentazione binaria di questo nodo **hierarchyid**.
  
## <a name="return-types"></a>Tipi restituiti  
**Tipo CLR restituito: void**
  
## <a name="remarks"></a>Remarks  
Write viene usato internamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando è necessario, ad esempio in caso di caricamento di dati da una colonna **hierarchyid**. Write viene anche chiamato internamente in caso di esecuzione di una conversione tra **hierarchyid** e **varbinary**.
  
## <a name="examples"></a>Esempi  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>Vedere anche
[Read &#40;motore di database&#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40;motore di database&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
