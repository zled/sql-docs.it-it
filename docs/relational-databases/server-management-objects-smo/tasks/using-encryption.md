---
title: Uso della crittografia | Microsoft Docs
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
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9045033e7158bcd2ab47f4e924a4485128f451a3
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555921"
---
# <a name="using-encryption"></a>Uso della crittografia
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO la chiave master del servizio è rappresentata dal <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey> oggetto. Ciò fa riferimento il <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto. Può essere rigenerata tramite il <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A> (metodo).  
  
 La chiave master del database è rappresentata dal <xref:Microsoft.SqlServer.Management.Smo.MasterKey> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A> proprietà indica se la chiave master del database viene crittografata dalla chiave master del servizio. La copia crittografata nel database master viene aggiornata automaticamente ogni volta che viene modificata la chiave master del database.  
  
 È possibile eliminare la chiave di crittografia di servizio utilizzando il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> metodo e crittografare la chiave master del database con una password. In questo caso sarà necessario aprire in modo esplicito la chiave master del database prima di accedere a chiavi private protette dalla chiave master.  
  
 Quando un database viene allegato a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è necessario specificare la password per la chiave master del database oppure eseguire il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> metodo per rendere disponibili per la crittografia con il servizio di una copia non crittografata della chiave master del database chiave master. Si consiglia di eseguire questo passaggio per evitare la necessità di aprire in modo esplicito la chiave master del database.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A> metodo rigenera la chiave master del database. In seguito alla rigenerazione della chiave master del database, tutte le chiavi crittografate con tale chiave vengono decrittografate e successivamente crittografate con la nuova chiave master del database. Il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> metodo rimuove la crittografia della chiave master del database tramite la chiave master del servizio. <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> con una copia della chiave master viene crittografata utilizzando la chiave master del servizio e archiviata sia nel database corrente che nel database master.  
  
 In SMO i certificati sono rappresentati dalla <xref:Microsoft.SqlServer.Management.Smo.Certificate> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.Certificate> oggetto include proprietà che specificano la chiave pubblica, il nome del soggetto, il periodo di validità e le informazioni sull'autorità emittente. L'autorizzazione per l'accesso al certificato è controllata tramite i metodi **Grant**, **Revoke** e **Deny** .  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-a-certificate-in-visual-c"></a>Aggiunta di un certificato in Visual C#  
 Nell'esempio di codice viene creato un certificato semplice con una password di crittografia. A differenza di altri oggetti, il <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> metodo dispone di diversi overload. L'overload utilizzato nell'esempio crea un nuovo certificato con una password di crittografia.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>Aggiunta di un certificato in PowerShell  
 Nell'esempio di codice viene creato un certificato semplice con una password di crittografia. A differenza di altri oggetti, il <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> metodo dispone di diversi overload. L'overload utilizzato nell'esempio crea un nuovo certificato con una password di crittografia.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate  
  
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -argumentlist $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Usando le chiavi di crittografia](../../../relational-databases/server-management-objects-smo/tasks/using-encryption.md)  
  
  
