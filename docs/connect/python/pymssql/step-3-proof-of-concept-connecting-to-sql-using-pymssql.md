---
title: 'Passaggio 3: Modello di prova di connessione a SQL tramite pymssql | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 5796c2d5faefdeef1a9bafe1a438b68c7461dd53
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>Passaggio 3: Modello di connessione a SQL tramite pymssql prova
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

In questo esempio deve essere considerato un modello solo di prova.  Il codice di esempio è semplificato per maggiore chiarezza e non rappresenta necessariamente le procedure consigliate da Microsoft.  
  
## <a name="step-1--connect"></a>Passaggio 1: connettersi  
  
Il [pymssql.connect](http://pymssql.org/en/latest/ref/pymssql.html) funzione viene utilizzata per connettersi al Database SQL.  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>Passaggio 2: Esecuzione di query  
  
Il [cursor.execute](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) funzione può essere utilizzata per recuperare un set di risultati da una query sul Database SQL. Questa funzione è essenzialmente accetta tutte le query e restituisce un set di risultati che è possibile eseguire un'iterazione con l'utilizzo di [cursor.fetchone()](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone).  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute('SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;')  
    row = cursor.fetchone()  
    while row:  
        print str(row[0]) + " " + str(row[1]) + " " + str(row[2])     
        row = cursor.fetchone()  
```  
  
## <a name="step-3--insert-a-row"></a>Passaggio 3: Inserire una riga  
  
In questo esempio verrà visualizzato come eseguire un [inserire](/sql-docs/docs/t-sql/statements/insert-transact-sql) istruzione in modo sicuro, passare parametri che la protezione dell'applicazione da [attacchi SQL injection](/sql-docs/docs/relational-databases/tables/primary-and-foreign-key-constraints) valore.    
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express', 'SQLEXPRESS', 0, 0, CURRENT_TIMESTAMP)")  
    row = cursor.fetchone()  
    while row:  
        print "Inserted Product ID : " +str(row[0])  
        row = cursor.fetchone()  
    conn.commit()
    conn.close()
```  
  
## <a name="step-4--rollback-a-transaction"></a>Passaggio 4: Rollback di una transazione  
  
Questo esempio di codice viene illustrato l'utilizzo di transazioni in cui è:  
  
* Avviare una transazione  
* Inserire una riga di dati  
* Eseguire il rollback della transazione per annullare l'inserimento  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>Passaggi successivi  
  
Per ulteriori informazioni, vedere il [Centro per sviluppatori Python](https://azure.microsoft.com/en-us/develop/python/).
