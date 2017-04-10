---
title: "MSSQL_ENG020596 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG020596 - errore"
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG020596
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20596|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|L'agente anonimo può essere eliminato solo da '%s' e dai membri del ruolo db_owner.|  
  
## Spiegazione  
 Non si dispone di autorizzazioni sufficienti per eliminare l'agente della sottoscrizione anonima. L'account di accesso utilizzato durante la chiamata [sp_dropanonymousagent & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) deve essere un membro del **sysadmin** ruolo predefinito del server nel server di distribuzione o **db_owner** ruolo predefinito del database nel database di distribuzione o l'utente deve essere quella che ha avviato la prima esecuzione dell'agente.  
  
## Azione dell'utente  
 Account di accesso con le credenziali appropriate ed eseguire **sp_dropanonymousagent**.  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  