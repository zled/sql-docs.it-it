---
title: Uso di server collegati in SMO | Microsoft Docs
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
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c864271d5ca3d9cfb4155f6b755493432d441110
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38029628"
---
# <a name="using-linked-servers-in-smo"></a>Utilizzo di server collegati in SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Un server collegato rappresenta un'origine dati OLE DB in un server remoto. Origini dati OLE DB remote vengono collegate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto.  
  
 I server di database remoto possono essere collegati all'istanza corrente di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando un Provider OLE DB. In SMO i server collegati sono rappresentati dal <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> proprietà fa riferimento a una raccolta di <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> oggetti. in cui sono archiviate le credenziali di accesso necessarie per stabilire una connessione con il server collegato.  
  
## <a name="ole-db-providers"></a>Provider OLE DB  
 In SMO i provider OLE DB installati sono rappresentati da una raccolta di oggetti <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Creazione di un collegamento a un server del provider OLE DB in Visual C#  
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenei mediante il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome del prodotto, accesso ai dati nel server collegato usando il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
 L'esempio di codice viene illustrato come creare un collegamento a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, origine dati eterogenei mediante il <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> oggetto. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome del prodotto, accesso ai dati nel server collegato usando il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client Provider OLE DB, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
  
  
