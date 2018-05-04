---
title: Gestisce | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 830c4b653af74097c59c9aff9e073267792a84b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="handles"></a>Selettori
Gli handle sono opachi a 32 bit di valori che identificano un particolare elemento; in ODBC, questo elemento può essere un ambiente, connessione, l'istruzione o descrittore. Quando l'applicazione chiama **SQLAllocHandle**, il Driver Manager o il driver crea un nuovo elemento del tipo specificato e restituisce il relativo handle per l'applicazione. In un secondo momento l'applicazione utilizza l'handle per identificare l'elemento quando si chiamano funzioni ODBC. Il gestore dei Driver e il driver è possibile utilizzare l'handle per individuare le informazioni sull'elemento.  
  
 Ad esempio, il codice seguente usa due handle di istruzione (*hstmtOrder* e *hstmtLine*) per identificare le istruzioni in cui creare il set di risultati delle vendite orders e sales order numeri di riga. In un secondo momento Usa questi handle per individuare il set di risultati per recuperare dati.  
  
```  
SQLHSTMT      hstmtOrder, hstmtLine; // Statement handles.  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
SQLRETURN     rc;  
  
// Prepare the statement that retrieves line number information.  
SQLPrepare(hstmtLine, "SELECT * FROM Lines WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter in the preceding statement.  
SQLBindParameter(hstmtLine, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
               &OrderID, 0, &OrderIDInd);  
  
// Bind the result sets for the Order table and the Lines table. Bind  
// OrderID to the OrderID column in the Orders table. When each row is  
// fetched, OrderID will contain the current order ID, which will then be  
// passed as a parameter to the statement tofetch line number  
// information. Code not shown.  
  
// Create a result set of sales orders.  
SQLExecDirect(hstmtOrder, "SELECT * FROM Orders", SQL_NTS);  
  
// Fetch and display the sales order data. Code to check if rc equals  
// SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmtOrder)) != SQL_NO_DATA) {  
   // Display the sales order data. Code not shown.  
  
   // Create a result set of line numbers for the current sales order.  
   SQLExecute(hstmtLine);  
  
   // Fetch and display the sales order line number data. Code to check  
   // if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLFetch(hstmtLine)) != SQL_NO_DATA) {  
      // Display the sales order line number data. Code not shown.  
   }  
  
   // Close the sales order line number result set.  
   SQLCloseCursor(hstmtLine);  
}  
  
// Close the sales order result set.  
SQLCloseCursor(hstmtOrder);  
```  
  
 Gli handle sono significativi solo per il componente ODBC che ha creato. vale a dire the Driver Manager è in grado di interpretare gli handle di gestione Driver e solo un driver è in grado di interpretare i proprio handle.  
  
 Si supponga, ad esempio, il driver dell'esempio precedente consente di allocare una struttura per archiviare informazioni su un'istruzione e restituisce un puntatore alla struttura come l'handle di istruzione. Quando l'applicazione chiama **SQLPrepare**, passa a un'istruzione SQL e l'handle dell'istruzione utilizzata per i numeri di riga ordine di vendita. Il driver invia l'istruzione SQL per l'origine dati, che prepara e restituisce un identificatore del piano di accesso. Il driver utilizza l'handle per trovare la struttura in cui archiviare questo identificatore.  
  
 Successivamente, quando l'applicazione chiama **SQLExecute** per generare il set di risultati di numeri di riga per un particolare ordine di vendita, passa l'handle stesso. Il driver utilizza l'handle per recuperare l'identificatore del piano di accesso dalla struttura. Invia l'identificatore per l'origine dati per indicare il piano da eseguire.  
  
 ODBC ha due livelli di handle: handle di gestione Driver e driver. L'applicazione utilizza gli handle di gestione Driver quando si chiama funzioni ODBC poiché chiama delle funzioni di gestione Driver. Gestione Driver Usa questo handle per trovare l'handle di driver corrispondenti e l'handle del driver quando si chiama la funzione nel driver. Per un esempio di come vengono usati driver e gli handle di gestione Driver, vedere [di gestione Driver ruolo nel processo di connessione](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Sono presenti due livelli di handle è un elemento dell'architettura ODBC; Nella maggior parte dei casi, non è pertinente per il driver o di applicazione. Sebbene non sia in genere a tale scopo, è possibile che l'applicazione per determinare gli handle di driver chiamando **SQLGetInfo**.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Handle di ambiente](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Handle di connessione](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Handle di istruzione](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Handle descrittore](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Transizioni di stato](../../../odbc/reference/develop-app/state-transitions.md)
