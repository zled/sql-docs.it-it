---
title: Creazione, modifica e rimozione di viste | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb90ebd600a17efc71c1195ed070091ca826fc4d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="creating-altering-and-removing-views"></a>Creazione, modifica e rimozione di viste
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] visualizzazioni sono rappresentate dal <xref:Microsoft.SqlServer.Management.Smo.View> oggetto.  
  
 La proprietà <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.View> definisce la vista. È l'equivalente di [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione SELECT per la creazione di una vista.  
  
## <a name="example"></a>Esempio  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Creazione, modifica e rimozione di una vista in Visual Basic  
 In questo esempio di codice viene illustrato come creare una vista di due tabelle tramite un inner join. La vista viene creata utilizzando la modalità testo, pertanto la <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> deve essere impostata.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a View object variable by supplying the parent database, view name and schema in the constructor.
Dim myview As View
myview = New View(db, "Test_View", "Sales")
'Set the TextHeader and TextBody property to define the view.
myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"
myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"
'Create the view on the instance of SQL Server.
myview.Create()
'Remove the view.
myview.Drop()
```
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Creazione, modifica e rimozione di una vista in Visual C#  
 In questo esempio di codice viene illustrato come creare una vista di due tabelle tramite un inner join. La vista viene creata utilizzando la modalità testo, pertanto la <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> deve essere impostata.  
  
```csharp  
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a>Creazione, modifica e rimozione di una vista in PowerShell  
 In questo esempio di codice viene illustrato come creare una vista di due tabelle tramite un inner join. La vista viene creata utilizzando la modalità testo, pertanto la <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> deve essere impostata.  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.   
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View `  
-argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.   
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.   
$myview.Create()  
  
# Remove the view.   
$myview.Drop();  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
  
  
