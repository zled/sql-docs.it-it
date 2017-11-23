---
title: IIF (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- IIF_TSQL
- IIF
dev_langs: TSQL
helpviewer_keywords: IIF function
ms.assetid: e3ccf8ed-1cec-43ac-90b7-d8597c24b050
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a7b58233c958d8ca9dc6b0fea9f9e69290d13679
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="logical-functions---iif-transact-sql"></a>Funzioni logiche - IIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Viene restituito uno di due valori a seconda che l'espressione booleana sia true o false in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IIF ( boolean_expression, true_value, false_value )  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression*  
 Espressione booleana valida.  
  
 Se questo argomento non è un'espressione booleana, viene generato un errore di sintassi.  
  
 *true_value*  
 Valore da restituire se *argomento boolean_expression* restituisce true.  
  
 *false_value*  
 Valore da restituire se *argomento boolean_expression* restituisce false.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce il tipo di dati con precedenza più alta tra i tipi nella *true_value* e *false_value*. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 IIF è un modo abbreviato per scrivere un'espressione CASE. Valuta l'espressione booleana passata come primo argomento, quindi restituisce uno dei due argomenti in base al risultato della valutazione. Vale a dire il *true_value* viene restituito se l'espressione booleana è true e *false_value* viene restituito se l'espressione booleana è false o unknown. *true_value* e *false_value* può essere di qualsiasi tipo. Le stesse regole applicate all'espressione CASE per espressioni booleane, gestione di valori Null e tipi restituiti vengono applicate anche a IIF. Per ulteriori informazioni, vedere [CASE &#40; Transact-SQL &#41; ](../../t-sql/language-elements/case-transact-sql.md).  
  
 La conversione di IIF in CASE influisce inoltre su altri aspetti del comportamento di questa funzione. Poiché le espressioni CASE possono essere nidificate solo fino a livello 10, anche le istruzioni IIF possono essere nidificate fino al livello massimo 10. Inoltre l'istruzione IIF viene eseguita in modalità remota in altri server come un'espressione CASE equivalente dal punto di vista semantico, con tutti i comportamenti di un'espressione CASE eseguita in modalità remota.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-iif-example"></a>A. Esempio semplice di IIF  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
TRUE  
  
(1 row(s) affected)  
```  
  
### <a name="b-iif-with-null-constants"></a>B. IIF con costanti NULL  
  
```  
SELECT IIF ( 45 > 30, NULL, NULL ) AS Result;  
```  
  
 Il risultato di questa istruzione è un errore.  
  
### <a name="c-iif-with-null-parameters"></a>C. IIF con parametri NULL  
  
```  
DECLARE @P INT = NULL, @S INT = NULL;  
SELECT IIF ( 45 > 30, @p, @s ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
NULL  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Scegliere &#40; Transact-SQL &#41;](../../t-sql/functions/logical-functions-choose-transact-sql.md)  
  
  
