---
title: CREARE lo schema di partizione (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE PARTITION SCHEME
- SCHEME
- PARTITION SCHEME
- CREATE_PARTITION_SCHEME_TSQL
- SCHEME_TSQL
- PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- partitioned indexes [SQL Server], schemes
- partitioned tables [SQL Server], schemes
- CREATE PARTITION SCHEME statement
- partition schemes [SQL Server], creating
- filegroups [SQL Server], partitions
- partitioned indexes [SQL Server], filegroups
- partitioned tables [SQL Server], filegroups
- mapping partitions [SQL Server]
ms.assetid: 5b21c53a-b4f4-4988-89a2-801f512126e4
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 13bd8b623604f8bfe93dcf4483c65be14f43f003
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-partition-scheme-transact-sql"></a>CREATE PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea uno schema nel database corrente per l'esecuzione del mapping tra le partizioni di una tabella o un indice partizionato e i filegroup. Il numero e il dominio delle partizioni di una tabella o un indice partizionato vengono determinati da una funzione di partizione. Una funzione di partizione deve essere creata prima in un [CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md) istruzione prima di creare uno schema di partizione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE PARTITION SCHEME partition_scheme_name  
AS PARTITION partition_function_name  
[ ALL ] TO ( { file_group_name | [ PRIMARY ] } [ ,...n ] )  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *partition_scheme_name*  
 Nome dello schema di partizione. I nomi degli schemi di partizione devono essere univoci all'interno del database e conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 *partition_function_name*  
 Nome della funzione di partizione che usano lo schema di partizione. Sulle partizioni create dalla funzione di partizione viene eseguito il mapping ai filegroup specificati nello schema di partizione. *partition_function_name* deve esistere nel database. In una singola partizione non possono essere presenti sia filegroup FILESTREAM che filegroup non FILESTREAM.  
  
 ALL  
 Specifica che tutte le partizioni sono mappate al filegroup specificato *file_group_name*, o per il filegroup primario se **[**primario**]** specificato. Se si specifica ALL, sola *file_group_name* può essere specificato.  
  
 *file_group_name* | **[** primario **]** [ **,***... n*]  
 Specifica i nomi dei filegroup per contenere le partizioni specificate da *partition_function_name*. *file_group_name* deve esistere nel database.  
  
 Se **[**primario**]** viene specificato, la partizione viene archiviata nel filegroup primario. Se si specifica ALL, sola *file_group_name* può essere specificato. Le partizioni vengono assegnate ai filegroup, a partire dalla partizione 1, nell'ordine in cui sono elencati i filegroup in [**,***... n*]. Lo stesso *file_group_name* può essere specificato più volte in [**,***... n*]. Se  *n*  non è sufficiente per contenere il numero di partizioni specificate nella *partition_function_name*, CREATE PARTITION SCHEME ha esito negativo con un errore.  
  
 Se *partition_function_name* genera partizioni inferiore ai filegroup, dal primo filegroup non assegnato viene contrassegnato come NEXT USED e viene visualizzato un messaggio di informazioni denominazione filegroup NEXT USED. Se si specifica ALL, l'unico *file_group_name* mantiene la proprietà NEXT USED per questo *partition_function_name*. Il filegroup NEXT USED riceverà una partizione aggiuntiva se ne viene creata una in un'istruzione ALTER PARTITION FUNCTION. Per creare filegroup non assegnati aggiuntivi per contenere le nuove partizioni, usare ALTER PARTITION SCHEME.  
  
 Quando si specifica il filegroup primario in *file_group_name* [1**,***... n*], database primario deve essere delimitato, ad esempio **[**primario**]** , poiché si tratta di una parola chiave.  
  
 L'unico valore supportato per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] è PRIMARY. Nell'esempio riportato di seguito E, vedere. 
  
## <a name="permissions"></a>Permissions  
 Per eseguire l'istruzione CREATE PARTITION SCHEME, è necessario usare le autorizzazioni seguenti:  
  
-   Autorizzazione ALTER ANY DATASPACE. Questa autorizzazione viene concessa per impostazione predefinita al ruolo predefinito del server **sysadmin** e ai ruoli predefiniti del database **db_owner** e **db_ddladmin** .  
  
-   Autorizzazione CONTROL o ALTER per il database nel quale viene creato lo schema di partizione.  
  
-   Autorizzazione CONTROL SERVER o ALTER ANY DATABASE per il server del database nel quale viene creato lo schema di partizione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-partition-scheme-that-maps-each-partition-to-a-different-filegroup"></a>A. Creazione di uno schema di partizione che esegue il mapping delle singole partizioni a un filegroup diverso  
 Nell'esempio seguente viene creata una funzione di partizione per suddividere una tabella o indice in quattro partizioni. Viene quindi creato uno schema di partizione che definisce i filegroup in cui archiviare le quattro partizioni. Nell'esempio si presuppone che i filegroup esistano già nel database.  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS1  
AS PARTITION myRangePF1  
TO (test1fg, test2fg, test3fg, test4fg);  
```  
  
 Le partizioni di una tabella che utilizza la funzione di partizione `myRangePF1` nella colonna di partizionamento **col1** verrebbe assegnato come illustrato nella tabella seguente.  
  
||||||  
|-|-|-|-|-|  
|**Filegroup**|`test1fg`|`test2fg`|`test3fg`|`test4fg`|  
|**Partizione**|1|2|3|4|  
|**Valori**|**Col1** <= `1`|**col1**  >  `1` AND **col1** <= `100`|**col1**  >  `100` AND **col1** <= `1000`|**Col1** > `1000`|  
  
### <a name="b-creating-a-partition-scheme-that-maps-multiple-partitions-to-the-same-filegroup"></a>B. Creazione di uno schema di partizione che esegue il mapping di più partizioni allo stesso filegroup  
 Se su tutte le partizioni viene eseguito il mapping allo stesso filegroup, usare la parola chiave ALL. Se su più partizioni, ma non su tutte, viene eseguito il mapping allo stesso filegroup, sarà tuttavia necessario ripetere il nome del filegroup come illustrato nell'esempio seguente.  
  
```  
CREATE PARTITION FUNCTION myRangePF2 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS2  
AS PARTITION myRangePF2  
TO ( test1fg, test1fg, test1fg, test2fg );  
```  
  
 Le partizioni di una tabella che utilizza la funzione di partizione `myRangePF2` nella colonna di partizionamento **col1** verrebbe assegnato come illustrato nella tabella seguente.  
  
||||||  
|-|-|-|-|-|  
|**Filegroup**|`test1fg`|`test1fg`|`test1fg`|`test2fg`|  
|**Partizione**|1|2|3|4|  
|**Valori**|**Col1** <= `1`|**col1** > 1 AND **col1** <= `100`|**col1**  >  `100` AND **col1** <= `1000`|**Col1** > `1000`|  
  
### <a name="c-creating-a-partition-scheme-that-maps-all-partitions-to-the-same-filegroup"></a>C. Creazione di uno schema di partizione che esegue il mapping di tutte le partizioni allo stesso filegroup  
 Nell'esempio seguente viene creata la stessa funzione di partizione dell'esempio precedente, ma viene creato uno schema di partizione che mappa tutte le partizioni allo stesso filegroup.  
  
```  
CREATE PARTITION FUNCTION myRangePF3 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS3  
AS PARTITION myRangePF3  
ALL TO ( test1fg );  
```  
  
### <a name="d-creating-a-partition-scheme-that-specifies-a-next-used-filegroup"></a>D. Creazione di uno schema di partizione che specifica un filegroup 'NEXT USED  
 Nell'esempio seguente viene creata la stessa funzione di partizione dell'esempio precedente, ma viene creato uno schema di partizione in cui è elencato un numero di filegroup maggiore delle partizioni create dalla funzione di partizione associata.  
  
```  
CREATE PARTITION FUNCTION myRangePF4 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS4  
AS PARTITION myRangePF4  
TO (test1fg, test2fg, test3fg, test4fg, test5fg)  
```  
  
 L'esecuzione dell'istruzione restituisce il messaggio seguente.  
  
Schema di partizione 'myRangePS4' è stato creato correttamente. 'test5fg' è contrassegnato come successivo filegroup utilizzato nello schema di partizione 'myRangePS4'.  
  
  
 Se la funzione di partizione `myRangePF4` viene modificata in modo da aggiungere una partizione, il filegroup `test5fg` riceverà la nuova partizione creata.  

### <a name="e-creating-a-partition-schema-only-on-primary---only-primary-is-supported-for-includesqldbesaincludessqldbesa-mdmd"></a>E. Creazione di uno schema di partizione solo su primario - solo primario è supportato per[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]

 Nell'esempio seguente viene creata una funzione di partizione per suddividere una tabella o indice in quattro partizioni. Viene quindi creato uno schema di partizione che specifica che tutte le partizioni vengono create nel filegroup primario.  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS1  
AS PARTITION myRangePF1  
ALL TO ( [PRIMARY] );  
```
   
## <a name="see-also"></a>Vedere anche  
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Creare tabelle e indici partizionati](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md)   
 [Sys. partition_schemes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys.destination_data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [Sys. Partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

