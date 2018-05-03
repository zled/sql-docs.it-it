---
title: 'Lezione 8: Definizione di azioni | Documenti Microsoft'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0a7c280b5473873c51345cc203dccbae6b5c198c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-8-defining-actions"></a>Lezione 8: Definizione di azioni
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

In questa lezione verranno descritte le procedure per definire le azioni del progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Un'azione è semplicemente un'istruzione MDX (Multidimensional Expressions) archiviata in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , che può essere incorporata in applicazioni client e avviata da un utente.  
  
> [!NOTE]  
> I progetti completati per tutte le lezioni in questa esercitazione sono disponibili online. È possibile passare a qualsiasi lezione utilizzando il progetto completato della lezione precedente come punto iniziale. [Fare clic qui](http://go.microsoft.com/fwlink/?LinkID=221866) per scaricare i progetti di esempio usati in questa esercitazione.  
  
Nella tabella seguente vengono descritti i tipi di azioni supportati da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
|||  
|-|-|  
|CommandLine|Esegue un comando al prompt dei comandi|  
|Set di dati|Restituisce un set di dati a un'applicazione client.|  
|Drill-through|Restituisce un'istruzione drill-through come un'espressione che viene eseguita dal client per restituire un set di righe|  
|Html|Esegue uno script HTML in un browser Internet|  
|Proprietario|Esegue un'operazione utilizzando un'interfaccia diversa da quelle elencate in questa tabella.|  
|Report|Invia una richiesta con parametri basata sull'URL a un server di report e restituisce un report a un'applicazione client.|  
|Set di righe|Restituisce un set di righe a un'applicazione client.|  
|Istruzione|Esegue un comando OLE DB.|  
|URL|Visualizza una pagina Web dinamica in un browser Internet|  
  
Le azioni consentono agli utenti di avviare un'applicazione o di eseguire altre procedure nell'ambito di un elemento selezionato. Per altre informazioni, vedere [Azioni &#40;Analysis Services - Dati multidimensionali&#41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md), [Azioni nei modelli multidimensionali](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
> [!NOTE]  
> Per ulteriori esempi di azioni, vedere quelli disponibili nella scheda Modelli nel riquadro Strumenti di calcolo oppure nel data warehouse di esempio [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW. Per altre informazioni sull'installazione di questo database, vedere [Installare dati di esempio e progetti per l'esercitazione di modellazione multidimensionale di Analysis Services](../analysis-services/install-sample-data-and-projects.md).  
  
Questa lezione include gli argomenti seguenti:  
  
[Definizione e utilizzo di un'azione drill-through](../analysis-services/lesson-8-1-defining-and-using-a-drillthrough-action.md)  
In questa procedura viene definita, utilizzata e utilizzerà e quindi modificata un'azione drill-through tramite la relazione di tipo Fatti citata precedentemente in questa esercitazione.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 9: Definizione di prospettive e traduzioni](../analysis-services/lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Vedere anche  
[Scenario di Analysis Services Tutorial](../analysis-services/analysis-services-tutorial-scenario.md)  
[Modellazione multidimensionale &#40;esercitazione di AdventureWorks&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[Azioni & #40; Analysis Services - dati multidimensionali & #41;](../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[Azioni nei modelli multidimensionali](../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  
