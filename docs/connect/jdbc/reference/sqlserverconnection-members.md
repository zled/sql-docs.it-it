---
title: I membri di SQLServerConnection | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 15e9af6857ca3a7f4c6695835d19e4900dfbf319
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverconnection-members"></a>Membri di SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 Nessuno  
  
## <a name="fields"></a>Campi  
  
|Nome|Description|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|Consente di specificare il livello di isolamento delle transazioni snapshot.|  
  
## <a name="inherited-fields"></a>Campi ereditati  
  
|Classe ereditata da:|Description|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE, TRANSACTION_READ_COMMITTED, TRANSACTION_READ_UNCOMMITTED, TRANSACTION_REPEATABLE_READ, TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|Cancella tutti gli avvisi segnalati per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[Chiudere](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|Rilascia il database per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto e le risorse JDBC immediatamente anziché attendere che vengano automaticamente rilasciate.|  
|[closeUnreferencedPreparedStatementHandles](../../../connect/jdbc/reference/closeunreferencedpreparedstatementhandles-method-sqlserverconnection.md)|Forza l'annullamento-preparare le richieste per le istruzioni preparate scartate in sospeso da eseguire.| 
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)|Rende tutte permanenti le modifiche apportate dopo il commit o rollback precedente e rilascia eventuali blocchi del database che sono correntemente utilizzati da questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)|Crea un **Java.SQL** oggetto senza dati.|  
|[createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)|Crea un **Java.SQL** oggetto senza dati.|  
|[createNClob](../../../connect/jdbc/reference/createnclob-method-sqlserverconnection.md)|Crea un **Java.SQL. NClob** oggetto senza dati.|  
|[createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)|Crea un [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto per l'invio di istruzioni SQL al database.|  
|[createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)|Crea un **Java.SQL** oggetto senza dati.|  
|[getAutoCommit](../../../connect/jdbc/reference/getautocommit-method-sqlserverconnection.md)|Recupera la modalità autocommit corrente per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[getCatalog](../../../connect/jdbc/reference/getcatalog-method-sqlserverconnection.md)|Recupera il nome del catalogo corrente per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[Metodo getClientConnectionID &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|Ottiene l'ID connessione del tentativo di connessione più recente, indipendentemente dalla riuscita o meno del tentativo.|  
|[getClientInfo](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)|Recupera informazioni relative alle proprietà delle informazioni client supportate dal driver JDBC.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverconnection.md)|Restituisce il valore di **disableStatementPooling** proprietà di connessione. Questa impostazione controlla se il pool di istruzione è attivato o meno per la connessione.|
|[getDiscardedServerPreparedStatementCount](../../../connect/jdbc/reference/getdiscardedserverpreparedstatementcount-method-sqlserverconnection.md)|Restituisce il numero di attualmente in attesa preparata istruzione unprepare azioni.|
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Restituisce il valore di **enablePrepareOnFirstPreparedStatementCall** proprietà di connessione.|
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|Recupera la trattenibilità corrente [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti creati tramite questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|Recupera un [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) oggetto che contiene i metadati sul database a cui [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto rappresenta una connessione.|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Restituisce il valore di **serverPreparedStatementDiscardThreshold** proprietà di connessione.|  
|[getStatementHandleCacheEntryCount](../../../connect/jdbc/reference/getstatementhandlecacheentrycount-method-sqlserverconnection.md)|Restituisce il numero corrente di handle di istruzione preparata in pool.|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverconnection.md)|Restituisce le dimensioni della cache dell'istruzione preparata per la connessione.|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|Recupera il livello di isolamento corrente per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|Recupera l'oggetto mappa che è associata a questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|Recupera il primo avviso segnalato dalle chiamate a questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[IsClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|Indica se questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto è stato chiuso.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|Indica se questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto è in modalità di sola lettura.|  
|[isStatementPoolingEnabled](../../../connect/jdbc/reference/isstatementpoolingenabled-method-sqlserverconnection.md)|Restituisce se il pool di istruzione è attivato o meno per la connessione.|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|Indica se questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto non è stato chiuso ed è ancora valido.|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|Converte l'istruzione SQL specificata nella grammatica SQL nativa del server di database.|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|Crea un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto per la chiamata di stored procedure del database.|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|Crea un [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto per l'invio di parametri di istruzioni SQL al database.|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|Rimuove l'oggetto specificato [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto dalla transazione corrente.|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|Annulla tutte le modifiche apportate nella transazione corrente e rilascia eventuali blocchi del database attualmente mantenuti attivi da questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|Imposta la modalità autocommit per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto allo stato specificato.|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|Imposta il nome di catalogo specificato per selezionare uno spazio secondario di questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) database dell'oggetto da utilizzare.|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|Imposta il valore delle proprietà delle informazioni client.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverconnection.md)|Imposta il pool di istruzione su true o false.|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Specifica il nuovo valore del **enablePrepareOnFirstPreparedStatementCall** proprietà di connessione.|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|Imposta sul valore [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti creati tramite questo [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto per la trattenibilità specificata.|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|Inserito [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto in modalità di sola lettura come hint per il driver JDBC per abilitare le ottimizzazioni del database.|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|Crea un punto di salvataggio senza nome nella transazione corrente e restituisce il nuovo [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto che lo rappresenta.|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Imposta il valore di nuovo il **serverPreparedStatementDiscardThreshold** proprietà di connessione.|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverconnection.md)|Imposta le dimensioni della cache dell'istruzione preparata per la connessione.|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|Tenta di modificare il livello di isolamento delle transazioni per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto a quello specificato.|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|Installa l'oggetto TypeMap specificato come mappa del tipo per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.lang.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
