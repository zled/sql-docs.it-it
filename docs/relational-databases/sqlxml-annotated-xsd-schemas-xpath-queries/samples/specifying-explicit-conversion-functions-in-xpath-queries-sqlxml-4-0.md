---
title: Specifica di funzioni di conversione esplicita nelle query XPath (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 17e6efeab07a4955ac115ef8a8a986e170e66330
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>Specifica di funzioni di conversione esplicita in query XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Negli esempi seguenti viene illustrato come specificare le funzioni di conversione esplicita nelle query XPath. Le query XPath di questi esempi vengono specificate sullo schema di mapping contenuto in SampleSchema1.xml. Per informazioni su questo schema di esempio, vedere [Schema XSD con annotazioni di esempio per gli esempi XPath & #40; SQLXML 4.0 & #41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>A. Utilizzo della funzione di conversione esplicita number ()  
 Il **Number()** funzione converte un argomento a un numero.  
  
 Supponendo che il valore di **ContactID** è un valore numerico, la query seguente converte **ContactID** a un numero e lo confronta con il valore 4. La query restituisce quindi tutti  **\<dipendente >** gli elementi figlio del nodo di contesto con il **ContactID** attributo con un valore numerico 4:  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 Un collegamento per il **attributo** asse (@) può essere specificato e poiché il **figlio** è l'asse predefinito, può essere omesso dalla query:  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 In termini relazionali, la query restituisce un dipendente con un **ContactID** di 4.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Per testare la query Xpath sullo schema di mapping  
  
1.  Copia il [schema codice di esempio](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) e incollarlo in un file di testo. Salvare il file con il nome SampleSchema1.xml.  
  
2.  Creare il modello seguente (ExplicitConversionA.xml) e salvarlo nella directory in cui è stato salvato il file SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping SampleSchema1.xml è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query di SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati relativo all'esecuzione di questo modello:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>B. Utilizzo della funzione di conversione esplicita string ()  
 Il **String()** funzione converte un argomento in una stringa.  
  
 La query seguente converte **ContactID** in una stringa e viene confrontato con la stringa di valore "4". La query restituisce tutti  **\<dipendente >** gli elementi figlio del nodo di contesto con un **ContactID** con un valore stringa "4":  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 Un collegamento per il **attributo** asse (@) può essere specificato e poiché il **figlio** è l'asse predefinito, può essere omesso dalla query:  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 Dal punto di vista funzionale questa query restituisce gli stessi risultati della query di esempio precedente, sebbene la valutazione venga fatta rispetto a un valore stringa e non al valore numerico (ovvero il numero 4).  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Per testare la query Xpath sullo schema di mapping  
  
1.  Copia il [schema codice di esempio](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) e incollarlo in un file di testo. Salvare il file con il nome SampleSchema1.xml.  
  
2.  Creare il modello seguente (ExplicitConversionB.xml) e salvarlo nella directory in cui è stato salvato il file SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping SampleSchema1.xml è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query di SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati relativo all'esecuzione del modello:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
