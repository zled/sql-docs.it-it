---
title: Creazione, modifica e rimozione dei database | Documenti Microsoft
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
helpviewer_keywords:
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
caps.latest.revision: "41"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1857f72d40bc7e5f38fcda603507b49314cdcd59
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="creating-altering-and-removing-databases"></a>Creazione, modifica e rimozione di database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In SMO un database è rappresentato dal <xref:Microsoft.SqlServer.Management.Smo.Database> oggetto.  
  
 Non è necessario creare un oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> per modificarlo o rimuoverlo. È possibile fare riferimento al database tramite una raccolta.  
  
## <a name="example"></a>Esempio  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a>Creazione, modifica e rimozione di un database in Visual Basic  
 In questo esempio di codice viene creato un nuovo database. I file e i filegroup del database vengono creati automaticamente.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define a Database object variable by supplying the server and the database name arguments in the constructor.
Dim db As Database
db = New Database(srv, "Test_SMO_Database")
'Create the database on the instance of SQL Server.
db.Create()
'Reference the database and display the date when it was created.
db = srv.Databases("Test_SMO_Database")
Console.WriteLine(db.CreateDate)
'Remove the database.
db.Drop()
```
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a>Creazione, modifica e rimozione di un database in Visual C#  
 In questo esempio di codice viene creato un nuovo database. I file e i filegroup del database vengono creati automaticamente.  
  
```csharp  
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a>Creazione, modifica e rimozione di un database in PowerShell  
 In questo esempio di codice viene creato un nuovo database. I file e i filegroup del database vengono creati automaticamente.  
  
```powershell  
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = get-item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.   
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
  
  
