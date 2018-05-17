---
title: 'Aggiornamento: documentazione di SSMS per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione di SQL Server Management Studio (SSMS) per SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssms
ms.date: 04/28/2018
ms.openlocfilehash: 1ce446219f71baca0f4cdedc835fca929b572a0f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Articoli nuovi e aggiornati di recente: SQL Server Management Studio (SSMS) per SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli presenti sul sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/02/2018** &nbsp; - &nbsp; **28/04/2018**
- *Area di interesse:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Esercitazione: Connettersi a un'istanza di SQL Server ed eseguire query con SQL Server Management Studio](tutorials/connect-query-sql-server.md)
2. [Esercitazione: Creare script per oggetti in SQL Server Management Studio](tutorials/scripting-ssms.md)
3. [Esercitazione: Componenti e configurazione di SQL Server Management Studio](tutorials/ssms-configuration.md)
4. [Esercitazione: Suggerimenti e consigli per l'uso di SSMS](tutorials/ssms-tricks.md)
5. [Esercitazione: Uso di modelli in SQL Server Management Studio](tutorials/templates-ssms.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [SQL Server Management Studio: log delle modifiche (SSMS)](#TitleNum_1)
2. [Esercitazioni per SQL Server Management Studio (SSMS)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>1. &nbsp; [SQL Server Management Studio: log delle modifiche (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 eb641ac39386a26a76dc303f5bd55eb3f9f4c78d f560f09b51ea30b255c10f7eb86857c3090881d9  (PR=5676  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[SSMS 17.6]**


Numero di versione: 17.6<br>
Numero di build: 14.0.17230.0<br>
Data di rilascio: 20 marzo 2018

**Novità**


**SQL Server Management Studio (SSMS) - Generale**

Istanza gestita di database SQL di Azure:

- Aggiunto un supporto per [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Istanza gestita di database SQL di Azure (anteprima) è una nuova versione del database SQL di Azure che offre quasi il 100% di compatibilità con SQL Server in locale, un'implementazione nativa della [rete virtuale (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) che risolve i problemi di sicurezza più comuni e un [modello di business](https://azure.microsoft.com/pricing/details/sql-database/) ideale per i clienti di SQL Server locale.
- Supporto per scenari di gestione comuni, ad esempio:
   - Creazione e modifica dei database.
   - Backup e ripristino dei database.
   - Importazione, esportazione, estrazione e pubblicazione di applicazioni livello dati.
   - Visualizzazione e modifica delle proprietà server.
   - Supporto completo di Esplora oggetti.
   - Generazione di script per oggetti di database.
   - Supporto per i processi di SQL Agent.
   - Supporto per i server collegati.
- Altre informazioni sulle istanze gestite sono disponibili [qui](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/).

Esplora oggetti:
- Aggiunte impostazioni che consentono di non racchiudere i nomi tra parentesi quadre quando si trascinano e rilasciano elementi da Esplora oggetti alla finestra di query (suggerimenti utente [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) e [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051)).

Classificazione dei dati:
- Miglioramenti generali e correzioni di bug.

**Integration Services (IS)**

- Aggiunto il supporto per la distribuzione dei pacchetti a un'[istanza gestita del database SQL](docs/ssms/https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tutorials-for-sql-server-management-studio-ssmstutorialstutorial-sql-server-management-studiomd"></a>2. &nbsp; [Esercitazioni per SQL Server Management Studio (SSMS)](tutorials/tutorial-sql-server-management-studio.md)

*Aggiornamento: 25/04/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1))

<!-- Source markdown line 49.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b272c75bab04912ebb706098cf6b6a6c80d9e2b8 d453ebc8251fb83ffcb1af58c9a08bb65b3e9fa2  (PR=5676  ,  Filename=tutorial-sql-server-management-studio.md  ,  Dirpath=docs\ssms\tutorials\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- Esercitazione: Connettersi ed eseguire query in SQL Server con SSMS

    In questa esercitazione si apprende come connettersi all'istanza di SQL Server. Sono disponibili anche informazioni su alcuni comandi Transact-SQL (T-SQL) di base per creare un nuovo database ed eseguire una query.

- Esercitazione: Scripting di oggetti in SSMS

    In questa esercitazione si apprende come creare lo script di vari oggetti in SSMS, tra cui database e query.

- Esercitazione: Uso di modelli in SSMS

    In questa esercitazione si apprende come usare i modelli preesistenti in SSMS. I modelli sono una funzionalità poco nota che consente di archiviare un certo numero di frammenti di codice Transact-SQL per varie attività di amministrazione dei database.

- Esercitazione: Configurazione di SSMS

    In questa esercitazione si apprendono le nozioni di base sulla configurazione dell'ambiente di SQL Server Management Studio, ad esempio la modifica del layout dell'ambiente. Questa esercitazione spiega anche che cosa sono i diversi componenti di SQL Server Management Studio.


- Esercitazione: Suggerimenti e consigli per l'uso di SSMS

    In questa esercitazione vengono illustrati suggerimenti e consigli aggiuntivi per l'uso di SSMS. L'esercitazione include gli argomenti seguenti:
    - Creazione di commenti e rimozione dei commenti sul testo
    - Rientro del testo
    - Filtro degli oggetti in Esplora oggetti
    - Accesso al log degli errori di SQL Server
    - Individuazione del nome dell'istanza








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

