---
title: 'Aggiornamento: documentazione di Tools per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione, per Tools per SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: tools
ms.date: 04/28/2018
ms.openlocfilehash: 0547653c4fc2d8bd04f851b843e74fd9ec78d2ea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MTE
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-tools-for-sql-server"></a>Nuovi e aggiornati: Tools per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **Tools per SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


- [strumento da riga di comando di query MSSQL-cli per SQL Server](mssql-cli.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

- [bcp Utility](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-bcp-utilitybcp-utilitymd"></a>1. &nbsp; [Utilità BCP](bcp-utility.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 189.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c85e6c6ff13ad20f432ead67febfc48c784f3f9a 27de3822192fc64f0d99b4dbc21f05a3e4def186  (PR=5676  ,  Filename=bcp-utility.md  ,  Dirpath=docs\tools\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**-G**<a name="G"></a> Questa opzione viene usata dal client durante la connessione al database SQL di Azure o ad Azure SQL Data Warehouse per specificare che l'utente venga autenticato tramite l'autenticazione di Azure Active Directory. L'opzione -G richiede [versione 14.0.3008.27 o versione successiva](http://go.microsoft.com/fwlink/?LinkID=825643). Per determinare la versione, eseguire bcp-v. Per ulteriori informazioni, vedere [utilizzare Azure Active Directory l'autenticazione per l'autenticazione con il Database SQL o SQL Data Warehouse](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

> [!TIP]
>  Per verificare se la versione dell'utilità bcp include il supporto per il tipo di Azure Active Directory l'autenticazione (AAD) **bcp -** (bcp\<spazio >\<dash >\<dash >) e verificare che venga visualizzato - lettera G nell'elenco di argomenti disponibili.

- **Nome utente e password di Azure Active Directory:**

    Quando si vuole usare nome utente e password di Azure Active Directory, è possibile fornire l'opzione **-G** e anche usare nome utente e password fornendo le opzioni **-U** e **-P** .

    Nell'esempio seguente esporta dati utilizza il nome utente di Active Directory di Azure e la Password in utente e la password è una credenziale di AAD. Nell'esempio vengono esportati tabella `bcptest` dal database `testdb` dal server Azure `aadserver.database.windows.net` e archivia i dati nel file `c:\last\data1.dat`:
```
    bcp bcptest out "c:\last\data1.dat" -c -t -S aadserver.database.windows.net -d testdb -G -U alice@aadtest.onmicrosoft.com -P xxxxx
```

    The following example imports data using Azure AD Username and Password where user and password is an AAD credential. The example imports data from file `c:\last\data1.dat` into table `bcptest` for database `testdb` on Azure server `aadserver.database.windows.net` using Azure AD User/Password:
```
    bcp bcptest in "c:\last\data1.dat" -c -t -S aadserver.database.windows.net -d testdb -G -U alice@aadtest.onmicrosoft.com -P xxxxx
```



- **Integrazione con Azure Active Directory**

    Per l'autenticazione integrata di Azure Active Directory, fornire l'opzione **-G** senza nome utente o password. Questa configurazione si presuppone che l'account utente di Windows corrente (l'account viene eseguito il comando bcp) è federata con Azure AD:







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (11+6):&nbsp; documentazione di &nbsp;**Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (18+0): &nbsp; documentazione di &nbsp;**Analysis Services per SQL Server**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (218+14):**documentazione della**connessione a SQL Server](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (14+0):&nbsp; documentazione del &nbsp;**motore di database per SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (3+2): documentazione di &nbsp;&nbsp;**SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+3):&nbsp; documentazione di &nbsp;**Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (7+10):&nbsp; documentazione dei &nbsp;**database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+3):&nbsp; documentazione di &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (2+3):&nbsp; documentazione di &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (5+2):&nbsp; documentazione di &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+1): documentazione di &nbsp;&nbsp;**Tools per SQL Server**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0):**documentazione della**piattaforma di strumenti analitici per SQL Server](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)

