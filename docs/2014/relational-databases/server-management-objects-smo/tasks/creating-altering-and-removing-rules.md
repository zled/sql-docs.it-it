---
title: Creazione, modifica e rimozione di regole | Documenti Microsoft
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
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
caps.latest.revision: 44
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1e3b9022911f69576cead7c44283fcad362d57c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064019"
---
# <a name="creating-altering-and-removing-rules"></a>Creazione, modifica e rimozione di regole
  In SMO le regole sono rappresentate dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule>. La regola è definita dalla proprietà <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A>, ovvero una stringa di testo contenente un'espressione della condizione che utilizza operatori o predicati, ad esempio IN, LIKE o BETWEEN. Una regola non può fare riferimento a colonne o ad altri oggetti di database. È possibile includere funzioni predefinite che non fanno riferimento a oggetti di database.  
  
 La definizione nella proprietà <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> deve contenere una variabile che fa riferimento al valore di dati immesso. Quando si crea la regola, è possibile utilizzare qualsiasi nome o simbolo per rappresentare il valore, ma il primo carattere deve essere il simbolo di chiocciola (@).  
  
## <a name="example"></a>Esempio  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto di Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oppure [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a>Creazione, modifica e rimozione di una regola in Visual Basic  
 In questo esempio di codice viene illustrato come creare una regola, collegarla a una colonna, modificare le proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule>, scollegarla dalla colonna e infine eliminarla.  
  
 L'istruzione `Dim` per l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule> viene specificata con il percorso completo dell'assembly per evitare ambiguità con un oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule> nell'assembly System.Data.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a>Creazione, modifica e rimozione di una regola in Visual C#  
 In questo esempio di codice viene illustrato come creare una regola, collegarla a una colonna, modificare le proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule>, scollegarla dalla colonna e infine eliminarla.  
  
 L'istruzione `Dim` per l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule> viene specificata con il percorso completo dell'assembly per evitare ambiguità con un oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule> nell'assembly System.Data.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a>Creazione, modifica e rimozione di una regola in PowerShell  
 In questo esempio di codice viene illustrato come creare una regola, collegarla a una colonna, modificare le proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule>, scollegarla dalla colonna e infine eliminarla.  
  
 L'istruzione `Dim` per l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule> viene specificata con il percorso completo dell'assembly per evitare ambiguità con un oggetto <xref:Microsoft.SqlServer.Management.Smo.Rule> nell'assembly System.Data.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule `  
-argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.   
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.   
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and   
# column as arguments in the BindToColumn method.   
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.   
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
  
  