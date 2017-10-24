---
title: CHECKSUM (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKSUM_TSQL
- CHECKSUM
dev_langs:
- TSQL
helpviewer_keywords:
- hash indexes
- CHECKSUM function
- checksum values
ms.assetid: e26d3339-845c-49c2-9d89-243376874c13
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0379260c517f546bf00c5e757f6a3069f574f102
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="checksum-transact-sql"></a>CHECKSUM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Restituisce il valore di checksum calcolato su una riga di una tabella o su un elenco di espressioni. La funzione CHECKSUM viene utilizzata per la compilazione di indici hash.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CHECKSUM ( * | expression [ ,...n ] )  
```  
  
## <a name="arguments"></a>Argomenti  
\*  
Specifica che il calcolo viene eseguito su tutte le colonne della tabella. Se il tipo di dati di una colonna non è confrontabile, la funzione CHECKSUM restituisce un errore. Tipi di dati non confrontabili sono **testo**, **ntext**, **immagine**, XML, e **cursore**, nonché **sql_variant**con uno qualsiasi dei tipi precedenti come tipo di base.
  
*espressione*  
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo, ad eccezione di un tipo di dati non confrontabili.
  
## <a name="return-types"></a>Tipi restituiti
 **int**  
  
## <a name="remarks"></a>Osservazioni  
La funzione CHECKSUM calcola un valore hash, denominato checksum, sul relativo elenco di argomenti. Tale valore viene utilizzato per la compilazione di indici hash. Se gli argomenti di CHECKSUM sono colonne e viene compilato un indice sul valore calcolato di CHECKSUM, il risultato sarà un indice hash, che può essere utilizzato per eseguire ricerche di uguaglianza sulle colonne.
  
La funzione CHECKSUM soddisfa le proprietà di una funzione hash in quanto quando viene applicata su due qualsiasi elenchi di espressioni restituisce lo stesso valore se gli elementi corrispondenti dei due elenchi sono dello stesso tipo di dati e risultano uguali quando vengono confrontati tramite l'operatore di uguaglianza (=). In questo contesto, i valori Null di un tipo specificato vengono considerati uguali ai fini del confronto. Se uno dei valori nell'elenco di espressioni cambia, in genere cambia anche il valore di checksum dell'elenco. È comunque possibile che il valore di checksum rimanga invariato. Per questo motivo, non è consigliabile utilizzare CHECKSUM per rilevare se i valori sono stati modificati a meno che l'applicazione non possa tollerare l'occasionale omissione di una modifica. È consigliabile utilizzare [HashBytes](../../t-sql/functions/hashbytes-transact-sql.md) invece. Quando viene specificato un algoritmo hash MD5, le probabilità che HashBytes restituisca lo stesso risultato per due diversi input sono notevolmente inferiori rispetto a CHECKSUM.
  
L'ordine delle espressioni influisce sul risultato di CHECKSUM. L'ordine delle colonne utilizzate con CHECKSUM(*) corrisponde all'ordine delle colonne specificate nella definizione della tabella o della vista, incluse le colonne calcolate.
  
Il valore CHECKSUM dipende dalle regole di confronto. Lo stesso valore archiviato con regole di confronto diverse restituirà un valore di checksum diverso.
  
## <a name="examples"></a>Esempi  
Negli esempi seguenti viene illustrato l'utilizzo di `CHECKSUM` per la compilazione di indici hash. L'indice hash viene compilato tramite l'aggiunta di una colonna checksum alla tabella da indicizzare e quindi tramite la compilazione di un indice su questa colonna.
  
```sql
-- Create a checksum index.  
SET ARITHABORT ON;  
USE AdventureWorks2012;   
GO  
ALTER TABLE Production.Product  
ADD cs_Pname AS CHECKSUM(Name);  
GO  
CREATE INDEX Pname_index ON Production.Product (cs_Pname);  
GO  
```  
  
L'indice checksum può essere utilizzato come indice hash, soprattutto per migliorare la velocità di indicizzazione quando la colonna da indicizzare è di tipo carattere Long. Può inoltre essere utilizzato per l'esecuzione di ricerche di uguaglianza.
  
```sql
/*Use the index in a SELECT query. Add a second search   
condition to catch stray cases where checksums match,   
but the values are not the same.*/  
SELECT *   
FROM Production.Product  
WHERE CHECKSUM(N'Bearing Ball') = cs_Pname  
AND Name = N'Bearing Ball';  
GO  
```  
  
La creazione dell'indice sulla colonna calcolata materializza la colonna checksum, alla quale verranno propagate tutte le modifiche apportate al valore `ProductName`. In alternativa, è possibile compilare un indice direttamente sulla colonna indicizzata. Se, tuttavia, i valori di chiave sono di tipo Long, è probabile che le prestazioni ottenute con un indice checksum siano migliori.
  
## <a name="see-also"></a>Vedere anche
[CHECKSUM_AGG &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-agg-transact-sql.md)  
[HASHBYTES &#40; Transact-SQL &#41;](../../t-sql/functions/hashbytes-transact-sql.md)  
[BINARY_CHECKSUM &#40; Transact-SQL &#41;](../../t-sql/functions/binary-checksum-transact-sql.md)
  
  

