---
title: Sviluppare e distribuire SQL Server di database per Linux | Documenti Microsoft
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: sql-linux
ms.openlocfilehash: 41eabe46f654f2cb0464d2f7589cb0ce50a7c214
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Utilizzare Visual Studio per creare database per SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) diventa un potente database lifecycle management (DLM) ambiente di sviluppo e Visual Studio per SQL Server in Linux. È possibile sviluppare, compilare, testare e pubblicare il database da un progetto di controllo del codice sorgente, esattamente come si sviluppa il codice dell'applicazione.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Installare Visual Studio e SQL Server Data Tools

1. Se non è già installato Visual Studio nel computer Windows, [scaricare e installare Visual Studio]. Se non si dispone di una licenza di Visual Studio, Visual Studio Community edition è un IDE gratuito, con funzionalità complete per studenti, gli sviluppatori open source e singoli.

2. Durante l'installazione di Visual Studio, selezionare **personalizzato** per il **scegliere il tipo di installazione** opzione. Scegliere **Avanti**

3. Selezionare **Microsoft SQL Server Data Tools**, **Git per Windows**, e **estensione GitHub per Visual Studio** dall'elenco di selezione funzionalità.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Continuare e completare l'installazione di Visual Studio. Può richiedere alcuni minuti.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>L'aggiornamento di SQL Server Data Tools alla versione di SSDT 17,0 RC

2017 di SQL Server in Linux è supportata da SSDT versione 17,0 RC o versione successiva.

* [Scaricare e installare SSDT 17,0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Creare un nuovo progetto di database nel controllo del codice sorgente

1. Avviare Visual Studio.

2. Selezionare **Team Explorer** sul **vista** menu. 

3. Fare clic su **New** in **Git Repository locale** sezione la **Connetti** pagina.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Fare clic su **Crea**. Dopo aver creato il repository Git locale, fare doppio clic su **SSDTRepo**.

4. Fare clic su **New** nel **soluzioni** sezione. Selezionare **SQL Server** in **altri linguaggi** nodo il **nuovo progetto** finestra di dialogo.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Digitare **TutorialDB** per il nome e fare clic su **OK** per creare un nuovo progetto di database.

## <a name="create-a-new-table-in-the-database-project"></a>Creare una nuova tabella nel progetto di database

1. Selezionare **Esplora** sul **vista** menu.

2. Aprire il menu di progetto di database facendo clic su **TutorialDB** in Esplora soluzioni.

3. Selezionare **tabella** in **aggiungere**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. Utilizzando Progettazione tabelle, aggiungere due colonne, nome `nvarchar(50)` e il percorso `nvarchar(50)`, come illustrato nell'immagine. Genera l'errore SSDT di `CREATE TABLE` script quando si aggiungono le colonne nella finestra di progettazione.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Salvare il **Table1.sql** file.

## <a name="build-and-validate-the-database"></a>Creare e convalidare il database

1. Aprire il menu di progetto di database in **TutorialDB** e selezionare **compilare**. SSDT consente di compilare file di codice sorgente con estensione SQL nel progetto e viene generato un file di pacchetto (con estensione dacpac) di applicazione livello dati. Questa operazione consente di pubblicare un database all'istanza di SQL Server 2017 in Linux. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Controllare il messaggio di conferma di compilazione **Output** finestra in Visual Studio. 

## <a name="publish-the-database-to-sql-server-2017-instance-on-linux"></a>Pubblicare il database all'istanza di SQL Server 2017 su Linux

1. Aprire il menu di progetto di database in **TutorialDB** e selezionare **pubblica**.

2. Fare clic su **modifica** per selezionare l'istanza di SQL Server in Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. Nella finestra di dialogo di connessione, digitare il nome di host o indirizzo IP dell'istanza di SQL Server in Linux, nome utente e password.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Fare clic su di **pubblica** pulsante nella finestra di dialogo di pubblicazione.

5. Archiviare lo stato di pubblicazione di **operazioni degli strumenti dati** finestra.

6. Fare clic su **vista Reulst** o **Visualizza Script** per visualizzare i dettagli del database di pubblicare i risultati in SQL Server in Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Creare un nuovo database nell'istanza di SQL Server in Linux e appreso le nozioni di base dello sviluppo di un database con un progetto di database di controllo del codice sorgente completata.

## <a name="next-steps"></a>Passaggi successivi

Se si ha familiarità con T-SQL, vedere [esercitazione: scrittura di istruzioni Transact-SQL] e [riferimento a Transact-SQL (motore di Database)].

Per ulteriori informazioni sullo sviluppo di un database con gli strumenti dati SQL, vedere [documenti MSDN di SSDT]

[scaricare e installare Visual Studio]:https://www.visualstudio.com/downloads/
[Download and Install SSDT 17.0 RC2]:https://aka.ms/ssdt-download
[documenti MSDN di SSDT]: https://msdn.microsoft.com/en-us/library/hh272686(v=vs.103).aspx
[esercitazione: scrittura di istruzioni Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[riferimento a Transact-SQL (motore di Database)]:https://msdn.microsoft.com/library/bb510741.aspx
