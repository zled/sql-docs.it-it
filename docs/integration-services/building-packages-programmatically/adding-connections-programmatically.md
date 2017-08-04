---
title: Aggiunta di connessioni a livello di codice | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- connection managers [Integration Services], packages
- Integration Services packages, connections
- connections [Integration Services], packages
- SSIS packages, connections
- packages [Integration Services], connections
- intrinsic properties [Integration Services]
- SQL Server Integration Services packages, connections
- ConnectionManager class
- SSIS connection managers
- adding package connections
ms.assetid: d90716d1-4c65-466c-b82c-4aabbee1e3e5
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b768ad80f2b28cc3fb73a2210188bab26c902441
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="adding-connections-programmatically"></a>Aggiunta di connessioni a livello di programmazione
  La classe <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> rappresenta le connessioni fisiche alle origini dati esterne. La classe <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> isola i dettagli di implementazione della connessione dal runtime. In questo modo il runtime è in grado di interagire con ogni gestione connessione in modo coerente e stimabile. Le gestioni connessione contengono un set di proprietà predefinite comuni a tutte le connessioni, ad esempio <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>. Le proprietà <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, tuttavia, sono in genere le uniche necessarie per configurare una gestione connessione. A differenza di altri paradigmi di programmazione, in cui le classi di connessione espongono metodi quali **aprire** o **Connetti** per stabilire fisicamente una connessione all'origine dati, il motore di run-time gestisce tutte le connessioni per il pacchetto mentre è in esecuzione.  
  
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Connections> è una raccolta delle gestioni connessione aggiunte a tale pacchetto e disponibili per essere utilizzate in fase di esecuzione. È possibile aggiungere altre gestioni connessione alla raccolta utilizzando il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> della raccolta e fornendo una stringa che indica il tipo di gestione connessione. Il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> restituisce l'istanza <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> aggiunta al pacchetto.  
  
## <a name="intrinsic-properties"></a>Proprietà intrinseche  
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> espone un set di proprietà comuni a tutte le connessioni. Tuttavia, è talvolta necessario accedere a proprietà univoche per il tipo di connessione specifico. La raccolta <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> della classe <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> fornisce l'accesso a queste proprietà. La proprietà può essere recuperata dalla raccolta utilizzando l'indicizzatore o il nome della proprietà e **GetValue** (metodo) e i valori vengono impostati utilizzando il **SetValue** metodo. È possibile impostare le proprietà delle proprietà dell'oggetto connessione sottostante anche acquisendo un'istanza effettiva dell'oggetto e impostandone direttamente le proprietà. Per ottenere la connessione sottostante, utilizzare la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> della gestione connessione. Nella riga seguente di codice è mostrata una riga C# che crea una gestione connessione ADO.NET che dispone della classe sottostante, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>.  
  
 `ConnectionManagerAdoNetClass cmado = cm.InnerObject as ConnectionManagerAdoNet;`  
  
 Esegue il cast dell'oggetto gestione connessione gestito all'oggetto connessione sottostante. Se si utilizza C++, il **QueryInterface** metodo il <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> oggetto viene chiamato e viene richiesta l'interfaccia dell'oggetto connessione sottostante.  
  
 Nella tabella seguente sono elencate le gestioni connessioni incluse in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. e la stringa utilizzata nell'istruzione `package.Connections.Add("xxx")` Per un elenco di tutte le gestioni connessioni, vedere [Integration Services &#40; SSIS &#41; Connessioni](../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
|String|Gestione connessione|  
|------------|------------------------|  
|"OLEDB"|Gestione connessione per le connessioni OLE DB.|  
|"ODBC"|Gestione connessione per le connessioni ODBC.|  
|"ADO"|Gestione connessione per le connessioni ADO.|  
|"ADO.NET:SQL"|Gestione connessione per le connessioni ADO.NET (provider di dati SQL).|  
|"ADO.NET:OLEDB"|Gestione connessione per le connessioni ADO.NET (provider di dati OLE DB).|  
|"FLATFILE"|Gestione connessione per le connessioni file flat.|  
|"FILE"|Gestione connessione per le connessioni file.|  
|"MULTIFLATFILE"|Gestione connessione per le connessioni di più file flat.|  
|"MULTIFILE"|Gestione connessione per le connessioni di più file.|  
|"SQLMOBILE"|Gestione connessione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connessioni.|  
|"MSOLAP100"|Gestione connessione per le connessioni [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|"FTP"|Gestione connessione per le connessioni FTP.|  
|"HTTP"|Gestione connessione per le connessioni HTTP.|  
|"MSMQ"|Gestione connessione per le connessioni di accodamento messaggi (anche noto come MSMQ).|  
|"SMTP"|Gestione connessione per le connessioni SMTP.|  
|"WMI"|Gestione connessione per le connessioni Strumentazione gestioneWindows (WMI) di Microsoft.|  
  
 Nell'esempio di codice seguente è illustrata l'aggiunta di una connessione FILE e OLE DB alla raccolta <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> di un oggetto <xref:Microsoft.SqlServer.Dts.Runtime.Package>. Nell'esempio vengono quindi impostate le proprietà <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      // Create a package, and retrieve its connections.  
      Package pkg = new Package();  
      Connections pkgConns = pkg.Connections;  
  
      // Add an OLE DB connection to the package, using the   
      // method defined in the AddConnection class.  
      CreateConnection myOLEDBConn = new CreateConnection();  
      myOLEDBConn.CreateOLEDBConnection(pkg);  
  
      // View the new connection in the package.  
      Console.WriteLine("Connection description: {0}",  
         pkg.Connections["SSIS Connection Manager for OLE DB"].Description);  
  
      // Add a second connection to the package.  
      CreateConnection myFileConn = new CreateConnection();  
      myFileConn.CreateFileConnection(pkg);  
  
      // View the second connection in the package.  
      Console.WriteLine("Connection description: {0}",  
        pkg.Connections["SSIS Connection Manager for Files"].Description);  
  
      Console.WriteLine();  
      Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count);  
  
      Console.Read();  
    }  
  }  
  // <summary>  
  // This class contains the definitions for multiple  
  // connection managers.  
  // </summary>  
  public class CreateConnection  
  {  
    // Private data.  
    private ConnectionManager ConMgr;  
  
    // Class definition for OLE DB Provider.  
    public void CreateOLEDBConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("OLEDB");  
      ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" +  
        "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" +  
        "Data Source=(local);";  
      ConMgr.Name = "SSIS Connection Manager for OLE DB";  
      ConMgr.Description = "OLE DB connection to the AdventureWorks database.";  
    }  
    public void CreateFileConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("File");  
      ConMgr.ConnectionString = @"\\<yourserver>\<yourfolder>\books.xml";  
      ConMgr.Name = "SSIS Connection Manager for Files";  
      ConMgr.Description = "Flat File connection";  
    }  
  }  
  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    ' Create a package, and retrieve its connections.  
    Dim pkg As New Package()  
    Dim pkgConns As Connections = pkg.Connections  
  
    ' Add an OLE DB connection to the package, using the   
    ' method defined in the AddConnection class.  
    Dim myOLEDBConn As New CreateConnection()  
    myOLEDBConn.CreateOLEDBConnection(pkg)  
  
    ' View the new connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for OLE DB").Description)  
  
    ' Add a second connection to the package.  
    Dim myFileConn As New CreateConnection()  
    myFileConn.CreateFileConnection(pkg)  
  
    ' View the second connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for Files").Description)  
  
    Console.WriteLine()  
    Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
' This class contains the definitions for multiple  
' connection managers.  
  
Public Class CreateConnection  
  ' Private data.  
  Private ConMgr As ConnectionManager  
  
  ' Class definition for OLE DB provider.  
  Public Sub CreateOLEDBConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("OLEDB")  
    ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" & _  
      "Data Source=(local);"  
    ConMgr.Name = "SSIS Connection Manager for OLE DB"  
    ConMgr.Description = "OLE DB connection to the AdventureWorks database."  
  End Sub  
  
  Public Sub CreateFileConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("File")  
    ConMgr.ConnectionString = "\\<yourserver>\<yourfolder>\books.xml"  
    ConMgr.Name = "SSIS Connection Manager for Files"  
    ConMgr.Description = "Flat File connection"  
  End Sub  
  
End Class  
```  
  
 **Esempio di Output:**  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Number of connections in package: 2`  
  
## <a name="external-resources"></a>Risorse esterne  
 Articolo tecnico relativo [le stringhe di connessione](http://go.microsoft.com/fwlink/?LinkId=220743), sul sito Web carlprothman.net.  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40; SSIS &#41; Connessioni](../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Creare gestioni connessioni](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  
