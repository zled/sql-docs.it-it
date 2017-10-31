---
title: uniqueidentifier (Transact-SQL) | Documenti Microsoft
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
- uniqueidentifier
- uniqueidentifier_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- globally unique identifiers [SQL Server]
- GUIDs [SQL Server]
ms.assetid: b026035b-f3d2-4d70-989d-3884b4ca0233
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 1450aa86e3f47ef27be5acd5b5410fe40dd5983e
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="uniqueidentifier-transact-sql"></a>uniqueidentifier (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

GUID a 16 byte.
  
## <a name="remarks"></a>Osservazioni  
Una colonna o una variabile locale di **uniqueidentifier** tipo di dati può essere inizializzato su un valore nei modi seguenti:
-   Tramite la funzione NEWID.  
-   Tramite la conversione da una costante stringa nel formato *xxxxxxxx*-*xxxx*-*xxxx*-*xxxx* - *xxxxxxxxxxxx*, in cui ogni *x* è una cifra esadecimale compresa nell'intervallo 0-9 o a-f. Ad esempio, 6F9619FF-8B86-D011-B42D-00C04FC964FF è un valido **uniqueidentifier** valore.  
  
Gli operatori di confronto possono essere utilizzati con **uniqueidentifier** valori. Quando si confrontano gli schemi di bit dei due valori, tuttavia, l'ordinamento non viene implementato. Le uniche operazioni che possono essere eseguite con un **uniqueidentifier** valore sono i confronti (=, <>, \<, >, \<=, > =) e la ricerca di NULL (IS NULL e IS NOT NULL). Non è possibile utilizzare altri operatori aritmetici. Tutti i vincoli di colonna e le proprietà, ad eccezione di IDENTITY possono essere utilizzate nel **uniqueidentifier** tipo di dati.
  
Merge di replica e la replica transazionale con aggiornamento delle sottoscrizioni utilizzano **uniqueidentifier** colonne per garantire che le righe vengano identificate univocamente in più copie della tabella.
  
## <a name="converting-uniqueidentifier-data"></a>Conversione del tipo di dati uniqueidentifier  
Il **uniqueidentifier** viene considerato un tipo di carattere ai fini di conversione da un'espressione di caratteri e pertanto è soggetto alle regole di troncamento per la conversione in un tipo di carattere. Vale a dire che, se un'espressione di caratteri viene convertita in un tipo di dati carattere di dimensioni diverse, i valori troppo lunghi per il nuovo tipo di dati vengono troncati. Vedere la sezione relativa agli esempi.
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni

Questi strumenti e funzionalità non supportano il `uniqueidentifier` tipo di dati:
- PolyBase
- [strumento di caricamento dwloader](https://msdn.microsoft.com/sql/analytics-platform-system/dwloader) per Parallel Data Warehouse

## <a name="examples"></a>Esempi  
Nell'esempio seguente un valore `uniqueidentifier` viene convertito in un tipo di dati `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Nell'esempio seguente viene illustrato il troncamento dei dati quando il valore è troppo lungo per il tipo di dati in cui avviene la conversione. Poiché il **uniqueidentifier** tipo è limitato a 36 caratteri, i caratteri che superano tale lunghezza vengono troncati.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)  
[NEWSEQUENTIALID &#40; Transact-SQL &#41; ](../../t-sql/functions/newsequentialid-transact-sql.md) 
 [Impostare @local_variable &#40; Transact-SQL &#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)
  
  

