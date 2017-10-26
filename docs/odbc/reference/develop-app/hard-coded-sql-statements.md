---
title: Istruzioni SQL hard-Coded | Documenti Microsoft
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
- SQL statements [ODBC], hard-coded
- hard-coded SQL statements [ODBC]
- SQL statements [ODBC], constructing
ms.assetid: e355f5f1-4f1a-4933-8c74-ee73e90d2d19
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 60f0ad180a334c1d4ad08f49057bb5598df22f59
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="hard-coded-sql-statements"></a>Istruzioni SQL hard-Coded
Applicazioni che eseguono attività fissa in genere contengono le istruzioni SQL hard-coded. Ad esempio, un sistema di immissione degli ordini è possibile utilizzare la chiamata seguente a ordini di vendita Apri elenco:  
  
```  
SQLExecDirect(hstmt, "SELECT OrderID FROM Orders WHERE Status = 'OPEN'", SQL_NTS);  
```  
  
 Esistono numerosi vantaggi per le istruzioni SQL hard-coded: possono essere verificate quando l'applicazione è scritta. sono più semplici da implementare rispetto alle istruzioni create in fase di esecuzione. e semplificano l'applicazione.  
  
 Utilizzo dei parametri di istruzione e preparazione di istruzioni ancora migliore consentono di utilizzare le istruzioni SQL hard-coded. Si supponga, ad esempio, che nella tabella parti contiene le colonne PartID, la descrizione e prezzo. Un modo per inserire una nuova riga in questa tabella, è possibile creare ed eseguire un **inserire** istruzione:  
  
```  
#define DESC_LEN 51  
#define STATEMENT_LEN 51  
  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN], Statement[STATEMENT_LEN];  
SQLREAL       Price;  
  
// Set part ID, description, and price.  
GetNewValues(&PartID, Desc, &Price);  
  
// Build INSERT statement.  
sprintf_s(Statement, 100, "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (%d, '%s', %f)", PartID, Desc, Price);  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
```  
  
 Un metodo migliore consiste nell'utilizzare un'istruzione con parametri, a livello di codice. Questo ha due vantaggi rispetto a un'istruzione con valori di dati hardcoded. In primo luogo, risulta più semplice costruire un'istruzione con parametri perché i valori dei dati possono essere inviati nei rispettivi tipi nativi, ad esempio numeri interi e numeri a virgola mobile anziché la loro conversione in stringhe. In secondo luogo, tale istruzione consente più di una volta la modifica dei valori di parametro e rieseguire. non è necessario ricompilarlo.  
  
```  
#define DESC_LEN 51  
  
SQLCHAR * Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (?, ?, ?)";  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Set part ID, description, and price.  
GetNewValues(&PartID, Desc, &Price);  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
```  
  
 Supponendo che questa istruzione deve essere eseguita più volte, può essere preparato per una maggiore efficienza:  
  
```  
#define DESC_LEN 51  
  
SQLCHAR *Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (?, ?, ?)";  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Prepare the INSERT statement.  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Loop to continually get new values and insert them.  
while (GetNewValues(&PartID, Desc, &Price))  
   SQLExecute(hstmt);  
```  
  
 Ad esempio il modo più efficiente per utilizzare l'istruzione consiste nel creare una procedura contenente l'istruzione, come illustrato nell'esempio di codice seguente. Poiché la procedura viene costruita in fase di sviluppo e archiviata nell'origine dati, non è necessario preparare in fase di esecuzione. Uno svantaggio di questo metodo è che la sintassi per la creazione di procedure è specifico del sistema DBMS e procedure devono essere costruite separatamente per ogni sistema DBMS in cui l'applicazione deve essere eseguita.  
  
```  
#define DESC_LEN 51  
  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Loop to continually get new values and insert them.  
while (GetNewValues(&PartID, Desc, &Price))  
   SQLExecDirect(hstmt, "{call InsertPart(?, ?, ?)}", SQL_NTS);  
```  
  
 Per ulteriori informazioni sui parametri, le istruzioni preparate e procedure, vedere [l'esecuzione di un'istruzione](../../../odbc/reference/develop-app/executing-a-statement.md).

