---
title: ~ (NOT bit per bit) (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ~_TSQL
- bitwise
- NOT
- ~
- Bitwise NOT
dev_langs: TSQL
helpviewer_keywords:
- NOT keyword
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: 02da8016-f6c0-41ae-8d59-33eaa02bfc95
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bc129a0a62c393cb8aee03edca3e0c2b567f9488
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="-bitwise-not-transact-sql"></a>~ (NOT bit per bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue un'operazione con NOT logico bit per bit su un valore integer.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
~ expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) uno qualsiasi dei tipi di dati della categoria di tipi di dati integer, il **bit**, o **binario** o **varbinary** dati tipi. *espressione* viene considerato come un numero binario per l'operazione bit per bit.  
  
> [!NOTE]  
>  Un solo *espressione* può essere del **binario** o **varbinary** il tipo di dati in un'operazione bit per bit.  
  
## <a name="result-types"></a>Tipi restituiti  
 **int** se i valori di input sono **int**.  
  
 **smallint** se i valori di input sono **smallint**.  
  
 **tinyint** se i valori di input sono **tinyint**.  
  
 **bit** se i valori di input sono **bit**.  
  
## <a name="remarks"></a>Osservazioni  
 Il  **~**  operatore bit per bit esegue NOT logico bit per bit per il *espressione*, valutando ogni bit in serie. Se *espressione* ha un valore pari a 0, i bit nel set di risultati vengono impostati su 1; in caso contrario, il bit nel risultato viene cancellato su un valore pari a 0. In altre parole, i bit a uno vengono cambiati in zero e i bit a zero vengono modificati in uno.  
  
> [!IMPORTANT]  
>  Per l'esecuzione di qualsiasi operazione bit per bit, la lunghezza di archiviazione dell'espressione utilizzata nell'operazione è un fattore importante. È consigliabile utilizzare lo stesso numero di byte per l'archiviazione dei valori. Ad esempio, archiviare il valore decimale 5 come un **tinyint**, **smallint**, o **int** produce un valore archiviato con numeri diversi di byte: **tinyint** archivia i dati utilizzando 1 byte, **smallint** archivia i dati utilizzando 2 byte, e **int** archivia i dati utilizzando 4 byte. Pertanto, l'esecuzione di un'operazione bit per bit su un **int** valore decimale può produrre risultati diversi da quelli che utilizzano una conversione diretta binaria o esadecimale, soprattutto quando il  **~**  ( NOT bit per bit) viene utilizzato l'operatore. L'operazione con NOT bit per bit potrebbe essere eseguita su una variabile di lunghezza inferiore. In questo caso, quando la variabile di lunghezza inferiore viene convertita in una variabile con tipo di dati di lunghezza maggiore, i bit negli 8 bit superiori potrebbero non essere impostati sul valore previsto. È pertanto consigliabile convertire la variabile del tipo di dati di lunghezza minore nel tipo di dati di lunghezza maggiore ed eseguire quindi l'operazione NOT sul valore risultante.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella utilizzando il **int** digitare per archiviare i valori e inserisce i due valori in una riga di dati.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 Nella query seguente viene eseguita l'operazione con NOT bit per bit sulle colonne `a_int_value` e `b_int_value`.  
  
```  
SELECT ~ a_int_value, ~ b_int_value  
FROM bitwise;  
```  
  
 Set di risultati:  
  
```  
--- ---   
-171  -76   
  
(1 row(s) affected)  
```  
  
 La rappresentazione binaria di 170 (`a_int_value` o `A`) è `0000 0000 1010 1010`. L'esecuzione dell'operazione con NOT bit per bit su questo valore genera il risultato binario `1111 1111 0101 0101`, corrispondente al valore decimale 171. La rappresentazione binaria di 75 è `0000 0000 0100 1011`. L'esecuzione dell'operazione con NOT bit per bit genera il risultato `1111 1111 1011 0100`, ovvero il valore decimale -76.  
  
```  
 (~A)     
         0000 0000 1010 1010  
         -------------------  
         1111 1111 0101 0101  
(~B)     
         0000 0000 0100 1011  
         -------------------  
         1111 1111 1011 0100  
```  
  
 
## <a name="see-also"></a>Vedere anche  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  


