---
title: Introduzione alla protezione di SQL Server in Linux | Documenti Microsoft
description: In questo argomento vengono descritte le azioni di protezione tipiche.
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5256cf1d1c63139c43fbb9900876297294f2d30a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Procedura dettagliata per le funzionalità di sicurezza di SQL Server in Linux

Nel caso di un utente di Linux che è una novità di SQL Server, le attività seguenti illustrano alcune delle attività di protezione. Queste non sono specifiche di Linux o univoco, ma consente di farsi un'idea delle aree per approfondire la verifica. In ogni esempio viene fornito un collegamento alla documentazione approfondita per tale area.

>  [!NOTE]
>  L'esempio seguente usa il **AdventureWorks2014** database di esempio. Per istruzioni su come ottenere e installare il database di esempio, vedere [ripristinare un database di SQL Server da Windows a Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Creare un account di accesso e un utente del database 

Concedere ad altri utenti l'accesso a SQL Server mediante la creazione di un account di accesso nel database master utilizzando il [CREATE LOGIN](https://msdn.microsoft.com/library/ms189751.aspx) istruzione. Esempio:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

>  [!NOTE]
>  Utilizzare sempre una password complessa al posto di asterischi precedente.

Gli account di accesso possono connettersi a SQL Server e dispongono di accesso (con autorizzazioni limitate) al database master. Per connettersi a un database utente, un'identità corrispondente a livello di database, denominato di un utente del database è necessario un account di accesso. Gli utenti sono specifici di ogni database e devono essere creati separatamente in ogni database per concedere l'accesso. Nell'esempio seguente consente di passare al database AdventureWorks2014 e quindi utilizza il [CREATE USER](https://msdn.microsoft.com/library/ms173463.aspx) istruzione per creare un utente denominato Larry che è associato con l'account di accesso denominato Larry. Se l'account di accesso e l'utente sono correlati (mapping reciproco) sono oggetti diversi. L'account di accesso è un'entità a livello di server. L'utente è un'entità a livello di database.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Un account di amministratore di SQL Server può connettersi a qualsiasi database e può creare più account di accesso e utenti in qualsiasi database.  
- Quando si crea un database diventano il proprietario del database, in grado di connettersi a tale database. I proprietari del database è possono creare altri utenti.

In un secondo momento è possibile autorizzare altri account di accesso per creare un account di accesso più concedendo il `ALTER ANY LOGIN` autorizzazione. All'interno di un database, è possibile autorizzare altri utenti per creare altri utenti, concedendo il `ALTER ANY USER` autorizzazione. Esempio:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

A questo punto l'account di accesso erano può creare più account di accesso e l'utente erano possono creare altri utenti.


## <a name="granting-access-with-least-privileges"></a>La concessione dell'accesso con privilegi minimi

I primi utenti per connettersi a un database utente sarà l'amministratore e l'account del proprietario del database. Tuttavia, questi utenti hanno tutti il le autorizzazioni del database. Si tratta di autorizzazioni maggiori rispetto a cui la maggior parte degli utenti devono avere. 

Quando sono semplicemente operazioni preliminari, è possibile assegnare alcune categorie generali di autorizzazioni tramite l'oggetto incorporato *ruoli predefiniti del database*. Ad esempio, il `db_datareader` , leggere tutte le tabelle nel database del ruolo predefinito del database, ma non apportare alcuna modifica. Concedere l'appartenenza a un ruolo predefinito del database utilizzando il [ALTER ROLE](https://msdn.microsoft.com/library/ms189775.aspx) istruzione. Nell'esempio seguente viene aggiunta l'utente `Jerry` per il `db_datareader` ruolo predefinito del database.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Per un elenco dei ruoli predefiniti del database, vedere [ruoli a livello di Database](https://msdn.microsoft.com/library/ms189121.aspx).

In un secondo momento, quando si è pronti per configurare l'accesso più precisa ai dati (scelta consigliati), creare ruoli del database definiti dall'utente utilizzando [CREATE ROLE](https://msdn.microsoft.com/library/ms187936.aspx) istruzione. Quindi, assegnare autorizzazioni granulari specifiche all'utente, ruoli personalizzati.

Ad esempio, le istruzioni che seguono creano un ruolo del database denominato `Sales`, concede il `Sales` gruppo la possibilità di visualizzare, aggiornare ed eliminare le righe il `Orders` tabella e quindi aggiunge l'utente `Jerry` per il `Sales` ruolo.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

Per ulteriori informazioni sul sistema di autorizzazione, vedere [Introduzione alle autorizzazioni del motore di Database](https://msdn.microsoft.com/library/mt667986.aspx).


## <a name="configure-row-level-security"></a>Configurare la sicurezza a livello di riga  

[Sicurezza a livello di riga](https://msdn.microsoft.com/library/dn765131.aspx) consente di limitare l'accesso alle righe in un database in base all'utente che esegue una query. Questa funzionalità è utile per scenari come garantire che i clienti possono accedere solo i propri dati o che lavoratori possano accedere solo dati inerenti al proprio reparto.   

Accesso a livello di riga descritta di seguito una procedura di impostazione di due utenti diversi di `Sales.SalesOrderHeader` tabella. 

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
   
Creare un nuovo schema e inline con valori di tabella (funzione). La funzione restituisce 1 quando una riga di `SalesPersonID` colonna corrisponde all'ID di un `SalesPerson` account di accesso o se l'utente che esegue la query è l'utente di gestione.   
   
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

Creare un criterio di sicurezza aggiungendo la funzione come un filtro e predicato di blocco della tabella:  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Eseguire la seguente query di `SalesOrderHeader` tabella ciascun utente. Verificare che `SalesPerson280` vede solo le 95 righe le proprie vendite e che il `Manager` possono visualizzare tutte le righe nella tabella.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
Modificare i criteri di sicurezza per disabilitarli.  Ora entrambi gli utenti possono accedere a tutte le righe. 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>Abilitare la maschera dati dinamica

[La maschera dati dinamica](https://msdn.microsoft.com/library/mt130841.aspx) consente di limitare l'esposizione dei dati sensibili agli utenti di un'applicazione completamente o parzialmente maschera determinate colonne. 

Utilizzare un `ALTER TABLE` istruzione per aggiungere una funzione di maschera per la `EmailAddress` colonna il `Person.EmailAddress` tabella: 
 
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
 
Verificare che la funzione di maschera modifica l'indirizzo di posta elettronica del primo record da:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>Abilitazione di Transparent Data Encryption

Una minaccia per il database è il rischio che un utente verrà rubare i file di database dal disco rigido. Questo problema può verificarsi con un'intrusione che ottiene l'accesso con privilegi elevato al sistema, tramite le azioni di un dipendente di problema o furto del computer contenente i file (ad esempio un laptop).

Transparent Data Encryption (TDE) consente di crittografare i file di dati archiviati sul disco rigido. Il database master del motore di database di SQL Server con la chiave di crittografia, in modo che il motore di database può modificare i dati. Impossibile leggere i file di database senza accesso alla chiave. Gli amministratori di alto livello possono gestire, il backup e ricreare la chiave, pertanto può essere spostato il database, ma solo da utenti selezionati. Quando TDE è configurato, il `tempdb` database viene crittografato automaticamente. 

Poiché il motore di Database può leggere i dati, Transparent Data Encryption non fornisce protezione da accessi non autorizzati dagli amministratori del computer che possono leggere la memoria direttamente o accedere a SQL Server tramite un account amministratore.

### <a name="configure-tde"></a>Configurare Transparent Data Encryption

- Creare una chiave master
- Creare o ottenere un certificato protetto dalla chiave master
- Creare una chiave di crittografia del database e proteggerla mediante il certificato
- Impostare il database per l'uso della crittografia

Configurazione di TDE richiede `CONTROL` autorizzazione per il database master e `CONTROL` autorizzazione per il database utente. In genere un amministratore configura Transparent Data Encryption. 

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

Per rimuovere Transparent Data Encryption, eseguire`ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

Le operazioni di crittografia e decrittografia sono pianificate sui thread di background da SQL Server. Per visualizzare lo stato di queste operazioni, è possibile usare le viste del catalogo e le viste a gestione dinamica nell'elenco illustrato di seguito in questo argomento.   

>  [!WARNING]
>  I file di backup dei database in cui è abilitata la funzionalità TDE vengono crittografati anche tramite la chiave di crittografia del database. Di conseguenza, quando questi backup vengono ripristinati, è necessario disporre del certificato che protegge la chiave di crittografia del database. Pertanto, oltre ad eseguire il backup del database, è necessario assicurarsi di conservare un backup dei certificati server per impedire la perdita di dati. Se il certificato non è più disponibile, si verificherà la perdita di dati. Per altre informazioni, vedere [SQL Server Certificates and Asymmetric Keys](https://msdn.microsoft.com/library/bb895327.aspx).  

Per ulteriori informazioni su TDE, vedere [Transparent Data Encryption (TDE)](https://msdn.microsoft.com/en-us/library/bb934049.aspx).   


## <a name="configure-backup-encryption"></a>Configurare la crittografia dei backup
SQL Server ha la possibilità di crittografare i dati durante la creazione di un backup. Specificando l'algoritmo di crittografia e il componente di crittografia (certificato o chiave asimmetrica) durante la creazione di un backup, è possibile creare un file di backup crittografato.    
  
> [!WARNING]  
>  È molto importante eseguire il backup del certificato o della chiave asimmetrica e preferibilmente in un percorso diverso dal file di backup utilizzato per la crittografia. Senza il certificato o la chiave asimmetrica, non è possibile ripristinare il backup, rendendo il file di backup inutilizzabile. 
 
 
Nell'esempio seguente viene creato un certificato e quindi creato un backup protetto dal certificato.
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

Per ulteriori informazioni, vedere [crittografia dei Backup](https://msdn.microsoft.com/library/dn449489.aspx).


## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulle caratteristiche di sicurezza di SQL Server, vedere [centro di sicurezza per il motore di Database di SQL Server e Database SQL di Azure](https://msdn.microsoft.com/library/bb510589.aspx).

