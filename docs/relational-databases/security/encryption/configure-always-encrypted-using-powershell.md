---
title: "Configurare Always Encrypted tramite PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "09/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-security"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
caps.latest.revision: 15
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 13
---
# Configurare Always Encrypted tramite PowerShell
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Il modulo PowerShell SqlServer include i cmdlet per la configurazione di [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) nel database SQL di Azure e in SQL Server 2016.

Poiché la maggior parte dei cmdlet per Always Encrypted nel modulo SqlServer vengono usati con chiavi Always Encrypted o dati sensibili archiviati in colonne crittografate è importante eseguire i cmdlet in un computer protetto. Durante la gestione di Always Encrypted eseguire i cmdlet da un computer diverso dal computer che ospita l'istanza di SQL Server. 

Poiché l'obiettivo principale di Always Encrypted è garantire la sicurezza dei dati sensibili crittografati anche se il sistema di database viene compromesso, eseguire uno script di PowerShell che elabora le chiavi o i dati sensibili nel computer SQL Server può ridurre o annullare i vantaggi della funzionalità. Per altre indicazioni relative alla sicurezza, vedere [Considerazioni sulla sicurezza per la gestione delle chiavi](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md#SecurityForKeyManagement).

I collegamenti ai singoli articoli dei cmdlet sono presenti alla [fine di questa pagina](#aecmdletreference).

## Prerequisiti

Installare il [modulo SqlServer](https://msdn.microsoft.com/library/mt740629.aspx) in un computer protetto che NON sia il computer che ospita l'istanza di SQL Server. 

Installare il modulo SqlServer installando la versione più recente di [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).
Si noti che il modulo *SqlServer* è diverso dal modulo *sqlps* che non supporta Always Encrypted. Per informazioni dettagliate, vedere il post del blog [SQL PowerShell - July 2016 Update](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update) (SQL PowerShell - Aggiornamento luglio 2016) del team.

## <a name="importsqlservermodule"></a> Importazione del modulo SqlServer 

Per caricare il modulo SqlServer:

1.  Usare il cmdlet **Set-ExecutionPolicy** per impostare i criteri di esecuzione degli script appropriati.
2.  Usare il cmdlet **Import-Module** per importare il modulo SqlServer.

Questo esempio carica il modulo SqlServer.

```
# Import the SQL Server Module.  
Import-Module "SqlServer" 
```

## <a name="connectingtodatabase"></a> Connessione a un database

Alcuni dei cmdlet Always Encrypted possono essere usati con dati o metadati del database e richiedono la connessione al database. Quando si configura Always Encrypted con il modulo SqlServer è consigliabile connettersi al database con i due metodi seguenti: 
1. Connettersi usando SQL Server PowerShell.
2. Connettersi usando SQL Server Management Objects (SMO).

### Utilizzo di SQL Server PowerShell

Questo metodo si applica solo a SQL Server e non è supportato nel database SQL di Azure.

Con SQL Server PowerShell è possibile spostarsi tra i percorsi usando alias di Windows PowerShell simili ai comandi normalmente usati per spostarsi tra i percorsi del file system. Dopo essere passati all'istanza di destinazione e al database, i cmdlet successivi verranno eseguiti nel database come illustrato nell'esempio seguente:

```
# Import the SqlServer module.
Import-Module "SqlServer"
# Navigate to the database in the remote instance.
cd SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
# List column master keys in the above database.
Get-SqlColumnMasterKey
```

 
In alternativa, è possibile specificare un percorso di database usando il parametro generico **Path** anziché passare al database.


```
# Import the SqlServer module.
Import-Module "SqlServer" 
# List column master keys for the specified database.
Get-SqlColumnMasterKey -Path SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
```
 
### Utilizzo di SMO

Questo metodo si applica al database SQL di Azure e a SQL Server.
Con SMO, è possibile creare un oggetto di [classe Database](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.database.aspx) e quindi passare l'oggetto usando il parametro **InputObject** di un cmdlet che si connette al database.


```
# Import the SqlServer module
Import-Module "SqlServer"  

# Connect to your database (Azure SQL database).
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName] 

# List column master keys for the specified database.
Get-SqlColumnMasterKey -InputObject $database
```


In alternativa, è possibile usare il reindirizzamento:


```
$database | Get-SqlColumnMasterKey
```

## Attività Always Encrypted tramite PowerShell

- [Configure Always Encrypted Keys using PowerShell (Configurare le chiavi Always Encrypted tramite PowerShell)](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md) 
- [Ruotare le chiavi Always Encrypted tramite PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Configurare la crittografia della colonna tramite PowerShell](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Riferimento dei cmdlet di Always Encrypted

Per Always Encrypted sono disponibili i cmdlet di PowerShell seguenti:

|CMDLET |Descrizione
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://msdn.microsoft.com/library/mt759815.aspx)**  |Esegue l'autenticazione in Azure e acquisisce un token di autenticazione.
|**[Add-SqlColumnEncryptionKeyValue](https://msdn.microsoft.com/library/mt759817.aspx)**    |Aggiunge un nuovo valore crittografato per un oggetto chiave di crittografia della colonna esistente nel database.
|**[Complete-SqlColumnMasterKeyRotation](https://msdn.microsoft.com/library/mt759791.aspx)**    |Completa la rotazione di una chiave master della colonna.
|**[Get-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759814.aspx)** |Restituisce tutti gli oggetti chiave di crittografia della colonna definiti nel database oppure un solo oggetto chiave di crittografia della colonna con il nome specificato.
|**[Get-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759782.aspx)** |Restituisce tutti gli oggetti chiave master della colonna definiti nel database oppure un solo oggetto chiave master della colonna con il nome specificato.
|**[Invoke-SqlColumnMasterKeyRotation](https://msdn.microsoft.com/library/mt759810.aspx)**  |Avvia la rotazione di una chiave master della colonna.
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759795.aspx)**    |Crea un oggetto SqlColumnMasterKeySettings che descrive una chiave asimmetrica archiviata nell'insieme di credenziali delle chiavi di Azure.
|**[New-SqlCngColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759818.aspx)**  |Crea un oggetto SqlColumnMasterKeySettings che descrive una chiave asimmetrica archiviata in un archivio chiavi che supporta l'API CNG (Cryptography Next Generation).
|**[New-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759808.aspx)** |Crea un nuovo oggetto chiave di crittografia della colonna nel database.
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://msdn.microsoft.com/library/mt759794.aspx)**   |Produce un valore crittografato di una chiave di crittografia della colonna.
|**[New-SqlColumnEncryptionSettings](https://msdn.microsoft.com/library/mt759825.aspx)**    |Crea un nuovo oggetto SqlColumnEncryptionSettings che incapsula le informazioni sulla crittografia di una singola colonna, inclusi CEK e tipo di crittografia.
|**[New-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759813.aspx)** |Crea un nuovo oggetto chiave master della colonna nel database.
|**New-SqlColumnMasterKeySettings**|Crea un oggetto SqlColumnMasterKeySettings per una chiave master della colonna con il provider specificato e il percorso della chiave.
|**[New-SqlCspColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759784.aspx)**  |Crea un oggetto SqlColumnMasterKeySettings che descrive una chiave asimmetrica archiviata in un archivio chiavi con un CSP (Cryptography Service Provider) che supporta l'API Cryptography (CAPI).
|**[Remove-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759786.aspx)**  |Rimuove l'oggetto chiave di crittografia della colonna dal database.
|**[Remove-SqlColumnEncryptionKeyValue](https://msdn.microsoft.com/library/mt759783.aspx)** |Rimuove un valore crittografato da un oggetto chiave di crittografia della colonna esistente nel database.
|**[Remove-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759800.aspx)**  |Rimuove l'oggetto chiave master della colonna dal database.
|**[Set-SqlColumnEncryption](https://msdn.microsoft.com/library/mt759790.aspx)**    |Crittografa, decrittografa o ricrittografa le colonne specificate nel database.



## Risorse aggiuntive

- [Always Encrypted (Motore di database)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Panoramica della gestione delle chiavi per Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Using Always Encrypted with .NET Framework Data Provider for SQL Server (Uso di Always Encrypted con il provider di dati .NET Framework per SQL Server)](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [Configurare Always Encrypted usando SQL Server Management Studio](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)

