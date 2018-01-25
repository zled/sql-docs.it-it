---
title: R Server (Standalone) | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
vms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: ca9e48f1-67b8-4905-9b78-56752d7a4e81
caps.latest.revision: "22"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: d7136f051317f7ffeb26d779b3cf611edef13592
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="r-server-standalone"></a>R Server (Standalone)

In SQL Server 2016, Microsoft ha rilasciato **R Server (Standalone)**, come parte della piattaforma per il supporto analitica di classe enterprise.  Microsoft R Server garantisce scalabilità e sicurezza per il linguaggio R e risolve le limitazioni in memoria di open source R. Ad esempio SQL Server R Services, Microsoft R Server (Standalone) fornisce l'elaborazione parallela sia blocchi di dati, consentendo agli utenti di R utilizzare i dati di dimensioni molto maggiori rispetto a possono adattarsi alla memoria.

In SQL Server 2017, è stato aggiunto il supporto per il linguaggio Python, esercita un ampio supporto della community di machine learning e include le librerie comuni per analitica di testo e formazione.  Per riflettere il set più ampio di lingue, è stato rinominato anche a **Microsoft Machine Learning Server (Standalone)**.

## <a name="benefits-of-microsoft-r-server"></a>Vantaggi di Microsoft R Server

È possibile utilizzare Microsoft R Server per l'elaborazione distribuita su più piattaforme. Quando si installa dal programma di installazione di SQL Server, si verifica il basato su Windows server e tutti gli strumenti necessari per i modelli di pubblicazione e distribuzione. Per ulteriori informazioni su altre piattaforme, vedere queste risorse in MSDN library:

+ [Introducing Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver) (Introduzione a Microsoft R Server)
+ [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (R Server per Windows)

È anche possibile installare Microsoft R Server da utilizzare come un client di sviluppo, per ottenere le librerie RevoScaleR e gli strumenti necessari per creare soluzioni R che possono essere distribuite a SQL Server.

## <a name="whats-new-in-microsoft-machine-learning-server"></a>Novità di Server di Microsoft Machine Learning

Se si installa Servizi di apprendimento macchina (Standalone) utilizzando il programma di installazione di SQL Server 2017, è ora possibile aggiungere il linguaggio Python. Ovviamente, il linguaggio R è ancora un'opzione supportata ed è anche possibile installare entrambi i linguaggi, se lo si desidera.
 
In SQL Server 2017 CTP 2.0, l'installazione del server include anche il pacchetto mrsdeploy e altre utilità utilizzata per i modelli di operatività. Per ulteriori informazioni, vedere [rendere operativo con mrsdeploy](../../advanced-analytics/operationalization-with-mrsdeploy.md).

Gli utenti aziendali con SQL Server Machine Learning è possono utilizzare i programmi di installazione scaricabile per Microsoft R Server per aggiornare i componenti di R, in un processo denominato associazione. Per ulteriori informazioni, vedere [SqlBindR utilizzare per l'aggiornamento e l'istanza di SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

## <a name="get-microsoft-r-server-or-machine-learning-server-standalone"></a>Ottenere Microsoft R Server o Machine Learning Server (Standalone)

 Sono disponibili più opzioni per l'installazione di Microsoft R Server:

+ Utilizzare l'installazione guidata di SQL Server

  [Creare un server R autonomo](../r/create-a-standalone-r-server.md)

  Eseguire l'installazione di SQL Server 2016 per installare **Microsoft R Server (Standalone)**. Il linguaggio R viene aggiunto per impostazione predefinita.
  In alternativa, eseguire l'installazione di SQL Server 2017 per installare **Machine Learning Server (Standalone)** e selezionare R o Python o entrambi.

  > [!IMPORTANT]
  > L'opzione per installare il server è nel **Caratteristiche condivise di** sezione del programma di installazione. Non installare altri componenti.
  >
  > Preferibilmente, non installare il server in un computer in cui è stati installati SQL Server R Services o i servizi di SQL Server Machine Learning.

+ Usa le opzioni della riga di comando per l'installazione di SQL Server

  [Installare Microsoft R Server dalla riga di comando](../r/install-microsoft-r-server-from-the-command-line.md)

  Installazione di SQL Server supporta le installazioni automatiche tramite un'ampia gamma di argomenti della riga di comando.

+ Utilizzare il programma di installazione autonomo

  [Eseguire Microsoft R Server per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).

  È ora possibile utilizzare un nuovo programma di installazione di Windows per configurare una nuova istanza di Microsoft R Server o Server di Microsoft Machine Learning.  Microsoft R Server (e i Server di Microsoft Machine Learning) richiedono un contratto Enterprise di SQL Server. Tuttavia, dopo aver eseguito il programma di installazione autonomo, criteri di supporto per un'installazione esistente viene aggiornato, per usare i nuovi criteri del ciclo di vita moderna. Questa opzione di supporto garantisce che gli aggiornamenti ai componenti di machine learning sono applicati più frequentemente di quanto sarebbero quando si utilizzano le versioni del servizio SQL Server.

  
+ Aggiornare un'istanza di SQL Server

  [Utilizzo di SqlBindR per aggiornare un'istanza di R Services](./use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).
  
  È possibile utilizzare il programma di installazione autonomo per aggiornare un'istanza di SQL Server 2016 R Services di utilizzare la versione più recente di R. Quando si esegue il programma di installazione, i criteri di supporto del ciclo di vita moderna verranno applicati al server e i componenti di R otterrà gli aggiornamenti più frequenti.
  
  > [! Nota} attualmente questo metodo di aggiornamento è disponibile solo per le installazioni esistenti di SQL Server 2016. Tuttavia, gli aggiornamenti saranno supportati per SQL Server 2017 in futuro.

## <a name="related-machine-learning-products"></a>Apprendimento prodotti correlato

+ Macchine virtuali di Azure con R Server

  [Eseguire il provisioning di una macchina virtuale di R Server](../../advanced-analytics/r-services/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace include più immagini di macchine virtuali che includono R Server. Creazione di una nuova macchina virtuale R Server in Microsoft Azure è il modo più rapido per configurare un server da utilizzare per lo sviluppo e distribuzione di modelli predittivi. Le immagini sono dotati di funzionalità per la scalabilità e la condivisione è già configurato, che rende più semplice per incorporare analitica R all'interno delle applicazioni e integrare R con i sistemi back-end.

+ Macchina virtuale di analisi scientifica dei dati

  [Macchina virtuale di analisi scientifica dei dati - Windows 2016 Preview](http://aka.ms/dsvm/win2016)

  La versione più recente della macchina virtuale di analisi scientifica dei dati include R Server, SQL Server, e una matrice degli strumenti più comuni per machine learning, tutti preinstallato e testato. Creare server Jupyter notebook, lo sviluppo di soluzioni in Julia e utilizzare le librerie di formazione abilitato GPU come MXNet, CNTK e TensorFlow.

## <a name="resources"></a>Risorse

Per esempi, esercitazioni e altre informazioni su Microsoft R Server, vedere [prodotti di Microsoft R](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started).

## <a name="see-also"></a>Vedere anche

 [SQL Server R Services](../../advanced-analytics/r/sql-server-r-services.md)

