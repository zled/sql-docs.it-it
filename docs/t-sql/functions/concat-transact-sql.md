---
title: CONCAT (Transact-SQL) | Documenti Microsoft
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
- CONCAT
- CONCAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT function
ms.assetid: fce5a8d4-283b-4c47-95e5-4946402550d5
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 046278bb3016b39df8039a1450a58b177d2bc180
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Restituisce la stringa risultante dalla concatenazione di due o più valori stringa. (Per aggiungere un valore di separazione durante la concatenazione, vedere [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md).)
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CONCAT ( string_value1, string_value2 [, string_valueN ] )  
```  
  
## <a name="arguments"></a>Argomenti  
*valore_stringa*  
Valore stringa da concatenare agli altri valori.
  
## <a name="return-types"></a>Tipi restituiti
Stringa, lunghezza e tipo di cui dipende l'input.
  
## <a name="remarks"></a>Osservazioni  
**CONCAT** accetta un numero variabile di argomenti di stringa e concatenati in una singola stringa. È richiesto un minimo di due valori di input. In caso contrario, viene generato un errore. Tutti gli argomenti vengono convertiti in modo implicito nei tipi di stringa e successivamente concatenati. I valori Null vengono convertiti in modo implicito in una stringa vuota. Se tutti gli argomenti sono null, una stringa vuota di tipo **varchar**(1) viene restituito. Per la conversione implicita in stringhe vengono seguite le regole esistenti per le conversioni dei tipi di dati. Per ulteriori informazioni sulle conversioni dei tipi di dati, vedere [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Il tipo restituito dipende dal tipo degli argomenti. Nella tabella seguente viene illustrato il mapping.
  
|Tipo di input|Tipo di output e lunghezza|  
|---|---|
|Se un argomento è un tipo di sistema CLR SQL, un tipo definito dall'utente CLR SQL o `nvarchar(max)`|**nvarchar(max)**|  
|In caso contrario, se un argomento è **varbinary (max)** o **varchar (max)**|**varchar (max)** , a meno che uno dei parametri è un **nvarchar** di qualsiasi lunghezza. Se in tal caso, il risultato sarà **nvarchar (max)**.|  
|In caso contrario, se un argomento è **nvarchar**(< = 4000)|**nvarchar**(< = 4000)|  
|In caso contrario, in tutti gli altri casi|**varchar**(< = 8000), a meno che uno dei parametri è un tipo nvarchar di qualsiasi lunghezza. Se in tal caso, il risultato sarà **nvarchar (max)**.|  
  
Quando gli argomenti sono < = 4000 per **nvarchar**, o < = 8000 per **varchar**, conversioni implicite possono influire sulla lunghezza del risultato. Gli altri tipi di dati hanno lunghezze diverse quando vengono convertiti in modo implicito in stringhe. Ad esempio, un **int** (14) è una stringa di lunghezza pari a 12, mentre un **float** ha una lunghezza di 32. Di conseguenza, al risultato della concatenazione di due tipi Integer corrisponde una lunghezza non minore di 24.
  
Se nessuno degli argomenti di input è di un tipo LOB supportato, la lunghezza del tipo restituito viene troncata a 8000, indipendentemente dal tipo restituito. Questo troncamento consente di mantenere lo spazio e di generare il piano in modo efficiente.
  
La funzione CONCAT può essere eseguita in modalità remota su un server collegato che è una versione [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive. Per i server collegati precedenti, il CONCAT viene eseguita in locale dopo i valori non concatenati vengono restituiti dal server collegato.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-concat"></a>A. Utilizzo di CONCAT  
  
```sql
SELECT CONCAT ( 'Happy ', 'Birthday ', 11, '/', '25' ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------  
Happy Birthday 11/25  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-concat-with-null-values"></a>B. Utilizzo di CONCAT con valori NULL  
  
```sql
CREATE TABLE #temp (  
    emp_name nvarchar(200) NOT NULL,  
    emp_middlename nvarchar(200) NULL,  
    emp_lastname nvarchar(200) NOT NULL  
);  
INSERT INTO #temp VALUES( 'Name', NULL, 'Lastname' );  
SELECT CONCAT( emp_name, emp_middlename, emp_lastname ) AS Result  
FROM #temp;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
------------------  
NameLastname  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni stringa (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)   
  



