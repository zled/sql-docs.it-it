---
title: "Coercizioni dei tipi di dati e l'annotazione SQL: DataType (SQLXML 4.0) | Documenti Microsoft"
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8a2dc2c3d91eea67e9e08a87d5aa7735a1b45b1f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>Coercizioni dei tipi di dati e annotazione sql:datatype (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In uno schema XSD, il **xsd: Type** attributo specifica il tipo di dati XSD di un elemento o attributo. Quando viene utilizzato uno schema XSD per estrarre dati dal database, il tipo di dati specificato viene utilizzato per formattare i dati.  
  
 Oltre a specificare un tipo XSD in uno schema, è inoltre possibile specificare un Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il tipo di dati utilizzando il **SQL: DataType** annotazione. Il **xsd: Type** e **SQL: DataType** controllano il mapping tra tipi di dati XSD e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati.  
  
## <a name="xsdtype-attribute"></a>Attributo xsd:type  
 È possibile utilizzare il **xsd: Type** attributo per specificare il tipo di dati XML di un attributo o elemento che esegue il mapping a una colonna. Il **xsd: Type** influisce sul documento restituito dal server, nonché la query XPath eseguita. Quando viene eseguita una query XPath su uno schema di mapping contenente **xsd: Type**, XPath utilizza il tipo di dati specificato durante l'elaborazione della query. Per ulteriori informazioni sull'utilizzo di XPath **xsd: Type**, vedere [Mapping di tipi di dati XSD ai tipi di dati XPath &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md).  
  
 In un documento restituito tutti i tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono convertiti in rappresentazioni di stringa. Alcuni tipi di dati richiedono conversioni aggiuntive. Nella tabella seguente sono elencate le conversioni vengono utilizzate per varie **xsd: Type** valori.  
  
|Tipo di dati XSD|Conversione SQL Server|  
|-------------------|---------------------------|  
|Boolean|CONVERT(bit, COLUMN)|  
|Data|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Tutti gli altri|Nessuna conversione aggiuntiva|  
  
> [!NOTE]  
>  Alcuni dei valori restituiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe non essere compatibile con i tipi di dati XML specificati tramite **xsd: Type**, in quanto la conversione non è possibile (ad esempio, "XYZ" la conversione a un  **decimale** tipo di dati) o perché il valore supera l'intervallo di tale tipo di dati (ad esempio -100000 convertito in un **UnsignedShort** tipo XSD). Conversioni di tipi incompatibili possono restituire documenti XML non validi o errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Mapping dai tipi di dati di SQL Server a tipi di dati XSD  
 Nella tabella seguente viene illustrato un mapping evidente dai tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ai tipi di dati XSD. Se il tipo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è noto, nella tabella è disponibile il tipo XSD corrispondente che è possibile specificare nello schema XSD.  
  
|Tipo di dati di SQL Server|Tipo di dati XSD|  
|--------------------------|-------------------|  
|**bigint**|**Long**|  
|**binary**|**base64Binary**|  
|**bit**|**boolean**|  
|**char**|**string**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**base64Binary**|  
|**int**|**int**|  
|**money**|**decimal**|  
|**nchar**|**string**|  
|**ntext**|**string**|  
|**nvarchar**|**string**|  
|**numeric**|**decimal**|  
|**real**|**float**|  
|**smalldatetime**|**dateTime**|  
|**smallint**|**short**|  
|**smallmoney**|**decimal**|  
|**sql_variant**|**string**|  
|**sysname**|**string**|  
|**text**|**string**|  
|**timestamp**|**dateTime**|  
|**tinyint**|**unsignedByte**|  
|**varbinary**|**base64Binary**|  
|**varchar**|**string**|  
|**uniqueidentifier**|**string**|  
  
## <a name="sqldatatype-annotation"></a>Annotazione sql:datatype  
 Il **SQL: DataType** annotazione viene utilizzata per specificare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il tipo di dati deve essere specificato quando:  
  
-   Si esegue un caricamento bulk in un **dateTime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonna da un file XSD **dateTime**, **data**, o **ora** tipo. In questo caso, è necessario identificare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati di colonna utilizzando **SQL: DataType = "dateTime"**. Questa regola si applica anche agli updategram.  
  
-   Si esegue un caricamento bulk in una colonna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **uniqueidentifier** tipo e il valore XSD è un GUID che include parentesi graffe ({e}). Quando si specifica **SQL: DataType = "uniqueidentifier"**, le parentesi graffe vengono rimosse dal valore prima di essere inserito nella colonna. Se **SQL: DataType** non viene specificato, il valore viene inviato con le parentesi graffe e l'ha esito negativo insert o update.  
  
-   Il tipo di dati XML **base64Binary** esegue il mapping a varie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati (**binario**, **immagine**, o **varbinary**). Per mappare il tipo di dati XML **base64Binary** a uno specifico [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati, utilizzare il **SQL: DataType** annotazione. Questa annotazione specifica il tipo di dati esplicito di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della colonna a cui viene mappato l'attributo. Ciò risulta utile durante l'archiviazione dei dati nei database. Specificando il **SQL: DataType** annotazione, è possibile identificare la proprietà esplicita [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati.  
  
 È consigliabile specificare **SQL: DataType** nello schema.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per esecuzione esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Definizione dell'attributo xsd:type  
 Questo esempio viene illustrato come uno schema XSD **data** tipo specificato utilizzando il **xsd: Type** attributo nello schema influisce sul documento XML risultante. Lo schema fornisce una vista XML della tabella Sales.SalesOrderHeader nel database AdventureWorks.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 In questo schema XSD sono inclusi tre attributi che restituiscono un valore di data da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esaminare i casi seguenti per lo schema:  
  
-   Specifica **xsd: Type = data** sul **OrderDate** attributo, la parte della data del valore restituito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il **OrderDate** attributo viene visualizzato.  
  
-   Specifica **xsd: Type = tempo** sul **ShipDate** attributo, la parte dell'ora del valore restituito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il **ShipDate** attributo viene visualizzato.  
  
-   Non specificare **xsd: Type** sul **DueDate** attributo, lo stesso valore restituito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene visualizzato.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome xsdType.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome xsdTypeT.xml nella stessa directory in cui è stato salvato xsdType.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (xsdType.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query di SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati parziale:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 Di seguito viene indicato lo schema XDR equivalente:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>B. Definizione del tipo di dati SQL tramite sql:datatype  
 Per un esempio funzionante, vedere l'esempio G in [esempi di caricamento Bulk XML &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). In questo esempio viene eseguito il caricamento bulk di un valore GUID che include"{" e "}". In questo esempio lo schema specifica **SQL: DataType** per identificare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del tipo di dati come **uniqueidentifier**. Questo esempio viene illustrato quando **SQL: DataType** deve essere specificato nello schema.  
  
  
