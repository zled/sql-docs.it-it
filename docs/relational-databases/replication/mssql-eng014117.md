---
title: "MSSQL_ENG014117 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014117 - errore"
ms.assetid: e5906a76-9511-4c47-8826-8c765b58a39d
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014117
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14117|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|'%s' non è configurato come database di distribuzione.|  
  
## Spiegazione  
 Questo errore si può verificare in presenza di una o entrambe le condizioni seguenti:  
  
-   Manca la voce per il database di distribuzione specificato **msdb... MSdistributiondbs**.  
  
-   Non è presente una voce per il server locale nel **master** database o sulla voce che è corretto.  
  
     La replica prevede che tutti i server di una topologia vengano registrati utilizzando il nome del computer con il nome di un'istanza opzionale (nel caso di un'istanza cluster il nome del server virtuale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il nome dell'istanza opzionale). Per un corretto funzionamento della replica il valore restituito da `SELECT @@SERVERNAME` per ogni server nella topologia deve far corrispondere al nome dell'istanza opzionale il nome del computer o il nome del server virtuale.  
  
     Non sarà possibile eseguire la replica, se una qualsiasi delle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene registrata utilizzando l'indirizzo IP o il nome di dominio completo (FQDN, Fully Qualified Domain Name). Se durante la configurazione della replica una delle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stata registrata utilizzando l'indirizzo IP o il nome di dominio completo in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], è possibile che venga generato questo errore.  
  
## Azione dell'utente  
 Verificare la corretta registrazione dell'istanza del server di distribuzione. Se il nome di rete del computer e il nome dell'istanza di SQL Server sono diversi, procedere in uno dei modi seguenti:  
  
-   Aggiungere il nome dell'istanza di SQL Server come nome di rete valido. Uno dei metodi disponibili per impostare un nome di rete alternativo consiste nell'aggiungerlo al file hosts locale. Il file hosts locale è disponibile per impostazione predefinita nella cartella WINDOWS\system32\drivers\etc o WINNT\system32\drivers\etc. Per ulteriori informazioni, vedere la documentazione di Windows.  
  
     Ad esempio, se il nome del computer è comp1, l'indirizzo IP del computer è 10.193.17.129 e il nome dell'istanza è inst1/instname, aggiungere la voce seguente al file hosts:  
  
     10.193.17.129 inst1  
  
-   Disabilitare la distribuzione, registrare l'istanza e quindi riattivare la distribuzione. Se il valore di @@SERVERNAME non è corretto per un'istanza non cluster, eseguire la procedura seguente:  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     Dopo aver eseguito la [sp_addserver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) stored procedure, è necessario riavviare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio per @@SERVERNAME per rendere effettive le modifiche.  
  
     Se il valore di @@SERVERNAME non è corretto per un'istanza cluster, è necessario modificare il nome mediante Amministrazione cluster. Per ulteriori informazioni, vedere [istanze Cluster di Failover AlwaysOn & #40; SQL Server & #41;](../Topic/AlwaysOn%20Failover%20Cluster%20Instances%20\(SQL%20Server\).md).  
  
 Dopo aver verificato che l'istanza del server di distribuzione sia registrato correttamente, verificare che il database di distribuzione sia elencato in **msdb... MSdistributiondbs**. In caso contrario:  
  
1.  Inserire nello script la configurazione di distribuzione. Per altre informazioni, vedere [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
2.  Disabilitare la distribuzione e quindi attivarla nuovamente. Per ulteriori informazioni, vedere [Configura distribuzione](../../relational-databases/replication/configure-distribution.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  