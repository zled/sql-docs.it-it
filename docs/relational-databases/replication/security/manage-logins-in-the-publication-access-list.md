---
title: "Gestione degli account nell&#39;elenco di accesso alla pubblicazione | Microsoft Docs"
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
  - "logins [SQL Server replication], publication access list"
  - "publications [SQL Server replication], publication access lists"
  - "publication access list (PAL)"
  - "PAL (publication access list)"
  - "accessi [replica di SQL Server], gestione"
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Gestione degli account nell&#39;elenco di accesso alla pubblicazione
  In questo argomento si illustra come gestire gli account di accesso nell'elenco di accesso alla pubblicazione in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. L'accesso a una pubblicazione viene controllato tramite l'elenco di accesso alla pubblicazione. Accessi e gruppi possono essere aggiunti e rimossi dell'elenco di accesso alla pubblicazione.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
-   **Per gestire gli account di accesso nell'elenco di accesso alla pubblicazione, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   Prima di aggiungere l'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] all'elenco di accesso alla pubblicazione, è necessario associarlo a un utente di database nel database di pubblicazione.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Scegliere l'elenco di accesso (PAL) il **elenco accesso pubblicazione** pagina del **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo per gestire gli account di accesso. Per ulteriori informazioni su come accedere a questa finestra di dialogo, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per gestire gli account nell'elenco di accesso alla pubblicazione  
  
1.  Nel **elenco accesso pubblicazione** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, utilizzare il **Aggiungi**, **rimuovere**, e **Rimuovi tutto** pulsanti per aggiungere e rimuovere gli account di accesso e i gruppi da tale elenco. Non rimuovere **distributor_admin** da tale elenco. Questo account è usato dalla replica.  
  
    > [!NOTE]  
    >  Se si usano un server di distribuzione remoto, gli account nell'elenco di accesso alla pubblicazione devono essere disponibili sia nel server di pubblicazione che nel server di distribuzione. L'account deve essere un account di dominio o un account locale definito in entrambi i server. Le password associate a entrambi gli account di accesso devono essere identiche.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per visualizzare gruppi e account di accesso che appartengono all'elenco di accesso alla pubblicazione  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_help_publication_access](../../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md). Per **@publication**, specificare il nome della pubblicazione. Verranno visualizzate informazioni sui gruppi e gli account di accesso presenti nell'elenco di accesso alla pubblicazione.  
  
#### Per aggiungere gruppi e account di accesso all'elenco di accesso alla pubblicazione  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_grant_publication_access](../../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md). Per **@publication**, specificare il nome della pubblicazione e per **@login**il nome dell'account di accesso o del gruppo da aggiungere.  
  
#### Per rimuovere gruppi e account di accesso dall'elenco di accesso alla pubblicazione  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_revoke_publication_access](../../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md). Per **@publication**, specificare il nome della pubblicazione e per **@login**il nome dell'account di accesso o del gruppo da rimuovere.  
  
## Vedere anche  
 [Manage Logins in the Publication Access List](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)   
 [Modello di sicurezza dell'agente di replica](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Protezione di una topologia di replica](../../../relational-databases/replication/security/secure-a-replication-topology.md)   
 [Sicurezza del server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  