---
title: Utilizzare un'istruzione (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 50a4f012b556bb6f54a0b9e672c2f9ff16a44fd2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054311"
---
# <a name="use-a-statement-odbc"></a>Utilizzare un'istruzione (ODBC)
    
### <a name="to-use-a-statement"></a>Per utilizzare un'istruzione  
  
1.  Chiamare [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) con *HandleType* impostato su SQL_HANDLE_STMT per allocare un handle di istruzione.  
  
2.  È inoltre possibile chiamare [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) per impostare le opzioni dell'istruzione o [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) per ottenere gli attributi dell'istruzione.  
  
     Per utilizzare i cursori server, è necessario impostare gli attributi del cursore su valori diversi da quelli predefiniti.  
  
3.  Facoltativamente, se l'istruzione viene eseguita più volte, è possibile preparare l'istruzione per l'esecuzione con la [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360).  
  
4.  Se all'istruzione sono stati associati marcatori di parametro, è possibile associare i marcatori di parametro alle variabili di programma tramite [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md). Se l'istruzione è stata preparata, è possibile chiamare [SQLNumParams](http://go.microsoft.com/fwlink/?LinkId=58404) e [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) per trovare il numero e le caratteristiche dei parametri.  
  
5.  Eseguire un'istruzione direttamente mediante SQLExecDirect.  
  
     \- - oppure -  
  
     Se l'istruzione è stata preparata, eseguirla più volte tramite [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400).  
  
     \- - oppure -  
  
     Chiamare una funzione di catalogo, che restituisce i risultati.  
  
6.  Elaborare i risultati associando le colonne del set di risultati alle variabili di programma, spostando i dati dalle colonne del set di risultati alle variabili di programma tramite [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) oppure usando una combinazione dei due metodi.  
  
     Recuperare il set di risultati di un'istruzione una riga alla volta.  
  
     \- - oppure -  
  
     Recuperare il set di risultati più righe alla volta mediante un cursore a blocchi.  
  
     \- - oppure -  
  
     Chiamare [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) per determinare il numero di righe interessate da un'istruzione INSERT, UPDATE o DELETE.  
  
     Se l'istruzione SQL può avere più set di risultati, chiamare [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) alla fine di ogni set di risultati per stabilire se siano presenti altri set di risultati da elaborare.  
  
7.  Dopo l'elaborazione dei risultati, può essere necessario effettuare le seguenti azioni per consentire all'handle di istruzione di eseguire una nuova istruzione:  
  
    -   Se [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) non è stato chiamato fino a quando non sia stato restituito SQL_NO_DATA, chiamare [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) per chiudere il cursore.  
  
    -   Se i marcatori di parametro sono stati associati alle variabili di programma, chiamare [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) con *Option* impostato su SQL_RESET_PARAMS per liberare i parametri associati.  
  
    -   Se le colonne del set di risultati sono state associate alle variabili di programma, chiamare [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) con *Option* impostato su SQL_UNBIND per liberare le colonne associate.  
  
    -   Per riutilizzare l'handle di istruzione, andare al passaggio 2.  
  
8.  Chiamare [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) con *HandleType* impostato su SQL_HANDLE_STMT per liberare l'handle di istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query procedure &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  