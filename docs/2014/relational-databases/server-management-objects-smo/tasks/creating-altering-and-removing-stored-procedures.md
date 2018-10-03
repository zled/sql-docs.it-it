---
title: Creazione, modifica e rimozione di Stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe7fb603ae3b0f3550d63d4c9b886934b31a28ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074501"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>Creazione, modifica e rimozione di stored procedure
  Nelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedure sono rappresentate dal <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetto.  
  
 La creazione di un <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetti in SMO richiede l'impostazione di <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> proprietà per il [!INCLUDE[tsql](../../../includes/tsql-md.md)] script che definisce la stored procedure. I parametri richiedono il \@ prefissi e devono essere creati singolarmente utilizzando <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> gli oggetti e l'aggiunta al <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> insieme del <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetto.  
  
## <a name="example"></a>Esempio  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oppure [creare un Visual C#&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>Creazione, modifica e rimozione di una stored procedure in Visual Basic  
 Questo esempio di codice viene illustrato come creare una stored procedure per la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database. Nell'esempio viene restituito il cognome di un dipendente quando viene fornito il numero ID del dipendente. La stored procedure richiede un parametro di input per specificare il numero ID del dipendente e un parametro di output per restituire il cognome del dipendente.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>Creazione, modifica e rimozione di una stored procedure in Visual C#  
 Questo esempio di codice viene illustrato come creare una stored procedure per la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database. Nell'esempio viene restituito il cognome di un dipendente quando viene fornito il numero ID del dipendente (`BusinessEntityID`). La stored procedure richiede un parametro di input per specificare il numero ID del dipendente e un parametro di output per restituire il cognome del dipendente.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>Creazione, modifica e rimozione di una stored procedure in PowerShell  
 Questo esempio di codice viene illustrato come creare una stored procedure per la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database. Nell'esempio viene restituito il cognome di un dipendente quando viene fornito il numero ID del dipendente (`BusinessEntityID`). La stored procedure richiede un parametro di input per specificare il numero ID del dipendente e un parametro di output per restituire il cognome del dipendente.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
$sp  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure `  
-argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.   
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.   
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.   
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.   
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.   
$sp.Drop()  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
  
  
