---
title: "Librerie di connettività e Framework | Documenti Microsoft"
description: "Vengono elencati i driver di connettività che le applicazioni client è possono utilizzare dalle varie lingue per connettersi a Microsoft SQL Server in esecuzione in locale o nel cloud, in Linux, Windows o Docker, nonché per Database SQL di Azure e Azure SQL Data Warehouse."
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.workload: Inactive
ms.openlocfilehash: 765fb054ab4fb5332df7b2f9d2e202188f621b67
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Librerie di connettività e altri framework per Microsoft SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Estrarre il nostro [esercitazioni introduttive](http://aka.ms/sqldev) per iniziare a utilizzare linguaggi di programmazione quali c#, Java, Node.js, PHP e Python e compilare un'app usando SQL Server in Linux o di Windows o di Docker su macOS rapidamente.

La tabella seguente elenca le librerie di connettività o *driver* utilizzata dalle applicazioni client da una vasta gamma di linguaggi per connettersi e utilizzare Microsoft SQL Server in esecuzione in locale o nel cloud, in Linux, Windows o Docker, nonché per Database SQL di Azure e Azure SQL Data Warehouse. 

| Linguaggio | Piattaforma | Risorse aggiuntive | Scarica | Introduzione |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET for SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [Scarica](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Introduzione](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Microsoft JDBC Driver per SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [Scarica](http://go.microsoft.com/fwlink/?LinkId=245496) |  [Introduzione](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Driver SQL PHP per SQL Server](http://msdn.microsoft.com/library/dn865013.aspx) | Sistema operativo: <br/> \*[Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \*[Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \*[macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Introduzione](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Driver Node.js per SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Introduzione](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Driver SQL Python](../connect/python/python-driver-for-sql-server.md) <br/> \*[pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [Introduzione](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Driver Ruby per SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Introduzione](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Microsoft ODBC Driver per SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [Scarica](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

Nella tabella seguente sono elencati alcuni esempi di Framework relazionale Mapping ORM (Object) e altri framework web utilizzabili dalle applicazioni client con Microsoft SQL Server in esecuzione in locale o nel cloud, in Linux, Windows o Docker, nonché per Database SQL di Azure e Azure SQL Data Warehouse. 

| Linguaggio | Piattaforma | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](https://docs.microsoft.com/en-us/ef)<br>[Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/index) |
| Java | Windows, Linux, macOS |[Lo stato di ibernazione ORM](http://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (intuitivo)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby su Guide](http://rubyonrails.org/) |

## <a name="related-links"></a>Collegamenti correlati
- [Driver SQL Server](http://msdn.microsoft.com/library/mt654049.aspx) per la connessione dalle applicazioni client
