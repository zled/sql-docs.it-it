---
title: Note sulla versione SQL Server 2017 | Documenti Microsoft
ms.custom: 
ms.date: 05/16/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: a2950b6aef0e12653efbb9eb26fd3f1ae6cb951e
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="sql-server-2017-release-notes"></a>Note sulla versione di SQL Server 2017
Questo argomento descrive i limiti e i problemi relativi a [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Per informazioni correlate, vedere gli argomenti seguenti:

- [Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).
- [SQL Server in Linux note](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
- [note sulla versione di SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).

 **Per provarlo:**    
   -   [![Download da Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Scaricare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] da **[Evaluation Center](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>Versione finale candidata di SQL Server 2017 (RC1 - luglio 2017)

### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 - luglio 2017)
- **Problema e impatto per i clienti:** il parametro *runincluster* della stored procedure **[catalog].[create_execution]** è stato rinominato in *runinscaleout* per coerenza e leggibilità.
- **Soluzione alternativa:** se esistono script per eseguire i pacchetti in Scale Out, è necessario modificare il nome del parametro da *runincluster* a *runinscaleout* affinché gli script possano essere usati nella versione RC1.

- **Problema e impatto per i clienti:** in SQL Server Management Studio (SSMS) 17.1 e nelle versioni precedenti non è possibile eseguire i pacchetti in Scale Out nella versione RC1. Messaggio di errore: " *@runincluster*  non è un parametro per la procedura **create_execution**." Questo problema viene risolto nella versione 17.2 di SSMS. La versione 17.2 e le versioni successive di SSMS supportano il nuovo nome di parametro ed eseguono i pacchetti in Scale Out. 
- **Soluzione alternativa:** finché la versione 17.2 di SSMS non sarà disponibile, è possibile usare la versione esistente di SSMS per generare lo script che esegue i pacchetti, modificare il nome del parametro *runincluster* in *runinscaleout* nello script ed eseguire lo script.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server 2017 CTP 2.1 (maggio 2017)
### <a name="documentation-ctp-21"></a>Documentazione (CTP 2.1)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP 2.1)

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

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **Problema e cliente impatto:** dopo l'installazione in un computer dotato di una versione di 2016 *TSqlLanguageService.msi* (tramite l'installazione di SQL o come componente ridistribuibile autonomo) le v13.* (SQL 2016) versioni installate di *Microsoft.SqlServer.Management.SqlParser.dll* e *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* vengono rimossi. Tutte le applicazioni che presentano una dipendenza nelle versioni di tali assembly 2016 quindi smetterà di funzionare, fornendo un errore simile al: *errore: Impossibile caricare il file o l'assembly ' Microsoft.SqlServer.Management.SqlParser, versione = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91' o una delle sue dipendenze. Impossibile trovare il file specificato.*

   Inoltre, i tentativi di reinstallare una versione di TSqlLanguageService.msi 2016 avrà esito negativo con il messaggio: *installazione di Microsoft SQL Server 2016 T-SQL Language Service non riuscita perché una versione successiva è già presente nel computer*.

- **Soluzione alternativa** per risolvere questo problema e risolvere un'applicazione che dipende il v13 versione degli assembly di seguire questi passaggi:

   1. Passare a **Aggiungi/Rimuovi programmi**
   1. Trovare *vNext di Microsoft SQL Server CTP 2.1 di servizio linguaggio T-SQL*, pulsante destro del mouse e selezionare **Disinstalla**.
   1. Dopo che il componente è stato rimosso, ripristinare l'applicazione che viene interrotta (o reinstallare la versione appropriata di *TSqlLanguageService.MSI*)

   Questa soluzione alternativa rimuoverà la versione v14 di tali assembly, pertanto tutte le applicazioni che dipendono dalle versioni v14 non funzioneranno più. Se sono necessarie tali assembly, un'installazione separata senza eventuali 2016 installazioni side-by-side è obbligatoria.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (aprile 2017)
### <a name="documentation-ctp-20"></a>Documentazione (CTP 2.0)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.

### <a name="always-on-availability-groups"></a>Gruppi di disponibilità Always On

- **Problema e cliente impatto:** istanza di un SQL Server che ospita una replica secondaria del gruppo di disponibilità si blocca se la versione principale di SQL Server è inferiore rispetto all'istanza che ospita la replica primaria. Interessa gli aggiornamenti da tutte le versioni supportate di SQL Server che ospitano i gruppi di disponibilità di SQL Server [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 2.0. Ciò si verifica in seguito. 

> 1. Utente effettua l'aggiornamento di SQL Server istanza hosting replica secondaria in conformità con [consigliate](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).
> 2. Dopo l'aggiornamento, si verifica un failover e appena aggiornato secondaria diventa primaria prima di completare l'aggiornamento per tutte le repliche secondarie nel gruppo di disponibilità. Primario precedente è un database secondario che è una versione inferiore rispetto al database primario.
> 3. Il gruppo di disponibilità è in una configurazione supportata e tutte le repliche secondarie rimanenti potrebbero essere vulnerabili a arresto anomalo del sistema. 

- **Soluzione alternativa** Connetti all'istanza SQL Server che ospita la nuova replica primaria e rimuovere la replica secondaria errata dalla configurazione.

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   Consente di recuperare l'istanza di SQL Server che ha ospitato la replica secondaria.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Coinvolgimento del team di progettazione di SQL Server 
- [Stack Overflow (tag sql-server) - ask technical questions](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN Forums - ask technical questions](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - report bugs and request features](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - general discussion about R](https://www.reddit.com/r/SQLServer/)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
