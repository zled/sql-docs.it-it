---
title: Home page per la programmazione del client SQL | Documenti Microsoft
description: Pagina hub con annotazioni collegamenti ai download e la documentazione per diverse combinazioni di lingue e sistemi operativi per la connessione a SQL Server o in Database SQL di Azure.
author: MightyPen
ms.date: 09/13/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: connect
ms.suite: sql
ms.custom: 
ms.technology: drivers
ms.topic: article
ms.reviewer: meetb
ms.author: genemi
ms.workload: Inactive
ms.openlocfilehash: dbbb2e06521b364de7d8de1b32869380fbc2772a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Home page per client di programmazione per Microsoft SQL Server


Benvenuti nella homepage sul client per interagire con Microsoft SQL Server e Database SQL di Azure nel cloud di programmazione. In questo articolo fornisce le informazioni seguenti:

- Vengono elencate e descritte le combinazioni di lingua e i driver disponibili.
    - Vengono fornite informazioni per i sistemi operativi di Windows, Linux (Ubuntu e altri) e MacOS.
- Vengono forniti collegamenti alla documentazione dettagliata per ogni combinazione.
- Consente di visualizzare le aree e le sottoaree della documentazione gerarchica per determinate lingue, laddove appropriato.


#### <a name="azure-sql-database"></a>Database SQL di Azure

In qualsiasi lingua, il codice che si connette a SQL Server è quasi identico al codice per la connessione al Database SQL di Azure.

Per informazioni dettagliate sulle stringhe di connessione per la connessione al Database SQL di Azure, vedere:

- [Eseguire una query di un database SQL di Azure .NET Core (c#)](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core).
- Altri Database SQL di Azure presenti nelle vicinanze nell'articolo nella tabella del contenuto, informazioni sulle altre lingue. Ad esempio, vedere [PHP utilizzare query su un database SQL di Azure](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Pagine Web di compilazione-un-app

Il nostro *compilazione-un-app* pagine Web presenti esempi di codice, insieme alle informazioni di configurazione, in un formato alternativo. Per ulteriori informazioni, vedere più avanti in questo articolo il [sezione denominata *sito Web di compilazione-un-app*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Lingue e i driver per i programmi client


Nella tabella seguente, ogni immagine di lingua è un collegamento ai dettagli sull'utilizzo del linguaggio con SQL Server. Ogni collegamento consente di passare a una sezione più avanti in questo articolo.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp;[ ![C# logo][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp;[ ![ORM Entity Framework di .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp;[ ![Logo Java][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp;[ ![Logo Node.js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [**`ODBC for C++`**](#an-160-odbc-cpp-docu) | &nbsp;[ ![Logo PHP][image-ref-360-php]](#an-170-php-docu) |
| &nbsp;[ ![Logo Python][image-ref-370-python]](#an-180-python-docu) | &nbsp;[ ![Ruby logo][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Scarica e installa automaticamente

L'articolo è dedicato per il download e installare i driver di connessione SQL diversi, per l'utilizzo da linguaggi di programmazione:

- [Driver di SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![Logo di c#][image-ref-320-csharp] In c# con ADO.NET

I linguaggi .NET gestito, quali c# e Visual Basic, sono gli utenti più comuni di ADO.NET. *ADO.NET* è un nome casuale per un subset di classi .NET Framework.

#### <a name="code-examples"></a>Esempi di codice

|||
| :-- | :-- |
| [Modello di verifica la connessione a SQL mediante ADO.NET](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | Un esempio di codice esegue la connessione e l'esecuzione di query SQL Server. |
| [Connettere in modo resiliente a SQL con ADO.NET](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | La logica di riesecuzione in un esempio di codice, poiché le connessioni possono verificarsi occasionalmente momenti di perdita di connettività.<br /><br />Logica di riesecuzione si applica anche per le connessioni gestite tramite internet in qualsiasi database cloud, ad esempio al Database SQL Azure. |
| [Database SQL di Azure: Dimostrazione di come utilizzare .NET Core su Linux/Windows/macOS per creare un programma c#, per connettersi ed eseguire query](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Esempio di Database SQL Azure. |
| [Compilazione un'app: Windows in c#, ADO.NET,](http://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentazione

|||
| :-- | :-- |
| [In c# con ADO.NET](./ado-net/index.md)| Radice della documentazione. |
| [Namespace: System. Data](http://docs.microsoft.com/dotnet/api/system.data) | Un set di classi utilizzate per ADO.NET. |
| [Namespace: SqlClient](http://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Il set di classi che sono più direttamente il centro di ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Logo di Entity Framework][image-ref-333-ef] Entity Framework (EF) con C&#x23;

Entity Framework (EF) fornisce Mapping relazionale a oggetti (ORM). ORM rende più semplice per il codice sorgente di programmazione orientata a oggetti (OOP) modificare i dati recuperati da un database relazionale di SQL.

Entity Framework sono relazioni dirette o indirette con le tecnologie seguenti:

- .NET Framework
- [LINQ to SQL](http://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/), o [LINQ to Entities](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Miglioramenti di sintassi del linguaggio, ad esempio il  **=>**  operatore in c#.
- Programmi utili che generano codice sorgente per le classi di cui eseguire il mapping alle tabelle nel database SQL. Ad esempio, [EdmGen.exe](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>EF originale ed EF nuovo

Il [pagina iniziale per Entity Framework](http://docs.microsoft.com/ef/) introduce EF con una descrizione simile al seguente:

- Entity Framework è un mapping relazionale a oggetti (O/RM) che consente agli sviluppatori .NET di utilizzare un database utilizzando gli oggetti .NET. Elimina la necessità per la maggior parte del codice sorgente di accesso ai dati che in genere gli sviluppatori devono scrivere.

*Entity Framework* è un nome condiviso da due rami del codice sorgente separato. Un ramo di Entity Framework è precedente, e il relativo codice sorgente può ora essere gestito mediante pubblico. L'altro EF è nuovo. I due EFs sono descritte di seguito.

|     |     |
| :-- | :-- |
| [Entity Framework 6. x](http://docs.microsoft.com/ef/ef6/) | Innanzitutto, Microsoft ha rilasciato EF in agosto 2008. Marzo 2015 Microsoft ha annunciato che Entity Framework 6. x è la versione finale che sviluppa Microsoft. Microsoft ha rilasciato il codice sorgente nel dominio pubblico.<br /><br />Inizialmente EF faceva parte di .NET Framework. Ma Entity Framework 6. x è stato rimosso da .NET Framework.<br /><br />[Codice sorgente di 6. x EF su Github, nel repository *aspnet/EntityFramework6*](http://github.com/aspnet/EntityFramework6) |
| [EF Core](http://docs.microsoft.com/ef/core/) | Microsoft ha rilasciato il nucleo di EF concezione giugno 2016. Core di Entity Framework è progettato per migliorare la flessibilità e portabilità. EF Core è possibile eseguire nei sistemi operativi oltre solo Microsoft Windows. E Core EF possono interagire con i database oltre solo Microsoft SQL Server e altri database relazionali.<br /><br />**C&#x23; esempi di codice:**<br />[Introduzione a Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Introduzione a Entity Framework Core in .NET Framework con un Database esistente](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

Entity Framework e le tecnologie correlate sono potenti e sono molto da imparare per lo sviluppatore che desidera master l'intera area.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Logo Java][image-ref-330-java] Java e JDBC

Microsoft fornisce un driver Java Database Connectivity (JDBC) da utilizzare con SQL Server (o con Database SQL di Azure, naturalmente). Si tratta di un driver JDBC di tipo 4, e fornisce la connettività di database tramite le interfacce di programma dell'applicazione (API) JDBC standard.

#### <a name="code-examples"></a>Esempi di codice

|||
| :-- | :-- |
| [Esempi di codice](./jdbc/code-samples/index.md) | Esempi di codice che insegna sui tipi di dati, i set di risultati e i dati di grandi dimensioni. |
| [Esempio di URL di connessione](./jdbc/connection-url-sample.md) | Viene descritto come utilizzare un URL di connessione per connettersi a SQL Server. Utilizzarlo per utilizzare un'istruzione SQL per recuperare i dati. |
| [Esempio di origine dati](./jdbc/data-source-sample.md) | Viene descritto come utilizzare un'origine dati per connettersi a SQL Server. Utilizzare quindi una stored procedure per recuperare i dati. |
| [Usare Java per eseguire query di un database SQL di Azure](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Esempio di Database SQL Azure. |
| [Creazione di applicazioni Java utilizza SQL Server in Ubuntu](http://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentazione

La documentazione di JDBC include le aree principali seguenti:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Radice della documentazione JDBC. |
| [Riferimento](./jdbc/reference/index.md) | Interfacce, classi e membri. |
| [Guida di programmazione per il driver PHP per SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Logo di Node.js][image-ref-340-node] Node.js

Con Node.js è possibile connettersi a SQL Server da Windows, Linux o Mac. La radice della documentazione Node.js è [qui](./node-js/index.md).

Il driver di connessione di Node.js per SQL Server viene implementato in JavaScript. Il driver utilizza il protocollo TDS, supportato da tutte le versioni moderne di SQL Server. Il driver è un progetto open source, [disponibile in Github](http://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Esempi di codice

|||
| :-- | :-- |
| [Modello di connessione a SQL tramite Node.js prova](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Vasta gamma di codice sorgente per la connessione a SQL Server e l'esecuzione di una query. |
| [Database SQL di Azure: usare Node.js per query](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Esempio per il Database SQL di Azure nel cloud. |
| [Creazione di applicazioni Node.js per l'utilizzo di SQL Server in macOS](http://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC per C++ 

![Logo ODBC][image-ref-350-odbc]

(ODBC) Open database connectivity sviluppato nel 1990s e anticipa .NET Framework. ODBC è progettato per essere indipendente da qualsiasi sistema di database e indipendente dal sistema operativo.

Nel corso degli anni numerosi driver ODBC sono stati creati e rilasciati da gruppi all'interno e all'esterno di Microsoft. L'intervallo dei driver comportano diversi linguaggi di programmazione di client. L'elenco delle destinazioni di dati esula SQL Server.

Alcuni altri driver di connettività utilizzare ODBC internamente.

#### <a name="code-example"></a>Esempio di codice

- [Esempio di codice C++, tramite ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Struttura di documentazione

Il contenuto ODBC in questa sezione è incentrata sull'accesso a SQL Server o Database SQL di Azure da C++. La tabella seguente elenca una struttura approssimativa della documentazione principale per ODBC.


| Area | Area secondaria | Description |
| :--- | :------ | :---------- |
| [ODBC per C++](./odbc/index.md) | Radice della documentazione. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Informazioni sull'utilizzo di ODBC nei sistemi operativi Linux o Mac OS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Informazioni sull'utilizzo di ODBC nel sistema operativo Windows. |
| [Amministrazione](../odbc/admin/index.md) | &nbsp; | Lo strumento di amministrazione per la gestione di origini dati ODBC. |
| [Microsoft](../odbc/microsoft/index.md)  | &nbsp; | Driver ODBC diversi che vengono creati e fornito da Microsoft. |
| [Concettuale e riferimento](../odbc/reference/index.md) | &nbsp; | Informazioni concettuali sull'interfaccia ODBC, oltre a riferimento tradizionale. |
| &nbsp; " | [Appendici](../odbc/reference/appendixes/index.md)    | Tabelle di transizione di stato, la libreria di cursori ODBC e altro ancora. |
| &nbsp; " | [Sviluppo di app](../odbc/reference/develop-app/index.md)  | Funzioni, gli handle e molto altro ancora. |
| &nbsp; " | [Sviluppo di driver](../odbc/reference/develop-driver/index.md) | Come sviluppare driver ODBC, se si dispone di un'origine dati speciali. |
| &nbsp; " | [Installare](../odbc/reference/install/index.md) | Installazione di ODBC, sottochiavi e altro ancora. |
| &nbsp; " | [Sintassi](../odbc/reference/syntax/index.md)   | API per l'installazione, programma di installazione, la conversione e dati di accesso. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Logo PHP][image-ref-360-php] PHP

È possibile utilizzare PHP per interagire con SQL Server. La radice della documentazione Node.js è [qui](./php/index.md).

#### <a name="code-examples"></a>Esempi di codice

|||
| :-- | :-- |
| [Modello di verifica la connessione a SQL tramite PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Un esempio di codice esegue la connessione e l'esecuzione di query SQL Server. |
| [Connettere in modo resiliente a SQL con PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | La logica di riesecuzione in un esempio di codice, poiché le connessioni tramite Internet e il cloud possono verificarsi occasionalmente momenti di perdita di connettività. |
| [Database SQL di Azure: utilizzo PHP per query](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Esempio di Database SQL Azure. |
| [Creazione di applicazioni PHP per l'utilizzo di SQL Server su RHEL](http://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Logo di Python][image-ref-370-python] Python


È possibile utilizzare Python per interagire con SQL Server.

#### <a name="code-examples"></a>Esempi di codice

|||
| :-- | :-- |
| [Modello di verifica la connessione a SQL con Python mediante pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Un esempio di codice esegue la connessione e l'esecuzione di query SQL Server. |
| [Database SQL di Azure: usare Python per query](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Esempio di Database SQL Azure. |
| [Creazione di applicazioni PHP per l'utilizzo di SQL Server in SLES](http://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Documentazione

| Area | Description |
| :--- | :---------- |
| [Python a SQL Server](./python/index.md) | Radice della documentazione. |
| [driver pymssql](./python/pymssql/index.md) | Microsoft non gestire o il driver pymssql di test.<br /><br />Il driver di connessione pymssql è un'interfaccia semplice per i database SQL, per utilizzarli in programmi di Python. Pymssql si basa sulle disporre di FreeTDS per fornire un'interfaccia di Python (PEP 249) API DB per Microsoft SQL Server. |
| [driver pyodbc](./python/pyodbc/index.md)   | Il driver di connessione pyodbc è un modulo di origine aprire Python che semplifica l'accesso ai database ODBC. Implementa la specifica API DB 2.0, ma è dotato anche di praticità Pythonic. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Logo Ruby][image-ref-380-ruby] Ruby

È possibile utilizzare Ruby per interagire con SQL Server. La radice della documentazione Ruby è [qui](./ruby/index.md).

#### <a name="code-examples"></a>Esempi di codice

|||
| :-- | :-- |
| [Modello di connessione a SQL con Ruby prova](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Un esempio di codice esegue la connessione e l'esecuzione di query SQL Server. |
| [Database SQL di Azure: utilizzo Ruby alla query](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Esempio di Database SQL Azure. |
| [Creare App Ruby per utilizzare SQL Server su MacOS](http://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Informazioni di configurazione, insieme a esempi di codice. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpwwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Sito Web di compilazione-un-app, per lo sviluppo di SQL client](http://www.microsoft.com/sql-server/developer-get-started/)


Nel nostro [ *compilazione-un-app* ](https://www.microsoft.com/sql-server/developer-get-started/) pagine Web, è possibile scegliere tra un lungo elenco di linguaggi per la connessione a SQL Server di programmazione. E il programma client può eseguire una vasta gamma di sistemi operativi.

*Compilazione-un-app* evidenziare la semplicità e completezza per lo sviluppatore che è solo informazioni introduttive. Vengono descritte le attività seguenti:

1. Come installare Microsoft SQL Server
2. Come scaricare e installare gli strumenti e i driver.
3. Esecuzione di tutte le configurazioni necessarie, come appropriato per il sistema operativo scelto.
4. Viene descritto come compilare il codice sorgente specificato.
5. Come eseguire il programma.

Successivamente vengono contorni approssimativi un paio di dettaglio nel sito Web:

#### <a name="java-on-ubuntu"></a>Java su Ubuntu:

1. Configurare l'ambiente
    - Passaggio 1.1 installare SQL Server
    - Passaggio 1.2 installare Java
    - Passaggio 1.3 installare Java Development Kit (JDK)
    - Passaggio 1.4 installare Maven
2. Creare l'applicazione Java con SQL Server
    - Passaggio 2.1: creazione di un'applicazione Java che si connette a SQL Server ed esegue query
    - Passaggio 2.2 creare un'applicazione Java che si connette a SQL Server utilizzando il framework più diffuso di ibernazione
3. Rendere la tua app Java fino a 100 volte più veloce
    - Passaggio 3.1: creazione di un'applicazione Java per illustrare gli indici Columnstore

#### <a name="python-on-windows"></a>Python in Windows:

1. Configurare l'ambiente
    - Passaggio 1.1 installare SQL Server
    - Passaggio 1.2 installare Python
    - Passaggio 1.3 installare il Driver ODBC e utilità della riga di comando SQL per SQL Server
2. Creare applicazione Python con SQL Server
    - Passaggio 2.1 installare il driver di Python per SQL Server
    - Passaggio 2.2: creazione di un database per l'applicazione
    - Passaggio 2.3: creazione di un'applicazione Python che si connette a SQL Server ed esegue query
3. Rendere la tua app Python fino a 100 volte più veloce
    - Passaggio 3.1 creare una nuova tabella con 5 milioni di utilizzo di sqlcmd
    - Passaggio 3.2: creazione di un'applicazione Python che esegue una query in questa tabella e misura il tempo impiegato
    - Passaggio 3.3 misurare il tempo impiegato per eseguire la query
    - Aggiungi passaggio 3.4 un indice columnstore alla tabella
    - Passaggio 3.5 misurare il tempo impiegato per eseguire la query con un indice columnstore

Le schermate seguenti offrono un'idea generale dell'aspetto analogo al seguente sito di documentazione di sviluppo SQL.

#### <a name="choose-a-language"></a>Scegliere una lingua:

![Sito Web di sviluppo di SQL, introduzione][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Scegliere un sistema operativo:

![Sito Web di sviluppo di SQL, Ubuntu Java][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Altri sviluppo


In questa sezione vengono forniti collegamenti sulle altre opzioni di sviluppo. Questi includono l'utilizzo di queste stesse lingue per lo sviluppo di Azure in generale. Le informazioni non sono limitate come destinazione solo i Database SQL di Azure e Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Hub di sviluppatore per Azure

- [Hub di sviluppatore per Azure](http://docs.microsoft.com/azure/)
- [Azure per gli sviluppatori di .NET](http://docs.microsoft.com/dotnet/azure/)
- [Azure per gli sviluppatori Java](http://docs.microsoft.com/java/azure/)
- [Azure per gli sviluppatori di Node.js](http://docs.microsoft.com/nodejs/azure/)
- [Azure per sviluppatori Python](http://docs.microsoft.com/python/azure/)
- [Creare un'app web PHP in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Altri linguaggi

- [Creazione di applicazioni di Go tramite SQL Server in Windows](http://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

[image-ref-310-ado-net]: ./media/homepage-sql-connection-drivers/gm-ado-net-an51.png
[image-ref-322-cpp]: ./media/homepage-sql-connection-drivers/gm-cpp-4point-p61f.png
[image-ref-320-csharp]: ./media/homepage-sql-connection-drivers/gm-csharp-c10c.png
[image-ref-333-ef]: ./media/homepage-sql-connection-drivers/gm-entity-framework-ef20d.png
[image-ref-330-java]: ./media/homepage-sql-connection-drivers/gm-java-j18c.png
[image-ref-340-node]: ./media/homepage-sql-connection-drivers/gm-node-n30.png
[image-ref-350-odbc]: ./media/homepage-sql-connection-drivers/gm-odbc-ic55826-o35.png
[image-ref-360-php]: ./media/homepage-sql-connection-drivers/gm-php-php60.png
[image-ref-370-python]: ./media/homepage-sql-connection-drivers/gm-python-py72.png
[image-ref-380-ruby]: ./media/homepage-sql-connection-drivers/gm-ruby-un-r82.png
[image-ref-390-aka-ms-sqldev-choose-language]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-400-aka-ms-sqldev-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png

