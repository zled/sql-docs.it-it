---
title: Disconnessione da un'istanza di SQL Server | Documenti Microsoft
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
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f2ce4ae7ce42df42be9b6bc68c3d13acf949dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157667"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Disconnessione da un'istanza di SQL Server
  Chiusura e disconnessione manualmente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oggetti Management Objects (SMO) non è obbligatorio. Le connessioni vengono aperte e chiuse in base alle necessità.  
  
## <a name="connection-pooling"></a>Pool di connessioni  
 Quando il <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> metodo viene chiamato, la connessione non viene rilasciata automaticamente. Per rilasciare la connessione nel pool di connessioni, è necessario che il metodo <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> venga richiamato in modo esplicito. È inoltre possibile richiedere una connessione non in pool. Per eseguire questa operazione, impostare la proprietà <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> della proprietà <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> che fa riferimento all'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Disconnessione da un'istanza di SQL Server per RMO  
 La chiusura delle connessioni al server quando si programma con RMO funziona in modo leggermente diverso da SMO.  
  
 Poiché la connessione al server per un oggetto RMO viene gestita per il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dell'oggetto, questo oggetto viene inoltre usato durante la disconnessione da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando si programma tramite RMO. Per chiudere una connessione utilizzando il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> dell'oggetto, chiamare il <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> metodo dell'oggetto RMO. Dopo che è stata chiusa la connessione, gli oggetti RMO non possono essere utilizzati.  
  
## <a name="example"></a>Esempio  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Chiusura e disconnessione di un oggetto SMO in Visual Basic  
 Questo esempio di codice viene illustrato come richiedere una connessione non in pool impostando la <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà dell'oggetto.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Chiusura e disconnessione di un oggetto SMO in Visual C#  
 Questo esempio di codice viene illustrato come richiedere una connessione non in pool impostando la <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà dell'oggetto.  
  
```  
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
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  