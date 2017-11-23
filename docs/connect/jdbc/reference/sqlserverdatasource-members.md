---
title: I membri di SQLServerDataSource | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
caps.latest.revision: "43"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6feb87ad1bb5054b800a001a30af6b94679e977a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverdatasource-members"></a>Membri di SQLServerDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
  
|Nome|Description|  
|----------|-----------------|  
|[() Di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-constructor.md)|Inizializza una nuova istanza di [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) classe.|  
  
## <a name="fields"></a>Campi  
 nessuna.  
  
## <a name="inherited-fields"></a>Campi ereditati  
 nessuna.  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|Restituisce il valore della **applicationIntent** proprietà di connessione.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|Restituisce il nome dell'applicazione.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|Tenta di stabilire una connessione con i dati di origine da questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto rappresenta.|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|Restituisce il nome del database.|  
|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|Restituisce un **booleano** valore che indica se la proprietà di crittografia è abilitata.|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|Restituisce una descrizione dell'origine dati.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|Restituisce il nome del server di failover utilizzato nella configurazione del mirroring del database.|  
|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|Restituisce il nome host utilizzato per la convalida del certificato SSL (Secure Sockets Layer) di SQL Server.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|Restituisce il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] nome dell'istanza.|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|Restituisce un **booleano** valore che indica se la proprietà lastUpdateCount è abilitata.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|Restituisce un **int** valore che indica il numero di millisecondi di attesa prima che venga segnalato un timeout di blocco del database.|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|Restituisce il numero di secondi [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto di attesa durante il tentativo di stabilire una connessione.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|Restituisce un flusso di output dei caratteri da utilizzare per tutti i messaggi di registrazione e di traccia.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|Restituisce il valore della **multiSubnetFailover** proprietà di connessione.|  
|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|Restituisce le dimensioni di pacchetto di rete corrente utilizzata per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], specificato in byte.|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|Restituisce il numero di porta corrente utilizzato per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md)|Restituisce un riferimento a questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|Restituisce la risposta per questa modalità di buffering [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.|  
|[metodo getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|Restituisce il tipo di cursore predefinito utilizzato per tutti i set di risultati creati tramite questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|Restituisce un **booleano** valore che indica se l'invio di parametri di stringa al server in formato UNICODE è abilitato.|  
|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Restituisce l'impostazione del **SendTimeAsDatetime** proprietà di connessione.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|Restituisce il nome del computer che esegue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|Restituisce un **booleano** valore che indica se la proprietà trustServerCertificate è abilitata.|  
|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|Restituisce il percorso (incluso il nome file) del file trustStore del certificato.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|Restituisce l'URL utilizzato per la connessione all'origine dati.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|Restituisce il nome utente utilizzato per la connessione all'origine dati.|  
|[getUseSQLServerBaseDate](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Restituisce l'impostazione della proprietà di connessione useSQLServerBaseDate.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|Restituisce il nome del computer client utilizzato per la connessione all'origine dati.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|Restituisce un **booleano** valore che indica se la conversione di stati SQL in stati conformi a XOpen è abilitata.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)|Indica se questo oggetto origine dati è un wrapper per l'interfaccia specificata.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|Imposta il valore della **applicationIntent** proprietà di connessione.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|Imposta il nome dell'applicazione.|  
|[setAuthenticationScheme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|Indica il tipo di sicurezza integrata che si desidera venga utilizzata dall'applicazione.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|Imposta il nome del database a cui connettersi.|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|Imposta la descrizione dell'origine dati.|  
|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|Imposta un **booleano** valore che indica se la proprietà di crittografia è abilitata.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|Imposta il nome del server di failover utilizzato nella configurazione del mirroring del database.|  
|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|Imposta il nome host da utilizzare per la convalida del certificato SSL (Secure Sockets Layer) di SQL Server.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|Imposta il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] nome dell'istanza.|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|Imposta un **booleano** valore che indica se la proprietà integratedSecurity è abilitata.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|Imposta un **booleano** valore che indica se la proprietà lastUpdateCount è abilitata.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|Imposta un **int** valore che indica il numero di millisecondi di attesa prima che il database segnali un timeout di blocco.|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|Imposta il numero di secondi che questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto di attesa durante il tentativo di stabilire una connessione.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|Imposta un flusso di output dei caratteri da utilizzare per tutti i messaggi di registrazione e di traccia.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|Imposta il valore della **multiSubnetFailover** proprietà di connessione.|  
|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|Imposta le dimensioni di pacchetto di rete corrente utilizzata per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], specificato in byte.|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|Imposta la password utilizzata per connettersi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|Imposta il numero di porta utilizzato per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|Imposta la modalità per le connessioni create tramite questo di buffering delle risposte [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|Imposta il tipo di cursore predefinito utilizzato per tutti i set di risultati creati tramite questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|Imposta un **booleano** valore che indica se l'invio di parametri di stringa al server in formato UNICODE è abilitato.|  
|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|Specifica la modalità di invio dei valori java.sql.Time al server.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|Imposta il nome del computer che esegue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|Imposta un **booleano** valore che indica se la proprietà trustServerCertificate è abilitata.|  
|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|Imposta il percorso (incluso il nome file) del file trustStore del certificato.|  
|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|Imposta la password utilizzata per verificare l'integrità dei dati del file trustStore.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|Imposta l'URL utilizzato per la connessione all'origine dati.|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|Imposta il nome utente utilizzato per la connessione all'origine dati.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|Imposta il nome del computer client utilizzato per la connessione all'origine dati.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|Imposta un **booleano** valore che indica se la conversione di stati SQL in stati conformi a XOpen è abilitata.|  
|[Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)|Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-metodi specifici.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
