---
title: Funzioni API di livello 1, il Driver ODBC per Oracle | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC level 1 API functions [ODBC]
- ODBC driver for Oracle [ODBC], functions
- level 1 API functions [ODBC]
- API functions [ODBC]
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3cd7f827ecfc367536654b9ad825302f4dba9fcf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>Funzioni API di livello 1 (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Supporta funzioni in questo livello forniscono la conformità di interfaccia di base oltre a funzionalità aggiuntive, ad esempio delle transazioni.  
  
|Funzione API|Note|  
|------------------|-----------|  
|**SQLColumns**|Crea un set di risultati per una tabella, ovvero l'elenco di colonne per la tabella specificata o tabelle. Quando si richiedono di colonne per un sinonimo PUBLIC, è necessario aver impostato l'attributo di connessione SYNONYMCOLUMNS e specificare una stringa vuota come il *szTableOwner* argomento. Quando la restituzione di colonne per il sinonimo PUBLIC, il driver imposta la colonna nome della tabella in una stringa vuota. Il set di risultati contiene una colonna aggiuntiva, posizione ORDINALE, alla fine di ogni riga. Questo valore è la posizione ordinale della colonna nella tabella.|  
|**SQLDriverConnect**|Si connette a un'origine dati esistente. Per informazioni dettagliate, vedere [formato stringa di connessione e gli attributi](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**SQLGetConnectOption**|Restituisce l'impostazione corrente dell'opzione di connessione. Questa funzione è supportata parzialmente. Il driver supporta tutti i valori per il *fOption* argomento ma non supporta alcune *vParam* valori per il *fOption* argomento [SQL_TXN_ISOLATION ](../../odbc/microsoft/connect-options.md). Per ulteriori informazioni, vedere [opzioni di connessione](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Recupera il valore di un singolo campo del record corrente del set di risultati specificato.|  
|**SQLGetFunctions**|Restituisce TRUE per tutte le funzioni supportate. Implementato da Gestione Driver.|  
|**SQLGetInfo**|Restituisce informazioni, tra cui SQLHDBC, SQLUSMALLINT, SQLPOINTER, SQLSMALLINT e SQLSMALLINT \*, riguardanti il Driver ODBC per Oracle e l'origine dati associata a un handle di connessione, *hdbc*.|  
|**SQLGetStmtOption**|Restituisce l'impostazione corrente di un'opzione di istruzione. Per ulteriori informazioni, vedere [opzioni dell'istruzione](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Restituisce informazioni sui tipi di dati supportati da un'origine dati. Il driver restituisce le informazioni in un set di risultati SQL.|  
|**SQLParamData**|Usato in combinazione con **SQLPutData** per specificare i dati del parametro in fase di esecuzione di istruzione.|  
|**SQLPutData**|Consente a un'applicazione inviare i dati per un parametro o una colonna per il driver in fase di esecuzione di istruzione.|  
|**SQLSetConnectOption**|Consente di accedere alle opzioni che controllano gli aspetti della connessione. Questa funzione è supportata parzialmente: il driver supporta tutti i valori per il *fOption* argomento ma non supporta alcune *vParam* valori per il *fOption* argomento [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Per ulteriori informazioni, vedere [opzioni di connessione](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Imposta le opzioni relative a un handle di istruzione, *hstmt*. Per ulteriori informazioni, vedere [opzioni dell'istruzione](../../odbc/microsoft/statement-options.md).|  
|**SQLSpecialColumns**|Recupera il set di colonne ottimale che identifica in modo univoco una riga nella tabella.|  
|**SQLStatistics**|Recupera un elenco delle statistiche su una singola tabella e indici o nomi di tag associati alla tabella. Il driver restituisce le informazioni come set di risultati.|  
|**SQLTables**|Restituisce l'elenco dei nomi di tabella specificato dal parametro di **SQLTables** istruzione. Se viene specificato alcun parametro, restituisce i nomi delle tabelle archiviate nell'origine dati corrente. Il driver restituisce le informazioni come set di risultati.<br /><br /> Chiamate di tipo di enumerazione non riceveranno una voce del set di risultati per visualizzazioni remote o locale con parametri. Tuttavia, una chiamata a **SQLTables** con una tabella univoca identificatore di nome verrà trovata una corrispondenza per una vista, se presente, con lo stesso nome; in questo modo l'API verificare i conflitti di nome prima di creare una nuova tabella.<br /><br /> Il sinonimo PUBLIC viene restituito con un valore TABLE_OWNER "".<br /><br /> VISTE di proprietà di sistema o SYS vengono identificate come vista di sistema.|

