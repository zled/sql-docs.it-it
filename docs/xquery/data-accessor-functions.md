---
title: Le funzioni di accesso dati | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords: data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c77c0a1a9b6d61465956d8e1e81eb58e86f8b086
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="data-accessor-functions"></a>Funzioni di accesso ai dati
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Negli argomenti di questa sezione vengono descritte le funzioni di accesso ai dati e viene fornito codice di esempio.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Informazioni su fn:data(), fn:string() e text()  
 XQuery include una funzione **Fn** per estrarre valori scalari tipizzati dai nodi, un test di nodo **Text ()** per restituire i nodi di testo e la funzione **fn:string()** che restituisce il valore di stringa di un nodo. L'utilizzo di tali funzioni non è tuttavia intuitivo. Di seguito vengono riportate le linee guida da seguire per il corretto utilizzo di tali funzioni in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L'istanza XML \<age > 12 \< /age > viene utilizzato a scopo illustrativo.  
  
-   Dati XML non tipizzati: l'espressione di percorso /age/text() restituisce il nodo di testo "12". La funzione fn:data(/age) restituisce il valore stringa "12", così come la funzione fn:string(/age).  
  
-   Dati XML tipizzati: L'espressione /Age/Text () restituisce un errore statico per qualsiasi tipizzata semplice \<age > elemento. La funzione fn:data(/age) restituisce invece il valore intero 12, mentre fn:string(/age) restituisce la stringa "12".  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [stringa Function &#40; XQuery &#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [Funzione data &#40; XQuery &#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di percorso &#40; XQuery &#41;](../xquery/path-expressions-xquery.md)  
  
  
