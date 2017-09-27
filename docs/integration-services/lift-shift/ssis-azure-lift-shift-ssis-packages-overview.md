---
title: Spostare i carichi di lavoro di SQL Server Integration Services per il cloud | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: dbe6f832d4af55ddd15e12fba17a4da490fe19ae
ms.openlocfilehash: 3d22689e440b2a498f76d43ede74ad3f6f756796
ms.contentlocale: it-it
ms.lasthandoff: 09/25/2017

---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Spostare i carichi di lavoro di SQL Server Integration Services nel cloud
È ora possibile spostare i carichi di lavoro e i pacchetti di SQL Server Integration Services (SSIS) nel cloud di Azure.
-   Archiviare e gestire progetti SSIS e i pacchetti nel database di catalogo SSIS (SSISDB) nel Database SQL di Azure.
-   Eseguire i pacchetti in un'istanza di Runtime di integrazione di SSIS Azure, introdotto come parte della Data Factory di Azure versione 2.
-   Utilizzare strumenti familiari, ad esempio SQL Server Management Studio (SSMS) per queste attività comuni.

## <a name="benefits"></a>Vantaggi
Spostare i carichi di lavoro SSIS locale in Azure presenta i vantaggi seguenti:
-   **Ridurre i costi operativi** grazie alla riduzione dell'infrastruttura locale.
-   **Aumentare la disponibilità elevata** con più nodi al cluster, nonché le funzionalità di disponibilità elevata di Azure e di Database SQL di Azure.
-   **Aumentare la scalabilità** con la possibilità di specificare più core per nodo (scalabilità verticale) e più nodi al cluster (scalabilità orizzontale).
-   **Evitare le limitazioni** dell'esecuzione di SSIS su macchine virtuali di Azure.

## <a name="architecture-overview"></a>Panoramica dell'architettura
Nella tabella seguente vengono evidenziate le differenze tra SSIS in locale e SSIS in Azure. La differenza consiste nella separazione di archiviazione dal calcolo.

| Archiviazione | Runtime | Scalabilità |
|---|---|---|
| In locale (SQL Server) | SSIS runtime ospitato da SQL Server | SSIS Scale Out (in SQL Server 2017 e versioni successive)<br/><br/>Soluzioni personalizzate (nelle versioni precedenti di SQL Server) |
| In Azure (Database SQL) | Runtime di integrazione di Azure SSIS, un componente di Data Factory di Azure versione 2 | Opzioni di ridimensionamento per il IR SSIS |
| | | |

Azure Data Factory ospita il motore di runtime per i pacchetti SSIS in Azure. Il motore di runtime viene chiamato il Runtime di integrazione di Azure SSIS (SSIS IR).

Quando si esegue il provisioning di IR SSIS, è possibile applicare la scalabilità verticale e scalabilità orizzontale, specificare i valori per le opzioni seguenti:
-   La dimensione del nodo (incluso il numero di core) e il numero di nodi del cluster.
-   L'istanza esistente di Database SQL di Azure per ospitare il Database di catalogo SSIS (SSISDB) e il livello di servizio per il database.
-   Le esecuzioni parallele massime per ogni nodo.

È sufficiente eseguire il provisioning di una volta la IR SSIS. Successivamente, è possibile utilizzare strumenti familiari, ad esempio SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) per distribuire, configurare, eseguire, monitorare, pianificare e gestire i pacchetti.

Data Factory supporta anche altri tipi di runtime di integrazione. Per ulteriori informazioni su IR di SSIS e altri tipi di runtime di integrazione, vedere [runtime di integrazione in Azure Data Factory](/azure/data-factory/concepts-integration-runtime.md).

## <a name="package-features-on-azure"></a>Funzionalità dei pacchetti in Azure
Quando si esegue il provisioning di un'istanza del Database SQL per ospitare SSISDB, vengono installati l'Azure Feature Pack per SSIS e il pacchetto ridistribuibile di accesso. Questi componenti forniscono la connettività ai file di Excel e Access e da diverse origini dati di Azure. In questo momento, è possibile installare i componenti di terze parti per SSIS.

Continuare a progettare e compilare pacchetti locale in SSDT, o in Visual Studio con installato SSDT.

È necessario utilizzare il modello di distribuzione del progetto, non il modello di distribuzione del pacchetto, per i progetti che si distribuisce in SSISDB in un Database SQL di Azure.

Il nome del Database SQL che ospita SSISDB diventa la prima parte del nome in quattro parti da usare quando si distribuisce e gestire i pacchetti da SSDT e SSMS - `<sql_database_name>.database.windows.net`.

Per informazioni su come connettersi a origini dati locali dal cloud con l'autenticazione di Windows, vedere [connessione a origini dati locali con autenticazione di Windows](ssis-azure-connect-with-windows-auth.md).

## <a name="common-tasks"></a>Attività comuni

### <a name="provision"></a>Provisioning
Prima di è possibile distribuire ed eseguire pacchetti SSIS in Azure, è necessario eseguire il provisioning di database del catalogo SSISDB e il Runtime di integrazione di Azure SSIS. Eseguire il provisioning di passaggi di questo articolo: [sollevamento e spostamento dei pacchetti SQL Server Integration Services (SSIS) in Azure](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md).

### <a name="deploy-and-run-packages"></a>Distribuire ed eseguire pacchetti
Per distribuire i progetti e l'esecuzione di pacchetti nel Database SQL, è possibile utilizzare uno dei numerosi strumenti comuni e le opzioni di scripting:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (da SSMS, codice di Visual Studio o da un altro strumento)
-   Uno strumento da riga di comando
-   PowerShell
-   C# e il modello a oggetti gestione SSIS

### <a name="monitor-packages"></a>Pacchetti di monitoraggio
Per monitorare i pacchetti in esecuzione in SQL Server Management Studio, è possibile utilizzare uno dei seguenti strumenti di creazione di report in SQL Server Management Studio.
-   Fare doppio clic su **SSISDB**, quindi selezionare **operazioni attive** per aprire la **operazioni attive** la finestra di dialogo.
-   Selezionare un pacchetto in Esplora oggetti, pulsante destro del mouse e selezionare **report**, quindi **report Standard**, quindi **tutte le esecuzioni**.

### <a name="schedule-packages"></a>Pacchetti di pianificazione
Per pianificare l'esecuzione di pacchetti archiviati nel Database SQL, è possibile utilizzare gli strumenti seguenti:
-   Agente SQL Server locale
-   L'attività di Stored Procedure di Data Factory SQL Server

Per altre informazioni, vedere [del pacchetto SSIS di pianificazione di esecuzione in Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Passaggi successivi
Per iniziare con carichi di lavoro SSIS in Azure, vedere gli articoli seguenti:
-   [Spostare i pacchetti di SQL Server Integration Services (SSIS) in Azure](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md)
-   [Distribuire ed eseguire il monitoraggio di un pacchetto SSIS in Azure](ssis-azure-deploy-run-monitor-tutorial.md)

