---
title: I membri di SQLServerXADataSource | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04178645-915f-4569-8907-d45e299bbe7d
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2b81229c9c1f4164635e25342456d16b2c578168
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxadatasource-members"></a>Membri di SQLServerXADataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
  
|Nome|Description|  
|----------|-----------------|  
|[() Di SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-constructor.md)|Inizializza una nuova istanza di [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe.|  
  
## <a name="fields"></a>Campi  
 nessuna.  
  
## <a name="inherited-fields"></a>Campi ereditati  
 nessuna.  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il valore della **applicationIntent** proprietà di connessione.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il nome dell'applicazione.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) tenta di stabilire una connessione con l'origine dati che rappresenta l'oggetto DataSource.|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il nome del database.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il nome del server di failover utilizzato in una configurazione di mirroring del database.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] nome dell'istanza.|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce un **booleano** valore che indica se la proprietà lastUpdateCount è abilitata.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce un **int** valore che indica il numero di millisecondi di attesa prima che venga segnalato un timeout di blocco del database.|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il numero di secondi di attesa di questo oggetto origine dati durante il tentativo di stabilire una connessione.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce un flusso di output di caratteri da utilizzare per tutti i messaggi di traccia e registrazione.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) recupera il valore della **multiSubnetFailover** proprietà di connessione.|  
|[getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)|(Ereditato da [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)) tenta di stabilire una connessione di database fisica che può essere utilizzata come una connessione in pool.|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il numero di porta corrente utilizzato per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverxadatasource.md)|Restituisce un riferimento a questo [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md) oggetto.|  
|[metodo getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il tipo di cursore predefinito utilizzato per tutti i set di risultati creati tramite questo oggetto origine dati.|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce un **booleano** valore che indica se l'invio di **stringa** parametri al server in formato UNICODE è abilitato.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il nome del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce l'URL utilizzato per connettersi all'origine dati.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il nome utente utilizzato per connettersi all'origine dati.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce il nome del client computer utilizzato per connettersi all'origine dati.|  
|[getXAConnection](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)|Tenta di stabilire una connessione di database fisica che possa essere utilizzata in una transazione distribuita.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) restituisce un **booleano** valore che indica se la conversione di stati SQL in stati conformi a XOpen è abilitata.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)|Indica se questo oggetto è un wrapper per l'interfaccia specificata.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il valore della **applicationIntent** proprietà di connessione.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il nome dell'applicazione.|  
|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) indica il tipo di cui l'applicazione di utilizzare la sicurezza integrata.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il nome del database a cui connettersi.|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta la descrizione dell'origine dati.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il nome del server di failover utilizzato in una configurazione di mirroring del database.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] nome dell'istanza.|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta un **booleano** valore che indica se la proprietà integratedSecurity è abilitata.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta un **booleano** valore che indica se la proprietà lastUpdateCount è abilitata.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta un **int** valore che indica il numero di millisecondi di attesa prima che il database segnali un timeout di blocco.|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il numero di secondi di attesa di questo oggetto origine dati durante il tentativo di stabilire una connessione.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta un flusso di output di caratteri da utilizzare per tutti i messaggi di traccia e registrazione.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il valore della **multiSubnetFailover** proprietà di connessione.|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta la password che verrà utilizzata per connettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il numero di porta da utilizzare per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il tipo di cursore predefinito utilizzato per tutti i set di risultati creati tramite questo oggetto origine dati.|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta un **booleano** valore che indica se l'invio di **stringa** parametri al server in formato UNICODE è abilitato.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il nome del computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta l'URL utilizzato per connettersi all'origine dati.|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il nome utente utilizzato per connettersi all'origine dati.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta il client come nome del computer utilizzato per la connessione all'origine dati.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|(Ereditato da [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) imposta un **booleano** valore che indica se la conversione di stati SQL in stati conformi a XOpen è abilitata.|  
|[Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)|Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-metodi specifici.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource|getPooledConnection|  
|com.microsoft.sqlserver.jdbc.SQLServerDataSource|getApplicationName, getConnection, getDatabaseName, getDescription, getFailoverPartner, getInstanceName, getLastUpdateCount, getLockTimeout, getLoginTimeout, getLogWriter, getPortNumber, getSelectMethod, getSendStringParametersAsUnicode, getServerName, getURL, getUser, getWorkstationID, getXopenStates, setApplicationName, setDatabaseName, setDescription, setFailoverPartner, setInstanceName, setIntegratedSecurity, setLastUpdateCount, setLockTimeout, setLoginTimeout, setLogWriter, setPassword, setPortNumber, setSelectMethod, setSendStringParametersAsUnicode, setServerName, setURL, setUser, setWorkstationID, setXopenStates|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
|javax.sql.XADataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter|  
|javax.sql.ConnectionPoolDataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
