---
title: TERTIARY_WEIGHTS (Transact-SQL) | Documenti Microsoft
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
- TERTIARY_WEIGHTS_TSQL
- TERTIARY_WEIGHTS
dev_langs:
- TSQL
helpviewer_keywords:
- weights [SQL Server]
- SQL tertiary collations
- TERTIARY_WEIGHTS function
ms.assetid: 7e1f5350-260b-4c61-8c84-69bb1a214f1f
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7414f60414c14457dddc6f860201fd84409f1cb1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="collation-functions---tertiaryweights-transact-sql"></a>Funzioni di regole di confronto - TERTIARY_WEIGHTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce una stringa binaria di spessori per ogni carattere in un'espressione stringa non Unicode definita tramite una regola di confronto SQL terziaria.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
TERTIARY_WEIGHTS( non_Unicode_character_string_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
*non_Unicode_character_string_expression*  
È una stringa [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di tipo **char**, **varchar**, o **varchar (max)** definito in una regola di confronto SQL terziaria. Per un elenco di queste regole di confronto, vedere la sezione Osservazioni.
  
## <a name="return-types"></a>Tipi restituiti
TERTIARY_WEIGHTS restituisce **varbinary** quando *non_Unicode_character_string_expression* è **char** o **varchar**e restituisce **varbinary (max)** quando *non_Unicode_character_string_expression* è **varchar (max)**.
  
## <a name="remarks"></a>Osservazioni  
TERTIARY_WEIGHTS restituisce NULL quando *non_Unicode_character_string_expression* non è definito tramite un confronto SQL terziaria. Nella tabella seguente sono elencate le regole di confronto SQL terziarie.
  
|ID tipo di ordinamento|Regole di confronto SQL|  
|---|---|
|33|SQL_Latin1_General_Pref_CP437_CI_AS|  
|34|SQL_Latin1_General_CP437_CI_AI|  
|43|SQL_Latin1_General_Pref_CP850_CI_AS|  
|44|SQL_Latin1_General_CP850_CI_AI|  
|49|SQL_1xCompat_CP850_CI_AS|  
|53|SQL_Latin1_General_Pref_CP1_CI_AS|  
|54|SQL_Latin1_General_CP1_CI_AI|  
|56|SQL_AltDiction_Pref_CP850_CI_AS|  
|57|SQL_AltDiction_CP850_CI_AI|  
|58|SQL_Scandinavian_Pref_CP850_CI_AS|  
|82|SQL_Latin1_General_CP1250_CI_AS|  
|84|SQL_Czech_CP1250_CI_AS|  
|86|SQL_Hungarian_CP1250_CI_AS|  
|88|SQL_Polish_CP1250_CI_AS|  
|90|SQL_Romanian_CP1250_CI_AS|  
|92|SQL_Croatian_CP1250_CI_AS|  
|94|SQL_Slovak_CP1250_CI_AS|  
|96|SQL_Slovenian_CP1250_CI_AS|  
|106|SQL_Latin1_General_CP1251_CI_AS|  
|108|SQL_Ukrainian_CP1251_CI_AS|  
|113|SQL_Latin1_General_CP1253_CS_AS|  
|114|SQL_Latin1_General_CP1253_CI_AS|  
|130|SQL_Latin1_General_CP1254_CI_AS|  
|146|SQL_Latin1_General_CP1256_CI_AS|  
|154|SQL_Latin1_General_CP1257_CI_AS|  
|156|SQL_Estonian_CP1257_CI_AS|  
|158|SQL_Latvian_CP1257_CI_AS|  
|160|SQL_Lithuanian_CP1257_CI_AS|  
|183|SQL_Danish_Pref_CP1_CI_AS|  
|184|SQL_SwedishPhone_Pref_CP1_CI_AS|  
|185|SQL_SwedishStd_Pref_CP1_CI_AS|  
|186|SQL_Icelandic_Pref_CP1_CI_AS|  
  
TERTIARY_WEIGHTS deve essere utilizzato nella definizione di una colonna calcolata che corrisponde ai valori di un **char**, **varchar**, o **varchar (max)** colonna. Definizione di un indice nella colonna calcolata e **char**, **varchar**, o **varchar (max)** colonna può migliorare le prestazioni quando il **char**, **varchar**, o **varchar (max)** colonna specificata nella clausola ORDER BY di una query.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene creata una colonna calcolata in una tabella in cui la funzione `TERTIARY_WEIGHTS` viene applicata ai valori di una colonna di tipo `char`.
  
```sql
CREATE TABLE TertColTable  
(Col1 char(15) COLLATE SQL_Latin1_General_Pref_CP437_CI_AS,  
Col2 AS TERTIARY_WEIGHTS(Col1));  
GO   
```  
  
## <a name="see-also"></a>Vedere anche
[Clausola ORDER BY clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md)
  
  

