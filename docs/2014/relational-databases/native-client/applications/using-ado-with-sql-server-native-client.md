---
title: Utilizzo di ADO con SQL Server Native Client | Documenti Microsoft
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
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d292a0b39de8820fdb58d6c95d7925048d7eb8bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063817"
---
# <a name="using-ado-with-sql-server-native-client"></a>Utilizzo di ADO con SQL Server Native Client
  Per sfruttare i vantaggi delle nuove funzionalità introdotte [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] , ad esempio multiple active result set (MARS), le notifiche delle query, tipi definiti dall'utente (UDT) o il nuovo **xml** tipo di dati, le applicazioni esistenti che utilizzano ActiveX Data Objects (ADO) deve utilizzare il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client come provider di accesso ai dati.  
  
 L'uso del provider OLE DB di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client è necessario solo per utilizzare una delle caratteristiche introdotte in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se non si intende utilizzare tali caratteristiche, è possibile continuare a usare il provider di accesso ai dati corrente, generalmente SQLOLEDB. L'uso del provider OLE DB di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client è consigliabile se si intende potenziare un'applicazione esistente e si ha l'esigenza di utilizzare le nuove caratteristiche introdotte in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Se si sviluppa una nuova applicazione, è consigliabile valutare l'opportunità di utilizzare ADO.NET e il provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] anziché [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per accedere a tutte le nuove caratteristiche delle ultime versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per ulteriori informazioni sul provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], fare riferimento alla documentazione di .NET Framework SDK per ADO.NET.  
  
 Per consentire l'utilizzo in ADO delle nuove caratteristiche delle ultime versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sono stati apportati alcuni miglioramenti che estendono le caratteristiche principali di OLE DB. Questi miglioramenti consentono alle applicazioni ADO di utilizzare più recente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le funzionalità e di utilizzare due tipi di dati introdotti in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** e **udt**. Questi miglioramenti anche di sfruttare i miglioramenti per il **varchar**, **nvarchar**, e **varbinary** tipi di dati. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client consente di aggiungere la proprietà di inizializzazione SSPROP_INIT_DATATYPECOMPATIBILITY di proprietà DBPROPSET_SQLSERVERDBINIT per l'utilizzo nelle applicazioni ADO in modo che i nuovi tipi di dati sono esposti in modo compatibile con ADO. Inoltre, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce anche una nuova parola chiave della connessione stringa denominata `DataTypeCompatibility` impostato nella stringa di connessione.  
  
> [!NOTE]  
>  Le applicazioni ADO esistenti possono accedere a valori XML, UDT, nonché di campi binari e di testo valore di grandi dimensioni ed eseguirne l'aggiornamento utilizzando il provider SQLOLEDB. Il nuovo più grande **varchar (max)**, **nvarchar (max)**, e **varbinary (max)** i tipi di dati vengono restituiti come tipi ADO **adLongVarChar**, **adLongVarWChar** e **adLongVarBinary** rispettivamente. Colonne XML vengono restituite come **adLongVarChar**, e vengono restituite le colonne di tipo definito dall'utente come **adVarBinary**. Se tuttavia, si utilizza il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) anziché SQLOLEDB, è necessario assicurarsi di impostare la parola chiave `DataTypeCompatibility` su "80" in modo da consentire la corretta esecuzione del mapping dei nuovi tipi di dati ai tipi di dati ADO.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Abilitazione di SQL Server Native Client da ADO  
 Per abilitare l'utilizzo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, le applicazioni ADO devono implementare le parole chiave seguenti nelle stringhe di connessione:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Per ulteriori informazioni su ADO parole chiave supportate in stringhe di connessione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vedere [Using Connection String Keywords with SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Nell'esempio viene mostrato un esempio di stringa di connessione ADO pienamente abilitata per operare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, inclusa l'abilitazione della funzionalità MARS:  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a>Esempi  
 Nelle sezioni seguenti vengono forniti esempi di come è possibile utilizzare ADO con il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client.  
  
### <a name="retrieving-xml-column-data"></a>Recupero dei dati delle colonne XML  
 In questo esempio viene utilizzato un recordset per recuperare e visualizzare i dati da una colonna XML nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** database di esempio.  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  
  
' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  
  
con.Close  
Set con = Nothing  
```  
  
> [!NOTE]  
>  L'applicazione di filtri al recordset non è supportata con le colonne XML. Se si prova ad applicare i filtri, viene generato un errore.  
  
### <a name="retrieving-udt-column-data"></a>Recupero dei dati delle colonne con tipo definito dall'utente  
 In questo esempio, un **comando** oggetto viene usato per eseguire una query SQL che restituisce un tipo definito dall'utente, i dati di tipo definito dall'utente vengono aggiornati e quindi i nuovi dati vengono nuovamente inseriti nel database. Questo esempio si presuppone che il **punto** tipo definito dall'utente è già stato registrato nel database.  
  
```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  
  
' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  
  
' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  
  
con.Close  
Set con = Nothing  
```  
  
### <a name="enabling-and-using-mars"></a>Abilitazione e utilizzo di MARS  
 In questo esempio viene costruita la stringa di connessione per abilitare MARS mediante il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client e quindi due oggetti recordset vengono creati da eseguire utilizzando la stessa connessione.  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
  
Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  
  
Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  
  
con.Close  
Set con = Nothing  
```  
  
 Nelle versioni precedenti del provider OLE DB questo codice determinerebbe la creazione di una connessione implicita alla seconda esecuzione, in quanto per una sola connessione sarebbe possibile aprire un solo set attivo di risultati. Poiché la connessione implicita non sarebbe inserita nel pool di connessioni OLE DB, questa situazione provocherebbe overhead aggiuntivo. Con il servizio MARS esposto dal [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client, si ottengono più risultati attivi in un'unica connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  