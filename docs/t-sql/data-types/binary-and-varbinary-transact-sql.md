---
title: binary e varbinary (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 8/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- binary_TSQL
- varbinary_TSQL
- binary
- varbinary
dev_langs:
- TSQL
helpviewer_keywords:
- varbinary data type
- binary [SQL Server], about binary data type
ms.assetid: bcce65f9-10db-4b3e-bfaf-dfc06c6f820f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4ad5bce3cacc0f892f7087df785da8cedcb4e932
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="binary-and-varbinary-transact-sql"></a>binary e varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati binary a lunghezza fissa o variabile.
  
## <a name="arguments"></a>Argomenti  
**binario** [(  *n*  )] dati binari di lunghezza fissa con lunghezza  *n*  byte, in cui  *n*  è un valore tra 1 e 8.000. Le dimensioni di archiviazione sono  *n*  byte.
  
**varbinary** [(  *n*   |  **max**)] dati binari a lunghezza variabile. *n*può essere un valore compreso tra 1 e 8.000. **max** indica che le dimensioni massime di archiviazione sono 2 ^ 31-1 byte. Le dimensioni dello spazio di archiviazione corrispondono alla lunghezza effettiva dei dati immessi + 2 byte. È possibile che la lunghezza dei dati immessi sia pari a 0 byte. Il sinonimo ANSI SQL per **varbinary** è **binary varying**.
  
## <a name="remarks"></a>Osservazioni  
Quando  *n*  non è specificato nella definizione dei dati o istruzione di dichiarazione di variabile, la lunghezza predefinita è 1. Quando  *n*  non è specificato con la funzione CAST, la lunghezza predefinita è 30.

| Tipo di dati | Casi di utilizzo |
| --- | --- |
| **binary** | le dimensioni delle voci della colonna sono coerenti.|
| **varbinary** | le dimensioni delle voci della colonna variano notevolmente.|
| **varbinary(max)** | le voci della colonna dati superano a 8.000 byte.|


## <a name="converting-binary-and-varbinary-data"></a>Conversione di dati binary e varbinary
Quando i dati vengono convertiti da un tipo di dati string (**char**, **varchar**, **nchar**, **nvarchar**, **binario**, **varbinary**, **testo**, **ntext**, o **immagine**) a un **binario** o **varbinary** tipo di dati di lunghezza diversa, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue il riempimento o troncamento dei dati a destra. Quando altri tipi di dati vengono convertiti in **binario** o **varbinary**, i dati vengono aggiunti o troncati a sinistra. Il riempimento viene eseguito utilizzando zero esadecimali.
  
La conversione dei dati per il **binario** e **varbinary** tipi di dati è utile se **binario** dati sono il modo più semplice per spostarsi all'interno dei dati. Conversione di un valore di qualsiasi tipo di un valore binario di grandi dimensioni sufficienti e quindi al tipo, comporta sempre lo stesso valore se entrambe le conversioni vengono eseguite nella stessa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La rappresentazione binaria di un valore può variare da una versione all'altra di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
È possibile convertire **int**, **smallint**, e **tinyint** a **binario** o **varbinary**, ma se si convertire il **binario** valore al valore intero, questo valore sarà diverso dal valore integer originale se si è verificato un troncamento. L'istruzione SELECT seguente, ad esempio, mostra che il valore intero `123456` viene in genere archiviato come un dato di tipo binary `0x0001e240`:
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
Tuttavia, le operazioni seguenti `SELECT` istruzione mostra che se il **binario** destinazione è troppo piccola per contenere l'intero valore, le cifre iniziali invisibile all'utente vengono troncate in modo che lo stesso numero viene archiviato come `0xe240`:
  
```sql
SELECT CAST( 123456 AS BINARY(2) );  
```  
  
Il batch seguente illustra come il troncamento automatico possa influire sulle operazioni aritmetiche senza tuttavia generare errori:
  
```sql
DECLARE @BinaryVariable2 BINARY(2);  
  
SET @BinaryVariable2 = 123456;  
SET @BinaryVariable2 = @BinaryVariable2 + 1;  
  
SELECT CAST( @BinaryVariable2 AS INT);  
GO  
```  
  
Il risultato finale è `57921`, non `123457`.
  
> [!NOTE]  
>  Digitare le conversioni tra tutti i dati e **binario** tipi di dati non sono necessariamente essere uguale in versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
