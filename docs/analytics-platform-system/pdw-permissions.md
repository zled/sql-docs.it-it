---
title: Autorizzazioni PDW (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e271980-bec8-424b-9f68-cea11b4e64e8
caps.latest.revision: "23"
ms.openlocfilehash: 49bcb7cf5e8d4bb03acd9db5de87716ec2462191
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="pdw-permissions"></a>Autorizzazioni di PDW
Questo argomento descrive i requisiti e le opzioni per la gestione delle autorizzazioni di database per SQL Server PDW.  
  
## <a name="BackupRestoreBasics"></a>Nozioni fondamentali di autorizzazione motore di database  
Autorizzazioni del motore di database in SQL Server PDW vengono gestite a livello di server tramite gli account di accesso e a livello di database tramite gli utenti del database e i ruoli del database definiti dall'utente.  
  
**Account di accesso**  
Gli account di accesso sono singoli account utente per l'accesso a SQL Server PDW. SQL Server PDW supporta gli account di accesso utilizza l'autenticazione l'autenticazione di Windows e SQL Server.  Accesso con autenticazione di Windows può essere utenti di Windows o i gruppi di Windows di qualsiasi dominio considerato attendibile da SQL Server PDW. Gli account di accesso di autenticazione di SQL Server vengono definiti e autenticato da SQL Server PDW e deve essere creato specificando una password.  
  
I membri del **sysadmin** ruolo predefinito del server (ad esempio il **sa** account di accesso) può connettersi a un database senza che sia mappato a un utente del database. Queste vengono mappate al **dbo** utente. Il proprietario del database viene inoltre eseguito il mapping come il **dbo** utente.  
  
**Ruoli del server**  
Esistono quattro ruoli di server speciale con un set di ruoli preconfigurati che forniscono una serie appropriata di autorizzazioni a livello di server. Il **sysadmin**, **MediumRC**, **LargeRC**, e **XLargeRCfixed** ruoli del server sono ruoli del server solo attualmente implementati in SQL Server PDW. Il **sa** account di accesso è l'unico membro del **sysadmin** Impossibile aggiungere al ruolo predefinito del server e account di accesso aggiuntivi di **sysadmin** ruolo. Gli account di accesso può essere concessa la **CONTROL SERVER** autorizzazione, che è simile, ma non identiche, per il **sysadmin** ruolo predefinito del server. Utilizzare [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) per aggiungere membri ai ruoli del server. SQL Server PDW non supporta i ruoli del server definito dall'utente.  
  
**Utenti del database**  
Gli account di accesso viene concesso a un database mediante la creazione di un utente del database in un database e il mapping di tale utente di database a un account di accesso. In genere, il nome utente di database è identico al nome dell'account di accesso, anche se non è necessario. Ogni utente di database esegue il mapping a un singolo account di accesso. Il mapping di un account di accesso può essere eseguito a un solo utente in un database, ma può essere eseguito come utente di database in diversi database.  
  
**Ruoli predefiniti del Database**  
Ruoli predefiniti del database sono un set di ruoli preconfigurati che forniscono una serie appropriata di autorizzazioni a livello di database. Gli utenti del database e i ruoli del database definito dall'utente possono essere aggiunti ai ruoli predefiniti del database con il [sp_addrolemember](../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) stored procedure. Per ulteriori informazioni sui ruoli predefiniti del database, vedere [ruoli predefiniti del Database predefinito](#fixed-database-roles).  
  
**Ruoli predefiniti del Database definito dall'utente**  
Gli utenti con il **CREATE ROLE** autorizzazione è possibile creare nuovi ruoli del database definito dall'utente per rappresentare i gruppi di utenti con autorizzazioni comuni. In genere, le autorizzazioni vengono concesse o negate per l'intero ruolo, semplificando la gestione e il monitoraggio delle autorizzazioni.  
  
Le autorizzazioni vengono concesse alle entità di sicurezza (account di accesso, utenti e ruoli) con il **GRANT** istruzione. Le autorizzazioni vengono negate in modo esplicito utilizzando il **DENY** comando. Viene rimossa un' precedentemente concessa o negata l'autorizzazione con il **revocare** istruzione. Le autorizzazioni sono cumulative, con l'utente che riceve tutte le autorizzazioni concesse all'utente, all'account di accesso e a qualsiasi appartenenza a un gruppo. Tuttavia, la negazione di un'autorizzazione prevale su tutte le concessioni. <!-- MISSING LINKS (For information, syntax, and available permissions with these commands, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md)).  -->  
  
L'esempio seguente rappresenta un metodo comune e consigliato di configurazione delle autorizzazioni.  
  
1.  Se si utilizza l'autenticazione di Windows, è possibile creare un account di accesso per ogni utente di Windows o un gruppo di Windows che si connetterà a SQL Server PDW. Se si utilizza l'autenticazione di SQL Server, è possibile creare un account di accesso per ogni persona alla quale si connetterà a SQL Server PDW.  
  
2.  Creare un utente del database per ogni account di accesso in tutti i database necessari.  
  
3.  Creare uno o più ruoli del database definito dall'utente, ognuno dei quali rappresenta una funzione simile. ad esempio analista finanziario e analista vendite.  
  
4.  Aggiungere gli utenti del database a uno o più ruoli del database definito dall'utente.  
  
5.  Concedere le autorizzazioni ai ruoli del database definiti dall'utente.  
  
Account di accesso sono oggetti a livello di server e possono essere elencati visualizzando [Sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md). Solo le autorizzazioni a livello di server possono essere concesse a entità server.  
  
Gli utenti e ruoli del database sono oggetti a livello di database e possono essere elencati visualizzando [Sys. database_principals](../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md). Solo possibile concedere autorizzazioni a livello di database a entità di database.  
  
## <a name="BackupTypes"></a>Autorizzazioni predefinite  
L'elenco seguente descrive le autorizzazioni predefinite:  
  
-   Creazione di un account di accesso da using **CREATE LOGIN** istruzione, l'account di accesso riceve il **CONNECT SQL** autorizzazioni consentendo l'account di accesso per connettersi a SQL Server PDW.  
  
-   Quando un utente del database viene creato utilizzando il **CREATE USER** istruzione, l'utente riceve il **CONNECT ON DATABASE::***< database_name >* autorizzazioni, consentendo il account di accesso per connettersi al database come utente.  
  
-   Tutte le entità, tra cui il ruolo PUBLIC, non avere alcuna autorizzazione esplicite o implicite per impostazione predefinita poiché le autorizzazioni implicite vengono ereditate dalle autorizzazioni esplicite. Pertanto, quando non le autorizzazioni esplicite sono presenti, non può anche essere alcuna autorizzazione implicite.  
  
-   Quando un account di accesso diventa il proprietario di un oggetto o un database, l'account di accesso dispone di tutte le autorizzazioni per l'oggetto o un database. Le autorizzazioni di proprietà non sono visibili come le autorizzazioni esplicite. Il **GRANT**, **revocare**, e **DENY** istruzioni non hanno alcun effetto sulle autorizzazioni di proprietà. La proprietà può essere modificata utilizzando il [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md) istruzione.  
  
-   L'account di accesso sa ha tutte le autorizzazioni nel dispositivo. Analogamente alle autorizzazioni di proprietà, le autorizzazioni di amministratore di sistema non possono essere modificate e non sono visibili come le autorizzazioni esplicite. Il **GRANT**, **revocare**, e **DENY** istruzioni non hanno alcun effetto sulle autorizzazioni di amministratore di sistema.  
  
-   Ruolo del server PUBLIC non riceve alcuna autorizzazione per impostazione predefinita e non eredita le autorizzazioni da altri ruoli del server. Ruolo del server PUBLIC è possibile assegnare le autorizzazioni esplicite con le **GRANT**, **revocare**, e **DENY** istruzioni.  
  
-   Le transazioni non richiedono le autorizzazioni. Eseguire tutte le entità di **BEGIN TRANSACTION**, **COMMIT**, e **ROLLBACK** i comandi di transazione. Tuttavia, un'entità deve disporre delle autorizzazioni appropriate per eseguire ogni istruzione all'interno della transazione.  
  
-   Il **utilizzare** istruzione non richiede le autorizzazioni. Possono eseguire tutte le entità di **utilizzare** istruzione in qualsiasi database, ma per accedere a un database hanno un'identità utente nel database o l'utente guest deve essere abilitato.  
  
### <a name="the-public-role"></a>Il ruolo PUBLIC  
Tutti i nuovi account di accesso dispositivo automaticamente appartiene al ruolo PUBLIC. Ruolo del server PUBLIC presenta le caratteristiche seguenti:  
  
-   Ruolo del server PUBLIC non dispone di autorizzazioni per impostazione predefinita.  
  
-   Tutte le entità sono membri del ruolo del server PUBLIC e ruolo del server PUBLIC non è un membro di un altro ruolo di server.  
  
-   Ruolo del server PUBLIC non può ereditare le autorizzazioni implicite. Concedere in modo esplicito le autorizzazioni concesse al ruolo PUBLIC.  
  
## <a name="BackupProc"></a>Determinazione delle autorizzazioni  
O meno un account di accesso dispone dell'autorizzazione per eseguire un'azione specifica dipende dalle autorizzazioni concesse o negate per l'account di accesso, utenti e ruoli che utente è membro. Le autorizzazioni a livello di server (ad esempio **CREATE LOGIN** e **VIEW SERVER STATE**) sono disponibili per l'entità a livello di server (account di accesso). Le autorizzazioni a livello di database (ad esempio **selezionare** da una tabella o **EXECUTE** una stored procedure) sono disponibili per l'entità a livello di database (utenti e ruoli del database).  
  
### <a name="implicit-and-explicit-permissions"></a>Autorizzazioni implicite ed esplicite  
Un *autorizzazione esplicita* è un **GRANT** o **DENY** autorizzazioni concesse a un'entità da un **GRANT** o **DENY**istruzione. Cui sono elencate le autorizzazioni di livello di database di [Sys. database_permissions](../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) visualizzazione. Cui sono elencate le autorizzazioni di livello di server di [server_permissions](../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) visualizzazione.  
  
Un *autorizzazione implicita* è un **GRANT** o **DENY** autorizzazione che ha ereditato un'entità (account di accesso o ruolo server). Un'autorizzazione può essere ereditata nei modi seguenti.  
  
-   Un'entità può ereditare un'autorizzazione da un ruolo se l'entità è un membro del ruolo, anche se l'entità non dispone di un oggetto esplicito **GRANT** o **DENY** autorizzazione.  
  
-   Un'entità può ereditare un'autorizzazione su un oggetto subordinato (ad esempio una tabella), se l'entità dispone di un'autorizzazione su uno degli ambiti padre oggetti (ad esempio lo schema della tabella o l'autorizzazione per l'intero database).  
  
-   Un'entità può ereditare un'autorizzazione con un'autorizzazione che include un'autorizzazione subordinata. Ad esempio il **ALTER ANY USER** autorizzazione include il **CREATE USER** e **ALTER ON USER::**  *<name>*  autorizzazioni.  
  
### <a name="determining-permissions-when-performing-actions"></a>Determinazione delle autorizzazioni per eseguire le azioni  
Il processo di determinazione di autorizzazione da assegnare a un'entità è complesso. La complessità si verifica durante la determinazione di autorizzazioni implicite perché le entità possono essere membri di più ruoli e le autorizzazioni possono essere passate a più livelli nella gerarchia dei ruoli.  
  
L'elenco seguente descrive le regole generali per determinare le autorizzazioni:  
  
-   La proprietà implica l'autorizzazione.  
  
    Proprietario di un oggetto dispone di tutte le autorizzazioni sull'oggetto. Analogamente, un proprietario del database dispone di tutte le autorizzazioni per il database e tutte le autorizzazioni per gli oggetti nel database. Queste autorizzazioni non possono essere modificate.  
  
-   Le autorizzazioni possono essere ereditate attraverso più livelli nella gerarchia di appartenenze al ruolo di server.  
  
    Ad esempio, si supponga la situazione seguente:  
  
    -   David account di accesso è un membro del ruolo del database PerfAnalysts.  
  
    -   PerfAnalysts è un membro del ruolo del database di produzione.  
  
    -   Non dispongono di David e PerfAnalysts **selezionare** autorizzazione per la tabella Customer. L'autorizzazione è stata mai esplicitamente concesso o revocato.  
  
    -   Produzione **selezionare** autorizzazione per la tabella Customer.  
  
    In questo caso, eredita PerfAnalysts **GRANT** erediterà l'autorizzazione per la tabella Customer di produzione e David **GRANT** autorizzazione per la tabella Customer dalla produzione.  
  
-   **DENY** esegue l'override **GRANT** le autorizzazioni sono in conflitto.  
  
    Si supponga ad esempio account di accesso David non dispone di autorizzazioni per la tabella Customer e sia un membro di due ruoli del database: dbgroup1, che ha **DENY** l'autorizzazione per la tabella Customer e dbgroup2, che ha **GRANT** l'autorizzazione per la tabella Customer. In questo caso, David eredita il **DENY** autorizzazione per la tabella Customer. Questo è il caso se i ruoli ha ottenuto le autorizzazioni in modo esplicito o implicito.  
  
### <a name="auditing-permissions"></a>Autorizzazioni di controllo  
Per cercare le autorizzazioni di un utente di controllare le operazioni seguenti.  
  
-   Eseguire la query seguente per determinare gli account di accesso sono amministratori di sistema.  
  
    ```sql  
    SELECT SPLogins.name, 'is a member of ', SPRoles.name   
    FROM sys.server_role_members AS SRM   
    JOIN sys.server_principals AS SPRoles   
        ON SRM.role_principal_id = SPRoles.principal_id   
    JOIN sys.server_principals AS SPLogins   
        ON SRM.member_principal_id = SPLogins.principal_id;  
    ```  
  
-   Eseguire la query seguente per determinare gli account di accesso dispone di autorizzazioni esplicite.  
  
    ```sql  
    SELECT name, 'has the ', state_desc , permission_name, ' permission'  
    FROM sys.server_permissions AS SP  
    JOIN sys.server_principals AS SPRoles   
        ON SP.grantee_principal_id = SPRoles.principal_id;  
    ```  
  
-   Eseguire la query seguente in un database utente per determinare gli utenti di database che sono membri di un ruolo del database.  
  
    ```sql  
    SELECT DPUsers.name, 'is a member of ', DPRoles.name    
    FROM sys.database_role_members AS DRM  
    JOIN sys.database_principals AS DPRoles   
        ON DRM.role_principal_id = DPRoles.principal_id  
    JOIN sys.database_principals AS DPUsers  
        ON DRM.member_principal_id = DPUsers.principal_id;  
    ```  
  
-   Eseguire la query seguente in un database utente per determinare quali utenti e ruoli concessi o negati autorizzazioni specifiche. È necessario visualizzazioni aggiuntive di query, ad esempio Sys. Objects e Schemas per identificare gli elementi descritti, con la major_id.  
  
    ```sql  
    SELECT DPUsers.name, 'has the ', permission_name,   
    'permission on the item described as class = ', class, 'id = ', major_id  
    FROM sys.database_permissions AS DP  
    JOIN sys.database_principals AS DPUsers  
        ON DP.grantee_principal_id = DPUsers.principal_id;  
    ```  
  
## <a name="RestoreProc"></a>Procedure consigliate per le autorizzazioni di database  
  
-   Concedere le autorizzazioni di livello più granulare che possono essere. Concessione delle autorizzazioni nella tabella o le autorizzazioni a livello di visualizzazione può diventare difficile da gestire. Ma concedono autorizzazioni a livello di database potrebbe essere troppo permissiva. Se il database è progettato con gli schemi per definire i limiti di lavoro, ad esempio la concessione di un'autorizzazione per lo schema è un compromesso tra il livello di tabella e il livello di database appropriato.  
  
-   Concedere le autorizzazioni ai ruoli anziché agli utenti o account di accesso. La gestione dei diritti utilizzando i ruoli anziché agli utenti semplifica rapidamente concedere o revocare un set di autorizzazioni per un utente o un account di accesso spostandoli da o verso il ruolo. Quando una funzione passa da un utente a un altro, le autorizzazioni possono rimangono invariate a livello di ruolo durante le modifiche di appartenenza al ruolo.  
  
-   Concedere autorizzazioni ai ruoli in base alle funzionalità e ruoli dei gruppi di livello superiore che consentono di combinare i ruoli di funzione di processo in base al gruppo di società eseguendo le azioni.  
  
-   Ogni utente finale deve avere un account di accesso univoco. Non consentire agli utenti di condividere gli account di accesso. Fornire un account di accesso per ogni utente garantisce un audit trail e semplifica la gestione delle autorizzazioni.  
  
## <a name="fixed-database-roles"></a>Ruoli predefiniti del database
SQL Server fornisce ruoli a livello di database (predefiniti) preconfigurati che consentono di gestire le autorizzazioni su un server. I ruoli configurati in precedenza vengono corretti in quanto non è possibile modificare le autorizzazioni assegnate. Inoltre è possibile creare ruoli del database definito dall'utente. È possibile modificare le autorizzazioni assegnate ai ruoli del database definito dall'utente.  
  
I ruoli sono entità di sicurezza che raggruppano altre entità. Ruoli del database sono a livello di database nel proprio ambito di autorizzazioni. Gli utenti del database e altri ruoli del database possono essere aggiunti come membri dei ruoli del database. Impossibile aggiungere i ruoli predefiniti del database a altro. I*ruoli* equivalgono ai *gruppi* nel sistema operativo Windows.  
  
Esistono 9 ruoli predefiniti del database.  
  
-   **db_owner**  
  
-   **db_securityadmin**  
  
-   **db_accessadmin**  
  
-   **db_backupoperator**  
  
-   **db_ddladmin**  
  
-   **db_datawriter**  
  
-   **db_datareader**  
  
-   **db_denydatawriter**  
  
-   **db_denydatareader**  
  
### <a name="permissions-of-the-fixed-database-roles"></a>Autorizzazioni dei ruoli predefiniti del Database  
Il sistema di ruoli predefiniti del server e ruoli predefiniti del database è un sistema legacy ha avuto origine in anni ' 80. Ruoli predefiniti sono ancora supportati e sono utili in ambienti in cui sono presenti alcuni utenti e alle esigenze di sicurezza sono semplici. A partire da SQL Server 2005, è stato creato un sistema di concessione dell'autorizzazione per più dettagliato. Questo nuovo sistema è più granulare, che fornisce molte altre opzioni per la concessione e negazione di autorizzazioni. La complessità del sistema più granulare aggiuntiva rende più difficile per ulteriori informazioni, ma la maggior parte dei sistemi aziendali devono concedere le autorizzazioni anziché utilizzare i ruoli predefiniti. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md). -->Il grafico seguente sono indicate le autorizzazioni associate a ogni ruolo predefinito del database. Tutte le autorizzazioni in questa immagine di SQL Server non sono disponibili (o necessario) nei punti di accesso.  
  
![Ruoli predefiniti del database per la sicurezza APS](./media/pdw-permissions/APS_security_fixed_db_roles.png "APS_security_fixed_db_roles")  
  
### <a name="related-content"></a>Contenuto correlato  
  
-   Per creare i ruoli definiti dall'utente, vedere [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md).  
  
  
## <a name="fixed-server-roles"></a>Ruoli predefiniti del server
Ruoli predefiniti del server vengono creati automaticamente da SQL Server. SQL Server PDW è un'implementazione limitata di ruoli predefiniti del server di SQL Server. Solo il **sysadmin** e **pubblica** presenti account di accesso utente come membri. Il **setupadmin** e **dbcreator** vengono utilizzati internamente da SQL Server PDW. Membri aggiuntivi non possono essere aggiunti o rimossi da alcun ruolo.  
  
### <a name="sysadmin-fixed-server-role"></a>sysadmin ruolo Server predefinito  
I membri del ruolo predefinito del server **sysadmin** possono eseguire qualsiasi attività nel server. Il **sa** account di accesso è l'unico membro del **sysadmin** ruolo predefinito del server. Non è possibile aggiungere account di accesso aggiuntivi per il **sysadmin** ruolo predefinito del server. Concessione di **CONTROL SERVER** autorizzazione è all'incirca l'appartenenza al **sysadmin** ruolo predefinito del server. Nell'esempio seguente viene concessa la **CONTROL SERVER** dell'autorizzazione per un account di accesso denominato Fay.  
  
```sql  
USE master;  
GO  
GRANT CONTROL SERVER TO Fay;  
```  
  
> [!IMPORTANT]  
> Il **CONTROL SERVER** autorizzazione fornisce controllo quasi completato di SQL Server PDW. Quando possibile, è possibile fornire più granulare delle autorizzazioni per gli account di accesso. Si consideri ad esempio la concessione di **VIEW SERVER STATE**, **ALTER ANY LOGIN**, **VIEW ANY DATABASE**, o **CREATE ANY DATABASE** autorizzazioni.  
  
### <a name="public-server-role"></a>Ruolo Server Public  
Ogni account di accesso che possono connettersi a SQL Server PDW è membro il **pubblica** ruolo del server. Tutti gli accessi ereditano le autorizzazioni concesse a **pubblica** su qualsiasi oggetto. È possibile assegnare solo **pubblica** autorizzazioni per un oggetto quando si desidera che l'oggetto sia disponibile per tutti gli utenti. Non è possibile modificare l'appartenenza di **pubblica** ruolo.  
  
> [!NOTE]  
> **Pubblica** viene implementato in modo diverso rispetto agli altri ruoli. Poiché tutte le entità server sono membri del ruolo public, l'appartenenza del **pubblica** ruolo non è elencato nel **server_role_members** DMV.  
  
### <a name="fixed-server-roles-vs-granting-permissions"></a>Vs i ruoli del Server predefinito. Concessione di autorizzazioni  
Il sistema di ruoli predefiniti del server e ruoli predefiniti del database è un sistema legacy ha avuto origine in anni ' 80. Ruoli predefiniti sono ancora supportati e sono utili in ambienti in cui sono presenti alcuni utenti e alle esigenze di sicurezza sono semplici. A partire da SQL Server 2005, è stato creato un sistema di concessione dell'autorizzazione per più dettagliato. Questo nuovo sistema è più granulare, che fornisce molte altre opzioni per la concessione e negazione di autorizzazioni. La complessità del sistema più granulare aggiuntiva rende più difficile per ulteriori informazioni, ma la maggior parte dei sistemi aziendali devono concedere le autorizzazioni anziché utilizzare i ruoli predefiniti. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  -->  
  
## <a name="related-topics"></a>Argomenti correlati  
  
- [Concedere autorizzazioni](grant-permissions.md)

<!-- MISSING LINKS
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->

