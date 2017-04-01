---
title: "MSSQL_ENG021798 | Microsoft Docs"
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
  - "MSSQL_ENG021798 - errore"
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021798
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21798|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Per continuare è necessario aggiungere il processo agente '%s' tramite '%s'. Vedere la documentazione relativa a '%s'.|  
  
## Spiegazione  
 Per creare una pubblicazione, è necessario essere un membro del **sysadmin** sul server di pubblicazione o un membro del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di pubblicazione. Se si è un membro del **db_owner** ruolo, questo errore viene generato se:  
  
-   Vengono eseguiti script da [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Il modello di sicurezza in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] è cambiato ed è necessario aggiornare questi script.  
  
-   La stored procedure **sp_addpublication** viene eseguita prima dell'esecuzione [sp_addlogreader_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Questo vale per tutte le pubblicazioni transazionali.  
  
-   La stored procedure **sp_addpublication** viene eseguita prima dell'esecuzione [sp_addqreader_agent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Questo vale per le pubblicazioni transazionali abilitate per le sottoscrizioni ad aggiornamento in coda (il valore TRUE per il **@allow_queued_tran** parametro **sp_addpublication**).  
  
 Le stored procedure **sp_addlogreader_agent** e **sp_addqreader_agent** ogni creazione di un processo dell'agente e consentono di specificare il [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di Windows in cui viene eseguito l'agente. Per gli utenti di **sysadmin** ruolo, i processi agente vengono creati implicitamente se **sp_addlogreader_agent** e **sp_addqreader_agent** non vengono eseguite; gli agenti vengono eseguiti nel contesto del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio agente nel server di distribuzione. Anche se **sp_addlogreader_agent** e **sp_addqreader_agent** non sono necessarie per gli utenti di **sysadmin** ruolo, è consigliabile specificare un account separato per gli agenti. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Azione dell'utente  
 Accertarsi di eseguire le procedure nell'ordine corretto. Per altre informazioni, vedere [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md). Se si dispone di script di replica di versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aggiornarli in modo che includano le stored procedure e i parametri richiesti da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Per ulteriori informazioni, vedere [aggiornare gli script di replica & #40; Programmazione Transact-SQL della replica & #41;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  