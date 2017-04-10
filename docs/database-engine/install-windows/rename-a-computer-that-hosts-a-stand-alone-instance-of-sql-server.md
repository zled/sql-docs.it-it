---
title: "Rinominare un computer che ospita un&#39;istanza autonoma di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errori di accesso remoto [SQL Server]"
  - "nomi di computer autonomi [SQL Server]"
  - "nomi [SQL Server], istanze autonome di SQL Server"
  - "ridenominazione di istanze autonome di SQL Server"
  - "tabella di sistema sysservers"
  - "rimozione di account di accesso remoto"
  - "eliminazione di account di accesso remoto"
  - "rimozione di account di accesso remoto"
ms.assetid: bbaf1445-b8a2-4ebf-babe-17d8cf20b037
caps.latest.revision: 31
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 31
---
# Rinominare un computer che ospita un&#39;istanza autonoma di SQL Server
  Quando si modifica il nome del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il nuovo nome viene riconosciuto durante l'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non è necessario eseguire nuovamente il programma di installazione per reimpostare il nome del computer. Utilizzare invece la procedura riportata di seguito per aggiornare i metadati di sistema archiviati in sys.servers e restituiti dalla funzione di sistema @@SERVERNAME. Aggiornare i metadati di sistema in modo da riflettere le modifiche apportate al nome del computer per le connessioni remote e le applicazioni che utilizzano @@SERVERNAME o che eseguono query sul nome del server da sys.servers.  
  
 La procedura seguente non può essere utilizzata per rinominare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma solo per rinominare la parte del nome di istanza corrispondente al nome del computer. Ad esempio, è possibile modificare il nome di un computer denominato MB1 che ospita un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominata Instance1 trasformandolo in MB2. La parte del nome che si riferisce all'istanza, ovvero Instance1, rimarrà tuttavia invariata. In questo esempio \\\\*ComputerName*\\*InstanceName* verrebbe trasformato da \\\MB1\Instance1 in \\\MB2\Instance1.  
  
 **Operazioni preliminari**  
  
 Prima di iniziare il processo di ridenominazione, esaminare le informazioni seguenti:  
  
-   Se un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fa parte di un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il processo di ridenominazione del computer è diverso da quello previsto per un computer che ospita un'istanza autonoma.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta la ridenominazione dei computer interessati dalla replica, a meno che non si usi il log shipping con replica. Il computer secondario nel log shipping può essere rinominato in caso di perdita definitiva del computer primario. Per altre informazioni, vedere [Log shipping e replica &#40;SQL Server&#41;](../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).  
  
-   Quando si rinomina un computer configurato per l'utilizzo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] potrebbe non essere disponibile in seguito alla modifica del nome del computer. Per altre informazioni, vedere [Rinominare un computer del server di report](../../reporting-services/report-server/rename-a-report-server-computer.md).  
  
-   Quando si rinomina un computer configurato per l'utilizzo del mirroring del database, è necessario disabilitare il mirroring del database prima dell'operazione di ridenominazione. Riattivare quindi il mirroring del database con il nuovo nome del computer. I metadati per il mirroring del database non verranno aggiornati automaticamente per riflettere il nuovo nome del computer. Per aggiornare i metadati di sistema, utilizzare la procedura indicata di seguito:  
  
-   Gli utenti che si connettono a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un gruppo di Windows che utilizza un riferimento specificato a livello di codice al nome del computer potrebbero non essere in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo problema può verificarsi in seguito alla ridenominazione se il gruppo di Windows specifica il nome del computer precedente. Per garantire che tale gruppo di Windows consenta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dopo l'operazione di ridenominazione, aggiornarlo in modo che specifichi il nuovo nome del computer.  
  
 È possibile connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il nuovo nome del computer in seguito al riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per garantire che @@SERVERNAME restituisca il nome aggiornato dell'istanza del server locale, è consigliabile eseguire manualmente la procedura descritta di seguito valida per il proprio scenario. La procedura varia a seconda che si aggiorni un computer che ospita un'istanza predefinita o un'istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Per rinominare un computer che ospita un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Per un computer rinominato che ospita un'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eseguire le procedure riportate di seguito:  
  
    ```  
    sp_dropserver <old_name>;  
    GO  
    sp_addserver <new_name>, local;  
    GO  
    ```  
  
     Riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Per un computer rinominato che ospita un'istanza denominata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eseguire le procedure riportate di seguito:  
  
    ```  
    sp_dropserver <old_name\instancename>;  
    GO  
    sp_addserver <new_name\instancename>, local;  
    GO  
    ```  
  
     Riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Al termine dell'operazione di ridenominazione  
 In seguito alla ridenominazione di un computer, tutte le connessioni che utilizzavano il nome precedente devono essere eseguite utilizzando il nuovo nome.  
  
#### Per verificare il corretto completamento dell'operazione di ridenominazione  
  
-   Selezionare le informazioni da @@SERVERNAME o sys.servers. La funzione @@SERVERNAME restituirà il nuovo nome e la tabella sys.servers includerà il nuovo nome. Nell'esempio seguente viene illustrato l'utilizzo di @@SERVERNAME.  
  
    ```  
    SELECT @@SERVERNAME AS 'Server Name';  
    ```  
  
## Ulteriori considerazioni  
 **Account di accesso remoto**: se il computer dispone di account di accesso remoto, l'esecuzione di **sp_dropserver** può generare un errore simile al seguente:  
  
 `Server: Msg 15190, Level 16, State 1, Procedure sp_dropserver, Line 44 There are still remote logins for the server 'SERVER1'.`  
  
 Per risolvere l'errore, è necessario eliminare gli account di accesso remoto per tale server.  
  
#### Per eliminare gli account di accesso remoto  
  
-   Per un'istanza predefinita, eseguire le procedure seguenti:  
  
    ```  
    sp_dropremotelogin old_name;  
    GO  
    ```  
  
-   Per un'istanza denominata, eseguire le procedure seguenti:  
  
    ```  
    sp_dropremotelogin old_name\instancename;  
    GO  
    ```  
  
 **Configurazioni del server collegato**: le configurazioni del server collegato saranno interessate dall'operazione di ridenominazione del computer. Usare **sp_addlinkedserver** o **sp_setnetname** per aggiornare i riferimenti ai nomi di computer. Per altre informazioni, vedere [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) oo [sp_setnetname &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setnetname-transact-sql.md).  
  
 **Nomi alias per i client**: gli alias per i client che usano named pipe verranno interessati dall'operazione di ridenominazione del computer. Se ad esempio è stato creato un alias "PROD_SRVR" per puntare a SRVR1 e viene utilizzato il protocollo Named Pipes, il nome pipe sarà simile al seguente: `\\SRVR1\pipe\sql\query`. Dopo la ridenominazione del computer, il percorso di named pipe non sarà più valido. Per altre informazioni sulle named pipe, vedere l'argomento [Creazione di una stringa di connessione valida tramite named pipe](http://go.microsoft.com/fwlink/?LinkId=111063).  
  
## Vedere anche  
 [Installare SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016.md)  
  
  