---
title: Utilizzo di raccolte | Documenti Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6e173ace756159f1cc2e359de6f68f8f67064ee7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-collections"></a>Utilizzo delle raccolte
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Una raccolta è un elenco di oggetti costruiti dalla stessa classe di oggetti e che condividono lo stesso oggetto padre. L'oggetto raccolta contiene sempre il nome del tipo di oggetto con il suffisso Collection. Per accedere ad esempio alle colonne di una tabella specificata, utilizzare il tipo di oggetto <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>. Questo tipo contiene tutti gli oggetti <xref:Microsoft.SqlServer.Management.Smo.Column> che appartengono allo stesso oggetto <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 Il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **per... Ogni** istruzione o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **foreach** istruzione può essere utilizzata per scorrere ogni membro della raccolta.  
  
## <a name="examples"></a>Esempi  
Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Riferimento a un oggetto tramite una raccolta in Visual Basic  
 Questo esempio di codice viene illustrato come impostare una proprietà di colonna utilizzando il <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, e <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> proprietà. Queste proprietà rappresentano le raccolte che è possibile utilizzare per identificare un determinato oggetto quando sono utilizzate con un parametro che ne specifica il nome. Il nome e lo schema sono necessari per il <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> proprietà dell'oggetto raccolta.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Modify a property using the Databases, Tables, and Columns collections to reference a column.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Nullable = True
'Call the Alter method to make the change on the instance of SQL Server.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Alter()
```
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Riferimento a un oggetto tramite una raccolta in Visual C#  
 Questo esempio di codice viene illustrato come impostare una proprietà di colonna utilizzando il <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, e <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> proprietà. Queste proprietà rappresentano le raccolte che è possibile utilizzare per identificare un determinato oggetto quando sono utilizzate con un parametro che ne specifica il nome. Il nome e lo schema sono necessari per il <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> proprietà dell'oggetto raccolta.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a>Scorrimento dei membri di una raccolta in Visual Basic  
 Questo esempio di codice si scorre il <xref:Microsoft.AnalysisServices.Server.Databases%2A> proprietà di raccolta e di visualizzare tutte le connessioni all'istanza del database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
Dim count As Integer
Dim total As Integer
'Iterate through the databases and call the GetActiveDBConnectionCount method.
Dim db As Database
For Each db In srv.Databases
    count = srv.GetActiveDBConnectionCount(db.Name)
    total = total + count
    'Display the number of connections for each database.
    Console.WriteLine(count & " connections on " & db.Name)
Next
'Display the total number of connections on the instance of SQL Server.
Console.WriteLine("Total connections =" & total)
```
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Scorrimento dei membri di una raccolta in Visual C#  
 Questo esempio di codice si scorre il <xref:Microsoft.AnalysisServices.Server.Databases%2A> proprietà di raccolta e di visualizzare tutte le connessioni all'istanza del database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
