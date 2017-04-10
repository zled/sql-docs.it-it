---
title: "Ruoli applicazione | Microsoft Docs"
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
  - "ruoli applicazione [SQL Server], informazioni sui ruoli applicazione"
  - "entità [SQL Server], ruoli applicazione"
  - "credenziali [SQL Server], ruoli"
  - "ruoli applicazione [SQL Server]"
  - "ruoli [SQL Server], applicazione"
  - "autorizzazioni [SQL Server], ruoli"
  - "utenti [SQL Server], ruoli applicazione"
  - "autenticazione [SQL Server], ruoli"
  - "gruppi [SQL Server], ruoli"
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Ruoli applicazione
  Un ruolo applicazione è un'entità di database che consente a un'applicazione di funzionare con proprie autorizzazioni simili a quelle per utenti. I ruoli applicazione possono essere utilizzati per consentire l'accesso a dati specifici solo agli utenti che si collegano attraverso un'applicazione particolare. A differenza dei ruoli di database, i ruoli applicazione non contengono membri e sono inattivi per impostazione predefinita. I ruoli applicazione funzionano con entrambe le modalità di autenticazione I ruoli applicazione vengono abilitati usando **sp_setapprole**, che richiede una password. Poiché si tratta di entità a livello di database, i ruoli applicazione possono accedere ad altri database solo tramite le autorizzazioni concesse in questi database all'account utente **guest**. Ogni database in cui l'account utente **guest** è stato disabilitato non sarà quindi accessibile ai ruoli applicazione di altri database.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i ruoli applicazione non possono accedere ai metadati a livello di server perché non sono associati a un'entità a livello di server. Per disabilitare questa limitazione e consentire quindi ai ruoli applicazione di accedere ai metadati a livello di server, impostare il flag globale 4616. Per altre informazioni, vedere [Flag di traccia &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md) e [DBCC TRACEON &#40;Transact-SQL&#41;](../../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md).  
  
## Connessione attraverso un ruolo applicazione  
 Il passaggio da un contesto di sicurezza all'altro da parte di un ruolo applicazione si svolge nel modo seguente:  
  
1.  Un utente esegue un'applicazione client.  
  
2.  L'applicazione client si collega a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come utente.  
  
3.  L'applicazione esegue quindi la stored procedure **sp_setapprole** con una password nota solo all'applicazione.  
  
4.  Se il nome del ruolo applicazione e la password sono validi, il ruolo applicazione viene abilitato.  
  
5.  A questo punto la connessione perde le autorizzazioni dell'utente e assume le autorizzazioni del ruolo applicazione.  
  
 Le autorizzazioni acquisite attraverso il ruolo applicazione rimangono valide per tutta la durata della connessione.  
  
 Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'unico modo per un utente di ritornare al contesto di sicurezza originale dopo l'avvio di un ruolo applicazione consiste nel disconnettersi e riconnettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **sp_setapprole** dispone di un'opzione che crea un cookie. Il cookie contiene informazioni di contesto precedenti all'abilitazione del ruolo applicazione. Questo cookie può essere usato da **sp_unsetapprole** per riportare la sessione al contesto originale. Per informazioni su questa nuova opzione e un esempio, vedere [sp_setapprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md).  
  
> [!IMPORTANT]  
>  L'opzione ODBC **encrypt** non è supportata da **SqlClient**. Per trasmettere informazioni riservate su una rete, utilizzare SSL (Secure Sockets Layer) o IPSec per crittografare il canale. Se è necessario mantenere le credenziali nell'applicazione client, crittografarle utilizzando le funzioni Crypto API. In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive, il parametro *password* è archiviato come hash unidirezionale.  
  
## Attività correlate  
  
|||  
|-|-|  
|Creare un ruolo applicazione.|[Creare un ruolo applicazione](../../../relational-databases/security/authentication-access/create-an-application-role.md) e [CREATE APPLICATION ROLE &#40; Transact-SQL &#41;](../../../t-sql/statements/create-application-role-transact-sql.md)|  
|Modificare un ruolo applicazione.|[ALTER APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-application-role-transact-sql.md)|  
|Eliminare un ruolo applicazione.|[DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-application-role-transact-sql.md)|  
|Utilizzo di un ruolo applicazione.|[sp_setapprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)|  
  
## Vedere anche  
 [Sicurezza di SQL Server](../../../relational-databases/security/securing-sql-server.md)  
  
  