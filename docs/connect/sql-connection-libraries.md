---
title: Raccolte di connessioni per i database SQL di Microsoft | Documenti Microsoft
description: Fornisce i collegamenti ai download per i moduli che consentono la connessione a Microsoft SQL Server e Database SQL di Azure da un'ampia gamma di linguaggi di programmazione client.
author: MightyPen
ms.service: ''
ms.component: connect
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.technology: dbe-data-tier-apps
ms.custom: ''
ms.workload: data-management
ms.topic: article
ms.date: 08/09/2017
ms.author: genemi
ms.openlocfilehash: 33df5e13dcdeb205a1dbc9fa9c1a5dc7efc754c2
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Moduli di connessione per i database SQL di Microsoft

Questo articolo fornisce collegamenti ai moduli di connessione per il download o *driver* che i programmi client possono utilizzare per l'interazione con [Microsoft SQL Server](../index.md)e con la disponibilità di una copia nel cloud [Azure Database SQL](http://docs.microsoft.com/azure/sql-database/). Sono disponibili driver per un'ampia gamma di linguaggi di programmazione, in esecuzione in sistemi operativi seguenti:

- Linux (Ubuntu)
- MacOS
- Windows


#### <a name="oop-to-relational-mismatch"></a>Mancata corrispondenza OOP-relational

*Relazionale*: i programmi Client che vengono scritti in un linguaggio (OOP) programmazione orientata agli oggetti spesso utilizzano i driver SQL che restituiscono dati di query in un formato più relazionale di orientata agli oggetti. Utilizzo di ADO.NET c# è un esempio. La mancata corrispondenza tra formato relazionale OOP talvolta rende il codice OOP più difficile la scrittura e la comprensione.

*ORM*: altri driver o un framework di restituiscono dati di query nel formato OOP, evitando la mancata corrispondenza. Questi driver utilizzare, è previsto che le classi sono state definite affinché corrisponda alle colonne di dati di tabelle SQL specifiche. Il driver esegue quindi il *mapping relazionale a oggetti* ORM () per restituire i dati di query come un'istanza di una classe. Microsoft Entity Framework (EF) per c# e ibernazione per Java, sono riportati due esempi.

Il presente articolo dedica sezioni separate per questi due tipi di driver di connessione.


<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Driver per un accesso relazionale


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->


| Lingua | Scaricare il driver SQL |
| :------- | :---------------------- |
| C#       | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[.NET Core, for Linux-Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core, per MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core, per Windows](https://www.microsoft.com/net/core) |
| C++      | [ODBC](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Java     | [JDBC](http://www.microsoft.com/download/details.aspx?id=55539) |
| Node.js  | [Node.js driver, le istruzioni di installazione](http://docs.microsoft.com/sql/connect/node-js/step-1-configure-development-environment-for-node-js-development) |
| PHP      | *Sistema operativo:*<br /><br />[Windows PHP driver](https://www.microsoft.com/download/details.aspx?id=55642)<br />[Linux o macOS driver PHP da Github](http://github.com/Microsoft/msphpsql/) |
| Python   | [pyodbc, le istruzioni di installazione](http://docs.microsoft.com/sql/connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development)<br />[Scaricare ODBC](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Ruby     | [Driver Ruby, le istruzioni di installazione](https://docs.microsoft.com/sql/connect/ruby/step-1-configure-development-environment-for-ruby-development)<br />[Pagina di download Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |


<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Driver per l'accesso ORM


Nella tabella seguente sono elencati esempi di Framework relazionale Mapping ORM (Object) utilizzate dalle applicazioni client per connettersi ai database di Microsoft SQL.


| Lingua | Download del driver ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6. x o versioni successive)](http://docs.microsoft.com/ef/) |
| Java | [Lo stato di ibernazione ORM](http://hibernate.org/orm)|
| PHP | [ORM intuitivo, inclusa in Laravel installazione](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby su Guide](http://rubyonrails.org/) |
| &nbsp; | <br /> |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Pagine Web di compilazione-un-app


[http://aka.ms/sqldev](http://aka.ms/sqldev) Consente di accedere a un set di *compilazione un'app* pagine Web. Le pagine Web forniscono informazioni sulle diverse combinazioni di programmazione di lingua, il sistema operativo e driver di connessione SQL. Tra le informazioni contenute nelle pagine Web di compilazione-un-app sono i seguenti elementi:

- Informazioni dettagliate su come iniziare a fin dall'inizio, per ogni combinazione di lingua del sistema operativo + driver.
    - Istruzioni per l'installazione dei driver più recenti di connessione SQL.
- Esempi di codice per ognuno dei seguenti elementi:
    - Esempi di codice relazionale a oggetti.
    - Esempi di codice ORM.
    - Demo di indice ColumnStore per ottenere migliori prestazioni.


#### <a name="first-page-of-build-an-app-webpages"></a>Prima pagina, delle pagine Web di compilazione-un-app

![Pagine di compilazione-un-app Web, prima schermata della pagina][image-ref-163-buildanapp-webpages-first-page]


#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menu per Java - Ubuntu, delle pagine Web di compilazione-un-app

![Pagine Web di compilazione-un-app, menu Ubuntu Java][image-ref-167-buildanapp-webpages-menu-java-ubuntu]


&nbsp;


## <a name="related-links"></a>Collegamenti correlati

- [Esempi di codice per la connessione al Database SQL di Azure nel cloud, con Java e altri linguaggi](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).


<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
