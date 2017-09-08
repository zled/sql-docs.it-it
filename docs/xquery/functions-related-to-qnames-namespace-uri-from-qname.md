---
title: namespace-uri-da-QName (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3af81f884ff54ff6bea5f07f97d31cf0ad2342
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Funzioni correlate a elementi QName - spazio dei nomi uri da QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una stringa che rappresenta l'uri dello spazio dei nomi dell'elemento QName specificato da *$arg*. Il risultato è una sequenza vuota se *$arg* è una sequenza vuota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 QName per il quale viene restituito l'URI dello spazio dei nomi.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. Recuperare l'URI dello spazio dei nomi per un QName  
 Per un esempio funzionante, vedere [nome locale da QName &#40; XQuery &#41; ](../xquery/functions-related-to-qnames-local-name-from-qname.md).  
  
### <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **namespace-uri-from-QName()** funzione restituisce istanze di xs: String anziché di xs: anyURI.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni correlate a elementi QName &#40; XQuery &#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
