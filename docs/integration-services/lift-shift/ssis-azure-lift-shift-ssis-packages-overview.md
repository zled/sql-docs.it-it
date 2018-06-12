---
title: Migrazione lift-and-shift dei carichi di lavoro di SQL Server Integration Services nel cloud | Microsoft Docs
ms.date: 05/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f62987a7edc2d04f88c3cfe98f04f0bd6043b44a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585573"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Migrazione lift-and-shift dei carichi di lavoro di SQL Server Integration Services nel cloud
È ora possibile spostare pacchetti e i carichi di lavoro di SQL Server Integration Services (SSIS) nel cloud di Azure.
-   Archiviare e gestire progetti e pacchetti SSIS nel database del catalogo SSIS (SSISDB) per il database SQL di Azure o l'Istanza gestita di database SQL (anteprima).
-   Eseguire i pacchetti in un'istanza del runtime di integrazione Azure-SSIS, un componente di Azure Data Factory.
-   Usare strumenti noti, ad esempio SQL Server Management Studio (SSMS), per le attività comuni.

## <a name="benefits"></a>Vantaggi
Spostare i carichi di lavoro SSIS locali in Azure presenta i potenziali vantaggi seguenti:
-   **Riduzione dei costi operativi** e riduzione delle attività di gestione dell'infrastruttura svolte quando si esegue SSIS in locale o in macchine virtuali di Azure.
-   **Aumento della disponibilità elevata** con la possibilità di specificare più nodi per cluster, nonché le funzionalità di disponibilità elevata di Azure e del database SQL di Azure.
-   **Aumento della scalabilità** con la possibilità di specificare più core per nodo (scalabilità verticale) e più nodi per cluster (scalabilità orizzontale).

## <a name="architecture-overview"></a>Panoramica dell'architettura
Nella tabella seguente vengono evidenziate le differenze tra SSIS in locale e SSIS in Azure. La differenza più significativa è la separazione dell'archiviazione dal runtime. Azure Data Factory ospita il motore di runtime per i pacchetti SSIS in Azure. Il motore di runtime è definito Runtime di integrazione Azure-SSIS (Azure-SSIS IR). Per altre informazioni, vedere [Runtime di integrazione Azure-SSIS](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime).

| Archiviazione | Runtime | Scalabilità |
|---|---|---|
| Locale (SQL Server) | Runtime SSIS ospitato da SQL Server | SQL Server Integration Services Scale Out (in SQL Server 2017 e versioni successive)<br/><br/>Soluzioni personalizzate (nelle versioni precedenti di SQL Server) |
| In Azure (database SQL o Istanza gestita di database SQL (anteprima)) | Runtime di integrazione Azure-SSIS, un componente di Azure Data Factory | Opzioni di scalabilità per il runtime di integrazione Azure-SSIS |
| | | |

È sufficiente eseguire il provisioning del runtime di integrazione Azure-SSIS una sola volta. Successivamente, è possibile usare strumenti familiari, ad esempio SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS), per distribuire, configurare, eseguire, monitorare, pianificare e gestire i pacchetti.

## <a name="version-support"></a>Supporto versione

È possibile distribuire in Azure un pacchetto creato con qualsiasi versione di SSIS. Quando si distribuisce un pacchetto in Azure, se non si verificano errori di convalida il pacchetto viene aggiornato automaticamente al formato più recente. In altri termini il pacchetto viene sempre aggiornato alla versione più recente di SSIS.

Il processo di distribuzione convalida i pacchetti, per verificare che siano eseguibili nel runtime di integrazione SSIS di Azure. Per altre informazioni, vedere [Convalidare pacchetti SSIS distribuiti in Azure](ssis-azure-validate-packages.md).

## <a name="prerequisites"></a>Prerequisites

Per distribuire pacchetti SSIS in Azure è necessario avere una delle versioni seguenti di SQL Server Data Tools (SSDT):
-   Per Visual Studio 2017, versione 15.3 o successiva.
-   Per Visual Studio 2015, versione 17.2 o successiva.

Per informazioni sui prerequisiti per il runtime di integrazione Azure-SSIS, vedere [Distribuire pacchetti SQL Server Integration Services in Azure - Prerequisiti](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure#prerequisites).

> [!NOTE]
> Durante l'anteprima pubblica, il runtime di integrazione Azure-SSIS non è ancora disponibile in tutte le aree. Per informazioni sulle aree supportate, vedere i [prodotti Microsoft Azure disponibili in base all'area geografica](https://azure.microsoft.com/regions/services/).

## <a name="provision-ssis-on-azure"></a>Provisioning di SSIS in Azure

Prima di distribuire ed eseguire i pacchetti SSIS in Azure, è necessario eseguire il provisioning del database del catalogo SSIS (SSISDB) e del runtime di integrazione SSIS di Azure. Per la procedura da seguire per il provisioning, vedere l'articolo [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

Quando si esegue il provisioning del runtime di integrazione Azure-SSIS è possibile applicare la scalabilità verticale e orizzontale specificando valori per le opzioni seguenti:
-   La dimensione del nodo, incluso il numero di core, e il numero di nodi del cluster.
-   L'istanza esistente del database SQL di Azure per ospitare il database del catalogo SSIS (SSISDB) e il livello di servizio per il database.
-   Le esecuzioni parallele massime per ogni nodo.

Per altre informazioni sulle prestazioni, vedere [Configurare il runtime di integrazione Azure-SSIS per garantire prestazioni elevate](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance).

## <a name="design-packages"></a>Progettare pacchetti

Continuare a **progettare e compilare i pacchetti** in locale in SSDT o in Visual Studio con SSDT installato.

### <a name="connect-to-data-sources"></a>Connettersi alle origini dati

Per informazioni su come connettersi alle **origini dati locali** dal cloud con l'autenticazione di Windows, vedere [Connettersi a origini dati locali e condivisioni file di Azure con autenticazione di Windows](ssis-azure-connect-with-windows-auth.md).

Per informazioni su come connettersi ai file e alle condivisioni file, vedere [Archiviare e recuperare file nelle condivisioni file in locale e in Azure con SSIS](ssis-azure-files-file-shares.md).

### <a name="available-ssis-components"></a>Componenti SSIS disponibili

Quando si esegue il provisioning di un'istanza del database SQL per ospitare SSISDB, vengono installati anche Azure Feature Pack per SSIS e le funzionalità di accesso ridistribuibili. Questi componenti offrono la connettività a varie origini dati di **Azure** e ai file di **Excel e Access**, oltre che alle origini dati supportate dai componenti predefiniti.

È anche possibile installare componenti aggiuntivi, ad esempio un driver non installato per impostazione predefinita. Per altre informazioni, vedere [Custom setup for the Azure-SSIS integration runtime](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md) (Configurazione personalizzata del runtime di integrazione SSIS di Azure).

Se l'utente è un ISV può aggiornare l'installazione dei componenti concessi in licenza per renderli disponibili in Azure. Per altre informazioni, vedere [Sviluppare componenti personalizzati a pagamento o concessi in licenza per il runtime di integrazione Azure-SSIS](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components).

### <a name="transaction-support"></a>Supporto delle transazioni

Con SQL Server in locale e nelle macchine virtuali Azure, è possibile usare le transazioni Microsoft Distributed Transaction Coordinator (MSDTC). Per configurare MSDTC in ogni nodo del runtime di integrazione Azure-SSIS usare la funzionalità di installazione personalizzata. Per altre informazioni, vedere [Custom setup for the Azure-SSIS integration runtime](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup) (Configurazione personalizzata del runtime di integrazione SSIS di Azure).

Con il database SQL di Azure è possibile usare solo le transazioni elastiche. Per altre informazioni, vedere [Transazioni distribuite in database cloud](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview).

## <a name="deploy-and-run-packages"></a>Distribuire ed eseguire i pacchetti

Per iniziare, vedere [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="connect-to-ssisdb"></a>Connettersi a SSISDB

Il **nome del database SQL** che ospita SSISDB diventa la prima parte del nome in quattro parti da usare quando si distribuiscono ed eseguono pacchetti da SSDT e SSMS, con il formato seguente: `<sql_database_name>.database.windows.net`. Per informazioni su come connettersi al database del catalogo SSIS in Azure, vedere [Connettersi al database del catalogo SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

### <a name="deploy-projects-and-packages"></a>Distribuire progetti e pacchetti

Per la distribuzione di progetti a SSISDB in Azure è necessario usare il **modello di distribuzione dei progetti** e non il modello di distribuzione dei pacchetti.

Per distribuire progetti in Azure è possibile usare diversi strumenti e opzioni di scripting comuni:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (da SSMS, Visual Studio Code o un altro strumento)
-   Uno strumento da riga di comando
-   PowerShell o C# e il modello a oggetti di gestione di SSIS

Per un esempio di distribuzione in cui si usano SSMS e la Distribuzione guidata Integration Services, vedere [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="run-packages"></a>Eseguire i pacchetti

Per una panoramica dei metodi che è possibile usare per eseguire i pacchetti SSIS distribuiti in Azure, vedere [Eseguire un pacchetto SSIS in Azure](ssis-azure-run-packages.md).

## <a name="pass-runtime-values-with-environments"></a>Passare i valori di runtime con gli ambienti

Per passare uno o più valori di runtime ai pacchetti eseguiti nell'ambito di una pipeline di Azure Data Factory, creare ambienti di esecuzione SSIS in SSISDB con SQL Server Management Studio (SSMS). In ogni ambiente creare variabili e assegnare valori corrispondenti ai parametri dei progetti o dei pacchetti. Configurare i pacchetti SSIS in SSMS in modo da associare le variabili di ambiente ai parametri del progetto o del pacchetto. Quando si eseguono i pacchetti in una pipeline di Data Factory, passare da un ambiente all'altro specificando percorsi di ambiente diversi nella scheda Impostazioni dell'interfaccia utente dell'attività Esegui pacchetto SSIS.

Per altre informazioni sugli ambienti SSIS, vedere [Creare ed eseguire il mapping di un ambiente server](../packages/deploy-integration-services-ssis-projects-and-packages.md#create-and-map-a-server-environment). Per altre informazioni sull'esecuzione di un pacchetto nell'ambito di una pipeline di Azure Data Factory, vedere [Eseguire un pacchetto SSIS tramite l'attività Esegui pacchetto SSIS in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="monitor-packages"></a>Monitorare i pacchetti
Per monitorare i pacchetti in esecuzione in SSMS, è possibile usare i seguenti strumenti di reporting di SSMS.
-   Fare clic con il pulsante destro del mouse su **SSISDB**, quindi selezionare **Operazioni attive** per aprire la finestra di dialogo **Operazioni attive**.
-   Selezionare un pacchetto in Esplora oggetti, fare clic con il pulsante destro del mouse e selezionare **Report**, quindi **Report standard** e infine **Tutte le esecuzioni**.

Per monitorare il runtime di integrazione Azure-SSIS, vedere [Monitorare il runtime di integrazione Azure-SSIS](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

## <a name="schedule-packages"></a>Pianificare i pacchetti
Per pianificare l'esecuzione dei pacchetti archiviati nel database SQL è possibile usare vari strumenti. Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Passaggi successivi
Per iniziare con carichi di lavoro SSIS in Azure, vedere gli articoli seguenti:
-   [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Distribuire, eseguire e monitorare un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md)
