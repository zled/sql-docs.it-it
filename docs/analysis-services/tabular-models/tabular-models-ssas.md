---
title: I modelli tabulari | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e85a618379b5b3c6da010c8b25782ed6836edb4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="tabular-models"></a>Modelli tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  I modelli tabulari sono database di Analysis Services eseguiti in memoria in o in modalità DirectQuery, che accedono ai dati direttamente dalle origini dati relazionali di back-end. Tramite il processore di query multithreading e algoritmi di compressione dell'arte, il motore analitica offre accesso rapido ai dati e agli oggetti modello tabulare segnalando applicazioni client quali Power BI ed Excel.  
  
 Mentre i modelli in memoria sono l'impostazione predefinita, DirectQuery è una modalità di query alternative per i modelli che possono essere troppo grande per essere contenuto in memoria o volatilità dei dati preclude una strategia di elaborazione ragionevole. DirectQuery offre parità con i modelli in memoria tramite il supporto per una vasta gamma di origini dati, capacità di gestire le tabelle calcolate e colonne in un modello DirectQuery, sicurezza a livello di riga tramite espressioni DAX che raggiungono il database back-end ed eseguire una query ottimizzazioni comportano una velocità effettiva.
  
 I modelli tabulari vengono creati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando il modello di progetto di modello tabulare che fornisce un'area di progettazione per la creazione di un modello, tabelle, relazioni e le espressioni DAX. È possibile importare i dati da più origini e migliorare il modello aggiungendo relazioni, tabelle colonne calcolate, misure, indicatori KPI, gerarchie e traduzioni.  
  
 I modelli possono quindi essere distribuiti in Azure Analysis Services o un'istanza di SQL Server Analysis Services configurata per la modalità server tabulare. I modelli tabulari distribuiti possono essere gestiti in SQL Server Management Studio. Man mano che i modelli, possono essere partizionati per elaborazioni ottimizzate e protetti a livello di riga tramite la sicurezza basata sui ruoli.  

  
  
