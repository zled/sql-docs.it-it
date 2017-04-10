---
title: "Avvio di SQL Server in modalit&#224; utente singolo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "avvio di SQL Server, modalità utente singolo"
  - "modalità utente singolo [SQL Server]"
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Avvio di SQL Server in modalit&#224; utente singolo
  In alcuni casi potrebbe essere necessario avviare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo usando l'**opzione di avvio -m**. Ad esempio, può risultare utile modificare le opzioni di configurazione del server oppure recuperare un database master o un altro database di sistema danneggiato. In entrambi i casi, è necessario avviare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo.  
  
 L'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo consente a qualsiasi membro del gruppo Administrators locale del computer di connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come membro del ruolo predefinito del server sysadmin. Per altre informazioni, vedere [Connettersi a SQL Server se gli amministratori di sistema sono bloccati](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Quando si avvia un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo, si noti quanto segue:  
  
-   La connessione al server è consentita a un solo utente.  
  
-   Il processo CHECKPOINT non viene eseguito. Per impostazione predefinita, tale processo viene eseguito automaticamente all'avvio.  
  
> [!NOTE]  
>  Arrestare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prima di connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo. In caso contrario, il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent utilizzerà la connessione, bloccandola.  
  
 Quando si avvia un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] può connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In Esplora oggetti in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] potrebbe verificarsi un errore perché per alcune operazioni sono necessarie più connessioni. Per gestire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo, eseguire istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] stabilendo la connessione solo tramite l'editor di query in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oppure usare l'utilità [sqlcmd](../../tools/sqlcmd-utility.md).  
  
 Quando si usa l'opzione **-m** con **sqlcmd** o [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], è possibile limitare le connessioni a un'applicazione client specifica. Ad esempio, **-m"sqlcmd"** limita le connessioni a una singola connessione, che deve identificarsi come programma client **sqlcmd**. Utilizzare questa opzione quando si avvia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo e un'applicazione client sconosciuta accede all'unica connessione disponibile. Per connettersi con l'editor di query in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], usare **-m"Microsoft SQL Server Management Studio - Query"**.  
  
> [!IMPORTANT]  
>  Non utilizzare tale opzione come caratteristica di sicurezza. L'applicazione client fornisce il nome dell'applicazione client stessa e può indicare un nome falso come parte della stringa di connessione.  
  
## Nota per le installazioni cluster  
 Per un'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un ambiente cluster, quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene avviato in modalità utente singolo, la dll della risorsa cluster utilizza tutta la connessione disponibile, bloccando pertanto qualsiasi altra connessione al server. Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si trova in questo stato, se si tenta di portare la risorsa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] online, potrebbe venire eseguito il failover della risorsa SQL a un nodo diverso se la risorsa è configurata in modo da influire sul gruppo.  
  
 Per aggirare il problema, attenersi alla procedura seguente:  
  
1.  Rimuovere il parametro di avvio -m dalle proprietà avanzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Portare la risorsa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offline.  
  
3.  Dal nodo del proprietario corrente di questo gruppo eseguire il comando seguente da a un prompt dei comandi:  
    net start MSSQLSERVER /m.  
  
4.  Verificare tramite Amministrazione cluster o tramite la console di gestione del cluster di failover che la risorsa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia ancora offline.  
  
5.  Connettersi ora a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il comando seguente ed eseguire l'operazione necessaria: SQLCMD -E -S\<nomeserver>.  
  
6.  Dopo aver completato l'operazione, chiudere il prompt dei comandi e riportare online SQL e le altre risorse tramite Amministrazione cluster.  
  
## Vedere anche  
 [Avvio, arresto o sospensione del servizio SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Connessione di diagnostica per gli amministratori di database](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)   
 [Utilità sqlcmd](../../tools/sqlcmd-utility.md)   
 [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  