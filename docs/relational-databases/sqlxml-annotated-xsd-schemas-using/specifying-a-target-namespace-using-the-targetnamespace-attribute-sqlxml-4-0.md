---
title: Specifica destinazione Namespace utilizzando l'attributo (SQLXML 4.0) targetNamespace | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9b0b325cea845e82519752b04591c2c7724b1acf
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>Specifica di uno spazio dei nomi di destinazione mediante l'attributo targetNamespace (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Nella creazione degli schemi XSD, è possibile utilizzare lo schema XSD **targetNamespace** attributo per specificare uno spazio dei nomi di destinazione. Questo argomento viene descritto come XSD **targetNamespace**, **elementFormDefault**, e **attributeFormDefault** gli attributi di lavoro, come influiscono l'istanza XML che è generato, e come vengono specificate query XPath con spazi dei nomi.  
  
 È possibile utilizzare il **xsd: targetNamespace** attributo per inserire elementi e attributi dello spazio dei nomi predefinito in uno spazio dei nomi diversi. È inoltre possibile specificare se gli elementi e gli attributi dello schema dichiarati localmente devono essere qualificati da uno spazio dei nomi, sia in modo esplicito mediante un prefisso sia in modo implicito per impostazione predefinita. È possibile utilizzare il **elementFormDefault** e **attributeFormDefault** gli attributi di  **\<xsd: schema >** elemento per specificare a livello globale la qualifica degli elementi locali e gli attributi, oppure è possibile utilizzare il **modulo** attributo per specificare separatamente i singoli elementi e attributi.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per esecuzione esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-a-target-namespace"></a>A. Specificare uno spazio dei nomi di destinazione  
 Lo schema XSD seguente specifica uno spazio dei nomi di destinazione utilizzando il **xsd: targetNamespace** attributo. Lo schema imposta inoltre il **elementFormDefault** e **attributeFormDefault** per i valori dell'attributo **"unqualified"** (il valore predefinito per questi attributi). Si tratta di una dichiarazione globale che influisce su tutti gli elementi locali (**\<ordine >** nello schema) e attributi (**CustomerID**, **ContactName**e  **OrderID** nello schema).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Nello schema:  
  
-   Il **CustomerType** e **OrderType** dichiarazioni di tipo sono globali e, pertanto, sono inclusi nello spazio dei nomi di destinazione dello schema. Di conseguenza, quando questi tipi viene fatto riferimento nella dichiarazione di  **\<cliente >** elemento e il relativo  **\<ordine >** elemento figlio, viene specificato un prefisso associato con lo spazio dei nomi di destinazione.  
  
-   Il  **\<cliente >** elemento viene inoltre incluso nello spazio dei nomi di destinazione dello schema perché è un elemento globale nello schema.  
  
 Eseguire sullo schema la query Xpath seguente:  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 La query XPath genera questo documento dell'istanza (sono mostrati solo alcuni ordini):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 Questo documento dell'istanza definisce lo spazio dei nomi urn: MyNamespace e associa un prefisso (y0) a esso. Il prefisso viene applicato solo al  **\<cliente >** elemento globale. (L'elemento è globale poiché è stato dichiarato come elemento figlio di  **\<xsd: schema >** elemento nello schema.)  
  
 Il prefisso non viene applicato agli elementi locali e gli attributi perché il valore di **elementFormDefault** e **attributeFormDefault** attributi è impostato su **"unqualified"** nello schema. Si noti che il  **\<ordine >** elemento è locale poiché la relativa dichiarazione appare come elemento figlio di  **\<complexType >** elemento che definisce il  **\< CustomerType >** elemento. Analogamente, gli attributi (**CustomerID**, **OrderID**, e **ContactName**) sono locali, non globali.  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>Per creare un esempio reale di questo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome targetNameSpace.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file come targetNameSpaceT.xml nella stessa directory nella quale è stato salvato targetNamespace.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     La query XPath nel modello restituisce il  **\<cliente >** elemento per il cliente con CustomerID 1. Notare che la query XPath specifica il prefisso dello spazio dei nomi per l'elemento nella query e non per l'attributo. Gli attributi locali non sono qualificati, come specificato nello schema.  
  
     Il percorso di directory specificato per lo schema di mapping (targetNamespace.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Se lo schema specifica **elementFormDefault** e **attributeFormDefault** attributi con valore **"qualified"**, il documento di istanza conterrà tutti locale elementi e attributi qualificati. È possibile modificare lo schema precedente per includere questi attributi di  **\<xsd: schema >** elemento ed eseguire nuovamente il modello. Poiché ora anche gli attributi sono qualificati nell'istanza, la query XPath verrà modificata per includere il prefisso dello spazio dei nomi.  
  
 La query XPath modificata è:  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 Di seguito è riportato il documento XML restituito:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
