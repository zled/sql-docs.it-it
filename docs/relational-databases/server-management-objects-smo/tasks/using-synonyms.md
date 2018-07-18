---
title: Utilizzo dei sinonimi | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d4971819e0731a5e72bd281f216a7afa4310dac1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000883"
---
# <a name="using-synonyms"></a>Utilizzo dei sinonimi
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Per sinonimo si intende un nome alternativo per un oggetto con ambito schema. In SMO i sinonimi sono rappresentati dalla <xref:Microsoft.SqlServer.Management.Smo.Synonym> oggetto. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.Synonym> è un elemento figlio dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database>. Ciò significa che i sinonimi sono validi solo all'interno dell'ambito del database nel quale sono definiti. Tuttavia, il sinonimo può fare riferimento agli oggetti in un altro database o in un'istanza remota di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 L'oggetto a cui viene assegnato un nome alternativo è noto come oggetto di base. La proprietà name dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Synonym> è il nome alternativo assegnato all'oggetto di base.  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-synonym-in-visual-c"></a>Creazione di un sinonimo in Visual C#  
 Nell'esempio di codice viene illustrato come creare un sinonimo o un nome alternativo per un oggetto con ambito schema. Le applicazioni client possono utilizzare un singolo riferimento per l'oggetto di base mediante un sinonimo anziché utilizzare un nome costituito da più parti per fare riferimento all'oggetto di base.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a>Creazione di un sinonimo in PowerShell  
 Nell'esempio di codice viene illustrato come creare un sinonimo o un nome alternativo per un oggetto con ambito schema. Le applicazioni client possono utilizzare un singolo riferimento per l'oggetto di base mediante un sinonimo anziché utilizzare un nome costituito da più parti per fare riferimento all'oggetto di base.  
  
```powershell  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym `  
-argumentlist $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../../t-sql/statements/create-synonym-transact-sql.md)  
  
  
