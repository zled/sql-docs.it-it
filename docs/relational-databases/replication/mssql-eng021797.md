---
title: "MSSQL_ENG021797 | Microsoft Docs"
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
  - "MSSQL_ENG021797 - errore"
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG021797
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21797|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|'%s' deve essere un account di accesso di Windows valido nel formato: 'COMPUTER\Account di accesso' o 'DOMINIO\Account di accesso'. Vedere la documentazione relativa a '%s'.|  
  
## Spiegazione  
 Questo errore viene generato dal seguente stored procedure di replica se il valore specificato per il **@job_login** parametro è null o non valido. Questo errore può verificarsi se un membro del **db_owner** ruolo predefinito del database esegue gli script da versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il modello di sicurezza in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] è cambiato ed è necessario aggiornare questi script.  
  
-   [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
-   [sp_addqreader_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
-   [sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
-   [sp_addpushsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)  
  
-   [sp_addpullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepushsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepullsubscription_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)  
  
 Queste stored procedure possono essere eseguite da un membro del **sysadmin** sul server appropriato o un membro del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database appropriato. Ogni stored procedure crea un processo agente e consente di specificare l'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows in base al quale viene eseguito l'agente. Per gli utenti di **sysadmin** ruolo, i processi agente vengono creati implicitamente anche se non viene specificato un account di Windows (se viene specificato un account, deve essere valido); gli agenti vengono eseguiti nel contesto del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di servizio dell'agente al server appropriato. Sebbene l'account non sia necessario, la procedura consigliata prevede di specificare un account separato per gli agenti. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Azione dell'utente  
 Assicurarsi specificare un account Windows valido per il **@job_login** parametro di ogni procedura. Se si dispone di script di replica di versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aggiornarli in modo che includano le stored procedure e i parametri necessari per [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Per ulteriori informazioni, vedere [aggiornare gli script di replica & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  