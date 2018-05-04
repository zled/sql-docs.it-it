---
title: Creazione di istruzioni SQL per i cursori | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6207d51509b4eed3ebb3ec0db5c40174b7b7ac9b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="constructing-sql-statements-for-cursors"></a>Costruzione di istruzioni SQL per i cursori
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizza cursori server per implementare la funzionalità di cursore definita nella specifica ODBC. Un'applicazione ODBC determina il comportamento del cursore utilizzando [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi di istruzione diversi. Di seguito sono indicati gli attributi e le rispettive impostazioni predefinite.  
  
|Attribute|Valore predefinito|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Quando queste opzioni sono impostate sui valori predefiniti in fase di esecuzione di un'istruzione SQL, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client non utilizza un cursore del server per implementare il set di risultati; ma utilizza un set di risultati predefinito. Se una di queste opzioni vengono modificata i valori predefiniti in fase di esecuzione di un'istruzione SQL, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client tenta di utilizzare un cursore del server per implementare il set di risultati.  
  
 I set di risultati predefiniti supportano tutte le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. Non sono presenti restrizioni sui tipi di istruzioni SQL che è possibile eseguire quando si utilizza un set di risultati predefinito.  
  
 I cursori server non supportano tutte le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] e non supportano un'istruzione SQL che genera più set di risultati.  
  
 Di seguito sono indicati i tipi di istruzioni non supportati dai cursori server:  
  
-   Batch  
  
     Istruzioni SQL compilate da due o più istruzioni SQL SELECT singole, ad esempio:  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   Stored procedure con più istruzioni SELECT  
  
     Istruzioni SQL che eseguono una stored procedure che contiene più di un'istruzione SELECT. Sono incluse le istruzioni SELECT che vengono inserite in parametri o variabili.  
  
-   Parole chiave  
  
     Istruzioni SQL contenenti le parole chiave FOR BROWSE o INTO.  
  
 Se in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un'istruzione SQL che corrisponde a una di queste condizioni viene eseguita con un cursore server, il cursore server viene convertito implicitamente in un set di risultati predefinito. Dopo aver **SQLExecDirect** o **SQLExecute** restituisce SQL_SUCCESS_WITH_INFO, il cursore attributi verranno nuovamente impostati sui valori predefiniti.  
  
 Le istruzioni SQL che non rientrano nelle categorie sopra riportate possono essere eseguite con qualsiasi impostazione degli attributi di istruzione. Il funzionamento è identico con un set di risultati predefinito o con un cursore server.  
  
## <a name="errors"></a>Errori  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 e versioni successive un tentativo di eseguire un'istruzione che produce più set di risultati genera SQL_SUCCESS_WITH INFO e il messaggio seguente:  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 Applicazioni ODBC che ricevono questo messaggio possono chiamare [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) per determinare le impostazioni del cursore corrente.  
  
 Un tentativo di eseguire una procedura con più istruzioni SELECT quando si utilizzano cursori server genera l'errore seguente:  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 Un tentativo di eseguire un batch con più istruzioni SELECT quando l'utilizzo di cursori server genera l'errore seguente:  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 Nelle applicazioni ODBC che ricevono questi errori devono essere reimpostati tutti gli attributi di istruzione di cursore sui valori predefiniti prima di tentare di eseguire l'istruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
