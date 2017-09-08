---
title: Money e smallmoney (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- money_TSQL
- money
- smallmoney
- smallmoney_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- money data type, about money data type
- money data type
- smallmoney data type
- values [SQL Server], monetary
- currency [SQL Server]
ms.assetid: 57861137-89ea-4b89-b361-390597d7bccc
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bd07ecd1cdacc686e0f831320fd5e939c0c174da
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="money-and-smallmoney-transact-sql"></a>money e smallmoney (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Tipi di dati che rappresentano valori monetari o valutari.
  
## <a name="remarks"></a>Osservazioni  
  
|Tipo di dati|Intervallo|Archiviazione|  
|---|---|---|
|**money**|-922.337.203.685.477,5808 a 922.337.203.685.477,5807 (-922,337,203,685,477.58<br />per 922,337,203,685,477.58 di Informatica.  Informatica solo supporta due numeri decimali, non quattro).|8 byte|  
|**smallmoney**|Da -214.748,3648 a 214.748,3647|4 byte|  
  
Il **money** e **smallmoney** sono accurati di un decimillesimo di unità di valuta che rappresentano i tipi di dati. Per Informatica, il **money** e **smallmoney** sono accurati per centesimo delle unità monetarie che rappresentano i tipi di dati.
  
Per separare le unità di valuta parziali, ad esempio i centesimi, da quelle intere, utilizzare il punto. Ad esempio, 2.15 indica 2 dollari e 15 centesimi.
  
È possibile utilizzare questi tipi di dati per i simboli di valuta illustrati di seguito.
  
![Tabella dei simboli di valuta, valori esadecimali](../../t-sql/data-types/media/money01.gif "tabella dei simboli di valuta, valori esadecimali")
  
Non è necessario racchiudere i dati di tipo valuta tra virgolette singole ('). È importante tenere presente che anche se è possibile specificare un simbolo di valuta che precede i valori di valuta, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le informazioni relative alla valuta archiviate non sono associate al simbolo, ma è presente solo il valore numerico.
  
## <a name="converting-money-data"></a>Conversione di dati money
Quando si converte **money** da tipi di dati integer, unità si presuppone che sia in unità di valuta. Ad esempio, il valore integer 4 viene convertito nel **money** equivalente di 4 unità di valuta.
  
L'esempio seguente converte **smallmoney** e **money** valori **varchar** e **decimale** tipi di dati, rispettivamente.
  
```sql
DECLARE @mymoney_sm smallmoney = 3148.29,  
        @mymoney    money = 3148.29;  
SELECT  CAST(@mymoney_sm AS varchar) AS 'SM_MONEY varchar',  
        CAST(@mymoney AS decimal)    AS 'MONEY DECIMAL';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
SM_MONEY VARCHAR               MONEY DECIMAL  
------------------------------ ----------------------  
3148.29                        3148    
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[Istruzione ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md) 
 [CAST e CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md) 
 [Crea una tabella &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md) 
 [Tipi di dati &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md) 
 [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
 [Impostare @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md) 
 [Sys. Types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

