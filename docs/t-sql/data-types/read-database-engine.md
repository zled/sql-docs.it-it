---
title: Lettura (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21f27c627a36f747d9e3ecbb52d14d1ac6bc5d28
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="read-database-engine"></a>Read (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Lettura legge una rappresentazione binaria di **SqlHierarchyId** da passato **BinaryReader** e imposta il **SqlHierarchyId** oggetto con tale valore. Lettura non può essere chiamato tramite [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilizzare invece CAST o CONVERT.
  
## <a name="syntax"></a>Sintassi  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>Argomenti  
*r*  
 Il **BinaryReader** oggetto che produce un flusso binario corrispondente a una rappresentazione binaria di un **hierarchyid** nodo.  
  
## <a name="return-types"></a>Tipi restituiti
 **Tipo CLR restituito: void**  
  
## <a name="remarks"></a>Osservazioni  
 Lettura non di convalida dell'input. Se viene fornito un input binario non valido, lettura potrebbe generare un'eccezione. O potrebbe avere esito positivo e produrre un oggetto non valido **SqlHierarchyId** oggetto i cui metodi possono restituire risultati imprevisti o generare un'eccezione.  
  
 Lettura può essere chiamato solo su un oggetto appena creato **SqlHierarchyId** oggetto.  
  
 Lettura viene utilizzato internamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando è necessario, ad esempio durante la scrittura di dati **hierarchyid** colonna. Lettura viene inoltre chiamato internamente quando viene eseguita una conversione tra **varbinary** e **hierarchyid**.  
  
## <a name="examples"></a>Esempi  
  
```sql
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>Vedere anche  
[Scrittura &#40; motore di Database &#41;](../../t-sql/data-types/write-database-engine.md)  
[ToString &#40; motore di Database &#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

