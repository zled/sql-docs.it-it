---
title: Funzioni XQuery per il tipo di dati xml | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
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
- XQuery, functions
- xml data type [SQL Server], XQuery
- functions [SQL Server], XQuery
ms.assetid: 8df0877d-a03f-4ca9-b84e-908c4bb42b5e
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f950e3bbeb239537bc606c38469b9fb79e36837b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xquery-functions-against-the-xml-data-type"></a>Funzioni XQuery per il tipo di dati XML
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questo argomento e nei relativi sottoargomenti descrivono le funzioni che è possibile utilizzare quando si specifica XQuery di **xml** tipo di dati. Per le specifiche W3C, vedere [http://www.w3.org/TR/2004/WD-xpath-functions-20040723](http://go.microsoft.com/fwlink/?LinkId=4873).  
  
 Le funzioni XQuery appartengono allo spazio dei nomi http://www.w3.org/2004/07/xpath-functions. Le specifiche W3C utilizzano il prefisso "fn:" dello spazio dei nomi per la descrizione di queste funzioni. Quando si utilizzano le funzioni non è necessario specificare esplicitamente il prefisso "fn:". Per questo motivo e per migliorare la leggibilità, in questa documentazione i prefissi dello spazio dei nomi sono in genere omessi.  
  
 La tabella seguente elenca le funzioni XQuery supportate sul **xml**tipo di dati.  
  
|Category|Nome funzione|  
|--------------|-------------------|  
|[Funzioni su valori numerici](http://msdn.microsoft.com/library/d5740a32-b174-43b9-b64d-1cc6edc50cff)|[limite massimo](../xquery/numeric-values-functions-ceiling.md)|  
||[floor](../xquery/numeric-values-functions-floor.md)|  
||[arrotondamento](../xquery/numeric-values-functions-round.md)|  
|[Funzioni XQuery su valori stringa](http://msdn.microsoft.com/library/2dccefef-5d90-4f56-bda7-4c1954d8a730)|[Concat](../xquery/functions-on-string-values-concat.md)|  
||[contiene](../xquery/functions-on-string-values-contains.md)|  
||[sottostringa](../xquery/functions-on-string-values-substring.md)|  
||[minuscole Function &#40; XQuery &#41;](../xquery/functions-on-string-values-lower-case.md)|  
||[lunghezza della stringa](../xquery/functions-on-string-values-string-length.md)|  
||[lettere maiuscole Function &#40; XQuery &#41;](../xquery/functions-on-string-values-upper-case.md)|  
|Funzioni su valori booleani|[non](../xquery/functions-on-boolean-values-not-function.md)|  
|[Funzioni sui nodi](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)|[numero](../xquery/functions-on-nodes-number.md)|  
||[Funzione local-name (XQuery)](../xquery/functions-on-nodes-local-name.md)|  
||[Funzione namespace-uri (XQuery)](../xquery/functions-on-nodes-namespace-uri.md)|  
|[Funzioni di contesto](http://msdn.microsoft.com/library/f7d8af33-9de9-450c-a667-23dee3129b5f)|[ultimo](../xquery/context-functions-last-xquery.md)|  
||[posizione](../xquery/context-functions-position-xquery.md)|  
|[Funzioni per le sequenze](http://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)|[vuoto](../xquery/functions-on-sequences-empty.md)|  
||[valori Distinct](../xquery/functions-on-sequences-distinct-values.md)|  
||[Funzione ID (XQuery)](../xquery/functions-on-sequences-id.md)|  
|[Funzioni di aggregazione &#40; XQuery &#41;](http://msdn.microsoft.com/library/be647ef1-291e-4a5d-ab18-07c759efe176)|[count](../xquery/aggregate-functions-count.md)|  
||[AVG](../xquery/aggregate-functions-avg.md)|  
||[Min](../xquery/aggregate-functions-min.md)|  
||[Max](../xquery/aggregate-functions-max.md)|  
||[somma](../xquery/aggregate-functions-sum.md)|  
|[Funzioni costruttore &#40; XQuery &#41;](../xquery/constructor-functions-xquery.md)|[Funzioni costruttore](../xquery/constructor-functions-xquery.md)|  
|[Funzioni di accesso ai dati](../xquery/data-accessor-functions.md)|[string](../xquery/data-accessor-functions-string-xquery.md)|  
||[dati](../xquery/data-accessor-functions-data-xquery.md)|  
|[Funzioni costruttore booleane &#40; XQuery &#41;](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)|[Funzione true (XQuery)](../xquery/boolean-constructor-functions-true-xquery.md)|  
||[Funzione false (XQuery)](../xquery/boolean-constructor-functions-false-xquery.md)|  
|[Funzioni correlate a elementi QName &#40; XQuery &#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)|[Expanded-QName (XQuery)](../xquery/functions-related-to-qnames-expanded-qname.md)|  
||[local-name-da-QName (XQuery)](../xquery/functions-related-to-qnames-local-name-from-qname.md)|  
||[namespace-uri-da-QName (XQuery)](../xquery/functions-related-to-qnames-namespace-uri-from-qname.md)|  
|[Funzioni per le estensioni XQuery SQL Server](http://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)|[funzione SQL: Column (XQuery)](../xquery/xquery-extension-functions-sql-column.md)|  
||[funzione SQL: variable (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  
