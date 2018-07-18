---
title: La memorizzazione nella cache per il Driver JDBC di metadati di istruzione preparata | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a291cfb9497cee4fea87db915ca088069c1ec3cf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833156"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Metadati di istruzione preparata la memorizzazione nella cache per il Driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

In questo articolo vengono fornite informazioni sulle due modifiche che vengono implementate per migliorare le prestazioni del driver.

## <a name="batching-of-unprepare-for-prepared-statements"></a>L'invio in batch di preparazione per le istruzioni preparate
Poiché è stato implementato versione 6.1.6-preview, un miglioramento delle prestazioni tramite riduzione dei round trip a SQL Server al server. In precedenza, per ogni query prepareStatement, una chiamata a unprepare anche di invio. A questo punto, il driver è batch unprepare query fino a soglia "ServerPreparedStatementDiscardThreshold", che ha un valore predefinito di 10.

> [!NOTE]  
>  Gli utenti possono modificare il valore predefinito con il metodo seguente: setServerPreparedStatementDiscardThreshold (valore int)

Una modifica di altre introdotta da 6.1.6-preview è che prima di questa driver sempre chiamerebbe sp_prepexec. A questo punto, per la prima esecuzione di un'istruzione preparata, il driver chiama sp_executesql e per il resto viene eseguita sp_prepexec e assegna un handle. Per reperire ulteriori dettagli [qui](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Gli utenti possono modificare il comportamento predefinito per le versioni precedenti di chiamare sempre sp_prepexec dall'impostazione enablePrepareOnFirstPreparedStatementCall per **true** utilizzando il metodo seguente: setEnablePrepareOnFirstPreparedStatementCall (valore booleano)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Elenco delle nuove API introdotte con questa modifica, per l'invio in batch di preparazione per le istruzioni preparate

 **SQLServerConnection**
 
|Nuovo metodo|Description|  
|-----------|-----------------|  
|getDiscardedServerPreparedStatementCount() int|Restituisce il numero di attualmente in attesa preparata istruzione unprepare azioni.|
|closeUnreferencedPreparedStatementHandles() void|Forza le richieste di unprepare per tutte le istruzioni preparate scartate in sospeso da eseguire.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Restituisce il comportamento per un'istanza di connessione specifica. Se false la prima esecuzione chiama sp_executesql e non prepara un'istruzione, dopo l'esecuzione del secondo caso chiama sp_prepexec e del programma di installazione effettivamente un handle di istruzione preparata. Seguenti esecuzioni chiamate sp_execute. Questo elimina la necessità di sp_unprepare in istruzione preparata chiudere se l'istruzione viene eseguita solo una volta. Il valore predefinito per questa opzione può essere modificato dalla chiamata setDefaultEnablePrepareOnFirstPreparedStatementCall().|
|setEnablePrepareOnFirstPreparedStatementCall(boolean value) void|Specifica il comportamento per un'istanza di connessione specifica. Se il valore è false la prima esecuzione chiama sp_executesql e non prepara un'istruzione, dopo l'esecuzione del secondo caso chiama sp_prepexec e del programma di installazione effettivamente un handle di istruzione preparata. Seguenti esecuzioni chiamate sp_execute. Questo elimina la necessità di sp_unprepare in istruzione preparata chiudere se l'istruzione viene eseguita solo una volta.|
|getServerPreparedStatementDiscardThreshold() int|Restituisce il comportamento per un'istanza di connessione specifica. Questa impostazione Controlla preparato in sospeso quanti Ignora istruzione azioni (sp_unprepare) possono essere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Se l'impostazione è < = 1, unprepare azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se è impostato su {@literal >} 1, queste chiamate sono raggruppate per evitare il sovraccarico della chiamata sp_unprepare troppo spesso. Il valore predefinito per questa opzione può essere modificato dalla chiamata getDefaultServerPreparedStatementDiscardThreshold().|
|setServerPreparedStatementDiscardThreshold(int value) void|Specifica il comportamento per un'istanza di connessione specifica. Questa impostazione Controlla preparato in sospeso quanti Ignora istruzione azioni (sp_unprepare) possono essere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Se l'impostazione è < = 1 unprepare azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se è impostata su 1 > queste chiamate sono raggruppate per evitare l'overhead della chiamata sp_unprepare troppo spesso.|

 **SQLServerDataSource**
 
|Nuovo metodo|Description|  
|-----------|-----------------|  
|setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall) void|Se questa configurazione è false la prima esecuzione di un'istruzione preparata chiama sp_executesql e non prepara un'istruzione, dopo l'esecuzione del secondo caso chiama sp_prepexec e del programma di installazione effettivamente un handle di istruzione preparata. Seguenti esecuzioni chiamate sp_execute. Questo elimina la necessità di sp_unprepare in istruzione preparata chiudere se l'istruzione viene eseguita solo una volta.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Se questa configurazione restituisce false, la prima esecuzione di un'istruzione preparata chiama sp_executesql e non prepara un'istruzione, dopo l'esecuzione del secondo caso, chiama sp_prepexec e del programma di installazione effettivamente un handle di istruzione preparata. Seguenti esecuzioni chiamate sp_execute. Questo elimina la necessità di sp_unprepare in istruzione preparata chiudere se l'istruzione viene eseguita solo una volta.|
|setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold) void|Questa impostazione Controlla preparato in sospeso quanti Ignora istruzione azioni (sp_unprepare) possono essere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Se l'impostazione è < = 1 unprepare azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se è impostato su {@literal >} 1 queste chiamate sono raggruppate per evitare l'overhead della chiamata sp_unprepare troppo spesso|
|getServerPreparedStatementDiscardThreshold() int|Questa impostazione Controlla preparato in sospeso quanti Ignora istruzione azioni (sp_unprepare) possono essere in attesa per ogni connessione prima che venga eseguita una chiamata per pulire l'handle in sospeso nel server. Se l'impostazione è < = 1 unprepare azioni vengono eseguite immediatamente in chiusura istruzione preparata. Se è impostato su {@literal >} 1 queste chiamate sono raggruppate per evitare l'overhead della chiamata sp_unprepare troppo spesso.|

## <a name="prepared-statement-metatada-caching"></a>Memorizzazione nella cache i metadati di istruzione preparata
A partire dalla versione 6.3.0-preview, Microsoft JDBC driver per SQL Server supporta la memorizzazione nella cache di istruzione preparata. Prima dell'anteprima di v6.3.0, se uno esegue una query che è stato già preparata e archiviata nella cache, chiamando di nuovo la stessa query non comporterà la preparazione. A questo punto, il driver esegue la ricerca di query nella cache e trovare l'handle ed eseguirlo con sp_execute.
Memorizzazione nella cache dei metadati di istruzione preparata è **disabilitato** per impostazione predefinita. Per abilitarlo, è necessario chiamare il metodo seguente per l'oggetto di connessione:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Per esempio: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Elenco delle nuove API introdotte con questa modifica, per l'istruzione preparata la memorizzazione nella cache di metadati

 **SQLServerConnection**
 
|Nuovo metodo|Description|  
|-----------|-----------------|  
|setDisableStatementPooling(boolean value) void|Imposta il pool di istruzione su true o false.|
|getDisableStatementPooling() booleano|Restituisce true se il pool di istruzioni è disabilitato.|
|setStatementPoolingCacheSize(int value) void|Specifica le dimensioni della cache dell'istruzione preparata per la connessione. Un valore inferiore a 1 non indica nessuna cache.|
|int getStatementPoolingCacheSize()|Restituisce le dimensioni della cache dell'istruzione preparata per la connessione. Un valore inferiore a 1 non indica nessuna cache.|
|int getStatementHandleCacheEntryCount()|Restituisce il numero corrente di handle di istruzione preparata in pool.|
|isPreparedStatementCachingEnabled() booleano|Se il pool di istruzione è attivato o meno per la connessione.|

 **SQLServerDataSource**
 
|Nuovo metodo|Description|  
|-----------|-----------------|  
|setDisableStatementPooling(boolean disableStatementPooling) void|Imposta l'istruzione pool su true o false|
|getDisableStatementPooling() booleano|Restituisce true se il pool di istruzioni è disabilitato.|
|setStatementPoolingCacheSize(int statementPoolingCacheSize) void|Specifica le dimensioni della cache dell'istruzione preparata per la connessione. Un valore inferiore a 1 non indica nessuna cache.|
|int getStatementPoolingCacheSize()|Restituisce le dimensioni della cache dell'istruzione preparata per la connessione. Un valore inferiore a 1 non indica nessuna cache.|

## <a name="see-also"></a>Vedere anche  
 [Uso del driver JDBC per il miglioramento di prestazioni e affidabilità](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
