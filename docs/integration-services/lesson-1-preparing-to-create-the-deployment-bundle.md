---
title: 'Lezione 1: Preparazione alla creazione del pacchetto di distribuzione | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c6f13cd239e51f15ac871b378b70b36a43530d11
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a>Lezione 1: Preparazione alla creazione del pacchetto di distribuzione
In questa lezione verranno illustrate le procedure per creare le cartelle di lavoro e le variabili di ambiente a supporto dell'esercitazione, per creare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , per aggiungere diversi pacchetti e i rispettivi file di supporto al progetto, nonché per implementare le configurazioni nei pacchetti.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consente di distribuire i pacchetti in base a un progetto. Il primo passaggio della creazione del pacchetto di distribuzione consiste pertanto nella raccolta di tutti i pacchetti e delle rispettive dipendenze in un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Risulta spesso utile includere altre informazioni nei pacchetti distribuiti, ad esempio un file Leggimi contenente la documentazione di base relativa al gruppo di pacchetti.  
  
Dopo aver aggiunto i pacchetti e i file, si procederà all'aggiunta delle configurazioni ai pacchetti nei quali non sono ancora utilizzate. Le configurazioni consentono di aggiornare le proprietà dei pacchetti e gli oggetti dei pacchetti in fase di esecuzione. In una lezione successiva si procederà alla modifica dei valori di tali configurazioni durante la distribuzione dei pacchetti allo scopo di supportare i pacchetti nell'ambiente di destinazione della distribuzione.  
  
Dopo aver aggiunto le configurazioni, è consigliabile aprire i pacchetti in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] , ovvero lo strumento grafico di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per la compilazione di pacchetti ETL, ed esaminare le proprietà di pacchetti e relativi elementi, nonché le configurazioni dei pacchetti per acquisire una migliore comprensione delle problematiche correlate alle esigenze di distribuzione. Uno dei pacchetti estrae ad esempio i dati da file di testo. Ai fini della corretta esecuzione dei pacchetti distribuiti, è pertanto necessario che il percorso dei file di dati venga aggiornato.  
  
**Tempo stimato per il completamento della lezione:** 1 ora  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Creazione di cartelle di lavoro e variabili di ambiente](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [Passaggio 2: Creazione del progetto di distribuzione](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [Passaggio 3: Aggiunta di pacchetti e altri file](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [Passaggio 4: Aggiunta delle configurazioni dei pacchetti](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [Passaggio 5: Test dei pacchetti aggiornati](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
[Passaggio 1: Creazione di cartelle di lavoro e variabili di ambiente](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
  
  
