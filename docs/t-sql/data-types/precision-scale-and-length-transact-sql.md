---
title: Precisione, scala e lunghezza (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], length
- data types [SQL Server], scale
- precision [SQL Server], data types
- lengths [SQL Server], data types
- number of digits
- scale [SQL Server]
- scale [SQL Server], data types
- data types [SQL Server], precision
ms.assetid: fbc9ad2c-0d3b-4e98-8fdd-4d912328e40a
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 557d7a5c45e9cc5a0839dfb4a1fdb0d08c2bf83f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="precision-scale-and-length-transact-sql"></a>Precisione, scala e lunghezza (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

La precisione è il numero di cifre in un numero. La scala è il numero di cifre a destra della virgola decimale in un numero. Il numero 123,45, ad esempio, ha una precisione di 5 e una scala di 2.
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la precisione massima predefinita di **numerico** e **decimale** tipi di dati è 38. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'impostazione massima predefinita era 28.
  
La lunghezza di un tipo di dati numerico è il numero di byte utilizzati per l'archiviazione del numero. La lunghezza del tipo di dati stringa di caratteri o Unicode corrisponde al numero di caratteri. La lunghezza per **binario**, **varbinary**, e **immagine** tipi di dati è il numero di byte. Ad esempio, un **int** tipo di dati può contenere 10 cifre, viene archiviato in 4 byte e non può contenere decimali. Il **int** tipo di dati ha una precisione pari a 10, una lunghezza pari a 4 e una scala pari a 0.
  
Quando due **char**, **varchar**, **binario**, o **varbinary** vengono concatenate espressioni, la lunghezza dell'espressione risultante è il somma delle lunghezze delle due espressioni di origine e 8.000 caratteri, a seconda del valore è minore.
  
Quando due **nchar** o **nvarchar** vengono concatenate espressioni, la lunghezza dell'espressione risultante è la somma delle lunghezze delle due espressioni di origine e di 4.000 caratteri, a seconda del valore è minore.
  
Se si confrontano due espressioni dello stesso tipo di dati ma di lunghezze diverse utilizzando UNION, EXCEPT o INTERSECT, la lunghezza risultante corrisponde alla lunghezza massima delle due espressioni.
  
La precisione e scala dei tipi di dati numerici, oltre a **decimale** sono fisse. Se un operatore aritmetico collega due espressioni dello stesso tipo, il risultato è costituito dallo stesso tipo di dati, con la precisione e la scala corrispondenti a tale tipo. Se un operatore collega due espressioni con tipi di dati numerici diversi, il tipo di dati del risultato viene stabilito dalle regole relative alla precedenza dei tipi di dati. La precisione e la scala del risultato corrispondono a quelle definite per il tipo di dati.
  
Nella tabella seguente definisce la modalità di precisione e scala del risultato vengono calcolati quando il risultato di un'operazione è di tipo **decimale**. Il risultato è **decimale** quando viene soddisfatta una delle operazioni seguenti:
-   Entrambe le espressioni sono **decimale**.  
-   Un'espressione è **decimale** e l'altro è un tipo di dati con precedenza inferiore rispetto a **decimale**.  
  
Le espressioni dell'operando sono definite come espressione e1, con precisione p1 e scala s1, e come espressione e2, con precisione p2 e scala s2. La precisione e scala per qualsiasi espressione che non è **decimale** è la precisione e scala definite per il tipo di dati dell'espressione.
  
|Operazione|Precisione del risultato|Scala del risultato*|  
|---|---|---|
|e1 + e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 - e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 * e2|p1 + p2 + 1|s1 + s2|  
|e1 / e2|p1 - s1 + s2 + max(6, s1 + p2 + 1)|max(6, s1 + p2 + 1)|  
|E1 {unione &#124; Ad eccezione di &#124; E2 INTERSECT}|max(s1, s2) + max(p1-s1, p2-s2)|max(s1, s2)|  
|e1 % e2|min(p1-s1, p2 -s2) + max( s1,s2 )|max(s1, s2)|  
  
\*La precisione del risultato e la scala hanno un valore assoluto massimo di 38. Quando una precisione del risultato è maggiore di 38, quest'ultimo viene ridotto a 38 e la scala corrispondente viene ridotta per tentare di evitare la parte integrale di un risultato. In alcuni casi, quali la moltiplicazione o divisione, fattore di scala non diminuisce per mantenere la precisione decimale, anche se può essere generato l'errore di overflow.

Nelle operazioni di addizione e sottrazione dobbiamo `max(p1 – s1, p2 – s2)` posizioni in cui archiviare parte integrante del numero decimale. Se non vi è spazio sufficiente per archiviarli ad esempio `max(p1 – s1, p2 – s2) < min(38, precision) – scale`, viene ridotta la scala per fornire spazio sufficiente per la parte integrale. Scala risulta è `MIN(precision, 38) - max(p1 – s1, p2 – s2)`, pertanto la parte frazionaria potrebbe essere arrotondata per adattarla al scala risulta.

Nelle operazioni di moltiplicazione e divisione dobbiamo `precision - scale` posizioni in cui archiviare la parte integrale del risultato. La scala potrebbe risultare ridotte utilizzando le regole seguenti:
1.  La scala risulta viene ridotta a `min(scale, 38 – (precision-scale))` se la parte integrale è minore di 32, perché non può essere maggiore di `38 – (precision-scale)`. Risultato potrebbe essere arrotondato in questo caso.
1. La scala non verrà modificata se è minore di 6 e la parte integrale è maggiore di 32. In questo caso, l'errore di overflow può essere generata se è più possibile inserire in un valore decimale (38, scala) 
1. La scala verrà impostata su 6 se è maggiore di 6 e se la parte integrale è maggiore di 32. In questo caso, potrebbe essere ridotto sia parte integrante e la scala e decimal(38,6) è di tipo risultante. Risultato potrebbe essere arrotondato a 6 cifre decimali o verrà generato un errore di overflow se parte integrante non si adattata 32 cifre.

## <a name="examples"></a>Esempi
L'espressione seguente restituisce risultati `0.00000090000000000` senza arrotondamento, perché i risultati possono essere contenuti in `decimal(38,17)`:
```sql
select cast(0.0000009000 as decimal(30,20)) * cast(1.0000000000 as decimal(30,20)) [decimal 38,17]
```
In questo caso la precisione è 61 e la scala è 40.
Parte integrante (scala di precisione = 21) è minore di 32, in modo che questo è un caso (1) nelle regole di moltiplicazione e scala viene calcolata come `min(scale, 38 – (precision-scale)) = min(40, 38 – (61-40)) = 17`. Tipo di risultato è `decimal(38,17)`.

L'espressione seguente restituisce risultati `0.000001` in modo da adattarsi `decimal(38,6)`:
```sql
select cast(0.0000009000 as decimal(30,10)) * cast(1.0000000000 as decimal(30,10)) [decimal(38, 6)]
```
In questo caso la precisione è 61 e la scala è 20.
La scala è maggiore di parte integrante e 6 (`precision-scale = 41`) è maggiore di 32. Ciò è possibile (3) nelle regole di moltiplicazione e tipo di risultato è `decimal(38,6)`.

## <a name="see-also"></a>Vedere anche
[Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

