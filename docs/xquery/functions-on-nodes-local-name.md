---
title: Funzione local-name (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 52ae1021c17469e8fb5691fcf1da527cc348c950
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="functions-on-nodes---local-name"></a>Funzioni sui nodi - local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce la parte locale del nome di *$arg* come xs: String che sarà la stringa di lunghezza zero o avrà il formato lessicale di un xs: NCName. Se non si specifica l'argomento, il valore predefinito è il nodo di contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Nome del nodo di cui verrà recuperata la parte local-name.  
  
## <a name="remarks"></a>Osservazioni  
  
-   In SQL Server, **fn:local-name()** senza un argomento può essere utilizzato solo nel contesto di un predicato dipendente dal contesto. In particolare, può essere utilizzata solo tra parentesi (`[ ]`).  
  
-   Se si specifica l'argomento e questo corrisponde alla sequenza vuota, la funzione restituisce la stringa di lunghezza zero.  
  
-   Se il nodo di destinazione non dispone di un nome specifico, in quanto è un nodo di documento, un nodo di commento o un nodo di testo, la funzione restituisce la stringa di lunghezza zero.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. Recupero del nome locale di un nodo specifico  
 La query seguente viene eseguita su un'istanza XML non tipizzata. L'espressione della query, `local-name(/ROOT[1])`, recupera la parte del nome locale del nodo specificato.  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 La query viene eseguita sulla colonna Instructions, una colonna xml tipizzata della tabella ProductModel. L'espressione `local-name(/AWMI:root[1]/AWMI:Location[1])` restituisce il nome locale `Location` del nodo specificato.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>B. Utilizzo della funzione local-name senza argomento in un predicato  
 La query seguente viene specificata sulla colonna Instructions, tipizzata **xml** colonna della tabella ProductModel. L'espressione restituisce tutti gli elementi figlio dell'elemento <`root`>, per il quale la parte di nome locale del nome completo (QName) è "Location". Il **Local** funzione è specificata nel predicato e non contiene argomenti del nodo di contesto viene utilizzato dalla funzione.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 La query restituisce tutti gli elementi figlio <`Location`> dell'elemento <`root`>.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni sui nodi](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Funzione namespace-uri &#40; XQuery &#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
