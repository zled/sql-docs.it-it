---
title: "MSSQL_ENG014152 | Microsoft Docs"
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
  - "MSSQL_ENG014152 - errore"
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014152
    
## Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14152|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Replica-%s: ripetizione dell'esecuzione dell'agente %s pianificata. %s|  
  
## Spiegazione  
 L'agente di replica specificato è stato pianificato in modo da tentare nuovamente l'esecuzione dell'operazione richiesta. Verranno eseguiti nuovi tentativi finché non verrà raggiunto il numero massimo di tentativi configurato per il passaggio del processo.  
  
 Viene in genere eseguito un nuovo tentativo per i motivi seguenti:  
  
-   Il **QueryTimeout** viene superato il valore.  
  
-   Il **LoginTimeout** viene superato il valore.  
  
-   Il processo di replica è stato scelto come vittima del deadlock.  
  
## Azione dell'utente  
 Se il messaggio relativo a nuovi tentativi non viene visualizzato di frequente, non è richiesto nessun intervento da parte dell'utente.  
  
 Utilizzare [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) per visualizzare l'impostazione corrente per il numero massimo di volte in cui il **eseguire agente** passaggio per l'agente di replica specificato. È possibile utilizzare il **@retry_attempts** parametro il [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) stored procedure per modificare il numero di tentativi di un passaggio di processo.  
  
 Se il messaggio relativo a nuovi tentativi viene visualizzato di frequente, risolvere il problema in base al messaggio che causa l'esecuzione di nuovi tentativi. Verificare nella cronologia dell'agente la presenza di messaggi che indicano il motivo per cui è stato necessario pianificare il nuovo tentativo. In alcuni casi potrebbe essere necessario attivare un livello di registrazione più dettagliato per l'agente di replica. Per ulteriori informazioni su come configurare la registrazione per la replica, vedere l'articolo della Microsoft Knowledge Base [312292](http://support.microsoft.com/kb/312292).  
  
## Vedere anche  
 [Errori e gli eventi riferimento & #40; Replica & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  