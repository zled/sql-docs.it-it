---
title: Aggiornato - SSMA per i documenti del Server SQL | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione per SQL Server Migration Assistant (SSMA) per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssma-sql-server-migration-assistant
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 68df82bc7da6d7ef5aed3522c06704fb92bb0982
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-migration-assistant-ssma"></a>Nuovi e aggiornati: SQL Server Migration Assistant (SSMA)



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-07-18** &nbsp; - a - &nbsp; **2017-09-11**
- *Area di interesse:* &nbsp; **SQL Server Migration Assistant**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti portano a nuovi articoli che sono stati aggiunti di recente.


***Nessun nuovo articolo da visualizzare.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati che sono elencati nella sezione estratti.

1. [Novità &#39; s di SSMA per DB2 (DB2ToSQL)](#TitleNum_1)
2. [SQL Server Migration Assistant](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-what39s-new-in-ssma-for-db2-db2tosqldb2what-s-new-in-ssma-for-db2-db2tosqlmd"></a>1. &nbsp;[Novità &#39; s di SSMA per DB2 (DB2ToSQL)](db2/what-s-new-in-ssma-for-db2-db2tosql.md)

*Ultimo aggiornamento: 2017-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 24.  ms.author= "Shamikg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c5dfb378ac578f54935a8a1fa7194398f3631017 f4427d1857894ad348cef5c92fbf6b51d00ee652  (PR=3070  ,  Filename=what-s-new-in-ssma-for-db2-db2tosql.md  ,  Dirpath=docs\ssma\db2\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



**SSMA v7.4**

La versione v7.4 di SSMA per DB2 contiene le seguenti modifiche:
- Il **timeout Query** l'opzione è disponibile durante l'individuazione di oggetti dello schema all'origine e di destinazione.
! [opzione di timeout di query.... /Media/query-timeout_red.PNG)

- La metrica della qualità e la conversione è stata migliorata con le correzioni di destinazione, in base ai suggerimenti dei clienti.

> [!IMPORTANT]
> .NET 4.5.2 è un prerequisito per l'installazione di SSMA v7.4. Inoltre, a partire da v7.4, la versione a 32 bit di SSMA è stata sospesa.

**SSMA v7.3**

La versione v7.3 di SSMA per DB2 contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Framework di estendibilità SSMA esposta tramite gli elementi seguenti:
  - La funzionalità di esportazione per un progetto di SQL Server Data Tools (SSDT).
    -   È ora possibile esportare script dello schema da SSMA a un progetto SSDT. È possibile utilizzare gli script di schema per apportare ulteriori modifiche dello schema e distribuire il database.
! [Salva come comando progetto SSDT. /Media/Export-schema-scripts_red.PNG)
  - Librerie che possono essere utilizzate da SSMA per l'esecuzione di conversioni personalizzate.
    - È ora possibile creare codice in grado di gestire le conversioni di sintassi personalizzata e che non sono stati precedentemente gestite dal SSMA.
      - Le istruzioni su come costruire un convertitore personalizzato sono disponibili in questo post di blog [funzionalità di conversione della estensione SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Progetto di esempio per la conversione possibile scaricare questo [post di blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

**Versione 7.2 SSMA**

La versione a versione 7.2 di SSMA per DB2 contiene le seguenti modifiche:
- Metrica qualità e la conversione migliorata con le correzioni di destinazione in base ai suggerimenti dei clienti.
- Miglioramenti di telemetria per fornire una migliore punti dati per risolvere i problemi dei clienti e migliorare il tasso di conversione di SSMA.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-migration-assistantsql-server-migration-assistantmd"></a>2. &nbsp;[SQL Server Migration Assistant](sql-server-migration-assistant.md)

*Ultimo aggiornamento: 2017-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1))

<!-- Source markdown line 36.  ms.author= "Shamikg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 340d718e85fa73c6722862a0a7ba90239b247389 b29f4be2b6d208fd6038c2f9e1c7f0b7bd6b9ed7  (PR=3070  ,  Filename=sql-server-migration-assistant.md  ,  Dirpath=docs\ssma\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



**Origini supportate e le versioni di destinazione**

Per origini supportate, esaminare le informazioni nell'area download per il download SSMA.

Le seguenti versioni di destinazione sono supportate per SSMA.

- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- Database SQL di Azure
- SQL Server, 2017 in Windows e Linux (anteprima)
- * * Azure SQL Data Warehouse

* * Questa destinazione è supportata solo da SSMA per Oracle.









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



