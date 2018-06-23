---
title: Chiamare le Stored procedure (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0846567d803eadf4364159fc01fdb8a7853e8a4f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068728"
---
# <a name="call-stored-procedures-odbc"></a>Chiamare stored procedure (ODBC)
  Quando un'istruzione SQL chiama una stored procedure utilizzando la clausola di escape ODBC CALL, tramite driver di Microsoft® SQL Server™ la stored procedure viene inviata a SQL Server utilizzando il meccanismo di chiamata RPC (Remote Procedure Call). Le richieste RPC ignorano la maggior parte dell'analisi delle istruzioni e dell'elaborazione dei parametri in SQL Server e sono più veloci rispetto a un'istruzione Transact-SQL EXECUTE.  
  
 Per un'applicazione di esempio che illustri questa caratteristica, vedere [processo di codici restituiti e parametri di Output &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Per eseguire una procedura come RPC  
  
1.  Costruire un'istruzione SQL che utilizzi la sequenza di escape ODBC CALL. Nell'istruzione vengono utilizzati marcatori di parametro per ogni parametro di input, input/output e di output e per il valore restituito della procedura, se disponibile:  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Chiamare [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) per ogni input, input/output, parametro di output e per la procedura di valore restituito (se presente).  
  
3.  Eseguire l'istruzione con [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Se un'applicazione invia una procedura utilizzando la sintassi Transact-SQL EXECUTE, invece della sequenza di escape ODBC CALL, il driver ODBC di SQL Server passa la chiamata di procedura a SQL Server come istruzione SQL anziché come chiamata RPC. Se viene utilizzata l'istruzione Transact-SQL EXECUTE, inoltre, i parametri di output non vengono restituiti.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di procedure per le Stored procedure &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Invio in batch chiamate a Stored Procedure](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Esecuzione di Stored procedure](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Chiamare una Stored Procedure](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procedure](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  