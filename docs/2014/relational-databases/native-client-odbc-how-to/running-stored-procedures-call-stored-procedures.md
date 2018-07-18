---
title: Chiamare le Stored procedure (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37ce27067c4ad30e38b6d3c168b8f676815b693d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411300"
---
# <a name="call-stored-procedures-odbc"></a>Chiamare stored procedure (ODBC)
  Quando un'istruzione SQL chiama una stored procedure utilizzando la clausola di escape ODBC CALL, tramite driver di Microsoft® SQL Server™ la stored procedure viene inviata a SQL Server utilizzando il meccanismo di chiamata RPC (Remote Procedure Call). Le richieste RPC ignorano la maggior parte dell'analisi delle istruzioni e dell'elaborazione dei parametri in SQL Server e sono più veloci rispetto a un'istruzione Transact-SQL EXECUTE.  
  
 Per un'applicazione di esempio che illustri questa caratteristica, vedere [processo di codici restituiti e parametri di Output &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Per eseguire una procedura come RPC  
  
1.  Costruire un'istruzione SQL che utilizzi la sequenza di escape ODBC CALL. Nell'istruzione vengono utilizzati marcatori di parametro per ogni parametro di input, input/output e di output e per il valore restituito della procedura, se disponibile:  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Chiamare [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) per ogni input, input/output, parametro di output e per la procedura di valore restituito (se disponibile).  
  
3.  Eseguire l'istruzione con [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Se un'applicazione invia una procedura utilizzando la sintassi Transact-SQL EXECUTE, invece della sequenza di escape ODBC CALL, il driver ODBC di SQL Server passa la chiamata di procedura a SQL Server come istruzione SQL anziché come chiamata RPC. Se viene utilizzata l'istruzione Transact-SQL EXECUTE, inoltre, i parametri di output non vengono restituiti.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di procedure per la Stored procedure &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Invio in batch chiamate alle Stored Procedure](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Esecuzione di Stored procedure](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Chiama una Stored Procedure](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procedure](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
