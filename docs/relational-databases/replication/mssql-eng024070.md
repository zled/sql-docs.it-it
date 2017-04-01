---
title: "MSSQL_ENG024070 | Microsoft Docs"
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
  - "MSSQL_ENG024070 - errore"
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG024070
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|24070|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Il client non dispone di un privilegio necessario.|  
  
## Spiegazione  
 Questo errore generale può essere generato indipendentemente dal fatto che la replica venga utilizzata o meno. Per un server di una topologia di replica, l'errore viene normalmente generato in seguito alla modifica dell'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tramite Gestione controllo servizi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, anziché tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando si tenta di eseguire un processo di agente dopo aver modificato l'account di servizio, il processo potrebbe avere esito negativo e restituire un messaggio di errore simile al seguente:  
  
 "Eseguito come utente: \< UserAccount>. Sottosistema Snapshot repliche: agente \< AgentName> non riuscita. Eseguito come utente: \< UserAccount>. Il client non dispone di un privilegio necessario. Passaggio non riuscito. [SQLSTATE 42000] (Errore 14151). Passaggio non riuscito."  
  
 Questo problema si verifica perché Gestione controllo servizi di Windows non concede le autorizzazioni necessarie al nuovo account di servizio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## Azione dell'utente  
 Per evitare questo problema in futuro, utilizzare sempre Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anziché Gestione controllo servizi di Windows per modificare gli account di servizio e le password.  
  
 Per risolvere il problema, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ripristinare l'account di servizio originale. Utilizzare quindi Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per modificare il nuovo account. Durante questa operazione, Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aggiunge il nuovo account al gruppo di sicurezza seguente:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 L'appartenenza a questo gruppo di sicurezza consente al nuovo account di ottenere le autorizzazioni necessarie per eseguire il processo dell'agente di replica.  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Gestione degli account di accesso e delle password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  