---
title: 'Specificare profondità nelle relazioni ricorsive mediante SQL: max-depth | Documenti Microsoft'
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
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 51728d15698d79b93d802c6f0be75fba8cf1ab0c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>Specifica del livello di nidificazione nelle relazioni ricorsive mediante sql:max-depth
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Quando nei database relazionali una tabella viene coinvolta in una relazione con sé stessa, si parla di relazione ricorsiva. In una relazione supervisore-supervisionato (supervisor-supervisee), ad esempio, una tabella in cui sono archiviati i record dei dipendenti è coinvolta in una relazione con sé stessa. In questo caso, la stessa tabella dei dipendenti ricopre il ruolo di supervisore da un lato della relazione e di supervisionato dall'altro lato.  
  
 Gli schemi di mapping possono includere relazioni ricorsive nelle quali un elemento e il rispettivo predecessore sono dello stesso tipo.  
  
## <a name="example-a"></a>Esempio A  
 Si consideri la tabella seguente:  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 Nella colonna ReportsTo di questa tabella viene archiviato l'ID dipendente del responsabile.  
  
 Si supponga di voler generare una gerarchia XML di dipendenti nella quale il dipendente responsabile si trova al primo posto e i dipendenti che sono sotto la supervisione del responsabile vengono visualizzati nella gerarchia corrispondente, come mostrato nel frammento XML di esempio seguente. Cosa questo frammento viene mostrato il *albero ricorsivo* per il dipendente 1.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 In questo frammento il dipendente 5 è sotto la supervisione del dipendente 4, il dipendente 4 è sotto la supervisione del dipendente 3 e i dipendenti 3 e 2 sono sotto la supervisione del dipendente 1.  
  
 Per produrre questo risultato, è possibile utilizzare lo schema XSD seguente e specificare una query XPath in tale schema. Nello schema viene descritto un  **\<Emp >** elemento di tipo EmployeeType, costituito un  **\<Emp >** elemento figlio dello stesso tipo EmployeeType. Si tratta di una relazione ricorsiva (l'elemento e il rispettivo predecessore sono dello stesso tipo). Inoltre, lo schema Usa un  **\<SQL: Relationship >** per descrivere la relazione padre-figlio tra il supervisore e supervisionato. Si noti che in questo  **\<SQL: Relationship >**, Emp rappresenta sia la tabella figlio che l'elemento padre.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Dal momento che la relazione è ricorsiva, è necessario trovare un modo per specificare il livello di nidificazione della ricorsione nello schema. In caso contrario, il risultato sarà una ricorsione infinita (il dipendente che è sotto la supervisione del dipendente che, a sua volta è sotto la supervisione del dipendente e così via). Il **SQL:max-depth** annotazione consente di specificare la profondità di ricorsione per passare. In questo particolare esempio, per specificare un valore per **SQL:max-depth**, è necessario conoscere la modalità della gerarchia di gestione di nidificazione della società.  
  
> [!NOTE]  
>  Specifica lo schema di **SQL:limit-campo** annotazione, ma non viene specificato il **SQL:limit-valore** annotazione. Questa situazione limita il nodo principale nella gerarchia risultante ai soli dipendenti che non sono sottoposti ad alcuna supervisione (ReportsTo è NULL). Specifica di **SQL:limit-campo** senza specificare **SQL:limit-valore** (con valore predefinito di NULL) annotazione esegue questa operazione. Se si desidera che il XML risulta includa ogni possibile reporting albero (l'albero gerarchico per ogni dipendente nella tabella), rimuovere il **SQL:limit-campo** annotazione dallo schema.  
  
> [!NOTE]  
>  Nella procedura riportata di seguito viene utilizzato il database tempdb.  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Creare una tabella di esempio chiamata Emp nel database tempdb al quale punta la radice virtuale.  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  Aggiungere i dati di esempio seguenti:  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome maxDepth.xml.  
  
4.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome maxDepthT.xml nella stessa directory nella quale è stato salvato maxDepth.xml. La query nel modello restituisce tutti i dipendenti della tabella Emp.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (maxDepth.xml) è relativo alla directory nella quale viene salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello. Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query di SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Risultato:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  Per produrre diversi livelli di nidificazione di gerarchie nel risultato, modificare il valore di **SQL:max-depth** annotazione nello schema ed eseguire il modello dopo ogni modifica.  
  
 Nello schema precedente, tutte le  **\<Emp >** elementi presentavano esattamente lo stesso set di attributi (**EmployeeID**, **FirstName**, e  **LastName**). Lo schema seguente è stato leggermente modificato per restituire un altro **ReportsTo** attributo per tutti i  **\<Emp >** gli elementi che fanno riferimento a un gestore.  
  
 Questo frammento XML, ad esempio, mostra i subalterni del dipendente 1:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 Questo è lo schema corretto:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a>Annotazione sql:max-depth  
 In un schema costituito da relazioni ricorsive il livello di nidificazione della ricorsione deve essere specificata in modo esplicito. Questa operazione è necessaria per produrre correttamente la query FOR XML EXPLICIT corrispondente che restituisce i risultati richiesti.  
  
 Utilizzare il **SQL: max-depth** annotazione nello schema per specificare la profondità di ricorsione in una relazione ricorsiva descritta nello schema. Il valore di **SQL:max-profondità** annotazione è un numero intero positivo (da 1 a 50) che indica il numero di ricorsioni: il valore 1 arresta la ricorsione in corrispondenza dell'elemento per cui il **SQL:max-profondità** annotazione viene specificata, il valore 2 Arresta la ricorsione al livello successivo rispetto all'elemento **SQL:max-profondità** viene specificato e così via.  
  
> [!NOTE]  
>  Nell'implementazione sottostante una query XPath specificata rispetto a un schema di mapping viene convertita in una query SELECT... FOR XML EXPLICIT. Questa query richiede che venga specificato un livello di nidificazione limitato della ricorsione. Maggiore è il valore specificato per **SQL: max-depth**, maggiore sarà la query FOR XML EXPLICIT che viene generato. con un probabile rallentamento del tempo di recupero.  
  
> [!NOTE]  
>  Gli updategram e il caricamento bulk XML ignorano l'annotazione max-depth, pertanto gli inserimenti o gli aggiornamenti ricorsivi si verificheranno indipendentemente dal valore specificato per max-depth.  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>Specifica di sql:max-depth per gli elementi complessi  
 Il **SQL:max-depth** annotazione può essere specificata su qualsiasi elemento di contenuto complesso.  
  
### <a name="recursive-elements"></a>Elementi ricorsivi  
 Se **SQL:max-depth** è specificata l'elemento padre sia l'elemento figlio in una relazione ricorsiva, il **SQL: max-profondità** annotazione specificata per l'elemento padre ha la precedenza. Ad esempio, nello schema seguente, il **SQL:max-depth** annotazione viene specificata per gli elementi figlio dipendente sia padre. In questo caso, **SQL: max-depth = 4**specificato per il  **\<Emp >** elemento padre (che ricopre il ruolo di supervisore), ha la precedenza. Il **SQL: max-depth** specificato sull'elemento figlio  **\<Emp >** elemento (che ricopre il ruolo di supervisionato) viene ignorato.  
  
#### <a name="example-b"></a>Esempio B  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Per testare questo schema, seguire i passaggi forniti per il precedente esempio A in questo argomento.  
  
### <a name="nonrecursive-elements"></a>Elementi non ricorsivi  
 Se il **SQL:max-depth** annotazione viene specificata per un elemento nello schema che non causa una ricorsione, viene ignorato. Nello schema seguente, un  **\<Emp >** elemento costituito da un  **\<costante >** elemento figlio, che, a sua volta, presenta un  **\<Emp >** elemento figlio.  
  
 In questo schema, il **SQL: max-depth** annotazione specificata per il  **\<costante >** elemento verrà ignorato perché non esiste nessuna ricorsione tra il  **\<Emp >** padre e  **\<costante >** elemento figlio. Ma non esiste ricorsione tra il  **\<Emp >** predecessore e  **\<Emp >** figlio. Lo schema specifica il **SQL:max-depth** annotazione su entrambi. Pertanto, il **SQL: max-depth** annotazione specificata per il predecessore (**\<Emp >** ricopre il ruolo di supervisore) ha la precedenza.  
  
#### <a name="example-c"></a>Esempio C  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Per testare questo schema, seguire i passaggi forniti per il precedente esempio A in questo argomento.  
  
## <a name="complex-types-derived-by-restriction"></a>Tipi complessi derivati dalla restrizione  
 Se si dispone di una derivazione del tipo complesso da  **\<restrizione >**, non è possibile specificare gli elementi del corrispondente tipo complesso di base di **SQL: max-depth** annotazione. In questi casi, il **SQL:max-depth** annotazione può essere aggiunta all'elemento del tipo derivato.  
  
 D'altra parte, se si dispone di una derivazione del tipo complesso da  **\<estensione >**, gli elementi del tipo complesso base corrispondente possono specificare il **SQL: max-depth** annotazione.  
  
 Ad esempio, lo schema XSD seguente genera un errore perché il **SQL:max-depth** annotazione viene specificata per il tipo di base. Questa annotazione non è supportata su un tipo derivato da  **\<restrizione >** da un altro tipo. Per risolvere questo problema, è necessario modificare lo schema e specificare il **SQL:max-depth** annotazione sull'elemento nel tipo derivato.  
  
#### <a name="example-d"></a>Esempio D  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 Nello schema, **SQL:max-depth** viene specificata una **CustomerBaseType** tipo complesso. Lo schema specifica anche un  **\<cliente >** elemento di tipo **CustomerType**, che deriva da **CustomerBaseType**. Una query XPath specificata per tale schema genererà un errore, perché **SQL:max-depth** non è supportato su un elemento definito in un tipo restriction di base.  
  
## <a name="schemas-with-a-deep-hierarchy"></a>Schemi con una gerarchia profonda  
 Si potrebbe avere uno schema che include una gerarchia profonda nella quale un elemento contiene un elemento figlio che, a sua volta, contiene un altro elemento figlio e così via. Se il **SQL:max-depth** l'annotazione specificata nello schema di questo tipo genera un documento XML che include una gerarchia di più di 500 livelli (con l'elemento di livello superiore al livello 1, il relativo figlio al livello 2 e così via), viene restituito un errore.  
  
  
