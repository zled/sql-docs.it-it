---
title: I modelli tabulari | Documenti Microsoft
ms.custom: 
ms.date: 01/29/2018
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
ms.openlocfilehash: edeea89c1d767364f4f087d0f4b2e6d566895c52
ms.sourcegitcommit: c77a8ac1ab372927c09bf241d486e96881b61ac9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="tabular-models"></a>Modelli tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]I modelli tabulari sono database di Analysis Services eseguiti in memoria o in modalità DirectQuery, accesso ai dati direttamente da origini dati relazionali di back-end.  
  
 Il valore predefinito è in memoria. Utilizzando un processore di query multithreading e algoritmi di compressione avanzati di, il motore analitica offre accesso rapido ai dati e agli oggetti modello tabulare da applicazioni di reporting client quali Power BI ed Excel.  
  
 DirectQuery è una modalità di query alternativa usata per i modelli che sono troppo grandi per rientrare nella memoria o quando la volatilità dei dati preclude una strategia di elaborazione ragionevole. In questa versione, DirectQuery offre maggiore parità con i modelli in memoria attraverso il supporto di altre origini dati, la capacità di gestire tabelle e colonne calcolate in un modello DirectQuery, la sicurezza a livello di riga con espressioni DAX che raggiungono il database back-end e le ottimizzazioni delle query che comportano una velocità effettiva maggiore rispetto alle versioni precedenti.
  
 I modelli tabulari vengono creati [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando il modello di progetto di modello tabulare che offre un'area di progettazione per la creazione di un modello, tabelle, relazioni ed espressioni DAX. È possibile importare i dati da più origini e migliorare il modello aggiungendo relazioni, tabelle colonne calcolate, misure, indicatori KPI, gerarchie e traduzioni.  
  
 I modelli possono quindi essere distribuiti in Azure Analysis Services o un'istanza di SQL Server Analysis Services configurata per la modalità server tabulare. I modelli tabulari distribuiti possono essere gestiti in SQL Server Management Studio solo come modelli multidimensionali. Tali modelli, inoltre, possono essere partizionati per elaborazioni ottimizzate e protetti a livello di riga tramite ruoli basati sulla sicurezza.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Soluzioni di modelli tabulari](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) -argomenti di questa sezione descrivono la creazione e la distribuzione di soluzioni di modelli tabulari.
  
 [Database modello tabulare](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) -argomenti in questa sezione viene descritto come gestire soluzioni di modello tabulare distribuito.
  
 [Accesso ai dati di modello tabulare](../../analysis-services/tabular-models/tabular-model-data-access.md) -in questa sezione vengono illustrate le connessione distribuire soluzioni di modelli tabulari.
  
## <a name="see-also"></a>Vedere anche  
 [Novità di Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Confronto tra soluzioni tabulari e multidimensionali](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Strumenti e applicazioni usate in Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Modalità DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
