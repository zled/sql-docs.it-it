---
title: Eseguire un notebook di esempio in un cluster di SQL Server 2019 big data | Microsoft Docs
description: Questa esercitazione illustra come è possibile caricare un'esecuzione di notebook Spark di esempio in un cluster di big data di SQL Server 2019 (anteprima).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/17/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 811c94615f0d69886f0f538357529ad3125e2925
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644160"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-2019-big-data-cluster"></a>Esercitazione: Eseguire un notebook di esempio in un cluster di big data di SQL Server 2019

Questa esercitazione illustra come caricare ed eseguire un notebook in Azure Data Studio in un cluster di big data di SQL Server 2019 (anteprima). In questo modo i data Scientist e data Engineer per eseguire il codice Python, R o Scala del cluster.

> [!TIP]
> Se si preferisce, è possibile scaricare ed eseguire uno script per i comandi in questa esercitazione. Per istruzioni, vedere la [esempi di Spark](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) su GitHub.

## <a id="prereqs"></a> Prerequisiti

* [Distribuire un cluster di big data su Kubernetes](deployment-guidance.md).
* [Installare Data Studio di Azure e l'estensione di SQL Server 2019](deploy-big-data-tools.md).
* [Caricare dati di esempio al cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="download-the-sample-notebook-file"></a>Scaricare il file di notebook di esempio

Usare le istruzioni seguenti per caricare il file di notebook di esempio **spark-sql.ipynb** in Azure Data Studio.

1. Aprire un prompt dei comandi bash (Linux) o Windows PowerShell.

1. Passare a una directory in cui si desidera scaricare il file di notebook di esempio a.

1. Eseguire il comando seguente **curl** comando per scaricare il file di notebook da GitHub:

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/spark-sql.ipynb' -o spark-sql.ipynb
   ```

## <a name="open-the-notebook"></a>Aprire il notebook

La procedura seguente illustra come aprire il file di notebook in Azure Data Studio:

1. In Azure Data Studio, connettersi al gateway HDFS/Spark del cluster di big data. Per altre informazioni, vedere [Connect per il gateway HDFS/Spark](deploy-big-data-tools.md#hdfs).

1. Fare doppio clic sulla connessione di gateway HDFS/Spark nel **server** finestra. Quindi selezionare **aprire Notebook**.

   ![Aprire notebook](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. Attendere che il **Kernel** e il contesto di destinazione (**collegare a**) in cui inserire. Impostare il **Kernel** al **PySpark3**e impostare **collegare a** all'indirizzo IP dell'endpoint di cluster di big data.

   ![Impostare Kernel e associare a](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Eseguire le celle del notebook

È possibile eseguire ogni cella del notebook facendo clic sul pulsante play a sinistra della cella. I risultati vengono visualizzati nel notebook dopo l'esecuzione della cella.

![Eseguire la cella notebook](media/tutorial-notebook-spark/run-notebook-cell.png)

Eseguire ogni cella del notebook di esempio in successione. Per altre informazioni sull'uso di notebook con cluster di big data di SQL Server, vedere le risorse seguenti:

- [Come usare i notebook in fase di anteprima di SQL Server 2019](notebooks-guidance.md)
- [Come gestire i notebook in Azure Data Studio](notebooks-how-to-manage.md)

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sui blocchi appunti:
> [!div class="nextstepaction"]
> [Scopri i notebook](notebooks-guidance.md)