---
title: Concedi autorizzazioni
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.openlocfilehash: 35542a9ea2544f0bdd357d3609937e1596e00a3f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="grant-permissions"></a>Concedi autorizzazioni

## <a name="grant-permissions-to-submit-database-queries"></a>Concedere le autorizzazioni per inviare le query di Database
In questa sezione viene descritto come concedere autorizzazioni ai ruoli del database e agli utenti di eseguire query sui dati nel dispositivo di SQL Server PDW.  
  
Le istruzioni utilizzate per concedere le autorizzazioni per eseguire query sui dati dipendono dall'ambito di accesso desiderato. Le istruzioni SQL seguenti creano un account di accesso denominato KimAbercrombie in grado di accedere al dispositivo, creare un utente di database denominato KimAbercrombie nel **AdventureWorksPDW2012** database, creare un ruolo del database denominato PDWQueryData aggiunge l'utilizzo KimAbercrombie ruolo PDWQueryData e opzioni di visualizzazione per la concessione dell'accesso a query, in base se l'accesso viene consentito a livello di database, o di oggetto.  
  
```sql  
USE master;  
GO  
  
CREATE LOGIN KimAbercrombie WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
USE AdventureWorksPDW2012;  
GO  
  
CREATE USER KimAbercrombie;  
GO  
  
CREATE ROLE PDWQueryData;  
GO  
  
EXEC sp_addrolemember 'PDWQueryData', 'KimAbercrombie'  
GO  
  
-- If the permission is granted against a table or view only, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO PDWQueryData;  
GO  
  
-- If the permission is granted for the database, use this syntax:  
GRANT SELECT ON DATABASE::AdventureWorksPDW2012 TO PDWQueryData;  
GO  
  
-- If KimAbercrombie is the only user that needs to access a table, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO KimAbercrombie;  
GO  
```  
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Concedere le autorizzazioni per utilizzare la Console di amministrazione
In questa sezione viene descritto come concedere autorizzazioni agli account di accesso per utilizzare la Console di amministrazione.  
  
**Utilizzare la Console di amministrazione**  
  
Utilizzare la Console di amministrazione di un account di accesso richiede il livello di server **VIEW SERVER STATE** autorizzazione. L'istruzione SQL seguente concede il **VIEW SERVER STATE** dell'autorizzazione per l'account di accesso `KimAbercrombie` Kim è possibile utilizzare la Console di amministrazione per il monitoraggio del dispositivo di SQL Server PDW.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Terminare le sessioni**  
  
Per concedere l'autorizzazione per terminare le sessioni di un account di accesso, concedere il **l'autorizzazione ALTER ANY CONNECTION** autorizzazione come indicato di seguito:  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Concedere le autorizzazioni per caricare i dati
In questa sezione viene descritto come concedere le autorizzazioni per gli utenti del database e i ruoli di database per caricare i dati nella PDWappliance di SQL Server.  
  
Nel seguente script vengono visualizzati le autorizzazioni necessarie per ogni opzione di caricamento. È possibile modificare per soddisfare esigenze specifiche.  
  
```sql  
-- Create server login for the examples that follow.  
USE master;  
CREATE LOGIN BI_ETLUser WITH PASSWORD = '******';  
  
--Grant BULK Load permissions   
GRANT ADMINISTER BULK OPERATIONS TO BI_ETLUser;  
  
--Grant Staging database permissions  
USE stagedb;  
CREATE USER BI_ETLUser for login BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
EXEC sp_addrolemember 'db_ddladmin','BI_ETLUser';  
  
-- The CREATE TABLE permission is required for the database hosting the temporary table.  
-- This may be the staging database (if specified) or destination database.   
-- The CREATE permission is not required if loading in fastappend mode.  
GRANT CREATE TABLE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in append or fastappend mode, the INSERT permission is required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
  
-- If loading in reload mode, the INSERT and DELETE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT DELETE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in upsert mode, the INSERT and UPDATE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT UPDATE ON database::stagedb TO BI_ETLUser;  
  
-- Destination DB  
USE tpch_1gb;  
CREATE USER BI_ETLUser FOR LOGIN BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
```  
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Concedere le autorizzazioni per copiare dati dal dispositivo
In questa sezione viene descritto come concedere le autorizzazioni per un utente o ruolo del database per copiare dati dal dispositivo di SQL Server PDW.  
  
Per spostare i dati in un'altra posizione, è necessario **selezionare** autorizzazione per la tabella che contiene i dati da spostare.  
  
Se la destinazione per i dati è un altro SQL Server PDW, l'utente deve disporre **CREATE TABLE** autorizzazione nella destinazione e **ALTER SCHEMA** autorizzazione per lo schema che conterrà la tabella.  
  
## <a name="grant-permissions-to-manage-databases"></a>Concedere le autorizzazioni per gestire i database
In questa sezione viene descritto come concedere autorizzazioni a un utente del database per gestire un database dell'accessorio di SQL Server PDW.  
  
In alcuni casi, una società assegna un gestore per un database. Il gestore controlla l'accesso di altri account di accesso per il database, nonché i dati e oggetti nel database. Per gestire tutti gli oggetti, ruoli e utenti in un database di concedono all'utente di **controllo** autorizzazione per il database. L'istruzione seguente concede il **controllo** l'autorizzazione per la **AdventureWorksPDW2012** database all'utente `KimAbercrombie`.  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Per concedere a un utente l'autorizzazione per controllare tutti i database nel dispositivo, concedere il **ALTER ANY DATABASE** autorizzazione nel database master.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Concedere le autorizzazioni per gestire gli account di accesso, utenti e ruoli del Database
In questa sezione viene descritto come concedere le autorizzazioni per gestire gli account di accesso, gli utenti del database e i ruoli del database.  
  
### <a name="PermsAdminConsole"></a>Concedere le autorizzazioni per gestire gli account di accesso  
**Aggiungere o gestire gli account di accesso**  
  
Le istruzioni SQL seguenti creano un account di accesso denominato KimAbercrombie che è possibile creare nuovi account di accesso tramite il [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) istruzione e modificare l'account di accesso esistenti tramite il [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) istruzione.  
  
Il **ALTER ANY LOGIN** autorizzazione concede la possibilità di creare nuovi account di accesso ed eliminare esistente. Una volta creato un account di accesso, l'account di accesso possono essere gestiti dagli account di accesso con il **ALTER ANY LOGIN** autorizzazione o **ALTER** autorizzazione tale account di accesso. Un account di accesso è possibile modificare il database predefinito e password per il proprio account di accesso.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Concedere le autorizzazioni per gestire sessioni di accesso  
Per avere la possibilità di visualizzare tutte le sessioni nel server, è necessario il **VIEW SERVER STATE** autorizzazione. Per terminare le sessioni di altri account di accesso, è necessario il **l'autorizzazione ALTER ANY CONNECTION** autorizzazione. L'esempio seguente usa il `KimAbercrombie` account di accesso creato in precedenza.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Concedere l'autorizzazione per gestire gli utenti del Database  
Creazione ed eliminazione di utenti del database richiede la **ALTER ANY USER** autorizzazione. La gestione di utenti esistenti richiede la **ALTER ANY USER** autorizzazione o **ALTER** dell'autorizzazione per tale utente. L'esempio seguente usa il `KimAbercrombie` account di accesso creato in precedenza.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Concedere l'autorizzazione per accedere per gestire i ruoli di Database  
Creare ed eliminare i ruoli del database definito dall'utente richiede la **ALTER ANY ROLE** autorizzazione. L'esempio seguente usa il `KimAbercrombie` account di accesso e utilizzo creato in precedenza.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Account di accesso, utenti e i grafici di autorizzazione ruolo  
I grafici seguenti possono generare confusione, ma devono essere visualizzate autorizzazioni di livello superiore come, ad esempio, includere le autorizzazioni più granulari che possono essere concesse separatamente (ad esempio ALTER). È consigliabile concedere sempre il numero minimo di autorizzazioni per un utente completare le attività necessarie. A tale scopo, concedere le autorizzazioni più specifiche, anziché le autorizzazioni di livello superiore.  
  
**Autorizzazioni di accesso:**  
  
![Le autorizzazioni di accesso di sicurezza APS](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Autorizzazioni utente:**  
  
![Autorizzazioni utente di sicurezza APS](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Autorizzazioni del ruolo:**  
  
![Autorizzazioni ruolo di sicurezza APS](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Concedere le autorizzazioni per il monitoraggio del dispositivo
Lo strumento di SQL Server PDW può essere monitorato da utilizzo delle viste di sistema della Console di amministrazione o di SQL Server PDW. Gli account di accesso richiedono il livello di server **VIEW SERVER STATE** autorizzazione per il monitoraggio del dispositivo. Gli account di accesso richiedono il **l'autorizzazione ALTER ANY CONNECTION** dell'autorizzazione per terminare le connessioni utilizzando la Console di amministrazione o **KILL** comando. Per informazioni sulle autorizzazioni necessarie per utilizzare la Console di amministrazione, vedere [concedere autorizzazioni per utilizzare la Console di amministrazione &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Concedere l'autorizzazione per controllare il dispositivo utilizzando viste di sistema  
Le istruzioni SQL seguenti creano un account di accesso denominato `monitor_login` e concede il **VIEW SERVER STATE** dell'autorizzazione per la `monitor_login` account di accesso.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Concedere l'autorizzazione per monitorare il dispositivo utilizzando viste di sistema e terminano le connessioni  
Le istruzioni SQL seguenti creano un account di accesso denominato `monitor_and_terminate_login` e concede il **VIEW SERVER STATE** e **l'autorizzazione ALTER ANY CONNECTION** delle autorizzazioni per il `monitor_and_terminate_login` account di accesso.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Per creare gli account di accesso di amministratore, vedere [ruoli Server](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>Vedere anche
[CREARE ACCOUNT DI ACCESSO](../t-sql/statements/create-login-transact-sql.md)  
[CREARE L'UTENTE](../t-sql/statements/create-user-transact-sql.md)  
[CREARE RUOLO](../t-sql/statements/create-role-transact-sql.md)  
[Carico](load-overview.md)  
