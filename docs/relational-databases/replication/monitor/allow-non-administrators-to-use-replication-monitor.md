---
title: "Autorizzazione di utenti non amministratori all&#39;utilizzo di Monitoraggio replica | Microsoft Docs"
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
  - "Monitoraggio replica, accesso a utenti non amministratori"
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Autorizzazione di utenti non amministratori all&#39;utilizzo di Monitoraggio replica
  In questo argomento viene descritto come consentire agli utenti non amministratore di utilizzare Monitoraggio replica in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Monitoraggio replica può essere utilizzato da membri che appartengono ai ruoli seguenti:  
  
-   Il ruolo predefinito del server **sysadmin** .  
  
     Questi utenti possono monitorare la replica e avere il controllo completo sulla modifica delle proprietà di replica, ad esempio le pianificazioni degli agenti, i profili agente e così via.  
  
-   Il ruolo di database **replmonitor** nel database di distribuzione.  
  
     Questi utenti possono monitorare la replica, ma non possono modificare le proprietà di replica.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per consentire a utenti non amministratori di utilizzare Monitoraggio replica tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per consentire a utenti non amministratori di utilizzare Monitoraggio replica, un membro del **sysadmin** ruolo predefinito del server è necessario aggiungere l'utente al database di distribuzione e assegnare all'utente il **replmonitor** ruolo.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per consentire a utenti non amministratori di utilizzare Monitoraggio replica  
  
1.  Connettersi al database di distribuzione in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere **database**, espandere **database di sistema**, quindi espandere il database di distribuzione (denominato **distribuzione** per impostazione predefinita).  
  
3.  Espandere **sicurezza**, fare doppio clic su **utenti**, quindi fare clic su **nuovo utente**.  
  
4.  Immettere un nome utente e un account di accesso per l'utente.  
  
5.  Selezionare uno schema predefinito di **replmonitor**.  
  
6.  Selezionare la casella di controllo **replmonitor** nella griglia **Appartenenza a ruoli del database** .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per aggiungere un utente al ruolo predefinito del database replmonitor  
  
1.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_helpuser & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md). Se l'utente non è elencato **UserName** nel set di risultati, l'utente deve essere concesso l'accesso al database di distribuzione mediante il [CREATE USER & #40; Transact-SQL & #41;](../../../t-sql/statements/create-user-transact-sql.md) istruzione.  
  
2.  Nel server di distribuzione nel database di distribuzione, eseguire [sp_helprolemember & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md), specificando il valore **replmonitor** per il **@rolename** parametro. Se l'utente è elencato in **MemberName** nel set di risultati, appartiene già al ruolo.  
  
3.  Se l'utente non appartiene al **replmonitor** ruolo, eseguire [sp_addrolemember & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) nel server di distribuzione nel database di distribuzione. Specificare il valore **replmonitor** per **@rolename** e il nome dell'utente del database o l'account di accesso di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows aggiunto per **@membername**.  
  
#### Per rimuovere un utente dal ruolo predefinito del database replmonitor  
  
1.  Per verificare che l'utente appartiene il **replmonitor** ruolo, eseguire [sp_helprolemember & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) nel server di distribuzione nel database di distribuzione e specificare un valore di **replmonitor** per **@rolename**. Se l'utente non è elencato nel set di risultati di **MemberName** , attualmente non appartiene al ruolo.  
  
2.  Se l'utente appartiene al **replmonitor** ruolo, eseguire [sp_droprolemember & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) nel server di distribuzione nel database di distribuzione. Specificare il valore **replmonitor** per **@rolename** e il nome dell'utente del database o l'account di accesso di Windows rimosso per **@membername**.  
  
  