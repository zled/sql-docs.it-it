---
title: Simulazione di un&quot;istruzione IF-WHILE EXISTS in un modulo compilato in modo nativo | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d509d0d749591a134a0b87aa457bb53d28901a99
ms.lasthandoff: 04/11/2017

---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>Simulazione di un'istruzione IF-WHILE EXISTS in un modulo compilato in modo nativo
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Le stored procedure compilate in modo nativo non supportano la clausola **EXISTS** nelle istruzioni condizionali come IF e WHILE.  
  
 L'esempio seguente illustra una soluzione alternativa che usa una variabile BIT con un'istruzione SELECT per simulare una clausola EXISTS:  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di migrazione relativi alle stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Costrutti Transact-SQL non supportati da OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
