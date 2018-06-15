---
title: Utilizzo del caricamento Bulk SQLXML nell'ambiente .NET | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 270abbb40bdf6081b7409cf76a97925a1cd2b3d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32970589"
---
# <a name="sqlxml-40-net-framework-support---using-bulk-load"></a>Supporto per SQLXML 4.0 di .NET Framework: utilizzo del caricamento Bulk
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In questo argomento viene illustrato l'utilizzo delle funzionalità di caricamento bulk XML nell'ambiente .NET. Per informazioni dettagliate sul caricamento Bulk XML, vedere [esecuzione caricamento Bulk di dati di XML & #40; SQLXML 4.0 & #41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).  
  
 Per utilizzare l'oggetto COM del caricamento bulk di SQLXML da un ambiente gestito, è necessario aggiungere un riferimento a un progetto a questo oggetto. In questo modo, viene generata un'interfaccia con wrapper gestito intorno all'oggetto COM del caricamento bulk.  
  
> [!NOTE]  
>  Il caricamento bulk XML gestito non può essere eseguito con flussi gestiti e richiede un wrapper intorno ai flussi nativi. Il componente di caricamento bulk di SQLXML non viene eseguito in un ambiente a thread multipli (attributo '[MTAThread]'). Se si tenta di eseguire il componente di caricamento Bulk in un ambiente a thread multipli, generata un'eccezione di InvalidCastException con le seguenti informazioni aggiuntive: "QueryInterface per interfaccia Sqlxmlbulkloadlib non riuscita." La soluzione consiste nel rendere l'oggetto che contiene il caricamento Bulk oggetto a thread singolo accessibile (ad esempio, tramite il **[STAThread]** attributo come illustrato nell'esempio).  
  
 In questo argomento viene fornita un'applicazione C# di esempio reale per eseguire il caricamento bulk dei dati nel database. Per creare un esempio reale, eseguire la procedura seguente:  
  
1.  Creare le tabelle seguenti:  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  Salvare lo schema seguente in un file (schema.xml):  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Salvare il documento XML di esempio seguente in un file (data.xml):  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  Avviare Visual Studio.  
  
5.  Creare un'applicazione console C#.  
  
6.  Dal **progetto** dal menu **Aggiungi riferimento**.  
  
7.  Nel **COM** , selezionare **libreria dei tipi Microsoft SQLXML Bulkload 4.0** (xblkld4.dll) e fare clic su **OK**. Verrà visualizzato il **sqlxmlbulkloadlib** assembly creati nel progetto.  
  
8.  Sostituire il metodo Main() con il codice seguente. Aggiornamento di **ConnectionString** proprietà e il percorso del file per i file di schema e i dati.  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. Per caricare i dati XML nella tabella creata, compilare ed eseguire il progetto.  
  
    > [!NOTE]  
    >  Il riferimento al componente di caricamento bulk (xblkld4.dll) può essere aggiunto anche utilizzando lo strumento tlbimp.exe, disponibile come parte di .NET Framework. Questo strumento crea un wrapper gestito per la DLL nativa (xblkld4.dll) che può quindi essere utilizzato in qualsiasi progetto .NET. Esempio:  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     Questa operazione crea la DLL del wrapper gestito (SQLXMLBULKLOADLib.dll) che è possibile utilizzare nel progetto .NET Framework. In .NET Framework aggiungere il riferimento al progetto alla nuova DLL creata.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione del caricamento Bulk di dati XML & #40; SQLXML 4.0 & #41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
