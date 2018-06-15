---
title: Utilizzo di ADO con il Driver OLE DB per SQL Server | Documenti Microsoft
description: Utilizzo di ADO con il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 89f11eda93f9ac8eb67259265b646a2544143ae5
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612196"
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>Utilizzo di ADO con il Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Per sfruttare i vantaggi delle nuove funzionalità introdotte [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] , ad esempio multiple active result set (MARS), le notifiche delle query, tipi definiti dall'utente (UDT) o il nuovo **xml** tipo di dati, le applicazioni esistenti che utilizzano ActiveX Data Objects (ADO) deve utilizzare il Driver OLE DB per SQL Server come provider di accesso ai dati.  
  
 Per abilitare ADO usare nuove funzionalità delle versioni recenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], sono stati apportati alcuni miglioramenti per il Driver OLE DB per SQL Server che estende le funzionalità di base di OLE DB. Questi miglioramenti consentono alle applicazioni ADO di utilizzare più recente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] funzionalità e di utilizzare due tipi di dati introdotti in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** e **udt**. Questi miglioramenti anche di sfruttare i miglioramenti per il **varchar**, **nvarchar**, e **varbinary** tipi di dati. Il Driver OLE DB per SQL Server aggiunge la proprietà di inizializzazione SSPROP_INIT_DATATYPECOMPATIBILITY di proprietà DBPROPSET_SQLSERVERDBINIT per l'utilizzo nelle applicazioni ADO in modo che i nuovi tipi di dati sono esposti in modo compatibile con ADO. Inoltre, il Driver OLE DB per SQL Server definisce anche una nuova parola chiave della connessione stringa denominata **DataTypeCompatibility** impostato nella stringa di connessione.  

> [!NOTE]  
>  Le applicazioni ADO esistenti possono accedere a valori XML, UDT, nonché di campi binari e di testo valore di grandi dimensioni ed eseguirne l'aggiornamento utilizzando il provider SQLOLEDB. Il nuovo maggiore **varchar (max)**, **nvarchar (max)**, e **varbinary (max)** tipi di dati vengono restituiti come i tipi ADO **adLongVarChar**, **adLongVarWChar** e **adLongVarBinary** rispettivamente. Le colonne XML vengono restituite come **adLongVarChar**, e vengono restituite le colonne di tipo definito dall'utente come **adVarBinary**. Tuttavia, se si utilizza il Driver OLE DB per SQL Server (MSOLEDBSQL) anziché SQLOLEDB, è necessario verificare di aver impostato il **DataTypeCompatibility** (parola chiave) su "80" in modo che i nuovi tipi di dati verranno eseguito il mapping correttamente ai tipi di dati ADO.  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>L'abilitazione di Driver OLE DB per SQL Server da ADO  
 Per abilitare l'utilizzo del Driver OLE DB per SQL Server, le applicazioni ADO dovrà implementare le parole chiave seguenti nelle stringhe di connessione:  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 Per ulteriori informazioni su ADO connessioni stringhe parole chiave supportate nel Driver OLE DB per SQL Server, vedere [Using Connection String Keywords con il Driver OLE DB per SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

 Di seguito è riportato un esempio di creazione di una stringa di connessione ADO pienamente abilitata per funzionare con il Driver OLE DB per SQL Server, inclusa l'abilitazione della funzionalità MARS:  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  

## <a name="examples"></a>Esempi  
 Nelle sezioni seguenti vengono forniti esempi di come è possibile utilizzare ADO con il Driver OLE DB per SQL Server.  

### <a name="retrieving-xml-column-data"></a>Recupero dei dati delle colonne XML  
 In questo esempio viene utilizzato un recordset per recuperare e visualizzare i dati da una colonna XML nel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** database di esempio.  

```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
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
 In questo esempio, un **comando** oggetto viene usato per eseguire una query SQL che restituisce un tipo definito dall'utente, i dati di tipo definito dall'utente vengono aggiornati e quindi i nuovi dati viene inseriti nel database. In questo esempio si presuppone che il **punto** tipo definito dall'utente è già stato registrato nel database.  

```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
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
 In questo esempio, la stringa di connessione viene creata per abilitare MARS mediante il Driver OLE DB per SQL Server e quindi vengono creati due oggetti di recordset da eseguire utilizzando la stessa connessione.  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
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

 Nelle versioni precedenti del provider OLE DB questo codice determinerebbe la creazione di una connessione implicita alla seconda esecuzione, in quanto per una sola connessione sarebbe possibile aprire un solo set attivo di risultati. Poiché la connessione implicita non sarebbe inserita nel pool di connessioni OLE DB, questa situazione provocherebbe overhead aggiuntivo. Con il servizio MARS esposto dal Driver OLE DB per SQL Server, si ottengono più risultati attivi in un'unica connessione.  

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
