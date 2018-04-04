---
title: I modelli tabulari | Documenti Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 54cd62aa50aff198d2397843c528f09a1a2fc83b
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="tabular-models"></a>Modelli tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  I modelli tabulari sono database di Analysis Services eseguiti in memoria in o in modalità DirectQuery, che accedono ai dati direttamente dalle origini dati relazionali di back-end. Tramite il processore di query multithreading e algoritmi di compressione dell'arte, il motore analitica offre accesso rapido ai dati e agli oggetti modello tabulare segnalando applicazioni client quali Power BI ed Excel.  
  
 Mentre i modelli in memoria sono l'impostazione predefinita, DirectQuery è una modalità di query alternative per i modelli che possono essere troppo grande per essere contenuto in memoria o volatilità dei dati preclude una strategia di elaborazione ragionevole. DirectQuery offre parità con i modelli in memoria tramite il supporto per una vasta gamma di origini dati, capacità di gestire le tabelle calcolate e colonne in un modello DirectQuery, sicurezza a livello di riga tramite espressioni DAX che raggiungono il database back-end ed eseguire una query ottimizzazioni comportano una velocità effettiva.
  
 I modelli tabulari vengono creati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando il modello di progetto di modello tabulare che fornisce un'area di progettazione per la creazione di un modello, tabelle, relazioni e le espressioni DAX. È possibile importare i dati da più origini e migliorare il modello aggiungendo relazioni, tabelle colonne calcolate, misure, indicatori KPI, gerarchie e traduzioni.  
  
 I modelli possono quindi essere distribuiti in Azure Analysis Services o un'istanza di SQL Server Analysis Services configurata per la modalità server tabulare. I modelli tabulari distribuiti possono essere gestiti in SQL Server Management Studio. Man mano che i modelli, possono essere partizionati per elaborazioni ottimizzate e protetti a livello di riga tramite la sicurezza basata sui ruoli.  

  
  
