---
title: Utilizzo di server collegati in SMO | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0499f5e755e9725990aae15bcb5f8cf356ff9920
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="using-linked-servers-in-smo"></a>Utilizzo di server collegati in SMO
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Un server collegato rappresenta un'origine dati OLE DB in un server remoto. Origini dati OLE DB remote vengono collegate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto.  
  
 Server di database remoti possono essere collegati all'istanza corrente di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite un Provider OLE DB. In SMO i server collegati sono rappresentati di <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> proprietà fa riferimento a una raccolta di <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> oggetti. in cui sono archiviate le credenziali di accesso necessarie per stabilire una connessione con il server collegato.  
  
## <a name="ole-db-providers"></a>Provider OLE DB  
 In SMO i provider OLE DB installati sono rappresentati da una raccolta di oggetti <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Creazione di un collegamento a un server del provider OLE DB in Visual C#  
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenea tramite il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome di prodotto, accesso ai dati nel server collegato tramite il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>Creazione di un collegamento a un server del provider OLE DB in PowerShell  
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenea tramite il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome di prodotto, accesso ai dati nel server collegato tramite il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```powershell  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
