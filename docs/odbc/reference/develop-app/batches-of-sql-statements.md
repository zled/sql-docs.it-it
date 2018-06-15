---
title: Batch di istruzioni SQL | Documenti Microsoft
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
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52d5b9953f193009f6aa521b08cf1af9b335e079
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911246"
---
# <a name="batches-of-sql-statements"></a>Batch di istruzioni SQL
Un batch di istruzioni SQL è un gruppo di due o più istruzioni SQL o una singola istruzione SQL che ha lo stesso effetto di un gruppo di due o più istruzioni SQL. In alcune implementazioni, l'istruzione dell'intero batch viene eseguito prima che i risultati siano disponibili. Questo è spesso più efficiente rispetto all'invio istruzioni separatamente, poiché il traffico di rete spesso può essere ridotto e l'origine dati in alcuni casi può ottimizzare l'esecuzione di un batch di istruzioni SQL. Nelle altre implementazioni di chiamata **SQLMoreResults** attiva l'esecuzione dell'istruzione successiva nel batch. ODBC supporta i seguenti tipi di batch:  
  
-   **Batch esplicita** un' *batch esplicita* è due o più istruzioni SQL separate da punti e virgola (;). Ad esempio, il batch di istruzioni SQL seguente consente di aprire un nuovo ordine vendita. Questa operazione richiede l'inserimento di righe in tabelle Orders e di righe. Si noti che non vi sia alcun punto e virgola dopo l'ultima istruzione.  
  
    ```  
    INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
       VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 1, 1234, 10);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 2, 987, 8);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 3, 566, 17);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 4, 412, 500)  
    ```  
  
-   **Procedure** se una stored procedure contiene più di un'istruzione SQL, viene considerato un batch di istruzioni SQL. Ad esempio, l'istruzione specifici di SQL Server seguente crea una routine che restituisce un set di risultati contenente informazioni su un cliente e un elenco di tutti gli ordini di vendita aperti relativi al cliente di set di risultati:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Il **CREATE PROCEDURE** istruzione stessa non è un batch di istruzioni SQL. Tuttavia, la procedura che viene creato è un batch di istruzioni SQL. Nessun punto e virgola di separare i due **selezionare** istruzioni perché il **CREATE PROCEDURE** istruzione specifiche di SQL Server e SQL Server non richiede un punto e virgola per separare più istruzioni in un  **CREATE PROCEDURE** istruzione.  
  
-   **Le matrici di parametri** matrici di parametri possono essere utilizzate con un'istruzione SQL con parametri come un metodo efficace per eseguire le operazioni bulk. Ad esempio, le matrici di parametri utilizzabili con le operazioni seguenti **inserire** inserire più righe nella tabella di righe durante l'esecuzione di una singola istruzione SQL dell'istruzione:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Se un'origine dati non supporta le matrici di parametri, il driver può emulare li eseguendo l'istruzione SQL una volta per ogni set di parametri. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md) e [matrici di valori di parametro](../../../odbc/reference/develop-app/arrays-of-parameter-values.md), più avanti in questa sezione.  
  
 I diversi tipi di batch non è possibile combinare in modo interoperativo. Vale a dire come un'applicazione determina il risultato dell'esecuzione di un batch esplicito che include stored procedure chiama un batch esplicito che usa le matrici di parametri, senza che sia una chiamata di stored procedure che utilizza le matrici di parametri specifici del driver.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Istruzioni per la generazione di risultati e senza risultati](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Esecuzione di batch](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Errori e batch](../../../odbc/reference/develop-app/errors-and-batches.md)
