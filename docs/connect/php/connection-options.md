---
title: Le opzioni di connessione | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a176aaa76934c10c4b7cd3526b59d889d1533268
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307240"
---
# <a name="connection-options"></a>Opzioni di connessione
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento sono elencate le opzioni che sono consentite nella matrice associativa (quando si utilizza [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) nel driver SQLSRV) o le parole chiave che sono consentite nel nome dell'origine dati (dsn) (quando si utilizza [PDO::__construct ](../../connect/php/pdo-construct.md) nel driver PDO_SQLSRV).  

## <a name="table-of-connection-options"></a>Tabella delle opzioni di connessione
|Key|valore|Description|Default|  
|-------|---------|---------------|-----------|  
|APP|String|Specifica il nome dell'applicazione usato nella traccia.|Nessun valore impostato.|  
|ApplicationIntent|String|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono ReadOnly e ReadWrite.<br /><br />Per ulteriori informazioni [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] supporto [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vedere [supporto per il ripristino di emergenza a disponibilità elevata](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|ReadWrite|  
|AttachDBFileName|String|Specifica il file di database a cui associare il server.|Nessun valore impostato.|  
|Autenticazione|Una delle seguenti stringhe:<br /><br />'SqlPassword'<br /><br />'ActiveDirectoryPassword'|Specifica la modalità di autenticazione.|Non è impostata.|  
|CharacterSet<br /><br />(non supportato nel driver PDO_SQLSRV)|String|Specifica il set di caratteri usato per l'invio di dati al server.<br /><br />I valori possibili sono SQLSRV_ENC_CHAR e UTF-8. Per altre informazioni, vedere [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md).|SQLSRV_ENC_CHAR|  
|ColumnEncryption<br /><br />(supportato solo in Windows)|**Abilitato** o **disabilitato**|Specifica se la funzionalità Always Encrypted è abilitata o meno. |Disabilitata|  
|ConnectionPooling|1 o **true** per il pool di connessioni attivato.<br /><br />0 o **false** per il pool di connessioni disattivato.|Specifica se la connessione viene assegnata da un pool di connessioni (1 o **true**) o non (0 o **false**).<sup> 1</sup>|**true** (1)|  
|ConnectRetryCount|Numero intero compreso tra 0 e 255 (inclusivo)|Il numero massimo di tentativi per ristabilire una connessione interrotta prima di rinunciare. Per impostazione predefinita, un singolo tenta di ristabilire una connessione quando vengono interrotti. Un valore pari a 0 indica che la riconnessione non verrà tentato di eseguire.|1|  
|ConnectRetryInterval|Numero intero compreso tra 1 e 60 (inclusi)|Tempo, in secondi, tra i tentativi per ristabilire una connessione. L'applicazione tenterà di riconnettersi immediatamente al rilevamento di una connessione interrotta e verrà quindi secondi ConnectRetryInterval prima di riprovare. Questa parola chiave viene ignorata se ConnectRetryCount è uguale a 0.|1|  
|Database|String|Specifica il nome del database in uso per la connessione stabilita<sup>2</sup>.|Il database predefinito per l'accesso in uso.|  
|Driver|String|Specifica di Microsoft ODBC driver utilizzato per comunicare con SQL Server.<br /><br />I valori possibili sono:<br />Driver ODBC 17 per SQL Server<br />ODBC Driver 13 for SQL Server<br />ODBC Driver 11 for SQL Server (solo Windows).|Quando non viene specificata la parola chiave Driver, Microsoft Drivers for PHP per SQL Server tenta di trovare l'esistenza dei driver Microsoft ODBC supportati nel sistema, a partire con la versione più recente di ODBC e così via.|  
|Encrypt|1 o **true** per la crittografia attivata.<br /><br />0 o **false** per la crittografia disattivata.|Specifica se la comunicazione con SQL Server è crittografata (1 o **true**) o non crittografata (0 o **false**)<sup>3</sup>.|**false** (0)|  
|Failover_Partner|String|Specifica il server e l'istanza di mirroring del database (se abilitato e configurato) da usare quando il server primario non è disponibile.<br /><br />L'uso di Failover_Partner con MultiSubnetFailover presenta alcune limitazioni. Per altre informazioni, vedere [Support for High Availability, Disaster Recovery](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|Nessun valore impostato.|  
|LoginTimeout|Integer (driver SQLSRV)<br /><br />Stringa (driver PDO_SQLSRV)|Specifica il numero di secondi trascorsi i quali il tentativo di connessione ha esito negativo.|Nessun timeout.|  
|MultipleActiveResultSets|1 o **true** per usare più set di risultati attivi.<br /><br />0 o **false** per disabilitare più set di risultati attivi.|Disabilita o abilita in modo esplicito il supporto di più set di risultati attivi (MARS).<br /><br />Per altre informazioni, vedere [procedura: disabilitare più set di risultati attivi &#40;MARS&#41;](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).|true (1)|  
|MultiSubnetFailover|String|Specificare sempre **multiSubnetFailover = yes** quando ci si connette al listener del gruppo di disponibilità di un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] gruppo di disponibilità o un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] istanza Cluster di Failover. **multiSubnetFailover = yes** configura [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] per fornire un rilevamento più veloce e connessione al server attualmente attivo. I valori possibili sono Yes e No.<br /><br />Per ulteriori informazioni [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] supporto [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vedere [supporto per il ripristino di emergenza a disponibilità elevata](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|no|  
|PWD<br /><br />(non supportato nel driver PDO_SQLSRV)|String|Specifica la password associata all'ID utente da utilizzare durante la connessione con autenticazione di SQL Server<sup>4</sup>.|Nessun valore impostato.|  
|QuotedId|1 o **true** per utilizzare le regole SQL-92.<br /><br />0 o **false** per usare le regole precedenti.|Specifica se utilizzare le regole SQL-92 per gli identificatori delimitati (1 o **true**) o per utilizzare le regole Transact-SQL legacy (0 o **false**).|**true** (1)|  
|ReturnDatesAsStrings<br /><br />(non supportato nel driver PDO_SQLSRV)|1 o **true** per restituire i tipi di data e ora come stringhe.<br /><br />0 o **false** per restituire i tipi di data e ora come tipi **DateTime** PHP.|Recupera i tipi di data e ora (datetime, date, time, datetime2 e datetimeoffset) come stringhe o come tipi PHP. Quando si usa il driver PDO_SQLSRV, le date vengono restituite come stringhe. Il driver PDO_SQLSRV non ha alcun **datetime** tipo.<br /><br />Per altre informazioni, vedere [Procedura: Recuperare il tipo data e ora come stringhe usando il driver SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).|**false**|  
|Scorrimento|String|"buffered" indica che si desidera un cursore sul lato client (memorizzato nel buffer) che consente di memorizzare nella cache un intero set di risultati. Per altre informazioni, vedere [tipi di cursore &#40;Driver SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).|Cursore forward-only|  
|Server<br /><br />(non supportato nel driver SQLSRV)|String|Istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a cui connettersi.<br /><br />È inoltre possibile specificare un nome di rete virtuale per connettersi a un gruppo di disponibilità AlwaysOn. Per ulteriori informazioni [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] supporto [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vedere [supporto per il ripristino di emergenza a disponibilità elevata](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|Server è una parola chiave obbligatoria (anche se non deve essere la prima parola chiave della stringa di connessione). Se il nome del server non viene passato alla parola chiave, viene effettuato un tentativo di connettersi all'istanza locale.<br /><br />Il valore passato a Server può essere il nome di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o l'indirizzo IP dell'istanza. È possibile specificare facoltativamente un numero di porta (ad esempio, `sqlsrv:server=(local),1033`).<br /><br />A partire dalla versione 3.0 di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] è inoltre possibile specificare un'istanza di LocalDB con `server=(localdb)\instancename`. Per altre informazioni, vedere [supporto per LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).|  
|TraceFile|String|Specifica il percorso del file usato per i dati di traccia.|Nessun valore impostato.|  
|TraceOn|1 o **true** per abilitare la traccia.<br /><br />0 o **false** per disabilitare la traccia.|Specifica se la traccia ODBC è abilitata (1 o **true**) o disattivato (0 o **false**) per la connessione stabilita.|**false** (0)|  
|TransactionIsolation|Il driver SQLSRV usa i valori seguenti:<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />Il driver PDO_SQLSRV usa i valori seguenti:<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|Specifica il livello di isolamento delle transazioni.<br /><br />Per ulteriori informazioni sull'isolamento delle transazioni, vedere [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md) nella documentazione di SQL Server.|SQLSRV_TXN_READ_COMMITTED<br /><br />o Gestione configurazione<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|TransparentNetworkIPResolution|**Abilitato** o **disabilitato**|Interessa la sequenza di connessione quando il primo risolto IP dell'host non risponde e non vi sono più indirizzi IP associati con il nome host.<br /><br />Questa utilità interagisce con MultiSubnetFailover per fornire le sequenze di connessione diversa. Per ulteriori informazioni, vedere [utilizzando la risoluzione IP di rete Transparent](https://docs.microsoft.com/en-us/sql/connect/odbc/using-transparent-network-ip-resolution).|Abilitata|
|TrustServerCertificate|1 o **true** per considerare il certificato attendibile.<br /><br />0 o **false** per non considerare il certificato attendibile.|Specifica se il client deve considerare attendibile (1 o **true**) o rifiutare (0 o **false**) un certificato server autofirmato.|**false** (0)|  
|UID<br /><br />(non supportato nel driver PDO_SQLSRV)|String|Specifica l'ID utente da utilizzare durante la connessione con autenticazione di SQL Server<sup>4</sup>.|Nessun valore impostato.|  
|WSID|String|Specifica il nome del computer per la traccia.|Nessun valore impostato.|  

1. Il `ConnectionPooling` attributo non può essere utilizzato per abilitare o disabilitare il pool di connessioni in Linux e Mac. Vedere [pool di connessioni (driver Microsoft per PHP per SQL Server)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).

2. Vengono apportate tutte le query eseguite durante la connessione al database specificato da di *Database* attributo. Tuttavia, se l'utente dispone delle autorizzazioni appropriate, in altri database di accedere ai dati utilizzando un nome completo. Ad esempio, se il *master* database viene impostato con il *Database* attributo di connessione, è comunque possibile eseguire una query Transact-SQL che accede il  *AdventureWorks.HumanResources.Employee* tabella utilizzando il nome completo.  

3. L'abilitazione di *Encryption* può compromettere le prestazioni di alcune applicazioni a causa dell'overhead computazionale necessario per la crittografia dei dati.  

4. Istanza di *UID* e *PWD* devono essere entrambi impostati durante la connessione con l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  

Molte delle chiavi supportate sono attributi della stringa di connessione ODBC. Per informazioni sulle stringhe di connessione ODBC, vedere [Using Connection String Keywords with SQL Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  

## <a name="see-also"></a>Vedere anche  
[Connessione al server](../../connect/php/connecting-to-the-server.md)  
