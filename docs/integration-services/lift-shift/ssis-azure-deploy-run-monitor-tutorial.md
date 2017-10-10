---
title: Distribuire ed eseguire il monitoraggio di un pacchetto SSIS in Azure | Documenti Microsoft
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: c2dbdf818ef15dc97020dd7b35f88cfa080537d3
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="deploy-run-and-monitor-an-ssis-package-on-azure"></a>Distribuire ed eseguire il monitoraggio di un pacchetto SSIS in Azure
In questa esercitazione viene illustrato come distribuire un progetto di SQL Server Integration Services per il database del catalogo di SSISDB in un Database SQL di Azure, eseguire un pacchetto nel Runtime di integrazione di Azure SSIS e monitorare il pacchetto in esecuzione.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, verificare di che aver 17.2 per o versione successiva di SQL Server Management Studio. Per scaricare la versione più recente di SSMS, vedere [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Assicurarsi di aver configurato il database SSISDB e il provisioning di integrazione di Azure-SSIS Runtime. Per informazioni su come eseguire il provisioning SSIS in Azure, vedere [sollevamento e spostamento dei pacchetti SQL Server Integration Services (SSIS) in Azure](https://docs.microsoft.com/en-us/azure/tutorial-deploy-ssis-packages-azure).

## <a name="connect-to-the-ssisdb-database"></a>Connettersi al database SSISDB

Utilizzare SQL Server Management Studio per connettersi al catalogo SSIS nel server di Database SQL di Azure. Per altre informazioni, vedere [Connetti al database del catalogo di SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

> [!IMPORTANT]
> Un server di Database SQL di Azure è in ascolto sulla porta 1433. Se si sta tentando di connettersi a un server di Database SQL di Azure all'interno di un firewall aziendale, questa porta deve essere aperta nel firewall aziendale per poter funzionare correttamente.

1. Aprire SQL Server Management Studio.

2. **Connettersi al server**. Nel **Connetti al Server** finestra di dialogo immettere le informazioni seguenti:

   | Impostazione       | Valore consigliato | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Il nome completo del server | Il nome deve essere nel formato: **mysqldbserver.database.windows.net**. Se è necessario il nome del server, vedere [Connetti al database del catalogo di SSISDB in Azure](ssis-azure-connect-to-catalog-database.md). |
   | **Autenticazione** | autenticazione di SQL Server | Questa Guida rapida Usa autenticazione di SQL Server. |
   | **Account di accesso** | L'account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | La password per l'account di amministratore del server | Questa è la password specificata al momento della creazione del server. |

3. **Connettersi al database SSISDB**. Selezionare **opzioni** per espandere il **Connetti al Server** la finestra di dialogo. Nella struttura **Connetti al Server** la finestra di dialogo, seleziona il **le proprietà di connessione** scheda. Nel **Connetti al database** campo, selezionare o immettere `SSISDB`.

4. Selezionare quindi **Connetti**. Viene visualizzata la finestra di Esplora oggetti in SQL Server Management Studio. 

5. In Esplora oggetti espandere **cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="deploy-a-project"></a>Distribuire un progetto

### <a name="start-the-integration-services-deployment-wizard"></a>Avviare la distribuzione guidata di Integration Services
1. In Esplora oggetti in SQL Server Management Studio, con la **cataloghi di Integration Services** nodo e **SSISDB** nodo espanso, espandere una cartella di progetto.

2.  Selezionare il **progetti** nodo.

3.  Fare clic su di **progetti** nodo e selezionare **Distribuisci progetto**. Verrà visualizzata la distribuzione guidata di Integration Services. È possibile distribuire un progetto da un database di catalogo SSIS o dal file system.

### <a name="deploy-a-project-with-the-deployment-wizard"></a>Distribuire un progetto con la distribuzione guidata
1. Nel **Introduzione** pagina della procedura guidata distribuzione, rivedere l'introduzione. Selezionare **Avanti** per aprire la **Seleziona origine** pagina.

2. Nel **Seleziona origine** pagina, selezionare il progetto SSIS esistente per la distribuzione.
    -   Per distribuire un file di distribuzione del progetto creato, selezionare **File distribuzione progetto** e immettere il percorso al file con estensione ispac.
    -   Per distribuire un progetto che si trova in un catalogo SSIS, selezionare **catalogo di Integration Services**, quindi immettere il nome del server e il percorso al progetto nel catalogo.
    -   Selezionare **Avanti** per visualizzare il **Seleziona destinazione** pagina.
  
3.  Nel **Seleziona destinazione** pagina, selezionare la destinazione per il progetto.
    -   Immettere il nome completo del server nel formato `<server_name>.database.windows.net`.
    -   Selezionare quindi **Sfoglia** per selezionare la cartella di destinazione in SSISDB.
    -   Selezionare **Avanti** per aprire la **revisione** pagina.  
  
4.  Nel **esaminare** pagina, rivedere le impostazioni selezionate.
    -   È possibile modificare le selezioni selezionando **precedente**, oppure selezionando uno dei passaggi nel riquadro a sinistra.
    -   Selezionare **Distribuisci** per avviare il processo di distribuzione.
  
5.  Al termine del processo di distribuzione, il **risultati** verrà visualizzata la pagina. Questa pagina consente di visualizzare l'esito positivo o negativo di ogni azione.
    -   Se l'azione non riuscita, selezionare **Failed** nel **risultato** colonna per visualizzare una spiegazione dell'errore.
    -   Facoltativamente, selezionare **Salva Report...**  per salvare i risultati in un file XML.
    -   Selezionare **Chiudi** chiudere la procedura guidata.

## <a name="run-a-package"></a>Eseguire un pacchetto

1. In Esplora oggetti in SQL Server Management Studio, selezionare il pacchetto che si desidera eseguire.

2. Mouse e scegliere **Execute** per aprire la **Esegui pacchetto** la finestra di dialogo.

3.  Nel **Esegui pacchetto** finestra di dialogo casella, configurare l'esecuzione del pacchetto tramite le impostazioni di **parametri**, **gestioni connessioni**, e **avanzate**  schede.

4.  Selezionare **OK** per eseguire il pacchetto.

## <a name="monitor-the-running-package-in-ssms"></a>Monitorare il pacchetto in esecuzione in SQL Server Management Studio

Per visualizzare lo stato di esecuzione di operazioni di Integration Services nel server Integration Services, ad esempio distribuzione, convalida ed esecuzione del pacchetto, utilizzare il **operazioni attive** nella finestra di dialogo di SQL Server Management Studio. Per aprire il **operazioni attive** la finestra di dialogo, fare doppio clic su **SSISDB**, quindi selezionare **operazioni attive**.

È inoltre possibile selezionare un pacchetto in Esplora oggetti, pulsante destro del mouse e selezionare **report**, quindi **report Standard**, quindi **tutte le esecuzioni**.

Per ulteriori informazioni su come monitorare pacchetti in esecuzione in SQL Server Management Studio, vedere [monitoraggio l'esecuzione di pacchetti e altre operazioni](https://docs.microsoft.com/en-us/sql/integration-services/performance/monitor-running-packages-and-other-operations).

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Monitorare il Runtime di integrazione di Azure SSIS

Per ottenere informazioni di stato sul Runtime di integrazione di Azure SSIS in cui si eseguono i pacchetti, utilizzare i comandi di PowerShell seguenti: per ognuno dei comandi, specificare i nomi delle Data Factory, IR di SSIS di Azure e il gruppo di risorse.

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Ottenere i metadati relativi al Runtime di integrazione di Azure SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Ottenere lo stato del Runtime di integrazione di Azure SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntimeStatus -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>Passaggi successivi
- Informazioni su come pianificare l'esecuzione del pacchetto. Per altre informazioni, vedere [del pacchetto SSIS di pianificazione di esecuzione in Azure](ssis-azure-schedule-packages.md)

