---
title: "Entit&#224; (Motore di database) | Microsoft Docs"
ms.custom: ""
ms.date: "01/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.roleproperties.selectroll.f1"
  - "sql13.swb.databaseuser.permissions.user.f1--May use common.permissions"
helpviewer_keywords: 
  - "certificati [SQL Server], entità"
  - "ruoli [SQL Server], entità"
  - "autorizzazioni [SQL Server], entità"
  - "##MS_SQLAuthenticatorCertificate##"
  - "entità [SQL Server]"
  - "##MS_SQLResourceSigningCertificate##"
  - "gruppi [SQL Server], entità"
  - "##MS_AgentSigningCertificate##"
  - "autenticazione [SQL Server], entità"
  - "schemi [SQL Server], entità"
  - "entità [SQL Server], informazioni sulle entità"
  - "sicurezza [SQL Server], entità"
  - "utenti [SQL Server], entità"
  - "##MS_SQLReplicationSigningCertificate##"
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
caps.latest.revision: 57
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# Entit&#224; (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  Le *entità* possono richiedere risorse di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Analogamente ad altri componenti del modello di autorizzazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le entità possono essere organizzate in una gerarchia. Il campo di influenza di un'entità dipende dall'ambito della definizione dell'entità (Windows, server o database) e dal tipo di entità (indivisibile o raccolta). Un account di accesso di Windows è un esempio di entità indivisibile mentre un gruppo di Windows è un esempio di entità costituita da una raccolta. Ogni entità dispone di un ID di sicurezza (SID).  
  
 **Entità a livello di Windows**  
  
-   Account di dominio di Windows  
  
-   Account di accesso locale di Windows  
  
 **Entità**-** a livello di** **SQL Server**  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Account di accesso  
  
-   Ruolo del server  
  
 **Entità a livello di database**  
  
-   Utente di database  
  
-   Ruolo del database  
  
-   Ruolo applicazione  
  
## Account di accesso sa di SQL Server  
 L'account di accesso sa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è un'entità a livello di server. Per impostazione predefinita, questo account viene creato durante l'installazione di un'istanza. A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], il database predefinito di sa è il database master. diversamente da quanto consentito nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## Ruolo di database public  
 Ogni utente di database appartiene al ruolo di database public. Quando a un utente non sono state concesse o negate autorizzazioni specifiche per un'entità a protezione diretta, l'utente eredita le autorizzazioni concesse al ruolo public su tale entità a protezione diretta.  
  
## INFORMATION_SCHEMA e sys  
 Ogni database comprende due entità che appaiono come utenti in viste di catalogo: INFORMATION_SCHEMA e sys. Queste entità sono richieste da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], e non posso essere modificate o eliminate.  
  
## Account di accesso basati su certificati di SQL Server  
 Le entità del server i cui nomi sono racchiusi tra due simboli di cancelletto (##) sono solo per uso interno di sistema. Al momento dell'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono create le seguenti entità che non devono essere eliminate.  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## L'utente Guest  
 Ogni database include un **guest**. Le autorizzazioni garantite all'utente **guest** sono ereditate dagli utenti che hanno accesso al database ma non dispongono di un account utente nel database. Non è possibile eliminare l'utente **guest**, ma è possibile disabilitarlo revocando la relativa autorizzazione **CONNECT**. L'autorizzazione **CONNECT** può essere richiamata eseguendo `REVOKE CONNECT FROM GUEST` all'interno di qualsiasi database diverso da master o tempdb.  
  
## Client e server di database  
 Per definizione, un client e un server di database sono entità di sicurezza e possono essere protetti. È possibile autenticare queste entità mutuamente prima che sia stabilita una connessione di rete sicura. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta il protocollo di autenticazione [Kerberos](http://go.microsoft.com/fwlink/?LinkId=100758) che definisce la modalità con la quale i client interagiscono con un servizio di autenticazione di rete.  
  
## Attività correlate  
 Per informazioni sulla progettazione di un sistema di autorizzazioni, vedere [Introduzione alle autorizzazioni del motore di database](../../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
 In questa sezione della documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], sono inclusi i seguenti argomenti:  
  
-   [Procedure per la gestione di account di accesso, utenti e schemi](../../../relational-databases/security/authentication-access/managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [Ruoli a livello di server](../../../relational-databases/security/authentication-access/server-level-roles.md)  
  
-   [Ruoli a livello di database](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
-   [Ruoli applicazione](../../../relational-databases/security/authentication-access/application-roles.md)  
  
## Vedere anche  
 [Sicurezza di SQL Server](../../../relational-databases/security/securing-sql-server.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.sql_logins &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [Ruoli a livello di server](../../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Ruoli a livello di database](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  