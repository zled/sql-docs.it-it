---
title: I membri di SQLServerResultSet | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a438d5d-2d6a-46a0-a2ae-f35fbae4a472
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 16088d8260afdd23c89d4d583153193b894f8249
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverresultset-members"></a>Membri di SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 nessuna.  
  
## <a name="fields"></a>Campi  
  
|Nome|Description|  
|----------|-----------------|  
|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] il tipo di concorrenza ottimistica senza alcun blocco di riga di lettura/scrittura.|  
|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] il tipo di concorrenza ottimistica senza alcun blocco di riga di lettura/scrittura.|  
|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] il tipo di concorrenza ottimistica con blocchi di riga di lettura/scrittura.|  
|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di cursore fast forward only di sola lettura.|  
|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di cursore dinamico.|  
|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] il tipo di cursore keyset.|  
|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di cursore statico.|  
|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|Utilizzato per specificare un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di cursore fast forward only di sola lettura.|  
  
## <a name="inherited-fields"></a>Campi ereditati  
  
|Classe ereditata da:|Description|  
|---------------------------|-----------------|  
|java.sql.ResultSet|CLOSE_CURSORS_AT_COMMIT, CONCUR_READ_ONLY, CONCUR_UPDATABLE, FETCH_FORWARD, FETCH_REVERSE, FETCH_UNKNOWN, HOLD_CURSORS_OVER_COMMIT, TYPE_FORWARD_ONLY, TYPE_SCROLL_INSENSITIVE, TYPE_SCROLL_SENSITIVE|  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[assoluto](../../../connect/jdbc/reference/absolute-method-sqlserverresultset.md)|Sposta il cursore nella riga specificata in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[afterLast](../../../connect/jdbc/reference/afterlast-method-sqlserverresultset.md)|Sposta il cursore dopo l'ultima riga di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[beforeFirst](../../../connect/jdbc/reference/beforefirst-method-sqlserverresultset.md)|Sposta il cursore prima della prima riga di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[cancelRowUpdates](../../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md)|Annulla gli aggiornamenti apportati alla riga corrente in questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverresultset.md)|Cancella tutti gli avvisi segnalati su questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[Chiudere](../../../connect/jdbc/reference/close-method-sqlserverresultset.md)|Rilascia questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) dell'oggetto database e le risorse JDBC immediatamente anziché attendere che ciò si verifica quando viene chiuso automaticamente.|  
|[deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)|Elimina la riga corrente da questo[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto e dal database sottostante.|  
|[finalizzazione](../../../connect/jdbc/reference/finalize-method-sqlserverresultset.md)|Chiude in modo esplicito questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[findColumn](../../../connect/jdbc/reference/findcolumn-method-sqlserverresultset.md)|Recupera l'indice della prima colonna corrispondente per il nome della colonna specificata in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[primo](../../../connect/jdbc/reference/first-method-sqlserverresultset.md)|Sposta il cursore sulla prima riga di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un oggetto matrice.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un flusso di caratteri ASCII.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)|Recupera il valore di indice della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un BigDecimal.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come flusso binario di byte non interpretati.|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto Blob nel linguaggio di programmazione Java.|  
|[getBoolean](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **booleano** nel linguaggio di programmazione Java.|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **byte** nel linguaggio di programmazione Java.|  
|[getBytes](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **byte** matrice nel linguaggio di programmazione Java.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.IO. Reader.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto Clob nel linguaggio di programmazione Java.|  
|[getConcurrency](../../../connect/jdbc/reference/getconcurrency-method-sqlserverresultset.md)|Recupera la modalità di concorrenza dell'oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getCursorName](../../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)|Recupera il nome del cursore SQL utilizzato da questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.SQL. date nel linguaggio di programmazione Java.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)|Recupera il valore della colonna specificata come un[classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **doppie** nel linguaggio di programmazione Java.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverresultset.md)|Recupera la direzione di recupero per questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)|Recupera la dimensione di recupero per questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **float** nel linguaggio di programmazione Java.|  
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverresultset.md)|Recupera la trattenibilità [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **int** nel linguaggio di programmazione Java.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **lungo** nel linguaggio di programmazione Java.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)|Recupera il numero, tipi e le proprietà di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) colonne dell'oggetto.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente del [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come lettore.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente del [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)oggetto come un **NClob** oggetto nel linguaggio di programmazione Java.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente del [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto sotto forma di stringa nel linguaggio linguaggio di programmazione.|  
|[getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)|Ottiene il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto nel linguaggio di programmazione Java.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto di riferimento nel linguaggio di programmazione Java.|  
|[getRow](../../../connect/jdbc/reference/getrow-method-sqlserverresultset.md)|Recupera il numero di riga corrente.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **breve** nel linguaggio di programmazione Java.|  
|[getStatement](../../../connect/jdbc/reference/getstatement-method-sqlserverresultset.md)|Recupera il [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto che ha generato questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **stringa** nel linguaggio di programmazione Java.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente del [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **SQLXML** oggetto.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.SQL. Time nel linguaggio di programmazione Java.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.SQL. timestamp nel linguaggio di programmazione Java.|  
|[getType](../../../connect/jdbc/reference/gettype-method-sqlserverresultset.md)|Recupera il tipo di cursore di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getUnicodeStream](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come flusso di caratteri Unicode.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)|Recupera il valore della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come URL.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverresultset.md)|Recupera il primo avviso segnalato dalle chiamate a questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)|Inserisce il contenuto della riga di inserimento in questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto e nel database.|  
|[isAfterLast](../../../connect/jdbc/reference/isafterlast-method-sqlserverresultset.md)|Specifica se il cursore si trova dopo l'ultima riga in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[isBeforeFirst](../../../connect/jdbc/reference/isbeforefirst-method-sqlserverresultset.md)|Specifica se il cursore si trova prima della prima riga in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverresultset.md)|Indica se questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto è stato chiuso.|  
|[isFirst](../../../connect/jdbc/reference/isfirst-method-sqlserverresultset.md)|Specifica se il cursore si trova nella prima riga di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[isLast](../../../connect/jdbc/reference/islast-method-sqlserverresultset.md)|Specifica se il cursore si trova nell'ultima riga di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[ultimo](../../../connect/jdbc/reference/last-method-sqlserverresultset.md)|Sposta il cursore sull'ultima riga in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[moveToCurrentRow](../../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)|Sposta il cursore nella posizione memorizzata, generalmente la riga corrente.|  
|[moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)|Sposta il cursore nella riga di inserimento.|  
|[Avanti](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)|Sposta il cursore di una riga verso il basso dalla posizione corrente.|  
|[precedente](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)|Sposta il cursore alla riga precedente in questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[refreshRow](../../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md)|Aggiorna la riga corrente con il relativo valore più recente nel database.|  
|[relativo](../../../connect/jdbc/reference/relative-method-sqlserverresultset.md)|Sposta il cursore della quantità specificata di righe rispetto alla riga corrente, in direzione positiva o negativa.|  
|[rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)|Recupera informazioni circa l'eventuale eliminazione di una riga.|  
|[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)|Recupera informazioni sull'eventuale presenza di un inserimento nella riga corrente.|  
|[rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md)|Recupera informazioni sull'eventuale aggiornamento della riga corrente.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)|Fornisce un hint per la direzione in cui le righe in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto verrà elaborato.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)|Fornisce al driver JDBC un hint per il numero di righe che devono essere recuperate dal database quando sono necessarie più righe per questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[updateArray](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)|Aggiorna la colonna designata con un oggetto matrice.|  
|[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore del flusso ASCII.|  
|[updateBigDecimal](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)|Aggiorna la colonna designata con un oggetto BigDecimal.|  
|[updateBinaryStream](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore del flusso binario.|  
|[updateBlob](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore java.sql.Blob.|  
|[updateBoolean](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **booleano** valore.|  
|[updateByte](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **byte** valore.|  
|[updateBytes](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)|Aggiorna la colonna designata con una matrice di **byte** valori.|  
|[updateCharacterStream](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore del flusso di caratteri.|  
|[updateClob](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore java.sql.Clob.|  
|[updateDate](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore di data.|  
|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)|Gli aggiornamenti una [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) colonna.|  
|[updateDouble](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **doppie** valore.|  
|[updateFloat](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **float** valore.|  
|[updateInt](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **int** valore.|  
|[updateLong](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **lungo** valore.|  
|[updateNCharacterStream](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore del flusso di caratteri.|  
|[updateNClob](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)|Aggiorna la colonna designata con il valore di oggetto specificato.|  
|[updateNString](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **stringa** valore.|  
|[updateNull](../../../connect/jdbc/reference/updatenull-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore Null.|  
|[updateObject](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **oggetto** valore.|  
|[updateRef](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore java.sql.Ref.|  
|[updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)|Aggiorna il database sottostante con il nuovo contenuto della riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[updateShort](../../../connect/jdbc/reference/updateshort-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **breve** valore.|  
|[updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **stringa** valore.|  
|[updateSQLXML](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)|Aggiorna la colonna designata con un **SQLXML** valore.|  
|[updateTime](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore di ora.|  
|[updateTimestamp](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)|Aggiorna la colonna designata con un valore di timestamp.|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlserverresultset.md)|Verifica se l'ultimo valore letto è un valore Null.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
