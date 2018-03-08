---
title: Linee guida per l'utilizzo di metodi con tipo di dati xml | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: 1a483aa1-42de-4c88-a4b8-c518def3d496
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79f10b22ba88d6dd860c608c9468e20a27615650
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="guidelines-for-using-xml-data-type-methods"></a>Linee guida per l'utilizzo dei metodi con tipo di dati xml
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questo argomento vengono fornite istruzioni per l'utilizzo di **xml** metodi con tipo di dati.  
  
## <a name="the-print-statement"></a>Istruzione PRINT  
 Il **xml** metodi con tipo di dati non possono essere utilizzati nell'istruzione PRINT come illustrato nell'esempio seguente. Il **xml** metodi con tipo di dati vengono considerati come sottoquery, e le sottoquery non sono consentite nell'istruzione PRINT. L'esempio seguente restituisce pertanto un errore:  
  
```  
DECLARE @x xml  
SET @x = '<root>Hello</root>'  
PRINT @x.value('/root[1]', 'varchar(20)') -- will not work because this is treated as a subquery (select top 1 col from table)   
```  
  
 Una soluzione consiste nell'assegnare il risultato del **Value ()** metodo a una variabile di **xml** digitare e quindi specificare la variabile nella query.  
  
```  
DECLARE @x xml  
DECLARE @c varchar(max)  
SET @x = '<root>Hello</root>'  
SET @c = @x.value('/root[1]', 'varchar(11)')  
PRINT @c                                                        
```  
  
## <a name="the-group-by-clause"></a>Clausola GROUP BY  
 Il **xml** metodi con tipo di dati vengono considerati internamente come sottoquery. Poiché GROUP BY richiede un valore scalare e non consente aggregazioni e sottoquery, è possibile specificare il **xml** metodi con tipo di dati nella clausola GROUP BY. Una soluzione è rappresentata da una chiamata a una funzione definita dall'utente all'interno della quale vengono utilizzati metodi XML.  
  
## <a name="reporting-errors"></a>Segnalazione degli errori  
 Quando si segnalano errori, **xml** metodi con tipo di dati generano un singolo errore nel formato seguente:  
  
```  
Msg errorNumber, Level levelNumber, State stateNumber:  
XQuery [database.table.method]: description_of_error  
```  
  
 Esempio:  
  
```  
Msg 2396, Level 16, State 1:  
XQuery [xmldb_test.xmlcol.query()]: Attribute may not appear outside of an element  
```  
  
## <a name="singleton-checks"></a>Verifiche dei singleton  
 Se il compilatore non è in grado di determinare se un determinato valore singleton è garantito in fase di esecuzione, i passi, i parametri delle funzioni e gli operatori che richiedono un singleton restituiranno un errore. Questo problema si verifica di frequente con i dati non tipizzati. Per la ricerca di un attributo, ad esempio, è necessario un elemento padre singleton. È sufficiente un numero ordinale che seleziona un nodo padre singolo. La valutazione di un **node ()**-**Value ()** combinazione per estrarre i valori di attributo può non richiedere di specificare il numero ordinale. come illustrato nell'esempio seguente.  
  
### <a name="example-known-singleton"></a>Esempio: singleton noto  
 In questo esempio, il **Nodes ()** metodo genera una riga distinta per ogni <`book`> elemento. Il **Value ()** metodo che viene valutata in un <`book`> nodo estrae il valore di @genre e, essendo un attributo, è un singleton.  
  
```  
SELECT nref.value('@genre', 'varchar(max)') LastName  
FROM   T CROSS APPLY xCol.nodes('//book') AS R(nref)  
```  
  
 Per la verifica dei dati XML tipizzati viene utilizzato un XML Schema. Se un determinato nodo è specificato come singleton nell'XML Schema, il compilatore utilizza tale informazione e non viene generato alcun errore. In caso contrario, è necessario specificare un numero ordinale che seleziona un nodo singolo. In particolare, l'utilizzo dell'asse descendant-or-self (/ /) dell'asse, ad esempio in /Book//Title /Book//Title l'inferenza della cardinalità singleton per, il \<titolo > elemento, anche se lo schema XML specifica come tale. ed è pertanto necessario riscriverlo come (/book//title)[1].  
  
 La differenza tra //first-name[1] e (//first-name)[1] è molto importante per la verifica dei tipi. Il primo restituisce una sequenza di \<first-name > nodi in cui ogni nodo è il più a sinistra \<first-name > nodo tra elementi di pari livello. Quest'ultimo restituisce il primo singleton \<first-name > nodo nell'ordine del documento nell'istanza XML.  
  
### <a name="example-using-value"></a>Esempio: utilizzo del metodo value()  
 La query seguente su una colonna XML non tipizzata generato un errore statico, di compilazione. In questo modo **Value ()** prevede un nodo singleton come primo argomento e il compilatore non è possibile determinare se un solo \<last-name > nodo verrà eseguita in fase di esecuzione:  
  
```  
SELECT xCol.value('//author/last-name', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Una possibile soluzione è la seguente:  
  
```  
SELECT xCol.value('//author/last-name[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Tale soluzione non risolve tuttavia il problema, perché in ogni istanza XML possono essere presenti più nodi <`author`>. Per risolvere il problema è necessario riscrivere il codice come segue:  
  
```  
SELECT xCol.value('(//author/last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Questa query restituisce il valore del primo elemento `<last-name>` in ogni istanza XML.  
  
## <a name="see-also"></a>Vedere anche  
 [metodi con tipo di dati xml](../../t-sql/xml/xml-data-type-methods.md)  
  
  
