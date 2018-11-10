---
title: Inviare il processo Spark nei cluster di SQL Server i big data in Azure Data Studio
description: Inviare il processo Spark nei cluster di SQL Server i big data in Azure Data Studio
services: SQL Server 2019 big data cluster spark
ms.service: SQL Server 2019 big data cluster spark
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.custom: ''
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: 4ff29460ade2a3e32f3650d2c2701f22548bdb60
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221607"
---
# <a name="submit-spark-job-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Inviare il processo Spark nei cluster di SQL Server i big data in Azure Data Studio

Uno degli scenari chiave è la possibilità di inviare il processo Spark per SQL Server 2019 CTP 2.1. La funzionalità di invio dei processi di Spark consente di inviare un file con estensione Jar o Py locali con riferimenti a cluster di big data di SQL Server 2019. Consente inoltre di eseguire un file con estensione Jar o Py, che sono già presenti nel file system HDFS. 

## <a name="prerequisite"></a>Prerequisiti 
Installare gli strumenti dei big data per SQL Server e connettersi a un cluster di big data prima di inviare processi Spark. Per informazioni dettagliate di installazione, fare riferimento per creare un collegamento [distribuire strumenti big data](deploy-big-data-tools.md).

## <a name="open-spark-job-submission-dialog"></a>Aprire la finestra di invio dei processi di Spark
Esistono diversi modi per aprire la finestra di invio dei processi di Spark. I modi in cui includere Dashboard, menu di scelta rapida in Esplora oggetti e pannello contenente comandi.

+ Fare clic su **nuovo processo Spark** nel dashboard per aprire la finestra di dialogo Spark submission processo.

    ![Menu Invia selezionando il dashboard ](./media/submit-spark-job/new-spark-job.png)
 
+ Fare doppio clic sul cluster in Esplora oggetti e selezionare **Submit Spark Job** dal menu di scelta rapida. Verrà aperto dialogo di invio dei processi Spark.  
 
    ![Menu Invia dal cluster pulsante destro del mouse](./media/submit-spark-job/submit-spark-job.png)

+ Fare doppio clic su un file con estensione Jar / all'anno precedente in Esplora oggetti e selezionare **Submit Spark Job** dal menu di scelta rapida. Verrà aperta una finestra con il campo Jar / all'anno precedente sia già popolato invio processo Spark. 
 
    ![Inviare i menu di scelta dal file di scelta rapida](./media/submit-spark-job/submit-spark-job-2.png)

+ Usare i comandi **Submit Spark Job** nel riquadro comandi digitando Cmd + MAIUSC + P (nel Mac) e Ctrl + MAIUSC + P (in Windows).

    ![Inviare comandi di menu in windows](./media/submit-spark-job/submit-spark-job-3.png)

    ![Inviare comandi di menu in mac](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Inviare processi Spark 
La finestra di dialogo Spark submission processo viene visualizzato come indicato di seguito. Immettere il nome del processo, percorso del file con estensione JAR / all'anno precedente, la classe principale e gli altri campi. Il file Jar / origine del file rispetto all'anno precedente potrebbe essere da locale o da un HDFS. Se il processo dispone di Spark fa riferimento a file con estensione jar, Py file o file aggiuntivi, fare clic su **avanzate** scheda e immettere i percorsi dei file corrispondenti. Fare clic su **Submit** per inviare processi Spark.
 
![Nuova finestra di dialogo spark processo](./media/submit-spark-job/submit-spark-job-section.png)

![Finestra di dialogo avanzata](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Monitorare l'invio di processi Spark
Dopo che viene inviato il processo Spark, le informazioni sullo stato invio e l'esecuzione del processo di Spark vengono visualizzati nella cronologia di attività sulla sinistra. E i dettagli sull'avanzamento e i log vengono visualizzati anche nella **OUTPUT** finestra nella parte inferiore.
+ Quando il processo Spark è in corso, il **la cronologia delle attività** pannello e **OUTPUT** finestra vengono aggiornati con lo stato di avanzamento.

![Processo spark di monitoraggio in corso](./media/submit-spark-job/monitor-spark-job-submission.png)

+ Quando il processo Spark è completata con esito positivo, è possibile visualizzare l'interfaccia utente di Spark e l'interfaccia utente di Yarn collegamenti nel **OUTPUT** finestra. È possibile scegliere i collegamenti per altre informazioni.

![Collegamento al processo Spark nell'output](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sul cluster di big data di SQL Server e gli scenari correlati, vedere [What ' s cluster di big data di SQL Server](big-data-cluster-overview.md)?

