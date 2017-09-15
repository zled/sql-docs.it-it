---
title: Aggiornato - T-SQL docs | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, Transact-SQL.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: t-sql
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fa2ad3f4bc6071c54b9996a893ee584ba215100f
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Nuovi e recentemente aggiornato: docs Transact-SQL



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-07-18** &nbsp; - a - &nbsp; **2017-09-11**
- *Area di interesse:* &nbsp; **T-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti portano a nuovi articoli che sono stati aggiunti di recente.


1. [STIMA (Transact-SQL)](queries/predict-transact-sql.md)
2. [LIBRERIA esterna ALTER (Transact-SQL)](statements/alter-external-library-transact-sql.md)
3. [CREARE una libreria esterna (Transact-SQL)](statements/create-external-library-transact-sql.md)
4. [ELIMINARE una libreria esterna (Transact-SQL)](statements/drop-external-library-transact-sql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati che sono elencati nella sezione estratti.

1. [CAST e CONVERT (Transact-SQL)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-cast-and-convert-transact-sqlfunctionscast-and-convert-transact-sqlmd"></a>1. &nbsp;[CAST e CONVERT (Transact-SQL)](functions/cast-and-convert-transact-sql.md)

*Ultimo aggiornamento: 2017-09-08* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 647.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b805ecddecda72ffc026c3866b5284a79b69fb3f f2906eaf87c7cdf1409922d4efba8cd1c5635674  (PR=0  ,  Filename=cast-and-convert-transact-sql.md  ,  Dirpath=docs\t-sql\functions\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



**K. Utilizzo di CAST con operatori aritmetici**

L'esempio seguente calcola un calcolo singola colonna dividendo il prezzo unitario del prodotto (`UnitPrice`) per la percentuale di sconto (`UnitPriceDiscountPct`). Il risultato viene convertito in un tipo di dati `int` dopo l'arrotondamento al numero intero più prossimo. Usa AdventureWorksDW.

```
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice
FROM dbo.FactResellerSales
WHERE SalesOrderNumber = 'SO47355'
      AND UnitPriceDiscountPct > .02;
```

..! Includi-NotShown - ssResult-... /.. /Includes/ssresult-MD.MD])

```
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1
```

**L. Utilizzo di CAST per la concatenazione**

Nell'esempio seguente consente di concatenare le espressioni non di tipo carattere tramite CAST. Usa AdventureWorksDW.

```
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice
FROM dbo.DimProduct
WHERE ListPrice BETWEEN 350.00 AND 400.00;
```

..! Includi-NotShown - ssResult-... /.. /Includes/ssresult-MD.MD])

```
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09
```

**M. Utilizzo di CAST per produrre leggibilità del testo**

Nell'esempio seguente usa CAST nell'elenco di selezione per convertire il `Name` colonna un **char (10)** colonna. Usa AdventureWorksDW.

```
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice
FROM dbo.DimProduct
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';
```

..! Includi-NotShown - ssResult-... /.. /Includes/ssresult-MD.MD])







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Questa sezione sono elencati gli articoli molto simili per gli articoli aggiornati di recente in altre aree di interesse, entro l'archivio pubblico di GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3 + 12): **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5 + 0): **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5 + 1): **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19 + 82): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1 + 8): **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12 + 1): **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0 + 1): **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7 + 1): **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1 + 1): **SQL Server Data Tools (SSDT)** documenti](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0 + 2): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1 + 4): **SQL Server Management Studio (SSMS)** documenti](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornati (4 + 1): **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0 + 1): **Tools per SQL** documenti](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0 + 0): **Analysis Services per SQL** documenti](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0 + 0): **Master Data Services (MDS) per SQL** documenti](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



