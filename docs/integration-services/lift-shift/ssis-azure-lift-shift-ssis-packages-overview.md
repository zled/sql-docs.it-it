---
title: Migrazione lift-and-shift dei carichi di lavoro di SQL Server Integration Services nel cloud | Microsoft Docs
ms.date: 04/13/2018
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10870216c2abc826a72bb16715701a794e651610
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Migrazione lift-and-shift dei carichi di lavoro di SQL Server Integration Services nel cloud
È ora possibile spostare pacchetti e i carichi di lavoro di SQL Server Integration Services (SSIS) nel cloud di Azure.
-   Archiviare e gestire progetti e pacchetti SSIS nel database del catalogo SSIS (SSISDB) per il database SQL di Azure o l'Istanza gestita di database SQL (anteprima).
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
| In Azure (database SQL o Istanza gestita di database SQL (anteprima)) | Runtime di integrazione SSIS di Azure, un componente di Azure Data Factory versione 2 | Opzioni di ridimensionamento per il runtime di integrazione SSIS |
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

## <a name="version-info"></a>Informazioni sulla versione

È possibile distribuire in Azure un pacchetto creato con qualsiasi versione di SSIS. Quando si distribuisce un pacchetto in Azure, se non si verificano errori di convalida il pacchetto viene aggiornato automaticamente al formato più recente. In altri termini il pacchetto viene sempre aggiornato alla versione più recente di SSIS.

Il processo di distribuzione convalida i pacchetti, per verificare che siano eseguibili nel runtime di integrazione SSIS di Azure. Per altre informazioni, vedere [Convalidare pacchetti SSIS distribuiti in Azure](ssis-azure-validate-packages.md).

## <a name="prerequisites"></a>Prerequisites

Le funzionalità descritte in questo articolo richiedono le seguenti versioni di SQL Server Data Tools (SSDT):
-   Per Visual Studio 2017, versione 15.3 (anteprima) o successiva.
-   Per Visual Studio 2015, versione 17.2 o successiva.

Per altre informazioni sui prerequisiti in Azure, vedere [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

## <a name="provision-ssis-on-azure"></a>Provisioning di SSIS in Azure
Prima di distribuire ed eseguire i pacchetti SSIS in Azure, è necessario eseguire il provisioning del database del catalogo SSIS (SSISDB) e del runtime di integrazione SSIS di Azure. Eseguire i passaggi di provisioning descritti nell'articolo [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

Il **nome del database SQL** che ospita SSISDB diventa la prima parte del nome in quattro parti da usare quando si distribuiscono e si gestiscono i pacchetti da SSDT e SSMS, `<sql_database_name>.database.windows.net`.

Per informazioni su come connettersi al database del catalogo SSIS, vedere [Connettersi al database del catalogo SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

## <a name="design-packages"></a>Progettare pacchetti
Continuare a **progettare e compilare i pacchetti** in locale in SSDT o in Visual Studio con SSDT installato.

Per informazioni su come connettersi alle **origini dati locali** dal cloud con l'autenticazione di Windows, vedere [Connettersi a origini dati locali e condivisioni file di Azure con autenticazione di Windows](ssis-azure-connect-with-windows-auth.md).

Per informazioni su come connettersi ai file e alle condivisioni file, vedere [Archiviare e recuperare file nelle condivisioni file in locale e in Azure con SSIS](ssis-azure-files-file-shares.md).

Quando si esegue il provisioning di un'istanza del database SQL per ospitare SSISDB, vengono installati anche Azure Feature Pack per SSIS e le funzionalità di accesso ridistribuibili. Questi componenti offrono la connettività a varie origini dati di **Azure** e ai file di **Excel e Access**, oltre che alle origini dati supportate dai componenti predefiniti.

È anche possibile installare componenti aggiuntivi. Per altre informazioni, vedere [Custom setup for the Azure-SSIS integration runtime](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md) (Configurazione personalizzata del runtime di integrazione SSIS di Azure).

## <a name="deploy-and-run-packages"></a>Distribuire ed eseguire i pacchetti
Per la distribuzione di progetti a SSISDB in Azure è necessario usare il **modello di distribuzione dei progetti** e non il modello di distribuzione dei pacchetti.

Per distribuire i progetti ed eseguire i pacchetti in Azure è possibile usare diversi strumenti e opzioni di scripting comuni:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (da SSMS, Visual Studio Code o un altro strumento)
-   Uno strumento da riga di comando
-   PowerShell
-   C# e il modello a oggetti di gestione di SSIS

Per iniziare, vedere [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md).

## <a name="monitor-packages"></a>Monitorare i pacchetti
Per monitorare i pacchetti in esecuzione in SSMS, è possibile usare uno dei seguenti strumenti di reporting di SSMS.
-   Fare clic con il pulsante destro del mouse su **SSISDB**, quindi selezionare **Operazioni attive** per aprire la finestra di dialogo **Operazioni attive**.
-   Selezionare un pacchetto in Esplora oggetti, fare clic con il pulsante destro del mouse e selezionare **Report**, quindi **Report standard** e infine **Tutte le esecuzioni**.

## <a name="schedule-packages"></a>Pianificare i pacchetti
Per pianificare l'esecuzione dei pacchetti archiviati nel database SQL, è possibile usare gli strumenti seguenti:
-   Istanza locale di SQL Server Agent
-   Attività stored procedure di SQL Server di Azure Data Factory

Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Passaggi successivi
Per iniziare con carichi di lavoro SSIS in Azure, vedere gli articoli seguenti:
-   [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)
-   [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md)
