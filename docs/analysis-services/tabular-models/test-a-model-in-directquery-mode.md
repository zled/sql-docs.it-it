---
title: "Test di un modello in modalità DirectQuery | Documenti Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71352e3066d7964ad6e795563d049368285c79e8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="test-a-model-in-directquery-mode"></a>Testare un modello in modalità DirectQuery

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Rivedere le opzioni per il test di un modello tabulare in modalità DirectQuery in ogni fase dello sviluppo, a partire dalla progettazione.  
  
## <a name="test-in-excel"></a>Testare in Excel 
  
 Quando si progetta il modello in SSDT, è possibile usare la funzionalità **Analizza in Excel** per testare le decisioni di modellazione su un set di dati di esempio in memoria o sul database relazionale.  Quando si fa clic su Analizza in Excel, viene visualizzata una finestra di dialogo in cui è possibile specificare opzioni.
 
 ![Opzioni DirectQuery di Analizza in Excel](../../analysis-services/tabular-models/media/analyze-in-excel-directquery-options.png)
 
 Se la modalità DirectQuery del modello è attiva, è possibile specificare la modalità di connessione DirectQuery, in cui sono disponibili due opzioni:
 - **Visualizzazione dati di esempio** : con questa opzione le query provenienti da Excel vengono indirizzate a partizioni di esempio contenenti un set di dati di esempio in memoria. Questa opzione è utile quando si vuole verificare che qualsiasi formula DAX presente nelle misure, nelle colonne calcolate o nella sicurezza a livello di riga possa essere eseguita correttamente.
 
 - **Visualizzazione dati completa** : con questa opzione le query provenienti da Excel vengono inviate ad Analysis Services e quindi al database relazionale. Questa opzione è, in effetti, completamente funzionante in modalità DirecQuery.
 
 ### <a name="other-clients"></a>Altri client
 Quando si usa Analizza in Excel, viene creato un file di connessione con estensione odc. È possibile usare le informazioni sulla stringa di connessione di questo file per connettersi al modello da altre applicazioni client. Viene aggiunto un parametro aggiuntivo, DataView=Sample, per specificare che il client deve connettersi alle partizioni dati di esempio.  
  
## <a name="monitor-query-execution-on-backend-systems-using-xevents-or-sql-profiler"></a>Monitorare l'esecuzione delle query sui sistemi back-end usando xEvents o SQL Profiler 
 Avviare una traccia della sessione, connessa al database relazionale di SQL Server, per monitorare le connessioni provenienti dal modello tabulare:  
  
-   [Monitorare Analysis Services con eventi estesi di SQL Server](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
-   [Utilizzare SQL Server Profiler per il monitoraggio di Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 Se si utilizza Oracle o Teradata, usare gli strumenti di monitoraggio della traccia.  
  
  
