---
title: STR (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STR
- STR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- converting numbers to characters
- characters [SQL Server], converting
- character data [SQL Server]
- STR function
ms.assetid: de03531b-d9e7-4c3c-9604-14e582ac20c6
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 27af210aca06130818fd00fea9d53eebcc8aa016
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="str-transact-sql"></a>STR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce dati di tipo carattere convertiti da dati di tipo numerico.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STR ( float_expression [ , length [ , decimal ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *argomento float_expression*  
 È un'espressione di numerico approssimato (**float**) il tipo di dati con un separatore decimale.  
  
 *length*  
 Lunghezza totale, che include il separatore decimale, il segno, le cifre e gli spazi. Il valore predefinito è 10.  
  
 *decimal*  
 Numero di posizioni a destra del separatore decimale. *decimale* deve essere minore o uguale a 16. Se *decimale* è maggiore di 16, il risultato viene troncato a sedici posizioni a destra del separatore decimale.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varchar**  
  
## <a name="remarks"></a>Osservazioni  
 Se fornito, i valori per *lunghezza* e *decimale* tali parametri devono essere positivi. Il numero viene arrotondato a un valore intero per impostazione predefinita o se il parametro decimal è 0. La lunghezza specificata deve essere maggiore o uguale alla parte intera del numero (a sinistra del separatore decimale) più il segno del numero, se disponibile. Un breve *argomento float_expression* viene allineato a destra, la lunghezza specificata e un valore long *argomento float_expression* viene troncato al numero specificato di posizioni decimali. Ad esempio, STR (12**,**10) restituisce il risultato 12. che viene allineato a destra nel set di risultati. Tuttavia, STR (1223**,**2) tronca il set di risultati a * *. Le funzioni stringa possono essere nidificate.  
  
> [!NOTE]  
>  Per convertire i dati Unicode, utilizzare STR in una conversione o [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) funzione di conversione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente un'espressione composta da cinque cifre e un separatore decimale viene convertita in una stringa di caratteri con sei posizioni. La parte frazionaria del numero viene arrotondata a una cifra decimale.  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 Quando l'espressione supera la lunghezza specificata, la stringa restituisce `**` per la lunghezza specificata.  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 Quando nella funzione `STR` i dati numerici sono nidificati, il risultato corrisponde comunque a dati di tipo carattere nel formato specificato.  
  
```  
SELECT STR (FLOOR (123.45), 8, 3;)  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente un'espressione composta da cinque cifre e un separatore decimale viene convertita in una stringa di caratteri con sei posizioni. La parte frazionaria del numero viene arrotondata a una cifra decimale.  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 Quando l'espressione supera la lunghezza specificata, la stringa restituisce `**` per la lunghezza specificata.  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 Quando nella funzione `STR` i dati numerici sono nidificati, il risultato corrisponde comunque a dati di tipo carattere nel formato specificato.  
  
```  
SELECT STR (FLOOR (123.45), 8, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


