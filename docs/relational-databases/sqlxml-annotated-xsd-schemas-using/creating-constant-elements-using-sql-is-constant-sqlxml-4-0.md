---
title: 'Creazione di elementi costanti tramite sql: è-constant (SQLXML 4.0) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 81ee34607d198e88eee397b9c9f254f2133d1b22
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32969386"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Creazione di elementi costanti tramite sql:is-constant (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Per specificare un elemento costante, vale a dire un elemento nello schema XSD che non esegue il mapping ad alcuna tabella di database o una colonna, è possibile utilizzare il **sql:costante-è** annotazione. Questa annotazione accetta un valore booleano (0=false, 1=true). I valori possibili sono 0, 1, true e false. Il **sql:costante-è** annotazione può essere specificata su un elemento che non dispone di attributi. Se viene specificata in un elemento con valore true (o 1), l'elemento non viene mappato al database ma viene comunque visualizzato nel documento XML.  
  
 Il **sql:costante-è** annotazione può essere utilizzata per:  
  
-   Aggiunta di un elemento di livello principale al documento XML. XML richiede un singolo elemento di livello principale (elemento radice) per il documento.  
  
-   Creazione di elementi contenitore, ad esempio un  **\<ordini >** elemento che esegue il wrapping di tutti gli ordini.  
  
 Il **sql: costante è** annotazione può essere aggiunta a un  **\<complexType >** elemento.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per esecuzione esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. Definizione di sql:is-constant per aggiungere un elemento contenitore  
 In questo schema con annotazioni di XSD,  **\<CustomerOrders >** viene definito come elemento costante specificando il **sql: costante è** attributo con un valore pari a 1. Pertanto,  **\<CustomerOrders >** non è mappato ad alcuna tabella di database o di una colonna. Questo elemento costante è costituito il  **\<ordine >** gli elementi figlio.  
  
 Sebbene  **\<CustomerOrders >** non è mappato ad alcuna tabella di database o di una colonna, viene comunque visualizzato nel documento XML risultante come elemento contenitore che contiene il  **\<ordine >** elementi figlio.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome isConstant.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome isConstantT.xml nella stessa directory in cui è stato salvato il file isConstant.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (isConstant.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati parziale:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
