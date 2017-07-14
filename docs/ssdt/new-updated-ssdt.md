---
title: 'Aggiornamento: documentazione di SSDT per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione di SQL Server Data Tools (SSDT) per SQL Server.
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
ms.date: 06/30/2017
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 5e43cb76dac922b3c43318b2a9f539ab19ec7bfe
ms.contentlocale: it-it
ms.lasthandoff: 07/03/2017

---
# Articoli nuovi e aggiornati di recente: SQL Server Data Tools (SSDT)
<a id="new-and-recently-updated-sql-server-data-tools-ssdt" class="xliff"></a>



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo di date degli aggiornamenti:* &nbsp; **17/05/2017** &nbsp; - &nbsp; **30/06/2017**
- *Area di interesse:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## Nuovi articoli creati di recente
<a id="new-articles-created-recently" class="xliff"></a>

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


*Nessun nuovo articolo da visualizzare.*



&nbsp;

## Articoli aggiornati con estratti
<a id="updated-articles-with-excerpts" class="xliff"></a>

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### 1. &nbsp;[Log delle modifiche per SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)
<a id="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd" class="xliff"></a>

*Aggiornamento: 19/05/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 21.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cf17883ce0daf75fdf88881171bf4042558b1cf4 536fe0fe41b023a4186f494a509fa14fcbafccf4  (PR=1777  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=5bd0e1d3955d898824d285d28979089e2de6f322) -->



Per i post dettagliati sulle novità e sulle modifiche, vedere [il blog del team di SSDT](https://blogs.msdn.microsoft.com/ssdt/)

**SSDT 17.1**

Numero di build: 14.0.61705.170

**Novità**

**Progetti AS:**
- Gli utenti possono impostare la codifica di hint per le colonne nell'interfaccia utente nei modelli 1400
- IntelliSense non correlati al modello è ora disponibile in modalità offline
- Esplora modelli tabulari ora contiene un nodo per rappresentare denominate espressioni M disponibili nel modello (modelli tabulari a livello di compatibilità di 1400)
- Azure Active Directory selezione utenti simile a una pagina IAM del portale di Microsoft Azure disponibili quando si imposta i membri del ruolo nei modelli tabulari

**Progetti di database:**
- Aggiornamento di DacFx 17,1

**Correzioni di bug**

- Risolto un problema in cui il nome del gruppo di finestre di progettazione di Business Intelligence è stato visualizzato in modo non corretto in Opzioni di Visual Studio in VS2017
- Risolto un problema in cui può verificarsi un arresto anomalo la generazione di una mappa del codice per una soluzione con un progetto di Report o come progetto
- Un numero fisso di problemi con l'integrazione di PowerQuery per i modelli tabulari di Analysis Services 1400 a livello di compatibilità
- Risolto un problema nel nuovo editor DAX finestra degli strumenti in cui l'operatore di assegnazione non è stato in una riga distinta quando si definisce una misura
- Risolto un problema che impedisce la visualizzazione tabulare misura dall'aggiornamento durante la ridenominazione delle misure nella prospettiva
- Aggiornato motore integrato dell'area di lavoro di Analysis Services e modello a oggetti tabulare che corregge un test di regressione che ha causato contenente traduzioni avrà esito negativo nei progetti tabulari 1200 distribuire nel server SQL Server 2016 Analysis Services
- Correzione di un problema di prestazioni che ha effettuato creation\deletion di nuove origini di dati tabulare 1400 molto lente
- Risolto un problema in cui il diagramma vista origine dati nei modelli multidimensionali Impossibile arresta rendering se la modifica di visualizzazione rapidamente tra diverse viste origine dati

**DacFx 17.1**

- Risolto un problema durante la crittografia di una colonna con le tabelle con ottimizzazione per la memoria con altre colonne di identità
- Supporto per l'opzione CATALOG_COLLATION per creare DATABASE SQLDOM





&nbsp;

<a name="compactupdatedlist"/>

## Compact elenco degli articoli aggiornato di recente
<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati elencati nella sezione precedente.

1. [Log delle modifiche per SQL Server Data Tools (SSDT)](#TitleNum_1)




<a name="sisters2"/>

&nbsp;

## Articoli sorella
<a id="sister-articles" class="xliff"></a>

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno dello stesso repository GitHub: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170630-1150  -->

#### Aree di interesse con articoli nuovi o aggiornati di recente
<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

- [Nuovo + aggiornato (12+2): **Advanced Analytics for SQL (Analisi avanzata per SQL)** Docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+2): **Connect to SQL (Connettersi a SQL)** Docs](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (3+0): **Database Engine for SQL (Motore di database per SQL)** Docs](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (1+2): **Integration Services for SQL (Integration Services per SQL)** Docs](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (2+8): **Linux for SQL (Linux per SQL)** Docs](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (1+0): **Master Data Services (MDS) for SQL (Master Data Services (MDS) per SQL)** Docs](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (5+5): **Relational Databases for SQL (Database relazionali per SQL)** Docs](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (2+0): **Reporting Services for SQL (Reporting Services per SQL)** Docs](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+4): **Microsoft SQL Server** Docs](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (1+0): **Tools for SQL (Strumenti per SQL)** Docs](../tools/new-updated-tools.md)


#### Aree di interesse senza articoli nuovi o aggiornati di recente
<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **Transact-SQL** Docs](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


&nbsp;


