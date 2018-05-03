---
title: 'Passaggio 3: Modello di connessione a SQL tramite Ruby prova | Documenti Microsoft'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ruby
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32d822293a6b46e23b36238dc084ef858ca6e22d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Passaggio 3: Modello di connessione a SQL tramite Ruby prova

In questo esempio deve essere considerato un modello solo di prova.  Il codice di esempio è semplificato per maggiore chiarezza e non rappresenta necessariamente le procedure consigliate da Microsoft.  
  
## <a name="step-1--connect"></a>Passaggio 1: connettersi  
  
Il [TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds) funzione viene utilizzata per connettersi al Database SQL.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Passaggio 2: Eseguire una query  
  
Copiare e incollare il codice seguente in un file vuoto. La chiamata test.rb. Quindi eseguirla immettendo il comando seguente dal prompt dei comandi:  
  
    ruby test.rb  
  
Nell'esempio di codice, il [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds) funzione viene utilizzata per recuperare un set di risultati da una query sul Database SQL. Questa funzione accetta una query e restituisce un set di risultati. Il set di risultati viene iterato premendo [result.each si | riga |](https://github.com/rails-sqlserver/tiny_tds).  
  
``` ruby 
    require 'tiny_tds'    
    print 'test'       
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC")  
    results.each do |row|  
    puts row  
    end  
```  
  
## <a name="step-3--insert-a-row"></a>Passaggio 3: Inserire una riga  
  
In questo esempio verrà visualizzato come eseguire un [inserire](../../t-sql/statements/insert-transact-sql.md) istruzione in modo sicuro, passare parametri che la protezione dell'applicazione da [attacchi SQL injection](../../relational-databases/tables/primary-and-foreign-key-constraints.md) valore.    
  
Per utilizzare TinyTDS con Azure, si consiglia di eseguire diversi `SET` istruzioni per modificare la modalità di gestione delle informazioni specifiche della sessione corrente. Consigliato `SET` vengono fornite le istruzioni nell'esempio di codice. Ad esempio, `SET ANSI_NULL_DFLT_ON` consentirà le nuove colonne create per consentire valori null, anche se lo stato di supporto di valori null della colonna non è dichiarato in modo esplicito.  
  
Per allineare con Microsoft SQL Server [datetime](http://msdn.microsoft.com/library/ms187819.aspx) formattare, utilizzare il [strftime](http://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) funzione per eseguire il cast al formato datetime corrispondente.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SET ANSI_NULLS ON")  
    results = client.execute("SET CURSOR_CLOSE_ON_COMMIT OFF")  
    results = client.execute("SET ANSI_NULL_DFLT_ON ON")  
    results = client.execute("SET IMPLICIT_TRANSACTIONS OFF")  
    results = client.execute("SET ANSI_PADDING ON")  
    results = client.execute("SET QUOTED_IDENTIFIER ON")  
    results = client.execute("SET ANSI_WARNINGS ON")  
    results = client.execute("SET CONCAT_NULL_YIELDS_NULL ON")  
    require 'date'  
    t = Time.now  
    curr_date = t.strftime("%Y-%m-%d %H:%M:%S.%L")  
    results = client.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate)  
    OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, '#{curr_date}' )")  
    results.each do |row|  
    puts row  
    end  
```
