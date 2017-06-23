---
title: Aggiornato - documentazione di SQL Server | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione per SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 7fba3b05943b93c0a2c0e76c2d0d5f2696a48d1c
ms.contentlocale: it-it
ms.lasthandoff: 06/23/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>Nuovi e recentemente aggiornato: documentazione di SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo degli aggiornamenti di date:* &nbsp; **2017-05-01** &nbsp; - a - &nbsp; **2017-05-23**
- *Area di interesse:* &nbsp; **SQL Server**.




&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd"></a>1. &nbsp;[Note sulla versione SQL Server 2017](sql-server-2017-release-notes.md)

*Updated: 2017-05-17* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 28.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 84e7a2a49f2893d49380db1ad75695d9a4fd59b2 27a145ad30c10fd667f926d2e092b88c0ba586c5 -->



**SQL Server 2017 CTP 2.1 (maggio 2017)**

**Documentazione (CTP 2.1)**

- **Problema e cliente impatto:** documentazione per [! Includi [ssSQLv14_md--... /Includes/sssqlv14-MD.MD)] è limitato e viene incluso con il contenuto di [! Includi [ssSQL15_md--... set di documentazione /Includes/sssql15-MD.MD]).  Contenuto negli articoli è specifico di [! Includi [ssSQLv14_md--... /Includes/sssqlv14-MD.MD]) sono indicate con **si applica a**. 
- **Problema e cliente impatto:** privo di contenuto non in linea è disponibile per [! Includi [ssSQLv14_md--... /Includes/sssqlv14-MD.MD)].

**SQL Server Reporting Services (CTP 2.1)**


- **Problema e cliente impatto:** se si dispone di SQL Server Reporting Services e Power BI Server di Report nello stesso computer e disinstallare uno di essi, non sarà in grado di connettersi al server di report rimanenti con Gestione configurazione Server di Report.
- **Soluzione alternativa** per risolvere questo problema, è necessario eseguire le operazioni seguenti dopo la disinstallazione di uno dei server.

    1. Avviare un prompt dei comandi in modalità amministratore.
    2. Passare alla directory in cui è installato il server di report rimanente.

        *Percorso predefinito per i Server di Report di Power BI: c:\Programmi\Microsoft Power BI Report Server*

        *Percorso predefinito per SQL Server Reporting Services: c:\Programmi\Microsoft SQL Server Reporting Services*

    3. Quindi passare alla cartella. Si tratterà *SSRS* o *PBIRS* a seconda di ciò che è rimanenti.
    4. Passare alla cartella WMI.
    5. Eseguire il comando seguente:

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        È possibile ignorare l'errore seguente, se è presente.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

**TSqlLanguageService.msi (CTP 2.1)**


- **Problema e cliente impatto:** dopo l'installazione in un computer dotato di una versione di 2016 *TSqlLanguageService.msi* (tramite l'installazione di SQL o come componente ridistribuibile autonomo) le v13.* (SQL 2016) versioni installate di *Microsoft.SqlServer.Management.SqlParser.dll* e *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* vengono rimossi. Tutte le applicazioni che presentano una dipendenza nelle versioni di tali assembly 2016 quindi smetterà di funzionare, fornendo un errore simile al: *errore: Impossibile caricare il file o l'assembly ' Microsoft.SqlServer.Management.SqlParser, versione = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91' o una delle sue dipendenze. Impossibile trovare il file specificato.*




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-what39s-new-in-sql-server-2017what-s-new-in-sql-server-2017md"></a>2. &nbsp;[Novità &#39; s New in SQL Server 2017](what-s-new-in-sql-server-2017.md)

*Updated: 2017-05-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 31.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b3e965f62414af06d42f88497958a4bca67befce 82ad09ae9a917f26db3e2210b5cf89585e0e4c4e -->



**Novità di SQL Server 2017 CTP 2.1 (maggio 2017)**

* * Il motore di Database SQL Server * *

- Un nuovo DMF, [sys.dm_db_log_stats--... / relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md), è stato introdotto per esporre attributi a livello di riepilogo e informazioni sui file di registro delle transazioni. è utile per il monitoraggio dello stato del log delle transazioni.  
- Questa versione CTP include correzioni di bug e miglioramenti delle prestazioni per il motore di Database.
- Per un elenco dettagliato dei 2017 miglioramenti CTP nelle versioni CTP precedenti, vedere [novità di SQL Server 2017 (motore di Database).... / database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

**SQL Server Reporting Services (SSRS)**

- SQL Server Reporting Services non è più disponibile per l'installazione tramite l'installazione di SQL Server a partire dalla versione CTP 2.1.
- I commenti sono ora disponibili per i report. I commenti consentono di aggiungere una prospettiva al contenuto in un report e collaborare con altri utenti nell'organizzazione. È inoltre possibile includere gli allegati con il commento.
- Per SSRS per ulteriori informazioni sulle novità, inclusi i dettagli delle versioni precedenti, vedere [novità in Reporting Services--... / reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 
- Per informazioni sul Server di Report di Power BI, vedere [Introduzione a Server di Report di Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

**Servizi di apprendimento macchina SQL Server**

- In questa versione CTP non esistono alcun nuove funzionalità di servizi di Machine Learning.
- Per ulteriori Machine Learning Services informazioni sulle novità, inclusi i dettagli da CTP precedenti, vedere [novità in SQL Server Machine Learning Services,... / advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).  

**SQL Server Analysis Services (SSAS)**

- In questa versione CTP non sono presenti nuove funzionalità di SSAS.  
- Per ulteriori informazioni sui miglioramenti e correzioni di bug in questa versione, vedere [novità in SQL Server 2017 Analysis Services,... / analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compact vengono forniti collegamenti a tutti gli articoli aggiornati elencati nella sezione precedente.

1. [Note sulla versione di SQL Server 2017](#TitleNum_1)
2. [Novità &#39; s New in SQL Server 2017](#TitleNum_2)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>Articoli sorella

In questa sezione sono elencati gli articoli molto simili per gli articoli aggiornati di recente in altre aree di interesse, nello stesso repository GitHub.


&nbsp;

[Microsoft /**sql-docs-pr** ](https://github.com/microsoftdocs/sql-docs-pr/) repository in GitHub.com:

- [Aggiornato di recente: **database relazionali e Microsoft SQL Server** documenti](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [Aggiornato di recente: **Microsoft SQL Server** documenti](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [Aggiornato di recente: **Transact-SQL in SQL Server** documenti](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



