---
title: Funzione CEILING (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f50d1816ea6adb7e11bbf583f37ca8e8b9176223
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="numeric-values-functions---ceiling"></a>Funzioni a valori numeriche - ceiling 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il più piccolo numero senza una parte frazionaria e non inferiore al valore del relativo argomento. Se l'argomento è una sequenza vuota, restituisce la sequenza vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:ceiling ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Numero al quale viene applicata la funzione.  
  
## <a name="remarks"></a>Osservazioni  
 Se il tipo di *$arg* è uno dei tre tipi numerici di base, **xs: float**, **xs: double**, o **xs: decimal**, il tipo restituito è identico il *$arg* tipo.  
  
 Se il tipo di *$arg* è un tipo derivato da uno dei tipi numerici, il tipo restituito è il tipo di base numerico.  
  
 Se l'input per le funzioni fn: floor, fn: Ceiling o Fn **xdt: untypedAtomic**, viene eseguito in modo implicito il cast **xs: double**.  
  
 Qualsiasi altro tipo di dati genera un errore statico.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. Utilizzo della funzione booleana XQuery ceiling()  
 Per il modello di prodotto 7, la query restituisce un elenco dei centri di lavorazione coinvolti nel processo di produzione del modello. Per ogni centro di lavorazione, la query restituisce l'ID, le ore di manodopera e la dimensione del lotto, se documentati. La query utilizza la **ceiling** funzione per restituire le ore di manodopera come valori di tipo **decimale**.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
     for $i in /AWMI:root/AWMI:Location  
     return   
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ ceiling($i/@LaborHours) }" >  
                    {   
                      $i/@LotSize  
                    }    
       </Location>  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il prefisso AWMI è l'acronimo di Adventure Works Manufacturing Instructions e fa riferimento allo stesso spazio dei nomi utilizzato nel documento sul quale viene eseguita la query.  
  
-   **Istruzioni** è un **xml** colonna di tipo. Pertanto, il [metodo query () (tipo di dati XML)](../t-sql/xml/query-method-xml-data-type.md) viene utilizzato per specificare una query XQuery. L'istruzione XQuery viene specificata come argomento per il metodo di query.  
  
-   **per … restituire** è un costrutto di ciclo. Nella query, il **per** ciclo identifica un elenco di \<percorso > elementi. Per ogni centro di lavorazione, la **restituire** istruzione il **per** ciclo descrive il codice XML generato:  
  
    -   Oggetto \<percorso > elemento con attributi LocationID e LaborHrs. L'espressione corrispondente racchiusa tra parentesi graffe ({ }) recupera i valori necessari dal documento.  
  
    -   Il {$i/@LotSize } espressione recupera l'attributo LotSize dal documento, se presente.  
  
    -   Risultato:  
  
```  
ProductModelID Result    
-------------- ------------------------------------------------------  
7      <Location LocationID="10" LaborHrs="3" LotSize="100"/>  
       <Location LocationID="20" LaborHrs="2" LotSize="1"/>     
       <Location LocationID="30" LaborHrs="1" LotSize="1"/>     
       <Location LocationID="45" LaborHrs="1" LotSize="20"/>  
       <Location LocationID="60" LaborHrs="3" LotSize="1"/>     
       <Location LocationID="60" LaborHrs="4" LotSize="1"/>  
```  
  
### <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **Ceiling ()** funzione esegue il mapping di tutti i valori integer a xs: decimal.  
  
## <a name="see-also"></a>Vedere anche  
 [floor (funzione) &#40; XQuery &#41;](../xquery/numeric-values-functions-floor.md)   
 [arrotondare Function &#40; XQuery &#41;](../xquery/numeric-values-functions-round.md)  
  
  
