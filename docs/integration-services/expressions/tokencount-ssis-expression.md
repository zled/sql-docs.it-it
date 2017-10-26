---
title: TOKENCOUNT (espressione SSIS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 77faf8083207373dee5dba3721fb38f91eefc3f2
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="tokencount-ssis-expression"></a>TOKENCOUNT (espressione SSIS)
  Restituisce il numero di token in una stringa che contiene token separati dai delimitatori specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Stringa che contiene token separati da delimitatori.  
  
 *delimiter_string*  
 Stringa che contiene caratteri delimitatori. Ad esempio, "; ,” contiene i caratteri delimitatori punto e virgola, spazio e virgola.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Osservazioni  
 Le osservazioni seguenti riguardano la funzione TOKEN:  
  
-   La stringa di delimitazione può contenere uno o più caratteri delimitatori.  
  
-   I delimitatori iniziali vengono ignorati.  
  
-   TOKENCOUNT funziona unicamente con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da TOKEN verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR.  
  
-   TOKENCOUNT restituisce 0 (zero) se character_expression è Null.  
  
-   È possibile utilizzare variabili e colonne come argomenti di questa espressione.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nell'esempio seguente, la funzione TOKENCOUNT restituisce 3 perché la stringa contiene tre token: "01", "12", "2011".  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 Nell'esempio seguente la funzione TOKENCOUNT restituisce 4 perché la stringa contiene quattro token ("a", "little", "white", "dog").  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 Nell'esempio seguente la funzione TOKENCOUNT restituisce 1. La funziona cerca i delimitatori nella stringa di input e poiché non ve ne sono, aggiunge l'intera stringa come primo token.  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 Nell'esempio seguente la funzione TOKENCOUNT restituisce 4. In questo esempio la stringa di delimitazione contiene 5 delimitatori. La stringa di input contiene 4 token: "a", "little", "white", "dog".  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 Nell'esempio seguente la funzione TOKENCOUNT restituisce 4. Tutti gli spazi iniziali vengono ignorati.  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; Espressione SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

