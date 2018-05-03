---
title: I membri di SQLServerStatement | Documenti Microsoft
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
ms.topic: conceptual
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8a22ca95f835f2eec139359f24a486e15cbee2e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverstatement-members"></a>Membri di SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 Nessuno  
  
## <a name="fields"></a>Campi  
 Nessuno  
  
## <a name="inherited-fields"></a>Campi ereditati  
  
|Nome|Description|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverstatement.md)|Aggiunge il comando SQL specificato all'elenco corrente dei comandi per questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|Annulla l'istruzione SQL attualmente eseguita da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverstatement.md)|Svuota l'elenco corrente di comandi SQL per questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|Cancella tutti gli avvisi segnalati su questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[Chiudere](../../../connect/jdbc/reference/close-method-sqlserverstatement.md)|Rilascia questa [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) database e le risorse JDBC immediatamente anziché attendere che vengano automaticamente rilasciate dell'oggetto.|  
|[Eseguire](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)|Esegue l'istruzione SQL specificata, che può restituire più risultati.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)|Invia al database un batch di comandi da eseguire. Se tutti i comandi vengono eseguiti correttamente, restituisce una matrice di conteggi aggiornamenti.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)|Esegue l'istruzione SQL specificata e restituisce un singolo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)|Esegue l'istruzione SQL specificata, che può essere un'istruzione INSERT, UPDATE, MERGE o DELETE, oppure un'istruzione SQL che non restituisce nulla, quale un'istruzione SQL DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|Recupera il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto che ha generato questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|Recupera la direzione per il recupero delle righe dalle tabelle di database che è l'impostazione predefinita per set di risultati generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|Recupera il numero di risultati dei set di righe che rappresenta la dimensione di recupero predefinita per gli oggetti generati da questo set di risultati [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|Recupera le chiavi generate automaticamente che vengono create come risultato dell'esecuzione di questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|Recupera il numero massimo di byte che possono essere restituite per i caratteri e i valori di colonna di dati binari in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|Recupera il numero massimo di righe che un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto può contenere.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|Passa al risultato successivo di questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|Recupera il numero di secondi di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] dovrà attendere [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto per l'esecuzione.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|Recupera la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|Recupera il risultato corrente come un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|Recupera il set di risultati per la concorrenza [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|Recupera il set di risultati trattenibilità per [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|Recupera il set di risultati per tipo di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|Recupera il risultato corrente come conteggio aggiornamenti.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|Recupera il primo avviso segnalato dalle chiamate a questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.|  
|[IsClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|Indica se questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto è stato chiuso.|  
|[oggetto isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|Restituisce un valore che indica se è possibile aggiungere un'istruzione al pool di istruzioni fornito dall'utente.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)|Indica se questo oggetto istruzione è un wrapper per l'interfaccia specificata.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|Imposta il nome del cursore SQL sulla stringa specificata, che sarà utilizzata dai metodi Execute successivi.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|Imposta la modalità di elaborazione di escape.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|Fornisce al driver JDBC un hint per la direzione da utilizzare per l'elaborazione delle righe del set di risultati.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|Fornisce al driver JDBC un hint per il numero di righe che devono essere recuperate dal database, qualora siano necessarie più righe.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|Imposta il limite per il numero massimo di byte in un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) colonna archivia i valori binari al numero specificato di byte o carattere.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|Imposta il limite per il numero massimo di righe da qualsiasi [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto può contenere il numero specificato.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|Richiede che un'istruzione sia o meno inserita in un pool.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|Imposta il numero di secondi, il driver rimarrà in attesa di un [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto per eseguire il numero di secondi specificato.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|Imposta la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto distinzione **stringa completa** o **adattivo**.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)|Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-metodi specifici.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
