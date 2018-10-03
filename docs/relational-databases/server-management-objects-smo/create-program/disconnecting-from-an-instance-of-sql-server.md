---
title: Disconnessione da un'istanza di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cddbf8cdfaf1c9793479f2d9cbb1877b696e377d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633929"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Disconnessione da un'istanza di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Chiusura e disconnessione manualmente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oggetti Management Objects (SMO) non è obbligatorio. Le connessioni vengono aperte e chiuse in base alle necessità.  
  
## <a name="connection-pooling"></a>Pool di connessioni  
 Quando la [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) viene chiamato il metodo, la connessione non viene rilasciata automaticamente. Il [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) metodo deve essere chiamato in modo esplicito per rilasciare la connessione al pool di connessioni. È inoltre possibile richiedere una connessione non in pool. A questo scopo, impostare il [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) proprietà delle <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà che fa riferimento il [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) oggetto.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Disconnessione da un'istanza di SQL Server per RMO  
 La chiusura delle connessioni al server quando si programma con RMO funziona in modo leggermente diverso da SMO.  
  
 Perché la connessione al server per un oggetto RMO viene mantenuta per la [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) dell'oggetto, questo oggetto viene anche usato durante la disconnessione da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando si programma tramite RMO. Per chiudere una connessione usando il [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) dell'oggetto, chiamare il [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) metodo dell'oggetto RMO. Dopo che è stata chiusa la connessione, gli oggetti RMO non possono essere utilizzati.  
  
## <a name="example"></a>Esempio  
Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Chiusura e disconnessione di un oggetto SMO in Visual Basic  
 Questo esempio di codice viene illustrato come richiedere una connessione non in pool impostando il [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà dell'oggetto.  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Chiusura e disconnessione di un oggetto SMO in Visual C#  
 Questo esempio di codice viene illustrato come richiedere una connessione non in pool impostando il [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà dell'oggetto.  
  
```csharp  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
