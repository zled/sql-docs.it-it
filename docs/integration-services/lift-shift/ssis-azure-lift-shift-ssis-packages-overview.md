---
title: Migrazione lift-and-shift dei carichi di lavoro di SQL Server Integration Services nel cloud | Microsoft Docs
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 36a844cb2dcda45701c29066b825e64a864d5757
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Migrazione lift-and-shift dei carichi di lavoro di SQL Server Integration Services nel cloud
È ora possibile spostare pacchetti e i carichi di lavoro di SQL Server Integration Services (SSIS) nel cloud di Azure.
-   Archiviare e gestire progetti e pacchetti SSIS nel database del catalogo SSIS (SSISDB) per il database SQL di Azure.
-   Eseguire i pacchetti in un'istanza del runtime di integrazione SSIS di Azure, introdotto come parte di Azure Data Factory versione 2.
-   Usare strumenti familiari, ad esempio SQL Server Management Studio (SSMS), per queste attività comuni.

## <a name="benefits"></a>Vantaggi
Spostare i carichi di lavoro SSIS locali in Azure presenta i potenziali vantaggi seguenti:
-   **Riduzione dei costi operativi** e riduzione delle attività di gestione dell'infrastruttura svolte quando si esegue SSIS in locale o in macchine virtuali di Azure.
-   **Aumento della disponibilità elevata** con la possibilità di specificare più nodi per cluster, nonché le funzionalità di disponibilità elevata di Azure e del database SQL di Azure.
-   **Aumento della scalabilità** con la possibilità di specificare più core per nodo (scalabilità verticale) e più nodi per cluster (scalabilità orizzontale).

## <a name="architecture-overview"></a>Panoramica dell'architettura
Nella tabella seguente vengono evidenziate le differenze tra SSIS in locale e SSIS in Azure. La differenza più significativa è la separazione dell'archiviazione dal calcolo.

| Archiviazione | Runtime | Scalabilità |
|---|---|---|
| Locale (SQL Server) | Runtime SSIS ospitato da SQL Server | SQL Server Integration Services Scale Out (in SQL Server 2017 e versioni successive)<br/><br/>Soluzioni personalizzate (nelle versioni precedenti di SQL Server) |
| Azure (SQL Database) | Runtime di integrazione SSIS di Azure, un componente di Azure Data Factory versione 2 | Opzioni di ridimensionamento per il runtime di integrazione SSIS |
| | | |

Azure Data Factory ospita il motore di runtime per i pacchetti SSIS in Azure. Il motore di runtime è definito Runtime di integrazione SSIS (SSIS IR) di Azure.

Quando si esegue il provisioning di SSIS IR è possibile applicare la scalabilità verticale e orizzontale specificando i valori per le opzioni seguenti:
-   La dimensione del nodo, incluso il numero di core, e il numero di nodi del cluster.
-   L'istanza esistente del database SQL di Azure per ospitare il database del catalogo SSIS (SSISDB) e il livello di servizio per il database.
-   Le esecuzioni parallele massime per ogni nodo.

È sufficiente eseguire il provisioning del runtime di integrazione SSIS solo una volta. Successivamente, è possibile usare strumenti familiari, ad esempio SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS), per distribuire, configurare, eseguire, monitorare, pianificare e gestire i pacchetti.

> [!NOTE]
> Durante l'anteprima pubblica, il runtime di integrazione SSIS di Azure non è ancora disponibile in tutte le aree. Per informazioni sulle aree supportate, vedere i [prodotti Microsoft Azure disponibili in base all'area geografica](https://azure.microsoft.com/regions/services/).

Data Factory supporta anche altri tipi di runtime di integrazione. Per altre informazioni sul runtime di integrazione SSIS e altri tipi di runtime di integrazione, vedere [Runtime di integrazione in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime).

## <a name="prerequisites"></a>Prerequisites
Le funzionalità descritte in questo articolo non richiedono SQL Server 2017 o SQL Server 2016.

Le funzionalità richiedono le seguenti versioni di SQL Server Data Tools (SSDT):
-   Per Visual Studio 2017, versione 15.3 (anteprima) o successiva.
-   Per Visual Studio 2015, versione 17.2 o successiva.

> [!NOTE]
> Quando i pacchetti vengono distribuiti in Azure, la distribuzione guidata aggiorna sempre i pacchetti al formato del pacchetto più recente.

Per altre informazioni sui prerequisiti in Azure, vedere [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

## <a name="ssis-features-on-azure"></a>Funzionalità SSIS in Azure

Quando si esegue il provisioning di un'istanza del database SQL per ospitare SSISDB, vengono installati anche Azure Feature Pack per SSIS e le funzionalità di accesso ridistribuibili. Questi componenti offrono la connettività ai file di **Excel e Access** e a varie origini dati di **Azure**, oltre alle origini dati supportate dai componenti predefiniti. Al momento non è possibile installare **componenti di terze parti** per SSIS, inclusi i componenti di terze parti da Microsoft come i componenti Oracle e Teradata di Attunity e SAP BI.

Il **nome del database SQL** che ospita SSISDB diventa la prima parte del nome in quattro parti da usare quando si distribuiscono e si gestiscono i pacchetti da SSDT e SSMS, `<sql_database_name>.database.windows.net`.

È necessario usare il **modello di distribuzione dei progetti**, non il modello di distribuzione dei pacchetti, per i progetti distribuiti in SSISDB in un database SQL di Azure.

Continuare a **progettare e compilare i pacchetti** in locale in SSDT o in Visual Studio con SSDT installato.

Per informazioni su come connettersi alle **origini dati locali** dal cloud con l'autenticazione di Windows, vedere [Connettersi a origini dati locali con autenticazione di Windows](ssis-azure-connect-with-windows-auth.md).

## <a name="common-tasks"></a>Attività comuni

### <a name="provision"></a>Provisioning
Prima di distribuire ed eseguire i pacchetti SSIS in Azure, è necessario eseguire il provisioning del database del catalogo SSISDB e del runtime di integrazione SSIS di Azure. Eseguire i passaggi di provisioning descritti nell'articolo [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

### <a name="deploy-and-run-packages"></a>Distribuire ed eseguire i pacchetti
Per distribuire i progetti ed eseguire i pacchetti nel database SQL, è possibile usare diversi strumenti e opzioni di scripting comuni:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (da SSMS, Visual Studio Code o un altro strumento)
-   Uno strumento da riga di comando
-   PowerShell
-   C# e il modello a oggetti di gestione di SSIS

Per iniziare, vedere [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="monitor-packages"></a>Monitorare i pacchetti
Per monitorare i pacchetti in esecuzione in SSMS, è possibile usare uno dei seguenti strumenti di reporting di SSMS.
-   Fare clic con il pulsante destro del mouse su **SSISDB**, quindi selezionare **Operazioni attive** per aprire la finestra di dialogo **Operazioni attive**.
-   Selezionare un pacchetto in Esplora oggetti, fare clic con il pulsante destro del mouse e selezionare **Report**, quindi **Report standard** e infine **Tutte le esecuzioni**.

### <a name="schedule-packages"></a>Pianificare i pacchetti
Per pianificare l'esecuzione dei pacchetti archiviati nel database SQL, è possibile usare gli strumenti seguenti:
-   Istanza locale di SQL Server Agent
-   Attività stored procedure di SQL Server di Azure Data Factory

Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Passaggi successivi
Per iniziare con carichi di lavoro SSIS in Azure, vedere gli articoli seguenti:
-   [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)
-   [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md)
