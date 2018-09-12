---
title: Usare dati XML nelle applicazioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [XML in SQL Server]
- XML [SQL Server], ADO
- columns [XML in SQL Server], ADO.NET
- ADO [XML in SQL Server]
- columns [XML in SQL Server], SQL Server Native Client
- xml data type [SQL Server], ADO
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- ADO.NET [XML in SQL Server]
- XML [SQL Server], ADO.NET
- columns [XML in SQL Server], ADO
- xml data type [SQL Server], ADO.NET
- XML [SQL Server], SQL Server Native Client
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2cd4cd4f0edba28fc8bb7171a2e120fe7439057c
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889807"
---
# <a name="use-xml-data-in-applications"></a>Utilizzo di dati XML nelle applicazioni
  In questo argomento vengono descritte le opzioni disponibili per l'utilizzo di `xml` tipo di dati nell'applicazione. Vengono fornite informazioni sugli aspetti seguenti:  
  
-   Gestione di dati XML da una colonna di tipo `xml` utilizzando ADO e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   Gestione di dati XML da un `xml` colonna del tipo tramite ADO.NET  
  
-   Gestione del tipo `xml` nei parametri utilizzando ADO.NET  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-ado-and-sql-server-native-client"></a>Gestione di XML da una colonna di tipo xml utilizzando ADO e SQL Server Native Client  
 Per usare i componenti MDAC e accedere alle funzionalità e ai tipi introdotti in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], è necessario impostare la proprietà di inizializzazione DataTypeCompatibility nella stringa di connessione di ADO.  
  
 Ad esempio, l'esempio di Visual Basic Scripting Edition (VBScript) seguente mostra i risultati di una query su un `xml` colonna tipo di dati `Demographics`, nel `Sales.Store` tabella del `AdventureWorks2012` database di esempio. Questa particolare query cerca il valore di istanza della colonna per la riga dove `CustomerID` è uguale a `3`.  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 Questo esempio illustra come impostare la proprietà di compatibilità del tipo di dati. Per impostazione predefinita, questa proprietà è impostata su 0 quando si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Se si imposta il valore su 80, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider Native Client renderà `xml` e le colonne di tipo definito dall'utente vengono visualizzate come [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] i tipi di dati. Vale a dire: rispettivamente DBTYPE_WSTR e DBTYPE_BYTES.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client deve essere installato anche nel computer client e la stringa di connessione deve specificare che venga usato come provider di dati tramite "`Provider=SQLNCLI11;...`".  
  
#### <a name="to-test-this-example"></a>Per testare l'esempio  
  
1.  Verificare che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sia installato e che MDAC 2 versione 6.0, o una versione successiva, sia installato sul computer client.  
  
     Per altre informazioni, vedere [Programmazione in SQL Server Native Client](../native-client/sql-server-native-client-programming.md).  
  
2.  Verificare che il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia installato.  
  
     Questo esempio richiede il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  Copiare il codice riportato precedentemente in questo argomento nel proprio editor di testo o di codice. Salvare il file col nome HandlingXmlDataType.vbs.  
  
4.  Modificare lo script come necessario per l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e salvare le modifiche.  
  
     Ad esempio, la stringa `MyServer` va sostituita con `(local)` o con il nome effettivo del server sul quale è installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
5.  Eseguire HandlingXmlDataType.vbs e lo script.  
  
 Si dovrebbe ottenere un risultato simile a quello riportato di seguito:  
  
```  
Row 1  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>1500000</AnnualSales>  
  <AnnualRevenue>150000</AnnualRevenue>  
  <BankName>Primary International</BankName>  
  <BusinessType>OS</BusinessType>  
  <YearOpened>1974</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>38000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>40</NumberEmployees>  
</StoreSurvey>  
  
Row 2  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-adonet"></a>Gestione di dati XML da una colonna di tipo xml utilizzando ADO.NET  
 Per la gestione di XML da un `xml` colonna tipo di dati tramite ADO.NET e la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] è possibile usare il comportamento standard del `SqlCommand` classe. Ad esempio, un' `xml` dati colonna di tipo e i relativi valori possono essere recuperati nello stesso modo di qualsiasi colonna SQL viene recuperato utilizzando un `SqlDataReader`. Tuttavia, se si desidera utilizzare il contenuto di un `xml` colonna tipo di dati come XML, è prima di tutto sarà necessario assegnarne il contenuto per un `XmlReader` tipo.  
  
 Per altre informazioni e codici di esempio, vedere "XML Column Values in a Data Reader" (Valori delle colonne XML in un lettore di dati) nella documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK.  
  
## <a name="handling-an-xml-type-column-in-parameters-by-using-adonet"></a>Gestione di una colonna di tipo xml in parametri utilizzando ADO.NET  
 Per gestire un tipo di dati xml passato come parametro in ADO.NET e [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], è possibile specificare il valore come un'istanza del tipo di dati `SqlXml`. Non è presente alcuna gestione speciale, poiché `xml` colonne di tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono accettare i valori dei parametri nello stesso modo di altre colonne e tipi di dati, ad esempio `string` o `integer`.  
  
 Per altre informazioni e codici di esempio, vedere "XML Values as Command Parameters" (Valori XML come parametri di comando) nella documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK.  
  
## <a name="see-also"></a>Vedere anche  
 [Dati XML &#40;SQL Server&#41;](xml-data-sql-server.md)  
  
  
