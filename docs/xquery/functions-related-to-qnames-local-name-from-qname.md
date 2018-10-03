---
title: local-name-from-QName (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name-from-QName function
- local-name-from-QName function
ms.assetid: fafed718-8c3c-403f-93ee-ec51fc157a6e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8bcccc438f64b31405b4234e0817878d9a11cf56
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798849"
---
# <a name="functions-related-to-qnames---local-name-from-qname"></a>Funzioni correlate a elementi QName - local-name-from-QName
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un xs: NCName che rappresenta la parte locale di QName specificata da *$arg*. Il risultato è una sequenza vuota se *$arg* è una sequenza vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
fn:local-name-from-QName($arg as xs:QName?) as xs:NCName?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 QName da cui deve essere estratto il nome locale.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo i [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.  
  
 L'esempio seguente usa il **local-name-from-QName()** parti di funzione per recuperare il nome locale e l'URI dello spazio dei nomi da un valore di tipo QName. Nell'esempio vengono eseguite le operazioni seguenti:  
  
-   Viene creata una raccolta di XML Schema.  
  
-   Viene creata una tabella con una colonna di tipo XML. Il tipo XML viene tipizzato tramite la raccolta di XML Schema.  
  
-   Viene archiviata un'istanza XML di esempio nella tabella. Usando il **query ()** metodo del tipo di dati xml, l'espressione di query viene eseguito per recuperare la parte del nome locale del valore di tipo QName dall'istanza.  
  
```  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<root xmlns="QNameXSD" xmlns:a="http://someURI">a:someLocalName</root>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare default element namespace "QNameXSD"; local-name-from-QName(/root[1])')  
FROM T  
-- Result = someLocalName  
-- You can retrive namespace URI part from the QName using the namespace-uri-from-QName() function  
SELECT xmlCol.query('declare default element namespace "QNameXSD"; namespace-uri-from-QName(/root[1])')  
FROM T  
-- Result = http://someURI  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni correlate a elementi QName &#40;XQuery&#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
