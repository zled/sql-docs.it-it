---
title: I membri di SQLServerCallableStatement | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: Assembly
ms.assetid: 5ebdc186-e50f-4d14-bbf4-95af5051e4a4
caps.latest.revision: 50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4efa8910cb11b6cada26afa4ebd034db8aac242c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlservercallablestatement-members"></a>Membri di SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 Nessuno  
  
## <a name="fields"></a>Campi  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="inherited-fields"></a>Campi ereditati  
 Nessuno  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Aggiunge un set di parametri al batch di comandi per questo oggetto CallableStatement.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Annulla l'istruzione SQL attualmente eseguita da questo oggetto CallableStatement.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Svuota l'elenco corrente di comandi SQL per questo oggetto CallableStatement.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Cancella immediatamente i valori di parametro correnti.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Cancella tutti gli avvisi segnalati su questo oggetto CallableStatement.|  
|[Chiudere](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Rilascia le risorse JDBC di questo oggetto CallableStatement immediatamente anziché attendere che vengano automaticamente rilasciate e di database.|  
|[Eseguire](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Esegue l'istruzione SQL in questo oggetto CallableStatement, che può essere qualsiasi tipo di istruzione SQL.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Invia al database un batch di comandi da eseguire. Se tutti i comandi vengono eseguiti correttamente, restituisce una matrice di conteggi aggiornamenti.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Esegue la query SQL in questo oggetto CallableStatement e restituisce il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato dalla query.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Esegue l'istruzione SQL in questo oggetto CallableStatement, che deve essere un'istruzione SQL INSERT, l'istruzione UPDATE, MERGE o DELETE. o un'istruzione SQL che non restituisce nulla, quale un'istruzione DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto che ha generato questo oggetto CallableStatement.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Recupera il valore della colonna specificata come un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera la direzione per il recupero di righe da tabelle di database che rappresenta il valore predefinito per il set di risultati generati da questo oggetto CallableStatement.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero di righe del set di risultati che rappresenta la dimensione di recupero predefinita per il risultato set di oggetti generati da questo oggetto CallableStatement.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera le chiavi generate automaticamente che vengono create come risultato dell'esecuzione di questo oggetto CallableStatement.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero massimo di byte che possono essere restituite per i caratteri e i valori di colonna di dati binari in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo oggetto CallableStatement.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero massimo di righe che un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo oggetto CallableStatement può contenere.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Recupera un [classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) oggetto che contiene informazioni sulle colonne di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) che sarà restituite quando viene eseguito questo oggetto CallableStatement.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Passa al risultato successivo di questo oggetto CallableStatement.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Recupera il numero, tipi e le proprietà dei parametri per questo oggetto CallableStatement.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto matrice.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come flusso di **ASCII** caratteri.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto java.math.BigDecimal.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come flusso binario di byte senza interruzioni.|  
|[GetBlob](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)|Recupera il valore del parametro Blob JDBC designato come oggetto Blob nel linguaggio di programmazione Java.|  
|[GetBoolean](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **booleano** valore.|  
|[GetByte](../../../connect/jdbc/reference/getbyte-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **byte** valore.|  
|[GetBytes](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come matrice di byte.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto java.io.Reader.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)|Recupera il valore del parametro Blob JDBC designato come oggetto Clob nel linguaggio di programmazione Java.|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto java.sql.Date nel linguaggio di programmazione Java.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Recupera il valore della colonna specificata come un[classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.|  
|[GetDouble](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **doppie** nel linguaggio di programmazione Java.|  
|[GetFloat](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **float** nel linguaggio di programmazione Java.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **int** nel linguaggio di programmazione Java.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **lungo** nel linguaggio di programmazione Java.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto lettore.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)|Recupera il valore di JDBC designato **NCLOB** parametro come un **NClob** oggetto nel linguaggio di programmazione Java.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)|Recupera il valore del tipo designato **NCHAR**, **NVARCHAR** o **LONGNVARCHAR** parametro sotto forma di stringa nel linguaggio linguaggio di programmazione.|  
|[GetObject](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto nel linguaggio di programmazione Java.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il numero di secondi di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] attenderà per l'esecuzione dell'oggetto CallableStatement.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto di riferimento nel linguaggio di programmazione Java.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il risultato corrente come un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il set di risultati per la concorrenza [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo oggetto CallableStatement.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il set di risultati trattenibilità per [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo oggetto CallableStatement.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il set di risultati per tipo di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo oggetto CallableStatement.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **breve** nel linguaggio di programmazione Java.|  
|[GetString](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come un **stringa** nel linguaggio di programmazione Java.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto java.sql.SQLXML.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto java.sql.Time nel linguaggio di programmazione Java.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto java.sql.Timestamp nel linguaggio di programmazione Java.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il risultato corrente come conteggio aggiornamenti.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)|Recupera il valore del parametro designato come oggetto nel linguaggio di programmazione Java URL.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Recupera il primo avviso segnalato dalle chiamate a questo oggetto CallableStatement.|  
|[IsClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Indica se questo oggetto istruzione è stata chiusa.|  
|[oggetto isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Restituisce un valore che indica se è possibile aggiungere un'istruzione al pool di istruzioni fornito dall'utente.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)|Indica se questo oggetto istruzione è un wrapper per l'interfaccia specificata.|  
|[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)|Registra il parametro OUT.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Imposta il numero di parametro designato sull'oggetto di matrice specificato.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)|Imposta il parametro designato sul flusso di input specificato.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlservercallablestatement.md)|Imposta il numero di parametro designato sull'oggetto BigDecimal specificato.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)|Imposta il parametro designato sul flusso di input specificato.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Imposta il parametro designato sull'oggetto Blob specificato.|  
|[SetBoolean](../../../connect/jdbc/reference/setboolean-method-sqlservercallablestatement.md)|Imposta il parametro designato il dato **booleano** valore.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlservercallablestatement.md)|Imposta il parametro designato il dato **byte** valore.|  
|[SetBytes](../../../connect/jdbc/reference/setbytes-method-sqlservercallablestatement.md)|Imposta il parametro designato sulla matrice specificata di **byte** valori.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto lettore specificato.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Imposta il parametro designato sull'oggetto specificato.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il nome del cursore SQL sulla stringa specificata, che sarà utilizzata dai metodi Execute successivi.|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlservercallablestatement.md)|Imposta il parametro designato sul valore di data specificato.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|Imposta il valore della colonna specificata per il [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore.|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlservercallablestatement.md)|Imposta il parametro designato il dato **doppie** valore.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta la modalità di elaborazione di escape.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Fornisce al driver JDBC un hint per la direzione da utilizzare per l'elaborazione delle righe del set di risultati.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Fornisce al driver JDBC un hint per il numero di righe che devono essere recuperate dal database, qualora siano necessarie più righe.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto specificato **float** valore.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto specificato **int** valore.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto specificato **lungo** valore.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il limite per il numero massimo di byte in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) colonna archivia i valori binari al numero specificato di byte o carattere.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il limite per il numero massimo di righe da qualsiasi [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto può contenere il numero specificato.|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)|Imposta il parametro designato per l'oggetto Reader specificato.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto specificato.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)|Imposta il parametro designato per l'oggetto String specificato.|  
|[SetNull](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)|Imposta il parametro designato su un valore Null, in base al tipo di parametro da impostare.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)|Imposta il valore del parametro designato tramite l'oggetto specificato.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Richiede che un'istruzione sia o meno inserita in un pool. Per impostazione predefinita, viene inserito quando crea un oggetto SQLServerCallableStatement.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta il numero di secondi, che il driver rimarrà in attesa per un oggetto CallableStatement eseguire il numero di secondi specificato.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Imposta il parametro designato sull'oggetto di riferimento specificato.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Ereditato da [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Imposta la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto distinzione **stringa completa** o **adattivo**.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto specificato **breve** valore.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)|Imposta il parametro designato per il linguaggio specificato **stringa** valore.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlservercallablestatement.md)|Imposta il parametro designato sull'oggetto specificato **SQLXML** oggetto.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)|Imposta il parametro designato sul valore di ora specificato.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)|Imposta il parametro designato sul valore timestamp specificato.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|(Ereditato da [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Imposta il numero di parametro designato sul flusso di input specificato, che disporrà del numero specificato di byte.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlservercallablestatement.md)|Imposta il parametro designato sul valore di URL specificato.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)|Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-metodi specifici.|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlservercallablestatement.md)|Recupera informazioni circa l'eventuale impostazione del valore SQL NULL per l'ultimo parametro OUT letto.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement|addBatch, clearBatch, clearParameters, close, execute, executeBatch, executeQuery, executeUpdate, getMetaData, getParameterMetaData, setArray, setAsciiStream, setBigDecimal, setBinaryStream, setBlob, setboolean, setByte, setBytes, setCharacterStream, setClob, setDate, setDouble, setFloat, setInt, setLong, setNull, setObject, setRef, setShort, setString, setTime, setTimestamp, setUnicodeStream, setURL|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|class java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait,|  
|java.sql.PreparedStatement|addBatch, clearParameters, execute, executeQuery, executeUpdate, getMetaData, getParameterMetaData, getSQLXML, setArray, setAsciiStream, setBigDecimal, setBinaryStream, setBlob, setboolean, setByte, setBytes, setCharacterStream, setClob, setDate, setDate, setDouble, setFloat, setInt, setLong, setNull, setObject, setRef, setShort, setString, setSQLXML, setTime, setTimestamp, setUnicodeStream, setURL|  
|java.sql.Statement|addBatch, cancel, clearBatch, clearWarnings, close, execute, executeBatch, executeQuery, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
