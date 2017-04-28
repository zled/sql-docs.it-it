---
title: "Entità a protezione diretta | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 51db5d7a36569601e7d21d5fc50d16230b85ea5d
ms.lasthandoff: 04/11/2017

---
# <a name="securables"></a>Entità a protezione diretta
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Le entità a protezione diretta sono le risorse il cui accesso è controllato dal sistema di autorizzazioni del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Ad esempio, una tabella è un'entità a protezione diretta. Alcune entità a protezione diretta possono essere contenute da altre, creando gerarchie nidificate denominate ambiti, che possono a loro volta essere protetti. Gli ambiti a protezione diretta sono **server**, **database**e **schema**.  
  
## <a name="securable-scope-server"></a>Ambito a protezione diretta: server  
 L'ambito a protezione diretta **server** contiene le entità a protezione diretta seguenti:  
  
-   Gruppo di disponibilità  
  
-   Endpoint  
  
-   Account di accesso  
  
-   Ruolo del server  
  
-   database  
  
## <a name="securable-scope-database"></a>Ambito a protezione diretta: database  
 L'ambito a protezione diretta **database** contiene le entità a protezione diretta seguenti:  
  
-   Ruolo applicazione  
  
-   Assembly  
  
-   Chiave asimmetrica  
  
-   Certificato  
  
-   Contratto  
  
-   Catalogo full-text  
  
-   Elenco di parole non significative full-text  
  
-   Tipo di messaggio  
  
-   Associazione al servizio remoto  
  
-   Ruolo (database)  
  
-   Route  
  
-   schema  
  
-   Elenco delle proprietà di ricerca  
  
-   Servizio  
  
-   Chiave simmetrica  
  
-   Utente  
  
## <a name="securable-scope-schema"></a>Ambito a protezione diretta: schema  
 L'ambito a protezione diretta **schema** contiene le entità a protezione diretta seguenti:  
  
-   Tipo  
  
-   Raccolta di XML Schema  
  
-   Oggetto. La classe oggetto include i membri seguenti:  
  
    -   Aggregate  
  
    -   Funzione  
  
    -   Procedura  
  
    -   Coda  
  
    -   Sinonimo  
  
    -   Tabella  
  
    -   Vista 
    
    -   Tabella esterna 
  
## <a name="controlling-access-to-a-securable"></a>Controllo di accesso a un'entità a protezione diretta  
 L'entità che riceve autorizzazione per un'entità a protezione diretta viene chiamata entità. Le entità più comuni sono gli account di accesso e gli utenti di database. L'accesso alle entità a protezione diretta viene controllato concedendo o negando autorizzazioni o aggiungendo accessi e utenti a ruoli che dispongono di accesso. Per informazioni sul controllo delle autorizzazioni, vedere [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md), [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md), [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md), [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) e [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md).  
  
> [!CAUTION]  
>  Le autorizzazioni predefinite concesso a oggetti di sistema durante l'installazione vengono valutati attentamente per individuare possibili minacce e non è quindi necessario modificarli per implementare misure di protezione avanzata dell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Eventuali modifiche alle autorizzazioni per gli oggetti di sistema possono limitare o compromettere la funzionalità e potrebbero lasciare l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uno stato non supportato.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
 [Sicurezza di SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
 [sys.server_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
 [sys.sql_logins &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)  
  
  

