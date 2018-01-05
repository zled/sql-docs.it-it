---
title: Linee guida e limitazioni di XML eseguire il caricamento Bulk (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 453ce7fe955af4ffe25d13b1ab1abfef0f48cf59
ms.sourcegitcommit: 7673ad0e84a6de69420e19247a59e39ca751a8aa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2018
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>Linee guida e limitazioni per il caricamento bulk XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Quando si utilizza il caricamento Bulk XML, è necessario conoscere le linee guida e le limitazioni seguenti:  
  
-   Gli schemi inline non sono supportati.  
  
     Se nel documento XML di origine è presente uno schema inline, questo viene ignorato dal caricamento bulk XML. È necessario specificare lo schema di mapping per il caricamento bulk XML come esterno ai dati XML. Non è possibile specificare lo schema di mapping in un nodo utilizzando il **xmlns = "x:schema"** attributo.  
  
-   Un documento XML viene controllato per verificare che utilizzi un formato corretto, ma non viene convalidato.  
  
     Il caricamento bulk XML controlla il documento XML per determinare se è nel formato corretto, ovvero per garantire che i dati XML rispondano ai requisiti di sintassi della specifica XML 1.0 del World Wide Web Consortium. Se il formato del documento non è corretto, il caricamento bulk XML annulla l'elaborazione e restituisce un errore. L'unica eccezione a questo comportamento è costituita dal caso in cui il documento è un frammento, ad esempio non dispone di un singolo elemento radice. In questo caso, il documento verrà caricato.  
  
     Il caricamento bulk XML non convalida il documento rispetto ad alcuno schema dati XML o DTD definito o a cui si fa riferimento all'interno del file di dati XML. Il caricamento bulk XML, inoltre, non convalida il file di dati XML rispetto allo schema di mapping fornito.  
  
-   Vengono ignorate tutte le informazioni sui prologhi XML.  
  
     Caricamento Bulk XML Ignora tutte le informazioni prima e dopo il \<radice > elemento nel documento XML. Il caricamento bulk XML, ad esempio, ignora qualsiasi dichiarazione XML, qualsiasi definizione DTD interna e tutti i riferimenti DTD esterni, i commenti e così via.  
  
-   Se è presente uno schema di mapping che definisce una relazione di chiave primaria/chiave esterna tra due tabelle, ad esempio tra Customer e CustOrder, la tabella con la chiave primaria deve essere descritta per prima nello schema. La tabella con la colonna chiave esterna deve essere visualizzata come successiva nello schema. Il motivo è che l'ordine in cui le tabelle vengono identificate nello schema è l'ordine in cui viene utilizzato per caricare i file nel database. Ad esempio, lo schema XDR seguente produrrà un errore quando viene utilizzato nel caricamento Bulk XML perché il  **\<ordine >** elemento viene descritto prima il  **\<cliente >** elemento. La colonna CustomerID in CustOrder è una colonna chiave esterna che fa riferimento alla colonna chiave primaria CustomerID nella tabella Cust.  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   Se lo schema non specifica colonne di overflow tramite il **SQL: overflow-campo** annotazioni, caricamento Bulk XML ignora tutti i dati presenti nel documento XML ma non sono descritti nello schema di mapping.  
  
     Il caricamento bulk XML applica lo schema di mapping specificato ogni volta che rileva tag noti nel flusso di dati XML e ignora i dati presenti nel documento XML ma che non sono descritti nello schema. Si supponga ad esempio si dispone di uno schema di mapping che descrive un  **\<cliente >** elemento. Il file di dati XML ha un  **\<AllCustomers >** radice tag (che non sono descritti nello schema) che include tutti i  **\<cliente >** elementi:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     In questo caso, il caricamento Bulk XML ignora il  **\<AllCustomers >** elemento e avvia il mapping al  **\<cliente >** elemento. Il caricamento bulk XML ignora gli elementi non descritti nello schema ma che sono presenti nel documento XML.  
  
     Si consideri un altro file di dati origine XML che contiene  **\<ordine >** elementi. Tali elementi non vengono descritti nello schema di mapping:  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     Caricamento Bulk XML ignora questi  **\<ordine >** elementi. Se tuttavia si utilizza il **SQL: overflow-campo**annotazione nello schema per identificare una colonna come colonna di overflow, il caricamento Bulk XML archivia tutti i dati non utilizzati in questa colonna.  
  
-   Le sezioni CDATA e i riferimenti a entità vengono convertiti nei rispettivi equivalenti in formato stringa prima di essere archiviati nel database.  
  
     In questo esempio, una sezione CDATA incapsula il valore per il  **\<City >** elemento. Caricamento Bulk XML estrae il valore di stringa ("NY") prima di inserire il  **\<City >** elemento nel database.  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     Il caricamento bulk XML non mantiene i riferimenti alle entità.  
  
-   Se lo schema di mapping specifica il valore predefinito per un attributo e i dati di origine XML non contengono tale attributo, il caricamento bulk XML utilizza il valore predefinito.  
  
     Lo schema XDR di esempio seguente viene assegnato un valore predefinito per il **HireDate** attributo:  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     In questi dati XML, il **HireDate** manca l'attributo del secondo  **\<clienti >** elemento. Quando il caricamento Bulk XML inserisce il secondo  **\<clienti >** elemento nel database, viene utilizzato il valore predefinito specificato nello schema.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   Il **SQL: URL-codificare** annotazione non è supportata:  
  
     Non è possibile specificare un URL nei dati XML di input e prevedere che il caricamento bulk legga i dati da tale posizione.  
  
     Vengono create le tabelle identificate nello schema di mapping (il database deve essere presente). Se esiste già uno o più delle tabelle nel database, sgdroptables-proprietà determina se tali tabelle preesistenti devono essere eliminati e ricreati.  
  
-   Se si specifica la proprietà SchemaGen (ad esempio, SchemaGen = true), vengono create le tabelle identificate nello schema di mapping. Ma SchemaGen eventuali vincoli (ad esempio, i vincoli di chiave primaria/chiave esterna) in tali tabelle non viene creata con una sola eccezione: se i nodi XML che costituiscono la chiave primaria in una relazione sono definiti come un tipo XML di ID (vale a dire **tipo = "XSD: ID"** per XSD) e sguseid-proprietà è impostata su True per SchemaGen, quindi non sono chiavi primarie create solo da ID digitati nodi, ma non vengono create relazioni di chiave esterna o chiave primarie da relazioni dello schema di mapping.  
  
-   SchemaGen non utilizzare facet dello schema XSD e per generare relazionale [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dello schema.  
  
-   Se si specifica la proprietà SchemaGen (ad esempio, SchemaGen = true) on Bulk Load, solo le tabelle (e non le viste nome condiviso) che vengono specificate vengono aggiornati.  
  
-   SchemaGen fornisce solo le funzionalità di base per la generazione dello schema relazionale da XSD con annotazioni. Se necessario, l'utente deve modificare manualmente le tabelle generate.  
  
-   In cui è presente più di una relazione tra tabelle, SchemaGen tenta di creare una singola relazione che include tutte le chiavi interessate tra le due tabelle. Questa limitazione può essere la causa di un errore [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   Quando si esegue il caricamento bulk di dati XML in un database, deve essere presente almeno un attributo o un elemento figlio nello schema di mapping mappato a una colonna del database.  
  
-   Se si inseriscono valori di data tramite il caricamento bulk XML, i valori devono essere specificati nel formato (-)AAAA-MM-GG((+-)FO). Si tratta del formato XSD standard per la data.  
  
-   Alcuni flag della proprietà non sono compatibili con altri flag della proprietà stessa. Ad esempio, il caricamento bulk non supporta **Ignoreduplicatekeys = true** con **Keepidentity = false**. Quando **Keepidentity = false**, caricamento bulk prevede che il server per generare i valori di chiave. Le tabelle devono avere un **identità** vincolo sulla chiave. Il server non genererà chiavi duplicate, ovvero non è necessario per **Ignoreduplicatekeys** sia impostato su **true**. **IgnoreDuplicateKeys** deve essere impostato su **true** solo durante il caricamento di valori di chiave primaria dai dati in ingresso in una tabella con righe ed è un potenziale conflitto di valori di chiave primaria.  
  
  
