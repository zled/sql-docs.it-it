---
title: Specificare una destinazione Namespace usando l'attributo targetNamespace (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa61e44575761d4ada96d68a887b584664735e7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166732"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>Specifica di uno spazio dei nomi di destinazione mediante l'attributo targetNamespace (SQLXML 4.0)
  Nella scrittura di schemi XSD, è possibile usare lo schema XSD **targetNamespace** attributo per specificare uno spazio dei nomi di destinazione. Questo argomento viene illustrato come XSD **targetNamespace**, **elementFormDefault**, e **attributeFormDefault** attributi funziona, loro influenza dell'istanza XML che è generato, e come vengono specificate query XPath con spazi dei nomi.  
  
 È possibile usare la **xsd: targetNamespace** attributo per posizionare gli elementi e gli attributi dello spazio dei nomi predefinito in uno spazio dei nomi diversi. È inoltre possibile specificare se gli elementi e gli attributi dello schema dichiarati localmente devono essere qualificati da uno spazio dei nomi, sia in modo esplicito mediante un prefisso sia in modo implicito per impostazione predefinita. È possibile usare la **elementFormDefault** e **attributeFormDefault** gli attributi di  **\<xsd: schema >** elemento per specificare a livello globale i qualifica degli elementi locali e gli attributi oppure è possibile usare la **form** attributo per specificare separatamente i singoli elementi e attributi.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per altre informazioni, vedere [requisiti per l'esecuzione di esempi di SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-a-target-namespace"></a>A. Specificare uno spazio dei nomi di destinazione  
 Lo schema XSD seguente specifica uno spazio dei nomi di destinazione usando il **xsd: targetNamespace** attributo. Lo schema imposta anche il **elementFormDefault** e **attributeFormDefault** per i valori dell'attributo **"unqualified"** (valore predefinito per questi attributi). Si tratta di una dichiarazione globale che influisce su tutti gli elementi locali (**\<ordine >** nello schema) e gli attributi (**CustomerID**, **ContactName**e  **OrderID** nello schema).  
  
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
  
-   Il **CustomerType** e **OrderType** dichiarazioni di tipo sono globali e, pertanto, sono inclusi nello spazio dei nomi di destinazione dello schema. Di conseguenza, quando questi tipi viene fatto riferimento nella dichiarazione della  **\<cliente >** elemento e la relativa  **\<ordine >** elemento figlio, viene specificato un prefisso che è associato con lo spazio dei nomi di destinazione.  
  
-   Il  **\<cliente >** elemento viene inoltre incluso nello spazio dei nomi di destinazione dello schema poiché è un elemento globale nello schema.  
  
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
  
 Questo documento dell'istanza definisce lo spazio dei nomi urn: MyNamespace e associa un prefisso (y0) a esso. Il prefisso viene applicato solo al  **\<cliente >** elemento globale. (L'elemento è globale poiché è stato dichiarato come elemento figlio  **\<xsd: schema >** elemento nello schema.)  
  
 Il prefisso non viene applicato agli elementi locali e gli attributi perché il valore di **elementFormDefault** e **attributeFormDefault** gli attributi è impostato su **"unqualified"** nello schema. Si noti che il  **\<ordine >** elemento è locale poiché la relativa dichiarazione appare come elemento figlio il  **\<complexType >** elemento che definisce il  **\< CustomerType >** elemento. Analogamente, gli attributi (**CustomerID**, **OrderID**, e **ContactName**) sono locali, non globali.  
  
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
  
     La query XPath nel modello restituisce il  **\<cliente >** (elemento) per il cliente con CustomerID 1. Notare che la query XPath specifica il prefisso dello spazio dei nomi per l'elemento nella query e non per l'attributo. Gli attributi locali non sono qualificati, come specificato nello schema.  
  
     Il percorso di directory specificato per lo schema di mapping (targetNamespace.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per altre informazioni, vedere [utilizzo di ADO per eseguire query SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Se lo schema specifica **elementFormDefault** e **attributeFormDefault** gli attributi con valore **"qualified"**, il documento di istanza conterrà tutti locale gli elementi e attributi qualificati. È possibile modificare lo schema precedente in modo da includere questi attributi nel  **\<xsd: schema >** elemento ed eseguire nuovamente il modello. Poiché ora anche gli attributi sono qualificati nell'istanza, la query XPath verrà modificata per includere il prefisso dello spazio dei nomi.  
  
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
  
  
