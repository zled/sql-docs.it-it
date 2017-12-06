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
ms.date: 12/02/2017
ms.author: genemi
ms.workload: t-sql
ms.openlocfilehash: 33c50454f34c1902ea7f7dedc9ecb0a54f99ce24
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Nuovi e recentemente aggiornato: docs Transact-SQL



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-09-28** &nbsp; - a - &nbsp; **2017-02-12**
- *Area di interesse:* &nbsp; **T-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


***Nessun nuovo articolo da visualizzare.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Barra rovesciata (continuazione di riga) (Transact-SQL)](#TitleNum_1)
2. [Selezionare, ordinare per clausola (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-backslash-line-continuation-transact-sqllanguage-elementssql-server-utilities-statements-backslashmd"></a>1. &nbsp;[Barra rovesciata (continuazione di riga) (Transact-SQL)](language-elements/sql-server-utilities-statements-backslash.md)

*Ultimo aggiornamento: 2017-11-15* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9484441710ac9a083a554ffadb59a3b7e92484b3 19b9c37c65ba462a32067c80e81a920eeb339851  (PR=3966  ,  Filename=sql-server-utilities-statements-backslash.md  ,  Dirpath=docs\t-sql\language-elements\  ,  MergeCommitSha40=b0c223ba0f78af5eb76948e68e2d1aab2e7b80c1) -->



**B. Suddividere una stringa binaria**


Nell'esempio seguente usa una barra rovesciata e un ritorno a capo per suddividere una stringa binaria in due righe.

```
SELECT 0xabc\
def AS [ColumnResult];

```

 ..! Includi-NotShown - ssResult-... /.. /Includes/ssresult-MD.MD])

```
 ColumnResult
 ------------
 0xABCDEF
```




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-select---order-by-clause-transact-sqlqueriesselect-order-by-clause-transact-sqlmd"></a>2. &nbsp;[Selezionare - ORDER BY clausola (Transact-SQL)](queries/select-order-by-clause-transact-sql.md)

*Ultimo aggiornamento: 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1))

<!-- Source markdown line 481.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b8d7bc7bab46e914eb2facf6c654a5944383077e de7e4f3f7826011e273120a2b6b08af4d263a510  (PR=3663  ,  Filename=select-order-by-clause-transact-sql.md  ,  Dirpath=docs\t-sql\queries\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



**<a name="Union"></a>Utilizzo di ORDER BY con UNION, EXCEPT e INTERSECT**

 Quando una query utilizza l'operatore UNION, EXCEPT o INTERSECT, è necessario specificare la clausola ORDER BY alla fine dell'istruzione e i risultati delle query combinate vengono ordinati. Nell'esempio seguente vengono restituiti tutti i prodotti rossi o gialli e questo elenco combinato viene ordinato in base alla colonna `ListPrice`.

```sql
USE AdventureWorks2012;
GO
SELECT Name, Color, ListPrice
FROM Production.Product
WHERE Color = 'Red'
-- ORDER BY cannot be specified here.
UNION ALL
SELECT Name, Color, ListPrice
FROM Production.Product
WHERE Color = 'Yellow'
ORDER BY ListPrice ASC;

```

**Esempi:.... Includi-NotShown - ssSDWfull-... /.. /Includes/sssdwfull-MD.MD)] e.... Includi-NotShown - ssPDW-... /.. /Includes/sspdw-MD.MD])**








## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3 + 14): **Analitica avanzate per SQL** documenti](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87 + 0): **Analitica Platform System per SQL** documenti](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5 + 4): **Connect to SQL** documenti](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0 + 1): **motore di Database per SQL** documenti](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2 + 2): **Integration Services per SQL** documenti](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10 + 9): **Linux per SQL** documenti](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2 + 4): **database relazionali di SQL** documenti](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornati (4 + 2): **Reporting Services per SQL** documenti](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0 + 1): **esempi per SQL** documenti](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21 + 0): **operazioni SQL Studio** documenti](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5 + 1): **Microsoft SQL Server** documenti](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1 + 0): **SQL Server Migration Assistant (SSMA)** documenti](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0 + 2): **Transact-SQL** documenti](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): **dati Migration Assistant (DMA) per SQL** documenti](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


