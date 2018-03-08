---
title: I modelli tabulari | Documenti Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 2df607b47e4bb2a5a770e27d1bceb5a6d7e6ebbc
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-models"></a>Modelli tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
I modelli tabulari sono database di Analysis Services eseguiti in memoria in o in modalità DirectQuery, che accedono ai dati direttamente dalle origini dati relazionali di back-end. Utilizzando gli algoritmi di compressione dell'arte e processore di query a thread multipli, il motore analitica offre accesso rapido ai dati e agli oggetti modello tabulare da applicazioni di reporting client quali Power BI ed Excel.  
  
 Anche se i modelli in memoria sono l'impostazione predefinita, DirectQuery è una modalità di query alternative per i modelli che sono troppo grandi per rientrare nella memoria o volatilità dei dati preclude una strategia di elaborazione ragionevole. DirectQuery offre parità con i modelli in memoria tramite il supporto per una vasta gamma di origini dati, capacità di gestire le tabelle calcolate e colonne in un modello DirectQuery, sicurezza a livello di riga tramite espressioni DAX che raggiungono il database back-end ed eseguire una query ottimizzazioni comportano una velocità effettiva.
  
 I modelli tabulari vengono creati [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando il modello di progetto di modello tabulare che offre un'area di progettazione per la creazione di un modello, tabelle, relazioni ed espressioni DAX. È possibile importare i dati da più origini e migliorare il modello aggiungendo relazioni, tabelle colonne calcolate, misure, indicatori KPI, gerarchie e traduzioni.  
  
 I modelli possono quindi essere distribuiti in Azure Analysis Services o un'istanza di SQL Server Analysis Services configurata per la modalità server tabulare. I modelli tabulari distribuiti possono essere gestiti in SQL Server Management Studio. Con l'aumentare dei modelli, possono essere partizionati per elaborazioni ottimizzate e protetti a livello di riga tramite la sicurezza basata sui ruoli.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Soluzioni di modelli tabulari](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) -articoli in questa sezione descrivono la creazione e la distribuzione di soluzioni di modelli tabulari.
  
 [Database modello tabulare](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) -articoli in questa sezione descrivono la gestione di soluzioni di modelli tabulari distribuiti.
  
 [Accesso ai dati di modello tabulare](../../analysis-services/tabular-models/tabular-model-data-access.md) -articoli in questa sezione descrivono la connessione a soluzioni di modelli tabulari distribuiti.
  
## <a name="see-also"></a>Vedere anche  
 [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Confronto tra soluzioni tabulari e multidimensionali](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Strumenti e applicazioni usate in Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Modalità DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Livello di compatibilità](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
