---
title: Note sulla versione di SQL Server 2017 | Microsoft Docs
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
ms.sourcegitcommit: b2f5d26757bd436cfd21076b2a4899376ee60c9f
ms.openlocfilehash: cd57edcb06ea6d9baced3ce5765743769caba04e
ms.contentlocale: it-it
ms.lasthandoff: 08/04/2017

---
# <a name="sql-server-2017-release-notes"></a>Note sulla versione di SQL Server 2017
Questo argomento descrive i limiti e i problemi relativi a [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Per informazioni correlate, vedere:
- [Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).
- [Note sulla versione di SQL Server in Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
  
[![Download da Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477).  Scaricare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] da **[Evaluation Center](http://go.microsoft.com/fwlink/?LinkID=829477)**.

## <a name="sql-server-2017-release-candidate-rc2---august-2017"></a>SQL Server 2017 Release Candidate (RC2, agosto 2017)
Non sono disponibili note sulla versione di SQL Server in Windows per questa versione. Vedere [Note sulla versione di SQL Server in Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>Versione finale candidata di SQL Server 2017 (RC1 - luglio 2017)
### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 - luglio 2017)
- **Problema e impatto sul cliente:** il parametro *runincluster* della stored procedure **[catalog].[create_execution]** è stato rinominato in *runinscaleout* per coerenza e leggibilità.
- **Soluzione alternativa:** se esistono script per eseguire i pacchetti in Scale Out, è necessario modificare il nome del parametro da *runincluster* a *runinscaleout* affinché gli script possano essere usati nella versione RC1.

- **Problema e impatto sul cliente:** in SQL Server Management Studio (SSMS) 17.1 e nelle versioni precedenti non è possibile eseguire i pacchetti in Scale Out nella versione RC1. Messaggio di errore: " *@runincluster*  non è un parametro per la procedura **create_execution**." Questo problema viene risolto nella versione 17.2 di SSMS. La versione 17.2 e le versioni successive di SSMS supportano il nuovo nome di parametro ed eseguono i pacchetti in Scale Out. 
- **Soluzione alternativa:** fino a quando non sarà disponibile SSMS versione 17.2:
  1. Usare la versione esistente di SSMS per generare lo script di esecuzione del pacchetto.
  2. Modificare il nome del parametro *runincluster* in *runinscaleout* nello script.
  3. Eseguire lo script.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server 2017 CTP 2.1 (maggio 2017)
### <a name="documentation-ctp-21"></a>Documentazione (CTP 2.1)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP 2.1)

- **Problema e impatto sul cliente:** se SQL Server Reporting Services e il server di report di Power BI sono presenti nello stesso computer e si disinstalla uno dei due, non è più possibile connettersi al server di report rimanente con Gestione configurazione del server di report.
- **Soluzione alternativa:** per risolvere questo problema, seguire questa procedura dopo aver disinstallato uno dei server.

    1. Avviare un prompt dei comandi in modalità amministratore.
    2. Passare alla directory in cui è installato il server di report rimanente.

        *Percorso predefinito per il Server di report di Power BI: c:\Programmi\Microsoft Power BI Report Server*

        *Percorso predefinito per il Server di report di Power BI: c:\Programmi\Microsoft SQL Server Reporting Services*

    3. Passare quindi alla cartella successiva, vale a dire *SSRS* o *PBIRS* a seconda del server di report rimanente.
    4. Passare alla cartella WMI.
    5. Eseguire il comando seguente:

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        È possibile ignorare l'errore seguente.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **Problema e impatto sul cliente:** dopo l'installazione in un computer in cui è installata una versione del 2016 di *TSqlLanguageService.msi* (mediante il programma di installazione di SQL Server o come ridistribuibile autonomo), vengono rimosse le versioni 13.* (SQL 2016) di *Microsoft.SqlServer.Management.SqlParser.dll* e *Microsoft.SqlServer.Management.SystemMetadataProvider.dll*. Tutte le applicazioni che presentano una dipendenza nelle versioni 2016 di tali assembly smetteranno pertanto di funzionare, producendo un errore simile a: *errore: Impossibile caricare il file o l'assembly 'Microsoft.SqlServer.Management.SqlParser, Version=13.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' o una delle sue dipendenze. Impossibile trovare il file specificato.*

   I tentativi di reinstallare una versione del 2016 di TSqlLanguageService.msi hanno esito negativo con il messaggio: *Installazione di Servizio linguaggio T-SQL di Microsoft SQL Server 2016 non riuscita. Nel computer è già presente una versione successiva*.

- **Soluzione alternativa:** per risolvere questo problema e correggere un'applicazione che dipende dalla versione 13 degli assembly, seguire questa procedura:

   1. Andare a **Installazione applicazioni**
   2. Cercare *Microsoft SQL Server vNext T-SQL Language Service CTP2.1*, fare clic con il pulsante destro del mouse e selezionare **Disinstalla**.
   3. Dopo che il componente è stato rimosso, riparare l'applicazione danneggiata o reinstallare la versione appropriata di *TSqlLanguageService.MSI*.

   Questa soluzione alternativa rimuove la versione 14 di tali assembly, quindi tutte le applicazioni che dipendono dalle versioni 14 non funzioneranno più. Se sono necessari tali assembly, occorre eseguire un'installazione separata senza installazioni side-by-side del 2016.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (aprile 2017)
### <a name="documentation-ctp-20"></a>Documentazione (CTP 2.0)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.

### <a name="always-on-availability-groups"></a>Gruppi di disponibilità Always On

- **Problema e impatto sul cliente:** un'istanza di SQL Server che ospita una replica secondaria del gruppo di disponibilità si blocca se la versione principale di SQL Server è di livello inferiore rispetto all'istanza che ospita la replica primaria. Ciò influisce sugli aggiornamenti di tutte le versioni supportate di SQL Server che ospitano i gruppi di disponibilità per SQL Server [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 2.0. Ciò avviene secondo i passaggi seguenti. 

> 1. L'utente effettua l'aggiornamento dell'istanza di SQL Server che ospita la replica secondaria, in conformità con le [procedure consigliate](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).
> 2. Dopo l'aggiornamento, si verifica un failover e la replica secondaria appena aggiornata diventa primaria prima che venga completato l'aggiornamento di tutte le repliche secondarie nel gruppo di disponibilità. La vecchia replica primaria è ora una replica secondaria, ovvero una versione inferiore rispetto a quella primaria.
> 3. Il gruppo di disponibilità è in una configurazione non supportata e tutte le repliche secondarie rimanenti potrebbero essere esposte a un arresto anomalo del sistema. 

- **Soluzione alternativa** Connettere all'istanza di SQL Server che ospita la nuova replica primaria e rimuovere la replica secondaria errata dalla configurazione.

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   Viene recuperata l'istanza di SQL Server che ospitava la replica secondaria.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Coinvolgimento del team di progettazione di SQL Server 
- [Stack Overflow (tag sql-server) - ask technical questions](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN Forums - ask technical questions](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - report bugs and request features](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - general discussion about SQL Server](https://www.reddit.com/r/SQLServer/) (Discussione generale su SQL Server)

## <a name="more-information"></a>Ulteriori informazioni
- [note sulla versione di SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).
- [Problemi noti di Machine Learning Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
