---
title: PATINDEX (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PATINDEX
- PATINDEX_TSQL
dev_langs: TSQL
helpviewer_keywords:
- first occurrence of pattern [SQL Server]
- searches [SQL Server], pattern starting position
- starting position of patten search
- pattern searching [SQL Server]
- PATINDEX function
ms.assetid: c0dfb17f-2230-4e36-98da-a9b630bab656
caps.latest.revision: "53"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: fd0df5a4dba946748dc39c245fcd54d50f1e97e5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="patindex-transact-sql"></a>PATINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la posizione di inizio della prima occorrenza di un modello in un'espressione specificata, oppure zero se il modello non viene trovato, in tutti i dati di tipo carattere e testo validi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
PATINDEX ( '%pattern%' , expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *modello*  
 Espressione di caratteri che contiene la sequenza da cercare. È possono utilizzare caratteri jolly; Tuttavia, il carattere % deve precedere e seguire *modello* (tranne nelle ricerche del primo o ultimo carattere). *modello* è un'espressione della categoria di tipi di dati di stringa carattere. *modello* è limitato a 8000 caratteri.  
  
 *espressione*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md), in genere una colonna che viene cercata il modello specificato. *espressione* è della categoria di tipi di dati di stringa carattere.  
  
## <a name="return-types"></a>Tipi restituiti  
 **bigint** se *espressione* è il **varchar (max)** o **nvarchar (max)** tipi di dati; in caso contrario **int**.  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore *modello* o *espressione* è NULL, PATINDEX restituisce NULL.  
  
 L'istruzione PATINDEX consente di eseguire i confronti in base alle regole di confronto dell'input. Per eseguire un confronto in base a regole di confronto specifiche, è possibile utilizzare COLLATE per applicare regole di confronto esplicite all'input.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Quando si utilizzano regole di confronto SC, il valore restituito verrà considerato qualsiasi coppia di surrogati UTF-16 *espressione* parametro come un singolo carattere. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 0x0000 (**char(0)**) è un carattere non definito nelle regole di confronto di Windows e non può essere incluso in PATINDEX.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-patindex-example"></a>A. Semplice esempio PATINDEX  
 L'esempio seguente verifica una breve stringa di caratteri (`interesting data`) per la posizione iniziale dei caratteri `ter`.  
  
```  
SELECT PATINDEX('%ter%', 'interesting data');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `3`  
  
### <a name="b-using-a-pattern-with-patindex"></a>B. Utilizzo di un modello con PATINDEX  
 Nell'esempio seguente viene individuata la posizione in cui il modello `ensure` ha inizio in una riga specifica della colonna `DocumentSummary` nella tabella `Document` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT PATINDEX('%ensure%',DocumentSummary)  
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
GO   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-----------  
64  
(1 row(s) affected)
```  
  
 Se non si imposta una limitazione per le righe in cui eseguire la ricerca tramite la clausola `WHERE`, la query restituisce tutte le righe della tabella, indicando valori diversi da zero per le righe in cui il modello è stato trovato e zero per tutte le righe in cui la ricerca ha avuto esito negativo.  
  
### <a name="c-using-wildcard-characters-with-patindex"></a>C. Utilizzo di caratteri jolly con PATINDEX  
 Nell'esempio seguente vengono utilizzati i caratteri jolly % e _ per individuare la posizione iniziale del modello `'en'`, seguito da un carattere qualsiasi e `'ure'` nella stringa specificata (l'indice comincia col valore 1):  
  
```  
SELECT PATINDEX('%en_ure%', 'please ensure the door is locked');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-----------  
8  
```  
  
 Il funzionamento di `PATINDEX` è uguale a quello di `LIKE`, pertanto è possibile utilizzare qualsiasi carattere jolly. Non è necessario racchiudere il modello tra percentuali. `PATINDEX('a%', 'abc')` restituisce 1 e `PATINDEX('%a', 'cba')` restituisce 3.  
  
 A differenza di `LIKE`, `PATINDEX` restituisce una posizione, analogamente a `CHARINDEX`.  
  
### <a name="d-using-collate-with-patindex"></a>D. Utilizzo di COLLATE con PATINDEX  
 Nell'esempio seguente viene utilizzata la funzione `COLLATE` per specificare in modo esplicito le regole di confronto dell'espressione indicante il contesto della ricerca.  
  
```  
USE tempdb;  
GO  
SELECT PATINDEX ( '%ein%', 'Das ist ein Test'  COLLATE Latin1_General_BIN) ;  
GO  
```  
  
### <a name="e-using-a-variable-to-specify-the-pattern"></a>E. Utilizzo di una variabile per specificare il modello  
 Nell'esempio seguente viene utilizzata una variabile per passare un valore per il *modello* parametro. Questo esempio viene utilizzato il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.  
  
```  
DECLARE @MyValue varchar(10) = 'safety';   
SELECT PATINDEX('%' + @MyValue + '%', DocumentSummary)   
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------------  
 22
 ```  
  

  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [&#40; Carattere jolly - carattere &#40; s &#41; in corrispondenza &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#40; Carattere jolly - carattere &#40; s &#41; Non corrispondenza &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)   
 [_ &#40; Carattere jolly - corrispondenze di singoli caratteri &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)   
 [Carattere di percentuale &#40; Carattere jolly - carattere &#40; s &#41; in corrispondenza &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)  
  
  


