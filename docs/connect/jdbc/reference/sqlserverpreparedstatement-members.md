---
title: I membri di SQLServerPreparedStatement | Documenti Microsoft
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
ms.assetid: 2363902f-d4c6-4cd4-a5fc-86079eb9e418
caps.latest.revision: "38"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 05f80d22f4eb968f6db9ce24a8c5e9808bd43356
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverpreparedstatement-members"></a>Membri di SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 nessuna.  
  
## <a name="fields"></a>Campi  
 nessuna.  
  
## <a name="inherited-fields"></a>Campi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|Aggiunge un set di parametri al batch di comandi per questo oggetto istruzione.|  
|[Annulla](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Annulla l'istruzione SQL attualmente eseguita da questo oggetto istruzione.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|Svuota l'elenco corrente di comandi SQL per questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|Cancella immediatamente i valori di parametro correnti.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Cancella tutti gli avvisi segnalati su questo oggetto istruzione.|  
|[Chiudere](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|Rilascia le risorse JDBC di questo oggetto istruzione immediatamente anziché attendere che vengano automaticamente rilasciate e di database.|  
|[eseguire](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|Esegue l'istruzione SQL in questo oggetto istruzione, che può essere qualsiasi tipo di istruzione SQL.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|Invia al database un batch di comandi da eseguire. Se tutti i comandi vengono eseguiti correttamente, restituisce una matrice di conteggi aggiornamenti.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|Esegue la query SQL in questo oggetto istruzione e restituisce il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato dalla query.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|Esegue l'istruzione SQL in questo oggetto istruzione, che deve essere un'istruzione SQL INSERT, l'istruzione UPDATE, MERGE o DELETE. o un'istruzione SQL che non restituisce nulla, quale un'istruzione DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto che ha generato questo oggetto istruzione.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera la direzione per il recupero di righe da tabelle di database che rappresenta il valore predefinito per il set di risultati generati da questo oggetto istruzione.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero di righe del set di risultati che rappresenta la dimensione di recupero predefinita per il risultato set di oggetti generati da questo oggetto istruzione.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera le chiavi generate automaticamente che vengono create come risultato dell'esecuzione di questo oggetto istruzione.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero massimo di byte che possono essere restituite per i caratteri e i valori di colonna di dati binari in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo oggetto istruzione.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero massimo di righe che un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo oggetto istruzione può contenere.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|Recupera un [classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) oggetto che contiene informazioni sulle colonne di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) che sarà restituite quando viene eseguito questo oggetto istruzione.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Passa al risultato successivo di questo oggetto istruzione.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|Recupera il numero, tipi e le proprietà dei parametri per questo oggetto istruzione.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero di secondi di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] rimarrà in attesa per questo oggetto istruzione per l'esecuzione.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il risultato corrente come un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il set di risultati per la concorrenza [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo oggetto istruzione.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il set di risultati trattenibilità per [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo oggetto istruzione.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il set di risultati per tipo di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo oggetto istruzione.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md),) recupera il risultato corrente come conteggio aggiornamenti.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il primo avviso segnalato dalle chiamate a questo oggetto istruzione.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Indica se questo oggetto istruzione è stata chiusa.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Restituisce un valore che indica se è possibile aggiungere un'istruzione al pool di istruzioni fornito dall'utente.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)|Indica se questo oggetto istruzione è un wrapper per l'interfaccia specificata.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|Imposta il numero di parametro designato sull'oggetto di matrice specificato.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)|Imposta il numero di parametro designato sull'oggetto InputStream specificato.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlserverpreparedstatement.md)|Imposta il numero di parametro designato sull'oggetto BigDecimal specificato.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sul flusso di input specificato.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto Blob specificato.|  
|[SetBoolean](../../../connect/jdbc/reference/setboolean-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **booleano** valore.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **byte** valore.|  
|[setBytes](../../../connect/jdbc/reference/setbytes-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sulla matrice di byte specificata.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)|Imposta il parametro designato per l'oggetto Reader specificato.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto Clob specificato.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il nome del cursore SQL sulla stringa specificata, che sarà utilizzata dai metodi Execute successivi.|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sul valore di data specificato.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|Imposta il valore della colonna specificata per il [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore.|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **doppie** valore.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta la modalità di elaborazione di escape.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Fornisce al driver JDBC un hint per la direzione da utilizzare per l'elaborazione delle righe del set di risultati.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Fornisce al driver JDBC un hint per il numero di righe che devono essere recuperate dal database, qualora siano necessarie più righe.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **float** valore.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **int** valore.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **lungo** valore.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il limite per il numero massimo di byte in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) colonna archivia i valori binari al numero specificato di byte o carattere.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il limite per il numero massimo di righe da qualsiasi [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto può contenere il numero specificato.|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)|Imposta il parametro designato per l'oggetto Reader specificato.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)|Imposta il parametro designato su un valore Null, in base al tipo di parametro da impostare.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)|Imposta il parametro designato sull'oggetto specificato **stringa** oggetto.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)|Imposta il valore del parametro designato tramite l'oggetto specificato.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Richiede che un'istruzione sia o meno inserita in un pool. Per impostazione predefinita, viene inserito quando crea un oggetto SQLServerPreparedStatement.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il numero di secondi, che il driver rimarrà in attesa per un oggetto istruzione da eseguire fino al numero di secondi specificato.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto di riferimento specificato.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto distinzione **stringa completa** o **adattivo**.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **breve** valore.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **stringa** valore.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sull'oggetto specificato **SQLXML** oggetto.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sul valore di ora specificato.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sul valore timestamp specificato.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|Imposta il numero del parametro designato sul flusso di input specificato, che disporrà del numero specificato di byte.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverpreparedstatement.md)|Imposta il parametro designato sul valore di URL specificato.|  
|[Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)|Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-metodi specifici.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Statement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
