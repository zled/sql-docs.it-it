---
title: 'Articolo aggiornato: documentazione dei database relazionali | Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione dei database relazionali.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: 
ms.component: relational-databases-misc
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: 
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.author: genemi
ms.openlocfilehash: c4ba0c20ca68b64ae377dfd3fb5855be30fed080
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Articoli nuovi e aggiornati di recente: documentazione dei database relazionali
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]


Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **11/09/2017** &nbsp; - &nbsp; **27/09/2017**
- *Area di interesse:* &nbsp; **database relazionali**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Importare ed esportare dati da SQL Server e dal database SQL di Microsoft Azure](import-export/overview-import-export.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Panoramica dei tipi di dati spaziali](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-spatial-data-types-overviewspatialspatial-data-types-overviewmd"></a>1. &nbsp; [Panoramica dei tipi di dati spaziali](spatial/spatial-data-types-overview.md)

*Aggiornamento: 26/09/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 27.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96dd44cf49e96d1d543a629d49de297dba9c1753 2e9629f852ea42a213c7c24831bcfa53e40358f2  (PR=0  ,  Filename=spatial-data-types-overview.md  ,  Dirpath=docs\relational-databases\spatial\  ,  MergeCommitSha40=b33976cf92f23fbb13cee0c353fd40608d002d94) -->



 -  Esistono due tipi di dati spaziali. Il tipo di dati **geometry** supporta dati planari o euclidei (terra piatta). Il tipo di dati **geometry** è conforme a Open Geospatial Consortium (OGC) Simple Features for SQL Specification versione 1.1.0 e a SQL MM (standard ISO).
 -
 - Inoltre, ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] supporta il tipo di dati **geography**, che archivia dati ellissoidali (terra rotonda), ad esempio coordinate di latitudine e longitudine GPS.
 -
 -> [!IMPORTANT]
 ->  Per una descrizione dettagliata e alcuni esempi delle funzionalità spaziali introdotte in ..!NCLUDE-NotShown--ssSQL11--../../includes/sssql11-md.md)],, tra cui i miglioramenti apportati ai tipi di dati spaziali, scaricare il white paper [Nuove funzionalità spaziali in SQL Server nome in codice "Denali"](http://go.microsoft.com/fwlink/?LinkId=226407).
 -
 -##  <a name="objects"></a> Oggetti dati spaziali
 - I tipi di dati **geometry** e **geography** supportano sedici oggetti dati spaziali o tipi di istanza. Solo per undici di questi tipi di istanza, tuttavia, è possibile *creare istanze*. È possibile creare e usare queste istanze (o crearne un'istanza) in un database. Queste istanze derivano determinate proprietà dai relativi tipi di dati padre che consentono di distinguerle come **Points**, **LineStrings, CircularStrings**, **CompoundCurves**, **Polygons**, **CurvePolygons** o come più istanze di **geometry** o **geography** in un oggetto **GeometryCollection**. Il tipo**Geography** dispone di un tipo di istanza aggiuntivo, **FullGlobe**.
 -
 - Nella figura seguente viene illustrata la gerarchia **geometry** sulla quale si basano i tipi di dati **geometry** e **geography** . I tipi di **geometry** e **geography** di cui è possibile creare istanze sono indicati in blu.
 -
 - ![geom_hierarchy--../../relational-databases/spatial/media/geom-hierarchy.gif)
 -
 - Come indicato nella figura, i dieci tipi di cui è possibile creare istanze dei tipi di dati **geometry** e **geography** sono **Point**, **MultiPoint**, **LineString**, **CircularString**, **MultiLineString**, **CompoundCurve**, **Polygon**, **CurvePolygon**, **MultiPolygon**e **GeometryCollection**. Vi è un tipo aggiuntivo di cui è possibile creare istanze per il tipo di dati geography, ovvero **FullGlobe**. I tipi **geometry** e **geography** sono in grado di riconoscere un'istanza specifica purché si tratti di un'istanza con formato corretto, anche se non definita in modo esplicito. Ad esempio, se si definisce un'istanza **Point** usando in modo esplicito il metodo STPointFromText(), **geometry** e **geography** riconoscono l'istanza come **Point**, purché il formato dell'input del metodo sia corretto. Se si definisce la stessa istanza utilizzando il metodo `STGeomFromText()` , entrambi i tipi di dati **geometry** e **geography** riconoscono l'istanza come **Point**.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+1): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (4+1): documentazione del **motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (17+0): documentazione di **Integration Services per SQL**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (3+0): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (1+1): documentazione dei **database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (2+0): documentazione di **Reporting Services per SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+1): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+0): documentazione di **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


