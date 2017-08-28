---
title: "Novità &#39; s New in Integration Services in SQL Server 2017 | Documenti Microsoft"
ms.custom: 
ms.date: 07/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 2d47d1bb82b586890e3bfc250cf09e929a64fb25
ms.contentlocale: it-it
ms.lasthandoff: 08/23/2017

---
# <a name="what39s-new-in-integration-services-in-sql-server-2017"></a>Novità &#39; s New in Integration Services in SQL Server 2017
Questo argomento descrive le funzionalità che sono state aggiunte o aggiornate in [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE]
> SQL Server 2017 include anche le funzionalità di SQL Server 2016 e le funzionalità aggiunte negli aggiornamenti di SQL Server 2016. Per informazioni sulle nuove funzionalità di SSIS in SQL Server 2016, vedere [Novità di Integration Services in SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="highlights-of-this-release"></a>Caratteristiche salienti di questa versione

Ecco le nuove funzionalità più importanti in servizi di integrazione per SQL Server 2017.

-   **Scalabilità orizzontale**. Distribuire più facilmente di esecuzione del pacchetto SSIS tra più computer di lavoro e gestire le esecuzioni e processi di lavoro da un singolo computer master. Per altre informazioni, vedere [Integration Services Scale Out](../integration-services/scale-out/integration-services-ssis-scale-out.md).

-   **Integration Services in Linux**. Eseguire pacchetti SSIS nel computer Linux. Per altre informazioni, vedere [di estrazione, trasformazione e caricamento dati in Linux con SSIS](../linux/sql-server-linux-migrate-ssis.md).

-   **Miglioramenti di connettività**. Connettersi al feed OData di Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online con i componenti aggiornati di OData. 

## <a name="new-in-the-azure-feature-pack"></a>Novità di Azure Feature Pack

Oltre ai miglioramenti di connettività in SQL Server, Integration Services Feature Pack per Azure ha aggiunto il supporto per l'archivio Azure Data Lake. Per altre informazioni, vedere [Azure Feature Pack per Integration Services (SSIS)](azure-feature-pack-for-integration-services-ssis.md).

## <a name="new-in-sql-server-data-tools-ssdt"></a>Novità di SQL Server Data Tools (SSDT)

È ora possibile sviluppare progetti SSIS e i pacchetti destinati a versioni di SQL Server 2012 tramite 2017 in Visual Studio 2017 o in Visual Studio 2015. Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="new-in-ssis-in-sql-server-2017-rc1"></a>Novità di SSIS in SQL Server 2017 RC1

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Funzionalità nuove e modificate in Scale Out per SSIS

-   Il master di scalabilità orizzontale supporta ora la disponibilità elevata. È possibile abilitare Always On per SSISDB e configurare Windows Server failover clustering per il server che ospita il servizio di scala Out Master. Applicando questa modifica scala Out master, evitare un singolo punto di errore e garantire un'elevata disponibilità per l'intera distribuzione orizzontale.
-   La gestione del failover dei log di esecuzione dai ruoli di lavoro di scalabilità orizzontale è stata migliorata. I log di esecuzione vengono rese persistenti su disco locale, nel caso in cui la scala Out lavoro imprevisto. In un secondo momento, quando il processo di lavoro viene riavviato, ricarica i log persistenti e continua il relativo salvataggio in SSISDB.
-   Il parametro *runincluster* della stored procedure **[catalog].[create_execution]** è stato rinominato in *runinscaleout* per coerenza e leggibilità. Questa modifica del nome di parametro con le seguenti conseguenze:
    -   Se si dispone di script esistenti per eseguire pacchetti in orizzontale, è necessario modificare il nome del parametro da *runincluster* a *runinscaleout* per fare in modo che gli script nella versione RC1.
    -   SQL Server Management Studio (SSMS) 17,1 e nelle versioni precedenti non possono attivare esecuzione del pacchetto in Scale Out nella versione RC1. Messaggio di errore: " *@runincluster*  non è un parametro per la procedura **create_execution**." Questo problema viene risolto nella versione 17.2 di SSMS. 17.2 per e versioni successive di SQL Server Management Studio supporta la nuova esecuzione pacchetto e il nome di parametro in orizzontale. Fino a quando non 17,2 versione SQL Server Management Studio è disponibile, in alternativa, è possibile utilizzare la versione esistente di SQL Server Management Studio per generare lo script di esecuzione del pacchetto, quindi modificare il nome del *runincluster* parametro *runinscaleout* nel script, eseguire lo script.
-   Il catalogo SSIS include una nuova proprietà globale che consente di specificare la modalità predefinita per l'esecuzione dei pacchetti SSIS. Questa nuova proprietà si applica quando si chiama il **[catalog]. [ create_execution]** stored procedure con il *runinscaleout* parametro impostato su null. Questa modalità si applica anche ai processi di agente SQL SSIS. È possibile impostare la nuova proprietà globale nella finestra di dialogo proprietà per il nodo SSISDB in SQL Server Management Studio o con il comando seguente:
    ```sql
    EXEC [catalog].[configure_catalog] @property_name=N'DEFAULT_EXECUTION_MODE', @property_value=1
    ```

## <a name="new-in-ssis-in-sql-server-2017-ctp-21"></a>Novità di SSIS in SQL Server 2017 CTP 2.1

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Funzionalità nuove e modificate in Scale Out per SSIS

-   È ora possibile usare il **Use32BitRuntime** parametro quando si attiva l'esecuzione in orizzontale.
-   Le prestazioni di registrazione per SSISDB per esecuzioni del pacchetto in orizzontale sono stata migliorata. I registri eventi messaggio e il contesto del messaggio vengono ora scritti SSISDB in modalità batch anziché singolarmente. Ecco alcune note aggiuntive su questo miglioramento:        
    - Alcuni report nella versione corrente di SQL Server Management Studio (SSMS) attualmente non vengono visualizzati questi registri per le esecuzioni in orizzontale. Si prevede che saranno supportati nella prossima versione di SQL Server Management Studio. I report interessati includono le *tutte le connessioni* report, il *contesto errore* report e *informazioni di connessione* sezione nel Dashboard di servizi di integrazione.
    - Una nuova colonna **event_message_guid** è stato aggiunto. Utilizzare questa colonna per creare un join [catalog]. visualizzazione [event_message_context] e [catalog]. Consente di visualizzare [event_messages] anziché **event_message_id** quando si esegue una query questi registri di esecuzioni in orizzontale.
-   Per ottenere l'applicazione di gestione per SSIS Scale Out [scaricare SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17,1 o versione successiva.

## <a name="new-in-ssis-in-sql-server-2017-ctp-20"></a>Novità di SSIS in SQL Server 2017 CTP 2.0

Non esistono alcuna nuova funzionalità SSIS in SQL Server 2017 CTP 2.0.

## <a name="new-in-ssis-in-sql-server-2017-ctp-14"></a>Novità di SSIS in SQL Server 2017 CTP 1.4

Non esistono alcuna nuova funzionalità SSIS in SQL Server 2017 CTP 1.4.

## <a name="new-in-ssis-in-sql-server-2017-ctp-13"></a>Novità di SSIS in SQL Server 2017 CTP 1.3

Non esistono alcuna nuova funzionalità SSIS in SQL Server 2017 CTP 1.3.

## <a name="new-in-ssis-in-sql-server-2017-ctp-12"></a>Novità di SSIS in SQL Server 2017 CTP 1.2

Non esistono alcuna nuova funzionalità SSIS in SQL Server 2017 CTP 1.2.

## <a name="new-in-ssis-in-sql-server-2017-ctp-11"></a>Novità di SSIS in SQL Server 2017 CTP 1.1

Non esistono alcuna nuova funzionalità SSIS in SQL Server 2017 CTP 1.1.

## <a name="new-in-ssis-in-sql-server-2017-ctp-10"></a>Novità di SSIS in SQL Server 2017 CTP 1.0

### <a name="scale-out-for-ssis"></a>Scalabilità orizzontale per SSIS

La funzionalità di scalabilità orizzontale semplifica l'esecuzione di [!INCLUDE[ssIS_md](../includes/ssis-md.md)] su più computer. 
   
Dopo l'installazione del master e dei ruoli di lavoro di scalabilità orizzontale, il pacchetto può essere distribuito per l'esecuzione automatica in diversi ruoli di lavoro. Se l'esecuzione viene terminata in modo imprevisto, viene ritentata automaticamente. Inoltre, tutte le esecuzioni e i ruoli di lavoro possono essere gestiti centralmente tramite Master.
   
Per altre informazioni, vedere [Scalabilità orizzontale di Integration Services](../integration-services/scale-out/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Supporto per le risorse di Microsoft Dynamics Online

L'origine OData e la gestione connessione OData supportano ora la connessione ai feed OData di Microsoft Dynamics AX Online e Microsoft Dynamics CRM Online.


