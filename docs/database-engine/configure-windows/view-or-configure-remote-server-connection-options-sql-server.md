---
title: "Visualizzazione o configurare le opzioni di connessione al server remoto (SQL Server) | Microsoft Docs"
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
  - "server remoti [SQL Server], opzioni di connessione"
  - "server [SQL Server], remoti"
  - "connessioni [SQL Server], server remoti"
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Visualizzazione o configurare le opzioni di connessione al server remoto (SQL Server)
  In questo argomento viene descritto come visualizzare e configurare a livello di server le opzioni di connessione al server remoto in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzazione o configurazione le opzioni di connessione al server remoto utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [dopo la configurazione delle opzioni di connessione al server remoto](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 L'esecuzione di **sp_serveroption** richiede l'autorizzazione ALTER ANY LINKED SERVER nel server.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per visualizzare o configurare le opzioni di connessione al server remoto  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un server, quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo **Proprietà SQL Server - \<***server_name***>** fare clic su **Connessioni**.  
  
3.  Nella pagina **Connessioni** esaminare le impostazioni relative a **Connessioni remote** e, se necessario, modificarle.  
  
4.  Ripetere i passaggi da 1 a 3 nell'altro server della coppia di server remoti.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per visualizzare le opzioni di connessione al server remoto  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene usato [sp_helpserver](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md) per restituire le informazioni su tutti i server remoti.  
  
```tsql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### Per configurare le opzioni di connessione al server remoto  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene illustrato come usare [sp_serveroption](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md) per configurare un server remoto. Nell'esempio viene configurata la compatibilità delle regole di confronto tra un server remoto corrispondente a un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3` e l'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Completamento: dopo la configurazione delle opzioni di connessione al server remoto  
 Per poter rendere effettiva l'impostazione, è necessario arrestare e riavviare il server remoto.  
  
## Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Server remoti](../../database-engine/configure-windows/remote-servers.md)   
 [Server collegati &#40;Motore di database&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)  
  
  