---
title: Associazione di dati relazionali all'interno di dati XML | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
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
- relational data binding [SQL Server]
- XML [SQL Server], binding relational data
- xml data type [SQL Server], relational data binding
- binding relational data [XML in SQL Server]
- variables [XML in SQL Server], relational data binding
- columns [XML in SQL Server], relational data binding
ms.assetid: 03d013a9-b53f-46c3-9628-da77f099c74a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fbb6d199812f90c07e9efa81da11f834e58cdb59
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="binding-relational-data-inside-xml-data"></a>Associazione di dati relazionali all'interno di dati XML
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  È possibile specificare [metodi con tipo di dati xml](../../t-sql/xml/xml-data-type-methods.md) contro un **xml** variabile o una colonna del tipo di dati. Ad esempio, il [query &#40; &#41; Metodo &#40; tipo di dati xml &#41; ](../../t-sql/xml/query-method-xml-data-type.md) esegue la query XQuery specificata su un'istanza XML. Quando si creano dati XML in questo modo, è possibile inserirvi un valore di una colonna di tipo non XML o di una variabile Transact-SQL. Questo processo viene definito associazione di dati relazionali all'interno di dati XML.  
  
 Nel Motore di database di SQL Server sono disponibili le pseudofunzioni seguenti che consentono di associare dati relazionali non XML all'interno di dati XML:  
  
-   [SQL: Column &#40; &#41; Funzione &#40; XQuery &#41; ](../../xquery/xquery-extension-functions-sql-column.md) Consente di utilizzare i valori di una colonna relazionale nell'espressione XQuery o XML DML.  
  
-   [SQL: variable &#40; &#41; Funzione &#40; XQuery &#41; ](../../xquery/xquery-extension-functions-sql-variable.md) . Consente di utilizzare il valore di una variabile SQL nell'espressione XQuery o XML DML.  
  
 È possibile utilizzare queste funzioni con **xml** metodi con tipo di dati ogni volta che si desidera esporre un valore relazionale nell'istanza XML.  
  
 È possibile utilizzare queste funzioni per fare riferimento ai dati in colonne o variabili del **xml**, CLR definito dall'utente tipi, datetime, smalldatetime, **testo**, **ntext**, **sql_variant**, e **immagine** tipi.  
  
 Inoltre, questo tipo di associazione è destinata a scopi di sola lettura, ovvero non è possibile scrivere dati nelle colonne che utilizzano queste funzioni. Ad esempio, sql:variable("@x") = "*alcune espressioni"* non è consentito.  
  
## <a name="example-cross-domain-query-using-sqlvariable"></a>Esempio: query tra domini tramite sql:variable()  
 Questo esempio viene illustrato come **SQL: variable** può consentire a un'applicazione di parametrizzare una query. Il codice ISBN viene passato utilizzando una variabile SQL @isbn. Sostituendo la costante con **SQL: variable**, la query consente di cercare qualsiasi codice ISBN, non solo gli elementi il cui ISBN è 0-7356-1588-2.  
  
```  
DECLARE @isbn varchar(20)  
SET     @isbn = '0-7356-1588-2'  
SELECT  xCol  
FROM    T  
WHERE   xCol.exist ('/book/@ISBN[. = sql:variable("@isbn")]') = 1  
```  
  
 **SQL: Column** può essere utilizzato in modo analogo e offre vantaggi aggiuntivi. Per migliorare l'efficienza è possibile utilizzare indici sulla colonna, in base a quanto stabilito dallo strumento Query Optimizer basato sui costi. Nella colonna calcolata può inoltre essere archiviata una proprietà promossa.  
  
## <a name="see-also"></a>Vedere anche  
 [metodi con tipo di dati xml](../../t-sql/xml/xml-data-type-methods.md)  
  
  

