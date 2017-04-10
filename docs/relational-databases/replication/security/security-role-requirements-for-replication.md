---
title: "Requisiti del ruolo di sicurezza per la replica | Microsoft Docs"
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
  - "sicurezza [replica di SQL Server], ruoli"
  - "ruoli [SQL Server], replica"
ms.assetid: b324a80f-4319-4cb2-847b-1910c49d90e0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Requisiti del ruolo di sicurezza per la replica
  La replica limita le azioni specifiche che un utente può eseguire in base ai ruoli a cui viene eseguito il mapping dell'account di accesso dell'utente. La replica concede determinate autorizzazioni per il **sysadmin** ruolo predefinito del server, il **db_owner** predefinito del database e gli account di accesso nell'elenco di accesso (PAL) alla pubblicazione.  
  
## Requisiti del ruolo di sicurezza per la configurazione della replica  
 Nella tabella seguente vengono descritti i livelli di autenticazione necessari per le normali attività di configurazione della replica:  
  
|Attività di configurazione|Requisito di appartenenza|  
|----------------|----------------------------|  
|Attivazione di un server di distribuzione, un server di pubblicazione o un Sottoscrittore.|**sysadmin** ruolo del server nel server di pubblicazione.|  
|Attivazione di un database per la replica.|**sysadmin** ruolo del server nel server di pubblicazione.|  
|Creazione di una pubblicazione.|**db_owner** ruolo del database nel database di pubblicazione nel server di pubblicazione o **sysadmin** ruolo del server nel server di pubblicazione.|  
|Visualizzazione delle proprietà della pubblicazione.|Membro del ruolo PAL nel server di pubblicazione, **db_owner** ruolo del database nel database di pubblicazione nel server di pubblicazione, o **sysadmin** ruolo del server nel server di pubblicazione.|  
|Creazione di una sottoscrizione.|**db_owner** ruolo del database nel database di pubblicazione nel server di pubblicazione o **sysadmin** ruolo del server nel server di pubblicazione.<br /><br /> **db_owner** ruolo del database nel database di sottoscrizione nel Sottoscrittore o **sysadmin** ruolo del server nel server di sottoscrizione.|  
|Configurazione dei profili agenti.|**sysadmin** ruolo del server nel server di distribuzione.|  
  
## Requisiti del ruolo di sicurezza per la manutenzione della replica  
 Nella tabella seguente vengono descritti i livelli di autenticazione necessari per le normali attività di manutenzione della replica:  
  
|Attività di manutenzione|Requisito di appartenenza|  
|----------------------|----------------------------|  
|Modifica o eliminazione di un server di distribuzione, un server di pubblicazione o un Sottoscrittore.|**sysadmin** ruolo del server sul server appropriato.|  
|Modifica o eliminazione di una pubblicazione.|**db_owner** ruolo del database nel database di pubblicazione nel server di pubblicazione o **sysadmin** ruolo del server nel server di pubblicazione.|  
|Modifica o eliminazione di una sottoscrizione nel server di pubblicazione.|**db_owner** ruolo del database nel database di pubblicazione nel server di pubblicazione o **sysadmin** ruolo del server nel server di pubblicazione.|  
|Modifica o eliminazione di una sottoscrizione nel Sottoscrittore.|**db_owner** ruolo del database nel database di sottoscrizione nel Sottoscrittore o **sysadmin** ruolo del server nel server di sottoscrizione.|  
|Contrassegno di una sottoscrizione per la reinizializzazione.|Sottoscrizione push: **db_owner** ruolo del database nel database di pubblicazione nel server di pubblicazione o **sysadmin** ruolo del server nel server di pubblicazione.<br /><br /> Sottoscrizione pull: **db_owner** ruolo del database nel database di sottoscrizione nel Sottoscrittore o **sysadmin** ruolo del server nel server di sottoscrizione.|  
|Visualizzazione dell'attività, degli errori e della cronologia della replica tramite Monitoraggio replica. Non è possibile modificare i profili degli agenti, le pianificazioni e così via, a meno che l'utente sia membro del **sysadmin** ruolo del server.|**replmonitor** ruolo del database nel database di distribuzione nel server di distribuzione o **sysadmin** ruolo del server nel server di distribuzione.|  
|Gestione degli agenti di replica.|**db_owner** ruolo del database nel database appropriato o **sysadmin** ruolo del server sul server appropriato.<br /><br /> Se l'agente è stato creato da un utente di **sysadmin** ruolo e un account proxy non è stato specificato per l'agente, l'agente viene eseguito nel contesto del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account dell'agente. In questo caso, un utente di **db_owner** non consente di modificare il processo associato all'agente.|  
|Avvio o arresto di un agente di replica.|Proprietario del processo dell'agente o **sysadmin** ruolo del server sul server appropriato.|  
  
## Vedere anche  
 [Procedure consigliate per la sicurezza della replica](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione & #40; Replica & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  