---
title: STRING_ESCAPE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs: TSQL
helpviewer_keywords: STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: add41d4ac936190316f432f810f40fec286e4647
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Caratteri speciali nei testi delle sequenze di escape e restituisce il testo con caratteri di escape. **STRING_ESCAPE** è una funzione deterministica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>Argomenti  
 *text*  
 È un **nvarchar**[espressione](../../t-sql/language-elements/expressions-transact-sql.md) espressione che rappresenta l'oggetto deve essere sottoposto a escape.  
  
 *type*  
 Regole di escape che verranno applicate. Il valore supportato è attualmente `'json'`.  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar (max)** testo con caratteri di escape speciali e caratteri di controllo. Attualmente **STRING_ESCAPE** fare in modo che solo i caratteri speciali JSON illustrati nelle tabelle seguenti.  
  
|Carattere speciale|Sequenza codificata|  
|-----------------------|----------------------|  
|Virgoletta (")|\\"|  
|frazione (\\)|\\\|  
|barra rovesciata (/)|\\/|  
|Backspace|\b|  
|Avanzamento carta|\f|  
|Nuova riga|\n|  
|Ritorno a capo|\r|  
|Tabulazione orizzontale|\t|  
  
|Carattere di controllo|Sequenza codificata|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="examples"></a>Esempi  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Escape di testo in base alle regole di formattazione JSON  
 La query seguente esegue l'escape di caratteri speciali, utilizzando le regole di JSON e restituisce il testo con caratteri di escape.  
  
```  
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>B. Oggetto JSON formato  
 La query seguente crea testo JSON da variabili di stringa e numero e delle sequenze di escape qualsiasi carattere speciale JSON nelle variabili.  
  
```  
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',   
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni stringa &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [SOTTOSTRINGA &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
  
  
