---
title: Gli aggiornamenti (ODBC) posizionati | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f03932af79d51cd78b2b72aad5cd9b6e44df1f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="positioned-updates-odbc"></a>Aggiornamenti posizionati (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In ODBC sono supportati due metodi per eseguire gli aggiornamenti posizionati in un cursore:  
  
-   **SQLSetPos**  
  
-   Clausola WHERE CURRENT OF  
  
 L'approccio più comune consiste nell'utilizzare **SQLSetPos**. che dispone delle opzioni seguenti.  
  
 SQL_POSITION  
 Posiziona il cursore in una riga specifica del set di righe corrente.  
  
 SQL_REFRESH  
 Aggiorna le variabili di programma associate alle colonne del set di risultati in base ai valori della riga su cui è posizionato il cursore.  
  
 SQL_UPDATE  
 Aggiorna la riga corrente del cursore con i valori archiviati nelle variabili di programma associate alle colonne del set di risultati.  
  
 SQL_DELETE  
 Elimina la riga corrente dal cursore.  
  
 **SQLSetPos** può essere utilizzato con qualsiasi istruzione set di risultati quando gli attributi del cursore handle di istruzione sono impostati per utilizzare i cursori del server. Le colonne del set di risultati devono essere associate a variabili di programma. Non appena il recupero di una riga chiama **SQLSetPos**(SQL_POSTION) per posizionare il cursore sulla riga. È possibile quindi chiamare SQLSetPos (SQL_DELETE) per eliminare la riga corrente o spostare i nuovi valori dei dati nelle variabili di programma associate e chiamare SQLSetPos (SQL_UPDATE) per aggiornare la riga corrente.  
  
 Le applicazioni possono aggiornare o eliminare qualsiasi riga nel set di righe con **SQLSetPos**. La chiamata **SQLSetPos** rappresenta un'alternativa utile alla creazione ed esecuzione di un'istruzione SQL. **SQLSetPos** opera su set di righe corrente e può essere usata solo dopo una chiamata a [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Dimensioni del set di righe sono impostata da una chiamata a [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) con un argomento di attributo di SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** utilizza nuove dimensioni del set di righe, ma solo dopo una chiamata a **SQLFetch** o **SQLFetchScroll**. Se le dimensioni del set di righe viene modificata, ad esempio **SQLSetPos** viene chiamato e quindi **SQLFetch** o **SQLFetchScroll** viene chiamato. La chiamata a **SQLSetPos** utilizza le dimensioni del set di righe precedenti, ma **SQLFetch** o **SQLFetchScroll** utilizza le nuove dimensioni del set di righe.  
  
 La prima riga nel set di righe è il numero di riga 1. L'argomento RowNumber in **SQLSetPos** deve identificare una riga nel set di righe; ovvero, il valore deve essere compreso nell'intervallo compreso tra 1 e il numero di righe recuperate più di recente. Questo valore potrebbe essere inferiore alle dimensioni del set di righe. Se RowNumber è 0, l'operazione viene applicata a ogni riga nel set di righe.  
  
 L'operazione di eliminazione di **SQLSetPos** consente all'origine dati di eliminare uno o più righe selezionate di una tabella. Per eliminare le righe con **SQLSetPos**, l'applicazione chiama **SQLSetPos** con Operation impostato su SQL_DELETE e RowNumber impostato sul numero della riga da eliminare. Se RowNumber è 0, tutte le righe nel set di righe vengono eliminate.  
  
 Dopo aver **SQLSetPos** restituisce, la riga eliminata è la riga corrente e lo stato è SQL_ROW_DELETED. La riga non può essere utilizzata in altre operazioni posizionate, ad esempio chiamate a [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) o **SQLSetPos**.  
  
 Quando si eliminano tutte le righe del set di righe (RowNumber è uguale a 0), l'applicazione può impedire il driver di eliminare determinate righe utilizzando la matrice di operazione riga esattamente come per l'operazione di aggiornamento di **SQLSetPos**.  
  
 Ogni riga eliminata deve essere una riga che esiste nel set di risultati. Se dopo il recupero i buffer dell'applicazione risultano pieni e se è stata conservata una matrice di stato della riga, i valori in ognuna di queste posizioni delle righe non devono essere SQL_ROW_DELETED, SQL_ROW_ERROR o SQL_ROW_NOROW.  
  
 Gli aggiornamenti posizionati possono inoltre essere eseguiti utilizzando la clausola WHERE CURRENT OF nelle istruzioni UPDATE, DELETE e INSERT. WHERE CURRENT OF richiede un nome di cursore che ODBC genererà quando il [SQLGetCursorName](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) viene chiamata la funzione, o che è possibile specificare chiamando **SQLSetCursorName**. Di seguito sono riportati i passaggi generali utilizzati per eseguire un aggiornamento di WHERE CURRENT OF in un'applicazione ODBC:  
  
-   Chiamare **SQLSetCursorName** per stabilire un nome di cursore per l'handle di istruzione.  
  
-   Compilare un'istruzione SELECT con una clausola FOR UPDATE OF ed eseguirla.  
  
-   Chiamare **SQLFetchScroll** per recuperare un set di righe o **SQLFetch** per recuperare una riga.  
  
-   Chiamare **SQLSetPos** (SQL_POSITION) per posizionare il cursore sulla riga.  
  
-   Compilare ed eseguire un'istruzione UPDATE con una clausola WHERE CURRENT OF utilizzando il nome di cursore impostato con **SQLSetCursorName**.  
  
 In alternativa, è possibile chiamare **SQLGetCursorName** dopo l'esecuzione dell'istruzione SELECT anziché chiamare **SQLSetCursorName** prima di eseguire l'istruzione SELECT. **SQLGetCursorName** restituisce un nome di cursore predefinito assegnato da ODBC se non si imposta un nome di cursore mediante **SQLSetCursorName**.  
  
 **SQLSetPos** è preferibile rispetto WHERE CURRENT OF quando si utilizza i cursori del server. Se si utilizza un cursore statico aggiornabile con la libreria di cursore ODBC, la libreria di cursori implementa gli aggiornamenti di WHERE CURRENT OF aggiungendo una clausola WHERE con i valori chiave per la tabella sottostante. Se le chiavi nella tabella non sono univoche, possono verificarsi aggiornamenti non desiderati.  
  
## <a name="see-also"></a>Vedere anche  
 [Tramite i cursori & #40; ODBC & #41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
