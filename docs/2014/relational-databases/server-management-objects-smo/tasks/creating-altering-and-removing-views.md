---
title: Creazione, modifica e rimozione di viste | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b70113899ccaa31aa0e8119ec2a42ba1daece1a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068696"
---
# <a name="creating-altering-and-removing-views"></a>Creazione, modifica e rimozione di viste
  In SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects), le viste di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono rappresentate dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.View>.  
  
 La proprietà <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.View> definisce la vista. È l'equivalente del [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione SELECT per la creazione di una vista.  
  
## <a name="example"></a>Esempio  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto di Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oppure [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Creazione, modifica e rimozione di una vista in Visual Basic  
 In questo esempio di codice viene illustrato come creare una vista di due tabelle tramite un inner join. La vista viene creata utilizzando la modalità testo, pertanto la <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> deve essere impostata.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Creazione, modifica e rimozione di una vista in Visual C#  
 In questo esempio di codice viene illustrato come creare una vista di due tabelle tramite un inner join. La vista viene creata utilizzando la modalità testo, pertanto la <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> deve essere impostata.  
  
```  
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
  
```  
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
  
  