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
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 8ae9a49443525524cf7f6ffceba4fb44984c7052
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Articoli nuovi e aggiornati di recente: SQL Server Data Tools (SSDT)



Quasi ogni giorno Microsoft aggiorna alcuni articoli presenti sul sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **18/07/2017** &nbsp; - &nbsp; **11/09/2017**
- *Area di interesse:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [SQL Server Data Tools - Condizioni di licenza](sql-server-data-tools-license-terms-vs2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Log delle modifiche per SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp;[Log delle modifiche per SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Aggiornamento: 23/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 23.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 536fe0fe41b023a4186f494a509fa14fcbafccf4 e5bc7b76c1755f5a1af77f6cd63d8e8691dafe7b  (PR=2927  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=71a2cbf181c94c4c1aff877614aadf890b2496e0) -->



**SSDT per Visual Studio 2017 (anteprima 15.3.0)**

Numero di build: 14.0.16121.0

**Novità**


Questa anteprima è la prima versione di SSDT per Visual Studio 2017. Questa versione introduce un'esperienza di installazione Web autonoma per i progetti SQL Server Database, Analysis Services, Reporting Services e Integration Services in Visual Studio 2017 15.3 o versioni successive.


**Problemi noti**

- Il programma di installazione non è localizzato.
- SSIS non è localizzato.
- L'attività di esecuzione pacchetti SSIS non supporta il debug quando *ExecuteOutofProcess* è impostato su *True*. Questo problema è limitato al debug. Il salvataggio, la distribuzione e l'esecuzione tramite DTExec.exe o il catalogo SSIS funzionano normalmente.
- Per un elenco completo delle modifiche, vedere [changelog--changelog-for-sql-server-data-tools-ssdt.md).
- Per segnalare eventuali problemi, è possibile usare il [Centro commenti e suggerimenti per SSDT Connect](https://connect.microsoft.com/SQLServer/Feedback).
- I pacchetti SSIS che contengono estensioni di terze parti non possono essere destinati all'uso con altre versioni di server.


**SSDT 17.2 per Visual Studio 2015**

Numero di build: 14.0.61707.300

**Novità**



**Progetti AS:**
- Ora è possibile configurare la sicurezza a livello di oggetto nella finestra di dialogo *Ruoli* per la sicurezza avanzata nei modelli tabulari con livello di compatibilità 1400.
- Nuova selezione di membri del ruolo AAD per gli utenti senza indirizzi di posta elettronica nei modelli di Azure Analysis Services nei progetti SSDT Analysis Services per Visual Studio 2017.
- Nuova proprietà del progetto "Chiedi sempre conferma" di Azure Analysis Services nei progetti tabulari di SSDT Analysis Services per personalizzare il comportamento di memorizzazione nella cache delle credenziali ADAL.


**Correzioni di bug**


**Generale**
- Aggiornati i riferimenti di personalizzazione per SQL Server 2017.

**Progetti AS**
- Notevole miglioramento delle prestazioni per migliorare l'esperienza durante il commit di modifiche delle misure DAX e altre modifiche al modello.
- Risolti alcuni problemi di integrazione di Power Query nei progetti di Analysis Services che usano i modelli tabulari con livello di compatibilità 1400.
- Risolto un problema relativo ai progetti multidimensionali limitato a Visual Studio 2017 che poteva impedire il caricamento della finestra di progettazione Progetta aggregazioni.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+12): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5+0): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5+1): documentazione di **Motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19+82): documentazione di **Integration Services per SQL**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1+8): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12+1): documentazione di **Database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+1): documentazione di **Reporting Services per SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1): documentazione di **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+2): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1+4): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (4+1): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0+1): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



