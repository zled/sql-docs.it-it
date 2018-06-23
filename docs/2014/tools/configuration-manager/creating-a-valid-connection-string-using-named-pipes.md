---
title: Creazione di una stringa di connessione valida tramite Named pipe | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 264c615e38baf39676f1310d6465bfaac2a92785
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065273"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>Creazione di una stringa di connessione valida tramite named pipe
  Se non viene modificato dall'utente, quando l'istanza predefinita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa sul protocollo named pipes, utilizza `\\.\pipe\sql\query` come nome della pipe. Il punto indica che il computer sia sul computer locale `pipe` indica che la connessione è una named pipe e `sql\query` è il nome della pipe. Per connettersi alla pipe predefinita, è necessario che il nome della pipe dell'alias sia `\\<computer_name>\pipe\sql\query`. Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato configurato per essere in attesa su una pipe diversa, è necessario che il nome della pipe utilizzi tale pipe. Se ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza `\\.\pipe\unit\app` come pipe, è necessario che l'alias utilizzi `\\<computer_name>\pipe\unit\app` come nome della pipe.  
  
 Per creare un nome di pipe valido, è necessario:  
  
-   Specificare un **Nome alias**.  
  
-   Selezionare **Named pipe** come il **protocollo**.  
  
-   Immettere il **nome Pipe**. In alternativa, è possibile lasciare **nome della Pipe** vuota e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager verrà completata il nome appropriato dopo aver specificato la **protocollo** e **Server**  
  
-   Specificare un **Server**. Per un'istanza denominata è possibile specificare un nome di server e un nome di istanza.  
  
 Al momento della connessione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] componente Native Client legge il server, protocollo e nome pipe dal Registro di sistema per il nome alias specificato e crea un nome di pipe nel formato `np:\\<computer_name>\pipe\<pipename>` o `np:\\<IPAddress>\pipe\<pipename>`. Per un'istanza denominata, il nome di pipe predefinito è `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.  
  
> [!NOTE]  
>  Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall chiude la porta 445 per impostazione predefinita. Poiché [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comunica sulla porta 445, è necessario aprire nuovamente tale porta se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è configurato per l'ascolto delle connessioni client in arrivo mediante named pipe. Per informazioni sulla configurazione di un firewall, vedere "Procedura: Configurazione di un firewall per l’accesso a SQL Server" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure vedere la documentazione relativa al firewall.  
  
## <a name="connecting-to-the-local-server"></a>Connessione al server locale  
 Quando si stabilisce una connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione nello stesso computer del client, è possibile utilizzare `(local)` come nome del server. L'utilizzo di `(local)` non è consigliabile in quanto genera ambiguità, ma può risultare utile se si è sicuri che il client venga eseguito nel computer desiderato. Se, ad esempio, si crea un'applicazione per gli utenti mobili non connessi, ad esempio il personale di vendita, e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà eseguito su computer portatili e utilizzato per archiviare dati di progetto, un client che si connette al server (local) si connetterà sempre all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione sul portatile. In sostituzione di `localhost` è possibile utilizzare la parola `(local)` o un punto (.).  
  
## <a name="verifying-your-connection-protocol"></a>Verifica del protocollo di connessione  
 La query seguente restituisce il protocollo utilizzato per la connessione corrente.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Esempi  
 Connessione tramite il nome del server alla pipe predefinita:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Connessione tramite indirizzo IP alla pipe predefinita:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 Connessione tramite il nome del server a una pipe non predefinita:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Connessione tramite il nome del server a un'istanza denominata:  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Connessione al computer locale tramite `localhost`:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 Connessione al computer locale tramite un punto:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  Per specificare il protocollo di rete come un **sqlcmd** parametro, vedere "procedura: connettersi a sqlcmd.exe il motore di Database tramite" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di una stringa di connessione valida mediante il protocollo Shared Memory](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Creazione di una stringa di connessione valida con TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Scelta di un protocollo di rete](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  