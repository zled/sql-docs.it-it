---
title: Requisiti del ruolo di sicurezza per la replica | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [SQL Server replication], roles
- roles [SQL Server], replication
ms.assetid: b324a80f-4319-4cb2-847b-1910c49d90e0
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6aa58b21c372c2575e5d152fe56c07a00ae3dfe6
ms.lasthandoff: 04/11/2017

---
# <a name="security-role-requirements-for-replication"></a>Requisiti del ruolo di sicurezza per la replica
  La replica limita le azioni specifiche che un utente può eseguire in base ai ruoli a cui viene eseguito il mapping dell'account di accesso dell'utente. La replica concede determinate autorizzazioni al ruolo predefinito del server **sysadmin** , al ruolo predefinito del database **db_owner** e agli account di accesso presenti nell'elenco di accesso alla pubblicazione.  
  
## <a name="security-role-requirements-for-replication-setup"></a>Requisiti del ruolo di sicurezza per la configurazione della replica  
 Nella tabella seguente vengono descritti i livelli di autenticazione necessari per le normali attività di configurazione della replica:  
  
|Attività di configurazione|Requisito di appartenenza|  
|----------------|----------------------------|  
|Attivazione di un server di distribuzione, un server di pubblicazione o un Sottoscrittore.|Ruolo del server**sysadmin** nel server di pubblicazione.|  
|Attivazione di un database per la replica.|Ruolo del server**sysadmin** nel server di pubblicazione.|  
|Creazione di una pubblicazione.|Ruolo del database**db_owner** nel database di pubblicazione nel server di pubblicazione o ruolo del server **sysadmin** nel server di pubblicazione.|  
|Visualizzazione delle proprietà della pubblicazione.|Membro dell'elenco di accesso alla pubblicazione nel server di pubblicazione, ruolo del database **db_owner** nel database di pubblicazione nel server di pubblicazione o ruolo del server **sysadmin** nel server di pubblicazione.|  
|Creazione di una sottoscrizione.|Ruolo del database**db_owner** nel database di pubblicazione nel server di pubblicazione o ruolo del server **sysadmin** nel server di pubblicazione.<br /><br /> Ruolo del database**db_owner** nel database di sottoscrizione nel Sottoscrittore o ruolo del server **sysadmin** nel Sottoscrittore.|  
|Configurazione dei profili agenti.|Ruolo del server**sysadmin** nel server di distribuzione.|  
  
## <a name="security-role-requirements-for-replication-maintenance"></a>Requisiti del ruolo di sicurezza per la manutenzione della replica  
 Nella tabella seguente vengono descritti i livelli di autenticazione necessari per le normali attività di manutenzione della replica:  
  
|Attività di manutenzione|Requisito di appartenenza|  
|----------------------|----------------------------|  
|Modifica o eliminazione di un server di distribuzione, un server di pubblicazione o un Sottoscrittore.|Ruolo del server**sysadmin** nel server appropriato.|  
|Modifica o eliminazione di una pubblicazione.|Ruolo del database**db_owner** nel database di pubblicazione nel server di pubblicazione o ruolo del server **sysadmin** nel server di pubblicazione.|  
|Modifica o eliminazione di una sottoscrizione nel server di pubblicazione.|Ruolo del database**db_owner** nel database di pubblicazione nel server di pubblicazione o ruolo del server **sysadmin** nel server di pubblicazione.|  
|Modifica o eliminazione di una sottoscrizione nel Sottoscrittore.|Ruolo del database**db_owner** nel database di sottoscrizione nel Sottoscrittore o ruolo del server **sysadmin** nel Sottoscrittore.|  
|Contrassegno di una sottoscrizione per la reinizializzazione.|Sottoscrizione push: ruolo del database **db_owner** nel database di pubblicazione nel server di pubblicazione o ruolo del server **sysadmin** nel server di pubblicazione.<br /><br /> Sottoscrizione pull: ruolo del database **db_owner** nel database di sottoscrizione nel Sottoscrittore o ruolo del server **sysadmin** nel Sottoscrittore.|  
|Visualizzazione dell'attività, degli errori e della cronologia della replica tramite Monitoraggio replica. Un utente può modificare i profili, le pianificazioni o altri elementi degli agenti solo se è membro del ruolo del server **sysadmin** .|Ruolo del database**replmonitor** nel database di distribuzione nel server di distribuzione o ruolo del server **sysadmin** nel server di distribuzione.|  
|Gestione degli agenti di replica.|Ruolo del database**db_owner** nel database appropriato o ruolo del server **sysadmin** nel server appropriato.<br /><br /> Se l'agente è stato creato da un utente nel ruolo **sysadmin** e per l'agente non è stato specificato alcun account proxy, l'agente verrà eseguito nel contesto dell'account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent. In questo caso, un utente nel ruolo **db_owner** non può modificare il processo associato all'agente.|  
|Avvio o arresto di un agente di replica.|Proprietario del processo dell'agente o ruolo del server **sysadmin** nel server appropriato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione &#40;replica&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
