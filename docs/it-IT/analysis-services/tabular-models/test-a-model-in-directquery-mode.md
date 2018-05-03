---
title: Test di un modello in modalità DirectQuery | Documenti Microsoft
ms.custom: ''
ms.date: 07/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 11260792-ff8b-4d0e-b845-ca210dd3fced
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b4663cf910a776fd7ce87005b604a2782377b041
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="test-a-model-in-directquery-mode"></a>Test di un modello in modalità DirectQuery
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
-   [Utilizzare SQL Server Profiler per monitorare Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 Se si utilizza Oracle o Teradata, usare gli strumenti di monitoraggio della traccia.  
  
  
