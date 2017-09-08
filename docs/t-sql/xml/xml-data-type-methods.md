---
title: Metodi con tipo di dati XML | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: d112b9c9-be9f-435c-a9e6-d21b65778fb7
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fcf16bd9b71f27ab91fb02bbfd7bb7625185b44e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-type-methods"></a>Metodi con tipo di dati XML
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  È possibile utilizzare il **xml** metodi per eseguire query di un'istanza XML archiviata in una variabile o colonna di tipo di dati **xml** tipo. Negli argomenti di questa sezione viene illustrato come utilizzare il **xml** metodi con tipo di dati.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[query &#40; &#41; Metodo &#40; tipo di dati xml &#41;](../../t-sql/xml/query-method-xml-data-type.md)|Viene descritto come utilizzare il metodo query() per eseguire una query su un'istanza XML.|  
|[valore &#40; &#41; Metodo &#40; tipo di dati xml &#41;](../../t-sql/xml/value-method-xml-data-type.md)|Viene descritto come utilizzare il metodo value() per recuperare un valore di tipo SQL da un'istanza XML.|  
|[esistere &#40; &#41; Metodo &#40; tipo di dati xml &#41;](../../t-sql/xml/exist-method-xml-data-type.md)|Viene descritto come utilizzare il metodo exist() per determinare se una query restituisce un risultato non vuoto.|  
|[modificare &#40; &#41; Metodo &#40; tipo di dati xml &#41;](../../t-sql/xml/modify-method-xml-data-type.md)|Viene descritto come utilizzare il metodo Modify () per specificare [linguaggio di manipolazione dei dati XML &#40; Linguaggio XML DML &#41; ](../../t-sql/xml/xml-data-modification-language-xml-dml.md)istruzioni per eseguire gli aggiornamenti.|  
|[nodi &#40; &#41; Metodo &#40; tipo di dati xml &#41;](../../t-sql/xml/nodes-method-xml-data-type.md)|Viene descritto come utilizzare il metodo nodes() per suddividere XML in più righe in modo da propagare sezioni di documenti XML in set di righe.|  
|[Associazione di dati relazionali all'interno di dati XML](../../t-sql/xml/binding-relational-data-inside-xml-data.md)|Viene descritto come eseguire l'associazione di dati non XML in XML.|  
|[Linee guida per l'utilizzo dei metodi con tipo di dati xml](../../t-sql/xml/guidelines-for-using-xml-data-type-methods.md)|Vengono fornite istruzioni per l'utilizzo di **xml** metodi con tipo di dati.|  
  
 Per chiamare questi metodi, è necessario utilizzare la sintassi di richiamo dei metodi di tipo definito dall'utente. Esempio:  
  
```  
SELECT XmlCol.query(' ... ')  
FROM   Table  
```  
  
> [!NOTE]  
>  Il **xml** metodi con tipo di dati **query ()**, **Value ()**, e **exist ()** restituire NULL se eseguiti in un'istanza XML NULL. Inoltre, **Modify ()** non restituisce alcun valore, ma **Nodes ()** restituisce set di righe e un set di righe vuoto con un input NULL.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  
