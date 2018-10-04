---
title: Uso di server collegati in SMO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8cdbbe3b44b2e3e6754f1f6c4dd084bec0032051
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213981"
---
# <a name="using-linked-servers-in-smo"></a>Utilizzo di server collegati in SMO
  Un server collegato rappresenta un'origine dati OLE DB in un server remoto. Origini dati OLE DB remote vengono collegate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto.  
  
 I server di database remoto possono essere collegati all'istanza corrente di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando un Provider OLE DB. In SMO i server collegati sono rappresentati dal <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> proprietà fa riferimento a una raccolta di <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> oggetti. in cui sono archiviate le credenziali di accesso necessarie per stabilire una connessione con il server collegato.  
  
## <a name="ole-db-providers"></a>Provider OLE DB  
 In SMO i provider OLE DB installati sono rappresentati da una raccolta di oggetti <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Esempio  
 Per l'esempio di codice seguente, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) e [creare un Visual C#&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Creazione di un collegamento a un server del provider OLE DB in Visual Basic  
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenei mediante il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome del prodotto, accesso ai dati nel server collegato usando il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Creazione di un collegamento a un server del provider OLE DB in Visual C#  
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenei mediante il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome del prodotto, accesso ai dati nel server collegato usando il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
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
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenei mediante il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome del prodotto, accesso ai dati nel server collegato usando il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
