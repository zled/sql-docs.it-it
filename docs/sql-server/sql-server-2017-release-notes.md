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
ms.translationtype: Human Translation
ms.sourcegitcommit: 67c1c0f3a9da6cc5d050da5db8a493f5da934c2a
ms.openlocfilehash: fa45fea4ebb378f035b4b4af2b1fa8a20bc152a5
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-2017-release-notes"></a>Note sulla versione di SQL Server 2017
Questo argomento descrive i limiti e i problemi relativi a [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Per informazioni correlate, vedere gli argomenti seguenti:

- [Novità di SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).
- [SQL Server in Linux note](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
- [Note sulla versione di SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).

 **Per provarlo:**    
   -   [![Download da Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Scaricare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] da **[Evaluation Center](http://go.microsoft.com/fwlink/?LinkID=829477)**

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


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-14-march--2017"></a>SQL Server 2017 CTP 1.4 (marzo 2017)

### <a name="documentation-ctp-14"></a>Documentazione (CTP 1.4)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-13-february--2017"></a>SQL Server 2017 CTP 1.3 (febbraio 2017)
### <a name="supported-installation-scenarios-ctp-13"></a>Scenari di installazione supportati (CTP 1.3)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è disponibile solo come versione di prova.  Le distribuzioni di produzione non sono supportate. Si consiglia di installare e provare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] in una macchina virtuale.

### <a name="documentation-ctp-13"></a>Documentazione (CTP 1.3)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.

### <a name="sql-server-integration-services-ssis-ctp-13"></a>SQL Server Integration Services (SSIS) (CTP 1.3)
#### <a name="cdc-components-not-supported-in-this-ctp-release"></a>Componenti CDC non supportati in questa versione CTP
-   **Problema e impatto sul cliente:**l'attività di controllo, l'origine e la barra di divisione CDC non sono supportate in questa versione CTP.
-   **Soluzione alternativa:**non esistono soluzioni alternative.


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-12-january--2017"></a>SQL Server 2017 CTP 1.2 (gennaio January 2017)
### <a name="supported-installation-scenarios-ctp-12"></a>Scenari di installazione supportati (CTP 1.2)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è disponibile solo come versione di prova.  Le distribuzioni di produzione non sono supportate. Si consiglia di installare e provare [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] in una macchina virtuale.

### <a name="sql-server-database-engine-ctp-12"></a>Motore di database di SQL Server (CTP 1.2)
- **Problema e impatto sul cliente:** in alcuni casi, il servizio MSSQLSERVER rimane bloccato nello stato "Iniziale".
- **Soluzione alternativa:** per risolvere questo problema:
  -  Creare una dipendenza tra il servizio `mssqlserver` e il servizio `keyiso` . A tale scopo, è possibile eseguire questo comando da un prompt dei comandi con privilegi elevati: `sc config mssqlserver depend= keyiso`
  - Riavviare il computer.

### <a name="documentation-ctp-12"></a>Documentazione (CTP 1.2)
- **Problema e impatto sul cliente:** la documentazione di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è limitata e il contenuto è incluso nel set di documentazione di [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Il contenuto di articoli specifici di [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] è indicato con **Si applica a:**. 
- **Problema e impatto sul cliente:** per [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]non è disponibile contenuto offline.
 
### <a name="sql-server-integration-services-ssis-ctp-12"></a>SQL Server Integration Services (SSIS) (CTP 1.2)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>L'eliminazione del catalogo SSIS può avere esito negativo se è installata la funzionalità di scalabilità orizzontale di SSIS
**Problema e impatto sul cliente:**quando la funzionalità di scalabilità orizzontale di SSIS è installata in un computer, l'eliminazione del database di catalogo SSISDB può avere esito negativo e restituire l'errore seguente: "Non è stato possibile eliminare l'account di accesso *'accountaccesso'* perché l'utente è connesso".
   
**Soluzione alternativa**:
-   In un computer con il master di scalabilità orizzontale, eseguire il comando "services.msc" per aprire la finestra Servizi. Arrestare il servizio Cluster Master di SQL Server Integration Services.
-   Nei computer con il ruolo di lavoro di scalabilità orizzontale, che si connettono al master, eseguire il comando "services.msc" per aprire la finestra Servizi. Arrestare il servizio Cluster Worker di SQL Server Integration Services.

È ora possibile eliminare il database di catalogo SSISDB.

### <a name="sql-server-master-data-services-ctp-12"></a>SQL Server Master Data Services (CTP 1.2)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>La transazione può non funzionare quando il tipo di log delle transazioni dell'entità viene impostato su attributo
**Problema e impatto sul cliente:** quando il tipo di log delle transazioni dell'entità è impostato su **Attributo** in [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (il valore predefinito è **Membro**), eseguire gli scenari seguenti:

* Le transazioni relative alle modifiche dell'entità non vengono visualizzate nel sito Web.
* Non è possibile aprire la pagina **Transazioni** sul sito Web e invertire una transazione.
* Non è possibile aggiornare un'entità con un'annotazione della transazione nel sito Web.

**Soluzione alternativa:**non esistono soluzioni alternative.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>La versione di copia può non funzionare se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su false
-  **Problema e impatto sul cliente:** se **Copy only committed version** (Copia solo la versione di cui è stato eseguito il commit) è impostata su **No** (il valore predefinito è **Yes**(Sì)), l'operazione di copia della versione può avere esito negativo. Non viene restituito alcune messaggio di errore.
-  **Soluzione alternativa:**non esistono soluzioni alternative.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Coinvolgimento del team di progettazione di SQL Server 
- [Stack Overflow (tag sql-server) - ask technical questions](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN Forums - ask technical questions](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - report bugs and request features](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - general discussion about R](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


