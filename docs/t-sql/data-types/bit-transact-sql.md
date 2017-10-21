---
title: bit (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bit_TSQL
- bit
dev_langs:
- TSQL
helpviewer_keywords:
- bit data type
ms.assetid: 40adfd08-a31c-49cb-a172-386bcaa6edee
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3817549e5846c68b422fb941907860896b956d9a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="bit-transact-sql"></a>bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Tipo di dati integer che può accettare un valore di 1, 0 o NULL.  
  
## <a name="remarks"></a>Osservazioni  
Il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Ottimizza l'archiviazione di **bit** colonne. Se sono presenti o inferiore a 8 **bit** colonne in una tabella, le colonne vengono archiviate come 1 byte. Se sono presenti da 9 a 16 **bit** colonne, le colonne vengono archiviate come 2 byte e così via.
  
I valori stringa TRUE e FALSE possono essere convertiti in **bit** valori: TRUE viene convertito in 1 e FALSE viene convertito in 0.
  
Nelle conversioni nel tipo di dati bit i valori diversi da zero vengono promossi a 1.
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Sys. Types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

