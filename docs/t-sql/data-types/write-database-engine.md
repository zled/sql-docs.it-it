---
title: Write (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs: TSQL
helpviewer_keywords: Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11980f26c4af4a2dabb57e5cce242d7e89028d16
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="write-database-engine"></a>Write (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Scrive una rappresentazione binaria di scrivere **SqlHierarchyId** per passato **BinaryWriter**. Scrittura non può essere chiamata tramite [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilizzare invece CAST o CONVERT.
  
## <a name="syntax"></a>Sintassi  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Argomenti  
*w*  
Oggetto **BinaryWriter** oggetto a cui la rappresentazione binaria dell'oggetto **hierarchyid** nodo verrà scritto.
  
## <a name="return-types"></a>Tipi restituiti  
**Tipo CLR restituito: void**
  
## <a name="remarks"></a>Osservazioni  
Scrittura viene utilizzata internamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando è necessario, ad esempio durante il caricamento di dati da un **hierarchyid** colonna. Scrittura viene inoltre chiamata internamente quando viene eseguita una conversione tra **hierarchyid** e **varbinary**.
  
## <a name="examples"></a>Esempi  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>Vedere anche
[Lettura &#40; motore di Database &#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40; motore di Database &#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
