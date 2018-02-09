---
title: Valore booleano effettivo (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- effective Boolean value [XQuery]
- Boolean values
- XQuery, effective Boolean values
- EBV
ms.assetid: 506682b1-b6c9-45e2-aa54-7abd5844c3f1
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93c3ecaf4a4ded90a4b65aed08c6112fd9b670f1
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="effective-boolean-value-xquery"></a>Valore booleano effettivo (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  I valori booleani effettivi sono:  
  
-   False se l'operando è una sequenza vuota o un valore booleano False.  
  
-   In caso contrario, il valore è True.  
  
 È possibile calcolare il valore booleano effettivo per le espressioni che restituiscono un valore booleano singolo, una sequenza di nodi o una sequenza vuota. Si noti che il valore booleano viene calcolato in modo implicito quando vengono elaborati i tipi seguenti di espressioni:  
  
-   Espressioni logiche  
  
-   Il [non funzionano](../xquery/functions-on-boolean-values-not-function.md)  
  
-   Clausola WHERE di un'espressione FLWOR  
  
-   [Espressioni condizionali](../xquery/conditional-expressions-xquery.md)  
  
-   [Espressioni quantificate](../xquery/quantified-expressions-xquery.md)  
  
 Di seguito è riportato un esempio di un valore booleano effettivo. Quando il **se** espressione viene elaborata, viene determinato il valore booleano effettivo della condizione. Poiché `/a[1]` restituisce una sequenza vuota, il valore booleano effettivo è False. Il risultato viene restituito in formato XML con un nodo di testo (false).  
  
```  
value is false  
DECLARE @x XML  
SET @x = '<b/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 Nell'esempio seguente, il valore booleano effettivo è True, perché l'espressione restituisce una sequenza non vuota.  
  
```  
DECLARE @x XML  
SET @x = '<a/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 Quando l'esecuzione di query digitato **xml** colonne o variabili, può contenere nodi di tipo Boolean. Il **data ()** in questo caso restituisce un valore booleano. Se l'espressione della query restituisce un valore booleano True, il valore booleano effettivo è True, come illustrato nell'esempio seguente. Nell'esempio viene inoltre illustrato quanto segue:  
  
-   Viene creata una raccolta di XML Schema. L'elemento \<b > della raccolta è di tipo Boolean.  
  
-   Un oggetto tipizzato **xml** variabile viene creata e query.  
  
-   L'espressione `data(/b[1])` restituisce un valore booleano True e pertanto in questo caso il valore booleano effettivo è True.  
  
-   L'espressione `data(/b[2])` restituisce un valore booleano false. e pertanto in questo caso il valore booleano effettivo è False.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="s" type="string"/>  
      <element name="b" type="boolean"/>  
</schema>'  
go  
DECLARE @x XML(SC)  
SET @x = '<b>true</b><b>false</b>'  
SELECT @x.query('if (data(/b[1])) then "true" else "false"')  
SELECT @x.query('if (data(/b[2])) then "true" else "false"')  
go  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su XQuery](../xquery/xquery-basics.md)   
 [Istruzione FLWOR e iterazione &#40; XQuery &#41;](../xquery/flwor-statement-and-iteration-xquery.md)  
  
  
