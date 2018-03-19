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

Consente di concatenare un numero variabile di argomenti con un delimitatore specificato nel primo argomento. (`CONCAT_WS` indica *concatenare con separatore*.)

##  <a name="syntax"></a>Sintassi   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>Argomenti   
separator  
Espressione di qualsiasi tipo di carattere (`nvarchar`, `varchar`, `nchar` o `char`).

argument1, argument2, argument*N*  
Espressione di qualsiasi tipo.

## <a name="return-types"></a>Tipi restituiti
Proprietà di tipo String. La lunghezza e il tipo dipendono dall'input.

## <a name="remarks"></a>Remarks   
`CONCAT_WS` consente di accettare un numero variabile di argomenti e di concatenarli in una singola stringa usando il primo argomento come separatore. È richiesto un separatore e un minimo di due argomenti . In caso contrario, viene generato un errore. Tutti gli argomenti vengono convertiti in modo implicito nei tipi di stringa e successivamente concatenati. 

Per la conversione implicita in stringhe vengono seguite le regole esistenti per le conversioni dei tipi di dati. Per altre informazioni sul comportamento e le conversioni dei tipi di dati, vedere [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Trattamento dei valori NULL

`CONCAT_WS` ignora l'impostazione `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}`.

Se tutti gli argomenti sono Null, viene restituita una stringa vuota di tipo `varchar(1)`. 

I valori Null vengono ignorati durante la concatenazione e non viene aggiunto il separatore. Ciò semplifica lo scenario comune di concatenazione di stringhe che contengono spesso valori vuoti, ad esempio un secondo campo dell'indirizzo. Vedere l'esempio B.

Se lo scenario richiede che i valori Null vengano inclusi con un separatore, vedere l'esempio C usando la funzione `ISNULL`.

## <a name="examples"></a>Esempi   

### <a name="a--concatenating-values-with-separator"></a>A.  Concatenazione di valori con separatore
Nell'esempio seguente viene illustrato come concatenare tre colonne della tabella sys.databases, separando i valori con un `- `.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - NONE |
|2 - SIMPLE - NONE |
|3 - FULL - NONE |
|4 - SIMPLE - NONE |


### <a name="b--skipping-null-values"></a>B.  Ignorare i valori Null
Nell'esempio seguente vengono ignorati i valori `NULL` nell'elenco degli argomenti.

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
Nell'esempio seguente viene usata una virgola come separatore e viene aggiunto il carattere di ritorno a capo per determinare il formato dei valori separati da virgola della colonna.

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

CONCAT_WS ignorerà i valori Null nelle colonne. Se alcune colonne sono di tipo nullable, eseguirne il wrapping con la funzione `ISNULL` e specificare il valore predefinito come nell'esempio seguente:

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
 [Funzioni stringa &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  

