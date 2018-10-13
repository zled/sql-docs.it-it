---
title: Introduzione alla sicurezza di SQL Server in Linux | Microsoft Docs
description: Questo articolo descrive le azioni di sicurezza standard.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.custom: sql-linux
ms.openlocfilehash: feae91ed25dafa499026b2cadf72a2eafa0c63ae
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906231"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Procedura dettagliata per la funzionalità di sicurezza di SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Se sei un utente di Linux che è una novità di SQL Server, le attività seguenti illustrano alcune delle attività di sicurezza. Questi non sono specifiche di Linux o univoco, ma è utile per dare un'idea delle aree per analizzare ulteriormente il problema. In ogni esempio viene fornito un collegamento alla documentazione approfondita per quell'area.

>  [!NOTE]
>  Gli esempi seguenti usano il **AdventureWorks2014** database di esempio. Per istruzioni su come ottenere e installare il database di esempio, vedere [ripristinare un database di SQL Server da Windows a Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Creare un account di accesso e un utente del database 

Concedere ad altri utenti l'accesso a SQL Server mediante la creazione di un account di accesso nel database master usando il [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) istruzione. Esempio:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

>  [!NOTE]
>  Usare sempre una password complessa al posto di un asterisco nel comando precedente.

Gli account di accesso possono connettersi a SQL Server e dispongono di accesso (con autorizzazioni limitate) al database master. Per connettersi a un database utente, un account di accesso richiede un'identità a livello di database, denominato un utente del database corrispondente. Gli utenti sono specifici per ogni database e devono essere creati separatamente in ogni database per concedere loro l'accesso. Nell'esempio seguente consente di passare al database AdventureWorks2014 e quindi Usa il [CREATE USER](../t-sql/statements/create-user-transact-sql.md) istruzione per creare un utente denominato Larry associato con l'account di accesso denominato Larry. Se l'account di accesso e l'utente sono correlate (mapping reciproco), sono oggetti diversi. L'account di accesso è un'entità a livello di server. L'utente è un'entità a livello di database.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Un account di amministratore di SQL Server può connettersi a qualsiasi database e possa creare più account di accesso e utenti in qualsiasi database.  
- Quando un utente crea un database diventano il proprietario del database, in grado di connettersi a tale database. I proprietari di database possono creare altri utenti.

In un secondo momento è possibile autorizzare altri account di accesso per creare un altro account di accesso da concedere loro il `ALTER ANY LOGIN` l'autorizzazione. All'interno di un database, è possibile autorizzare altri utenti per creare altre utenti concedendo il `ALTER ANY USER` l'autorizzazione. Esempio:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

L'account di accesso Larry possono ora creare ulteriori account di accesso e l'utente Jerry possono creare altri utenti.


## <a name="granting-access-with-least-privileges"></a>Concessione dell'accesso con privilegi minimi

I primi utenti di connettersi a un database utente sarà l'amministratore e gli account proprietario del database. Tuttavia questi utenti hanno tutte le autorizzazioni disponibili per il database. Si tratta di autorizzazioni maggiori rispetto a quasi tutti gli utenti devono avere. 

Quando sta iniziando, è possibile assegnare alcune categorie generali di autorizzazioni tramite l'oggetto incorporato *ruoli predefiniti del database*. Ad esempio, il `db_datareader` può leggere tutte le tabelle nel database del ruolo predefinito del database, ma senza apportare alcuna modifica. Concedere l'appartenenza a un ruolo predefinito del database usando il [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md) istruzione. Nell'esempio seguente l'utente di aggiungere `Jerry` per il `db_datareader` ruolo predefinito del database.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Per un elenco dei ruoli predefiniti del database, vedere [ruoli a livello di Database](../relational-databases/security/authentication-access/database-level-roles.md).

In un secondo momento, quando si è pronti per configurare l'accesso più preciso ai dati (altamente consigliati), creare ruoli database definiti dall'utente usando [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md) istruzione. Quindi assegnare specifiche autorizzazioni granulari all'utente i ruoli personalizzati.

Ad esempio, le istruzioni che seguono creano un ruolo del database denominato `Sales`, concede il `Sales` raggruppare la possibilità di visualizzare, aggiornare ed eliminare righe dal `Orders` tabella e quindi aggiunge l'utente `Jerry` per il `Sales` ruolo.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

Per altre informazioni sul sistema di autorizzazione, vedere [Introduzione a Database Engine Permissions](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## <a name="configure-row-level-security"></a>Configurare la sicurezza a livello di riga  

[Sicurezza a livello di riga](../relational-databases/security/row-level-security.md) consente di limitare l'accesso alle righe in un database basato sull'utente che esegue una query. Questa funzionalità è utile per scenari come garantire che i clienti possono accedere solo ai propri dati o che i ruoli di lavoro può accedere solo ai dati inerenti al dipartimento.   

I passaggi seguenti descrivono come impostare due utenti con accesso a livello di riga diversi per il `Sales.SalesOrderHeader` tabella. 

Creare due account utente per testare la sicurezza a livello di riga:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Concedere l'accesso in lettura nel `Sales.SalesOrderHeader` tabella per entrambi gli utenti:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Creare un nuovo schema e inline con valori di tabella (funzione). La funzione restituisce 1 quando una riga il `SalesPersonID` colonna corrisponde all'ID di un `SalesPerson` account di accesso o se l'utente che esegue la query è l'utente gestore.   
   
```     
CREATE SCHEMA Security;   
GO   
   
CREATE FUNCTION Security.fn_securitypredicate(@SalesPersonID AS int)     
    RETURNS TABLE   
WITH SCHEMABINDING   
AS     
   RETURN SELECT 1 AS fn_securitypredicate_result    
WHERE ('SalesPerson' + CAST(@SalesPersonId as VARCHAR(16)) = USER_NAME())     
    OR (USER_NAME() = 'Manager');    
```   

Creare criteri di sicurezza aggiungendo la funzione come un filtro e un predicato di blocco nella tabella:  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Eseguire il codice seguente per eseguire query di `SalesOrderHeader` ciascun utente di tabella. Verificare che `SalesPerson280` vede solo le 95 righe le proprie vendite e che il `Manager` possono vedere tutte le righe nella tabella.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
Modificare i criteri di sicurezza per disabilitarli.  A questo punto entrambi gli utenti possono accedere tutte le righe. 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>Abilitare la maschera dati dinamica

[Maschera dati dinamica](../relational-databases/security/dynamic-data-masking.md) consente di ridurre l'esposizione dei dati sensibili agli utenti di un'applicazione, completamente o parzialmente maschera alcune colonne. 

Usa un' `ALTER TABLE` istruzione per aggiungere una funzione di maschera al `EmailAddress` colonna il `Person.EmailAddress` tabella: 
 
```
USE AdventureWorks2014;
GO
ALTER TABLE Person.EmailAddress    
ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Creare un nuovo utente `TestUser` con `SELECT` autorizzazione per la tabella, quindi eseguire una query come `TestUser` per visualizzare i dati mascherati:   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
REVERT;    
```
 
Verificare che la funzione maschera viene modificato l'indirizzo di posta elettronica nel primo record da:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>Abilitazione di Transparent Data Encryption

Una minaccia al database è il rischio che un utente verrà rubare i file di database di fuori del disco rigido. Questo problema può verificarsi con un'intrusione che ottiene accesso con privilegi elevati nel sistema, tramite le azioni di un dipendente problema o per il furto di computer che contiene i file (ad esempio un portatile).

Transparent Data Encryption (TDE) consente di crittografare i file di dati archiviati nel disco rigido. Database master del motore di database di SQL Server con la chiave di crittografia, in modo che il motore di database può modificare i dati. I file di database non possono essere letti senza accesso alla chiave. Gli amministratori di alto livello possono gestire, backup e ricreare la chiave, in modo che il database può essere spostato, ma solo per gli utenti selezionati. Quando TDE è configurato, il `tempdb` database viene automaticamente crittografato. 

Poiché il motore di Database può leggere i dati, Transparent Data Encryption non offre protezione contro accessi non autorizzati da parte degli amministratori del computer che può leggere la memoria direttamente o accedere a SQL Server tramite un account amministratore.

### <a name="configure-tde"></a>Configurare Transparent Data Encryption

- Creare una chiave master
- Creare o ottenere un certificato protetto dalla chiave master
- Creare una chiave di crittografia del database e proteggerla mediante il certificato
- Impostare il database per l'uso della crittografia

Richiede la configurazione di TDE `CONTROL` l'autorizzazione per il database master e `CONTROL` autorizzazione per il database utente. In genere un amministratore configura Transparent Data Encryption. 

L'esempio seguente illustra come crittografare e decrittografare il database `AdventureWorks2014` usando un certificato installato nel server denominato `MyServerCert`.


```
USE master;  
GO  

CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**********';  
GO  

CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Database Encryption Key Certificate';  
GO  

USE AdventureWorks2014;  
GO
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO
  
ALTER DATABASE AdventureWorks2014  
SET ENCRYPTION ON;   
```

Per rimuovere Transparent Data Encryption, eseguire `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

Le operazioni di crittografia e decrittografia sono pianificate sui thread in background da SQL Server. Per visualizzare lo stato di queste operazioni, è possibile usare le viste del catalogo e le viste a gestione dinamica nell'elenco illustrato di seguito in questo argomento.   

>  [!WARNING]
>  I file di backup dei database in cui è abilitata la funzionalità TDE vengono crittografati anche tramite la chiave di crittografia del database. Di conseguenza, quando questi backup vengono ripristinati, è necessario disporre del certificato che protegge la chiave di crittografia del database. Pertanto, oltre ad eseguire il backup del database, è necessario assicurarsi di conservare un backup dei certificati server per impedire la perdita di dati. Se il certificato non è più disponibile, si verificherà la perdita di dati. Per altre informazioni, vedere [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

Per altre informazioni su TDE, vedere [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## <a name="configure-backup-encryption"></a>Configurare la crittografia dei backup
SQL Server è in grado di crittografare i dati durante la creazione di un backup. Specificando l'algoritmo di crittografia e il componente di crittografia (certificato o chiave asimmetrica) durante la creazione di un backup, è possibile creare un file di backup crittografato.    
  
> [!WARNING]  
>  È molto importante eseguire il backup del certificato o della chiave asimmetrica e preferibilmente in un percorso diverso dal file di backup utilizzato per la crittografia. Senza il certificato o la chiave asimmetrica, non è possibile ripristinare il backup, rendendo il file di backup inutilizzabile. 
 
 
Nell'esempio seguente viene creato un certificato e quindi crea un backup protetto dal certificato.
```
USE master;  
GO  
CREATE CERTIFICATE BackupEncryptCert   
   WITH SUBJECT = 'Database backups';  
GO 
BACKUP DATABASE [AdventureWorks2014]  
TO DISK = N'/var/opt/mssql/backups/AdventureWorks2014.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

Per altre informazioni, vedere [Crittografia dei backup](../relational-databases/backup-restore/backup-encryption.md).


## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulle funzionalità di sicurezza di SQL Server, vedere [Centro sicurezza per il motore di Database di SQL Server e Database SQL di Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
