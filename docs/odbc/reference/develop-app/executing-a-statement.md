---
title: Esecuzione di un'istruzione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], executing
ms.assetid: e5f0d2ee-0453-4faf-b007-12978dd300a1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddb265060dc0714ce4eafaa09ce336d289697309
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="executing-a-statement"></a>Esecuzione di un'istruzione
Sono disponibili quattro modi per eseguire un'istruzione, in base al momento della compilazione (autore) il motore di database e che sono definiti:  
  
-   **L'esecuzione diretta** l'applicazione definisce l'istruzione SQL. Viene preparata ed eseguita in fase di esecuzione in un unico passaggio.  
  
-   **Esecuzione preparata** l'applicazione definisce l'istruzione SQL. Viene preparata ed eseguita in fase di esecuzione in due fasi distinte. L'istruzione può essere una volta preparato ed eseguito più volte.  
  
-   **Procedure** l'applicazione è possibile definire e compilare uno o più istruzioni SQL in fase di sviluppo tempo e archiviano queste istruzioni nell'origine dati di una stored procedure. La procedura viene eseguita una o più volte in fase di esecuzione. L'applicazione può enumerare le stored procedure disponibili utilizzando funzioni di catalogo.  
  
-   **Funzioni di catalogo** il writer di driver crea una funzione che restituisce un set di risultati predefiniti. In genere, questa funzione Invia un'istruzione SQL predefinita o chiama una routine creata per questo scopo. La funzione viene eseguita una o più volte in fase di esecuzione.  
  
 Una determinata istruzione (come identificato dal relativo handle di istruzione) può essere eseguite un numero qualsiasi di volte. L'istruzione può essere eseguita con una serie di istruzioni SQL diverse oppure può essere eseguito ripetutamente con la stessa istruzione SQL. Ad esempio, il codice seguente usa lo stesso handle di istruzione (*hstmt1*) per recuperare e visualizzare le tabelle nel database Sales. Quindi, viene riutilizzato questo handle per recuperare le colonne in una tabella selezionata dall'utente.  
  
```  
SQLHSTMT    hstmt1;  
SQLCHAR *   Table;  
  
// Create a result set of all tables in the Sales database.  
SQLTables(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, NULL, 0, NULL, 0);  
  
// Fetch and display the table names; then close the cursor.  
// Code not shown.  
  
// Have the user select a particular table.  
SelectTable(Table);  
  
// Reuse hstmt1 to create a result set of all columns in Table.  
SQLColumns(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, Table, SQL_NTS, NULL, 0);  
  
// Fetch and display the column names in Table; then close the cursor.  
// Code not shown.  
```  
  
 E il codice seguente viene illustrato come utilizzare un singolo handle per eseguire ripetutamente la stessa istruzione per eliminare righe da una tabella.  
  
```  
SQLHSTMT      hstmt1;  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
  
// Prepare a statement to delete orders from the Orders table.  
SQLPrepare(hstmt1, "DELETE FROM Orders WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter for the OrderID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &OrderID, 0, &OrderIDInd);  
  
// Repeatedly execute hstmt1 with different values of OrderID.  
while ((OrderID = GetOrderID()) != 0) {  
   SQLExecute(hstmt1);  
}  
```  
  
 Per molti driver, istruzioni di assegnazione è un'attività dispendiosa, pertanto riutilizza la stessa istruzione in questo modo è in genere più efficiente consentendo a istruzioni esistenti e allocazione di nuovi. Applicazioni che creano set di risultati in un'istruzione è necessario fare attenzione a chiudere il cursore su set di risultati prima di rieseguire l'istruzione. Per ulteriori informazioni, vedere [la chiusura del cursore](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 Riutilizzo di istruzioni impone inoltre all'applicazione per evitare una limitazione di alcuni driver del numero di istruzioni che possono essere attive contemporaneamente. La definizione esatta di "attivo" è specifico del driver, ma spesso fa riferimento a qualsiasi istruzione che è stato preparato o eseguito e ha ancora risultati disponibili. Ad esempio, dopo un **inserire** istruzione è stata preparata, è in genere considerato attivo; dopo un **selezionare** è stata eseguita l'istruzione e il cursore è ancora aperto, viene in genere considerato essere attivo. Dopo un **CREATE TABLE** è stata eseguita l'istruzione, non è generalmente considerata come attiva.  
  
 Un'applicazione determina il numero di istruzioni possono essere attive in un'unica connessione alla volta chiamando **SQLGetInfo** con l'opzione SQL_MAX_CONCURRENT_ACTIVITIES. Un'applicazione può utilizzare le istruzioni attive supera questo limite, aprire più connessioni all'origine dati; Poiché le connessioni possono essere costosa, tuttavia, l'effetto sulle prestazioni da considerare.  
  
 Le applicazioni possono limitare la quantità di tempo assegnata per un'istruzione da eseguire con l'attributo di istruzione SQL_ATTR_QUERY_TIMEOUT. Se il periodo di timeout scade prima che l'origine dati restituisce il set di risultati, la funzione esegue l'istruzione SQL restituisce SQLSTATE HYT00 (Timeout scaduto). Per impostazione predefinita, non vi è alcun timeout.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Esecuzione diretta](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Esecuzione preparata](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Procedure](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Batch di istruzioni SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Esecuzione delle funzioni di catalogo](../../../odbc/reference/develop-app/executing-catalog-functions.md)
