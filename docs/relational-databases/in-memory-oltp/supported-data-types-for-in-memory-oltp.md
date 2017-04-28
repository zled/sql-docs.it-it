---
title: Tipi di dati supportati per OLTP in memoria | Microsoft Docs
ms.custom: 
ms.date: 05/27/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a928c1f77586198fd0d33cafa445ea406a437c6b
ms.lasthandoff: 04/11/2017

---
# <a name="supported-data-types-for-in-memory-oltp"></a>Tipi di dati supportati per OLTP In memoria
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questo articolo elenca i tipi di dati che non sono supportati per le funzionalità OLTP In memoria di:  
  
-   Tabelle con ottimizzazione per la memoria  
  
-   Stored procedure compilate in modo nativo  
  
## <a name="unsupported-data-types"></a>Tipi di dati non supportati  
 I tipi di dati indicati di seguito non sono supportati:  
  
||||  
|-|-|-|  
|[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography &#40;Transact-SQL&#41;](../../t-sql/spatial-geography/spatial-types-geography.md)|[geometry &#40;Transact-SQL&#41;](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md)|  
|[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)|[xml &#40;Transact-SQL&#41;](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)|Tipi definiti dall'utente|.|  
  
## <a name="notable-supported-data-types"></a>Tipi di dati supportati rilevanti  
 La maggior parte dei tipi di dati è supportata dalle funzionalità di OLTP In memoria. Di seguito sono riportati alcuni tipi che vale la pena notare in modo esplicito:  
  
|Tipi stringa e binari|Per ulteriori informazioni|  
|-----------------------------|--------------------------|  
|binary e varbinary*|[binary e varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char e varchar*|[char e varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar e nvarchar*|[nchar e nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
Per i precedenti tipi di dati string e binary, a partire da SQL Server 2016:  
  
- Una singola tabella con ottimizzazione per la memoria può contenere anche diverse colonne di grandi dimensioni, ad esempio `nvarchar(4000)`, anche se il totale delle relative lunghezze sarebbe superiore a quello delle dimensioni fisiche della riga di 8060 byte.  
  
- Una tabella con ottimizzazione per la memoria può includere colonne di tipo string e binary di lunghezza massima dei tipi di dati, ad esempio `varchar(max)`.  


### <a name="identify-lobs-and-other-columns-that-are-off-row"></a>Identificare le colonne LOB e altre colonne che si trovano all'esterno di righe

L'istruzione Transact-SQL SELECT seguente restituisce tutte le colonne che si trovano all'esterno di righe, per tabelle con ottimizzazione per la memoria. Tenere presente quanto segue:

- Tutte le colonne chiave di indice vengono archiviate all'interno di righe.
  - Le chiavi di indice non univoche possono ora includere colonne che ammettono valori Null in tabelle con ottimizzazione per la memoria.
  - Gli indici possono essere dichiarati come UNIQUE in una tabella con ottimizzazione per la memoria.
- Tutte le colonne LOB vengono archiviate all'esterno di righe.
- Un valore max_length pari a -1 indica una colonna con oggetti LOB.


```tsql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


#### <a name="natively-compiled-modules-support-for-lobs"></a>Supporto dei moduli compilati in modalità per le colonne LOB


Quando si usa una funzione per i valori stringa predefinita in moduli compilati in modalità nativa, ad esempio un processo nativo, la funzione può accettare un tipo di stringa LOB. In un processo nativo, ad esempio, la funzione LTrim può inserire un parametro di tipo nvarchar(max) o varbinary(max).

Queste colonne LOB possono essere il tipo restituito da una funzione definita dall'utente scalare compilata in modalità nativa.


### <a name="other-data-types"></a>Altri tipi di dati


|Altri tipi|Per ulteriori informazioni|  
|-----------------|--------------------------|  
|tipi di tabella|[Variabili di tabella con ottimizzazione per la memoria](http://msdn.microsoft.com/library/bd102e95-53e2-4da6-9b8b-0e4f02d286d3)|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di Transact-SQL per OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [Implementazione di colonne LOB in una tabella con ottimizzazione per la memoria](http://msdn.microsoft.com/en-us/bd8df0a5-12b9-4f4c-887c-2fb78dd79f4e)   
 [Implementazione di SQL_VARIANT in una tabella con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  

