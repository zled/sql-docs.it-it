---
title: CONCAT_WS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONCAT_WS
- CONCAT_WS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_WS function
ms.assetid: f1375fd7-a2fd-48bf-922a-4f778f0deb1f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7d7932c1887c82b2a10702f9054706e4cf9bce71
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Consente di concatenare un numero variabile di argomenti con un delimitatore specificato nell'argomento 1. (`CONCAT_WS` indica *concatenate con separatore*.)

##  <a name="syntax"></a>Sintassi   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>Argomenti   
separatore  
È un'espressione di qualsiasi tipo di carattere (`nvarchar`, `varchar`, `nchar`, o `char`).

argomento1, argomento2, argomento*N*  
È un'espressione di qualsiasi tipo.

## <a name="return-types"></a>Tipi restituiti
Proprietà di tipo String. La lunghezza e tipo dipende l'input.

## <a name="remarks"></a>Osservazioni   
`CONCAT_WS`accetta un numero variabile di argomenti che vengono concatenati in un'unica stringa utilizzando il primo argomento come separatore. Richiede un separatore e un minimo di due argomenti. in caso contrario, viene generato un errore. Tutti gli argomenti vengono convertiti in modo implicito in tipi di stringa e vengono quindi concatenati. 

Per la conversione implicita in stringhe vengono seguite le regole esistenti per le conversioni dei tipi di dati. Per ulteriori informazioni sulle conversioni dei tipi di comportamento e i dati, vedere [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Trattamento dei valori NULL

`CONCAT_WS`Ignora il `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}` impostazione.

Se tutti gli argomenti sono null, una stringa vuota di tipo `varchar(1)` viene restituito. 

I valori null vengono ignorati durante la concatenazione e non aggiunge il separatore. Ciò semplifica lo scenario comune di concatenazione di stringhe che contengono spesso valori vuoti, ad esempio un secondo campo dell'indirizzo. Vedere l'esempio B.

Se lo scenario richiede i valori null deve essere incluso con un separatore, vedere l'esempio C utilizzando la `ISNULL` (funzione).

## <a name="examples"></a>Esempi   

### <a name="a--concatenating-values-with-separator"></a>A.  Concatenazione di valori con separatore
Nell'esempio seguente consente di concatenare tre colonne della tabella di Sys. Databases, separare i valori con un `- `.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - NESSUNO |
|2 - SIMPLE - NESSUNO |
|3 - COMPLETO - NESSUNO |
|4 - SIMPLE - NESSUNO |


### <a name="b--skipping-null-values"></a>B.  Ignorare i valori NULL
Nell'esempio seguente viene ignorato `NULL` valori nell'elenco degli argomenti.

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>C.  Generazione di file CSV da tabella
Nell'esempio seguente viene utilizzata una virgola come separatore e aggiunge il ritorno a capo per determinare il formato della colonna con i valori separati.

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, recovery_model_desc, containment_desc), char(13)) AS DatabaseInfo
FROM sys.databases
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
DatabaseInfo
------------   
1,SIMPLE,NONE
2,SIMPLE,NONE
3,FULL,NONE 
4,SIMPLE,NONE 
```

CONCAT_WS ignorerà i valori NULL nelle colonne. Se alcune colonne sono nullable, eseguirne il wrapping con `ISNULL` funzione e fornire valore predefinito come nell'esempio seguente:

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>Vedere anche
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  

