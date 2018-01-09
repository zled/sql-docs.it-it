---
title: Utilizzo della crittografia | Documenti Microsoft
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
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a5069931c6e144dc574664e71c8f2a5d8964403
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-encryption"></a>Uso della crittografia
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In SMO la chiave master del servizio è rappresentata dal <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey> oggetto. Questo fa riferimento il <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto. Può essere rigenerata tramite il <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A> metodo.  
  
 La chiave master del database è rappresentata dal <xref:Microsoft.SqlServer.Management.Smo.MasterKey> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A> proprietà indica se la chiave master del database viene crittografata dalla chiave master del servizio. La copia crittografata nel database master viene aggiornata automaticamente ogni volta che viene modificata la chiave master del database.  
  
 È possibile eliminare la crittografia della chiave di servizio utilizzando il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> (metodo) e crittografare la chiave master del database con una password. In questo caso sarà necessario aprire in modo esplicito la chiave master del database prima di accedere a chiavi private protette dalla chiave master.  
  
 Quando un database è da connettere a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è necessario specificare la password per la chiave master del database oppure eseguire il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> metodo a disposizione una copia non crittografata della chiave master del database per la crittografia con il servizio chiave master. Si consiglia di eseguire questo passaggio per evitare la necessità di aprire in modo esplicito la chiave master del database.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A> metodo rigenera la chiave master del database. In seguito alla rigenerazione della chiave master del database, tutte le chiavi crittografate con tale chiave vengono decrittografate e successivamente crittografate con la nuova chiave master del database. Il <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> metodo rimuove la crittografia della chiave master del database dalla chiave master del servizio. <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> con una copia della chiave master viene crittografata utilizzando la chiave master del servizio e archiviata sia nel database corrente che nel database master.  
  
 In SMO i certificati sono rappresentati dal <xref:Microsoft.SqlServer.Management.Smo.Certificate> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.Certificate> oggetto include proprietà che specificano la chiave pubblica, il nome del soggetto, il periodo di validità e le informazioni sull'autorità emittente. L'autorizzazione per l'accesso al certificato è controllata tramite i metodi **Grant**, **Revoke** e **Deny** .  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
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
 [Utilizzando le chiavi di crittografia](../../../relational-databases/server-management-objects-smo/tasks/using-encryption.md)  
  
  
