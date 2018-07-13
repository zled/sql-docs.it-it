---
title: Creazione, modifica e rimozione di Stored procedure | Microsoft Docs
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
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
caps.latest.revision: 44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d7e4ddf95dc9fa08e52c9a312d3cc83c3c04bd05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223181"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>Creazione, modifica e rimozione di stored procedure
  Nelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedure sono rappresentate dal <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetto.  
  
 La creazione di un <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetti in SMO richiede l'impostazione di <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> proprietà per il [!INCLUDE[tsql](../../../includes/tsql-md.md)] script che definisce la stored procedure. I parametri richiedono il prefisso @ e devono essere creati singolarmente utilizzando oggetti <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> e aggiungendoli alla raccolta  <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>.  
  
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
  
  
