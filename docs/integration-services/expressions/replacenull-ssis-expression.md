---
title: REPLACENULL (espressione SSIS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b99a726d050dc2235f653061295e5f0829e93150
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="replacenull-ssis-expression"></a>REPLACENULL (espressione SSIS)
  Restituisce il valore del parametro della seconda espressione se il valore del parametro della prima è NULL. In caso contrario, restituisce il valore della prima espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression 1*  
 Il risultato di questa espressione viene verificato rispetto a NULL.  
  
 *expression 2*  
 Il risultato di questa espressione viene restituito se la prima espressione restituisce NULL.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Osservazioni  
  
-   La lunghezza di *expression 2* può essere zero.  
  
-   REPLACENULL restituisce un risultato Null se un argomento è Null.  
  
-   Le colonne BLOB (DT_TEXT, DT_NTEXT, DT_IMAGE) non sono supportate per nessun parametro.  
  
-   Le due espressioni devono avere lo stesso tipo restituito. In caso contrario, la funzione tenta di eseguire il cast della seconda espressione al tipo restituito della prima espressione, cosa che potrebbe generare un errore se i tipi di dati non sono compatibili.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nell'esempio seguente qualsiasi valore NULL in una colonna del database viene sostituito con una stringa (1900-01-01). Questa funzione viene soprattutto utilizzata nei modelli comuni di colonna derivata in cui si desidera restituire i valori NULL con altri valori.  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]  
>  Nell'esempio seguente viene illustrato come questa operazione è stata eseguita [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] / [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? “1900-01-01” : MyColumn)   
```  
  
  
