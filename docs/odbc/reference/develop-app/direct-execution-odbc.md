---
title: L'esecuzione ODBC diretta | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], direct execution
- direct execution [ODBC]
- SQL statements [ODBC], executing
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: abce5a1c9f4fceb38420c15159cf89a2430025dc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="direct-execution-odbc"></a>Esecuzione diretta ODBC
Esecuzione diretta è il modo più semplice per eseguire un'istruzione. Quando l'istruzione viene inviata per l'esecuzione, l'origine dati lo compila in un piano di accesso e quindi esegue il piano di accesso.  
  
 Esecuzione diretta viene comunemente utilizzata dalle applicazioni generiche che compilano ed eseguono le istruzioni in fase di esecuzione. Ad esempio, il codice seguente compila un'istruzione SQL e viene eseguito una sola volta:  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 Esecuzione diretta risulta più adatta per le istruzioni che verranno eseguite una sola volta. Il principale svantaggio è che l'istruzione SQL viene analizzata ogni volta che viene eseguita. Inoltre, l'applicazione non può recuperare le informazioni sul set di risultati creati tramite l'istruzione (se presente) fino a quando viene eseguita l'istruzione; Questo è possibile se l'istruzione viene preparata ed eseguita in due fasi distinte.  
  
 Per eseguire un'istruzione direttamente, l'applicazione esegue le azioni seguenti:  
  
1.  Imposta i valori dei parametri. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.  
  
2.  Chiamate **SQLExecDirect** e lo passa a una stringa contenente l'istruzione SQL.  
  
3.  Quando **SQLExecDirect** viene chiamato, il driver:  
  
    -   Modifica l'istruzione SQL per l'utilizzo di grammatica SQL dell'origine dati senza analizzare l'istruzione. Questo include sostituendo le sequenze di escape descritte in [sequenze di Escape ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). L'applicazione può recuperare il modulo di un'istruzione SQL modificato chiamando **SQLNativeSql**. Se è impostato l'attributo di istruzione SQL_ATTR_NOSCAN, le sequenze di escape non vengono sostituite.  
  
    -   Recupera i valori di parametro corrente e li converte in base alle esigenze. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.  
  
    -   Invia l'istruzione e i valori di parametro convertito all'origine dati per l'esecuzione.  
  
    -   Restituisce gli eventuali errori. Questi includono sequenziazione o diagnostica di stato, quali SQLSTATE 24000 (stato del cursore non valido), errori di sintassi, ad esempio SQLSTATE 42000 (sintassi o violazione di accesso) e gli errori semantici, ad esempio 42S02 SQLSTATE (Base tabella o vista non trovato).
