---
title: numero di funzione (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 65faec31c6e89421ce05bab28dae97e18195bdde
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031519"
---
# <a name="functions-on-nodes---number"></a>Funzioni sui nodi - number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore numerico del nodo in cui è indicato da *$arg*.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Nodo per il quale verrà restituito un valore numerico.  
  
## <a name="remarks"></a>Note  
 Se *$arg* viene omesso, viene restituito il valore numerico del nodo di contesto, convertito in valore double. In SQL Server **fn:number()** senza un argomento può essere utilizzato solo nel contesto di un predicato dipendente dal contesto. In particolare, può essere utilizzata solo tra parentesi ([ ]). Ad esempio, l'espressione seguente restituisce l'elemento <`ROOT`>.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 Se il valore del nodo non è una rappresentazione lessicale valida di un tipo semplice numerico, come definito in **XML Schema Part 2: Datatypes, la raccomandazione W3C**, la funzione restituisce una sequenza vuota. NaN non è supportato.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>A. Utilizzo della funzione XQuery number() per recuperare il valore numerico di un attributo  
 La query seguente recupera il valore numerico dell'attributo lotsize dal primo centro di lavorazione nel processo di produzione del modello di prodotto 7.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in (//AWMI:root//AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"   
                   LotSizeA="{  $i/@LotSize }"  
                   LotSizeB="{  number($i/@LotSize) }"  
                   LotSizeC="{ number($i/@LotSize) + 1 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il **Number ()** funzione non è necessaria, come illustrato dalla query per il **LotSizeA** attributo. Si tratta infatti di una funzione XPath della versione 1.0 ed è stata inclusa principalmente per motivi di compatibilità con le versioni precedenti.  
  
-   La query XQuery per **LotSizeB** specifica la funzione number ed è ridondante.  
  
-   La query per **LotSizeD** viene illustrato l'utilizzo di un valore numerico in un'operazione aritmetica.  
  
 Risultato:  
  
```  
ProductModelID   Result  
----------------------------------------------  
7              <Location LocationID="10"   
                         LotSizeA="100"   
                         LotSizeB="100"   
                         LotSizeC="101" />  
```  
  
### <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **Number ()** funzione accetta solo nodi. Non accetta valori atomici.  
  
-   Quando non possono essere restituiti valori sotto forma di numero, il **Number ()** funzione restituisce una sequenza vuota anziché NaN.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
