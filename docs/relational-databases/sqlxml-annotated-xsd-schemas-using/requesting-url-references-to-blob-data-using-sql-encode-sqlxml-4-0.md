---
title: 'Richiesta di riferimenti URL a dati BLOB utilizzando sql: encode (SQLXML 4.0) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 537e2656730c7659edd22ac68722bf43e892ad3d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32970656"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Richiesta di riferimenti URL a dati BLOB utilizzando sql:encode (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In uno schema XSD con annotazioni quando viene eseguito il mapping di un attributo o elemento a una colonna BLOB in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], i dati vengono restituiti in formato con codifica Base 64 in XML.  
  
 Se si desidera fare riferimento ai dati (URI) deve essere restituito che è utilizzabile in un secondo momento per recuperare i dati BLOB in un formato binario, specificare il **sql: codificare** annotazione. È possibile specificare **sql: codificare** su un attributo o elemento di tipo semplice.  
  
 Specificare il **sql: codificare** annotazione per indicare che deve essere restituito un URL per il campo anziché il valore del campo. **SQL: codificare** dipende dalla chiave primaria per la generazione di una selezione singleton nell'URL. La chiave primaria può essere specificata utilizzando il **SQL: Key-campi** annotazione.  
  
 Il **sql: codificare** annotazione può essere assegnata il valore "default" o "url". Il valore "default" restituisce dati in formato con codifica Base 64.  
  
 Il **sql: codificare** annotazione non può essere utilizzata con **SQL: use-cdata** o in base all'ID, IDREF, IDREFS, NMTOKEN o NMTOKENS tipi di attributo. Non può inoltre essere utilizzato con XSD **fissa** attributo.  
  
> [!NOTE]  
>  Non è possibile utilizzare le colonne di tipo BLOB come parte di una chiave o di una chiave esterna.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per esecuzione esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Specifica di sql:encode per ottenere un riferimento URL ai dati BLOB  
 In questo esempio, lo schema di mapping specifica **sql: codificare** sul **LargePhoto** attributo per recuperare il riferimento all'URI di una foto del prodotto specifico (invece di recuperare i dati binari in Base 64 - formato codificato).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file come sqlEncode.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file come sqlEncodeT.xml nella stessa directory nella quale è stato salvato sqlEncode.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (sqlEncode.xml) è relativo alla directory nella quale viene salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query di SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Risultato:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
