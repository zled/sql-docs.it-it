---
title: Programmazione di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bf88386fe9846ba1fee17f840a11ab635c050d01
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-programming"></a>Programmazione di data mining
  Se gli strumenti e i visualizzatori predefiniti disponibili in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] non soddisfano i propri requisiti, è possibile estendere le funzionalità di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] mediante la codifica di estensioni personalizzate. Questo approccio rende disponibili due opzioni:  
  
-   **XMLA**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]supporta XML for Analysis (XMLA) come protocollo per la comunicazione con applicazioni client. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta comandi aggiuntivi che estendono la specifica XML for Analysis.  
  
     Poiché [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizza XMLA per la definizione dei dati, la manipolazione dei dati e il supporto del controllo dei dati, è possibile creare strutture di data mining e modelli di data mining tramite gli strumenti visivi forniti da [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], quindi estendere gli oggetti di data mining creati tramite script DMX (Data Mining Extensions) e ASSL (Analysis Services Scripting Language).  
  
     È possibile creare e modificare completamente oggetti di data mining negli script XMLA ed eseguire query di stima sui modelli a livello di codice dalle applicazioni personalizzate.  
  
-   **Analysis Management Objects (AMO)**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] include inoltre un framework completo che consente ai provider di data mining di terze parti di integrare gli oggetti di data mining in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
     È possibile creare le strutture e i modelli di data mining tramite AMO. Vedere gli esempi seguenti in CodePlex:  
  
    -   Visualizzatore AMO  
  
         Si connette all'istanza di SSAS specificata e restituisce un elenco di tutti gli oggetti server e delle relative proprietà, inclusa la struttura di data mining e i modelli di data mining.  
  
    -   AMO Simple Sample  
  
         AS Simple Sample illustra l'accesso a livello di codice alla maggior parte degli oggetti principali e dimostra la visualizzazione dei metadati e l'accesso ai valori negli oggetti.  
  
         L'esempio illustra inoltre come creare ed elaborare una struttura e un modello di data mining, nonché sfogliare un modello di data mining esistente.  
  
-   **DMX**  
  
     È possibile utilizzare DMX per incapsulare istruzioni di comando, query di stima e query sui metadati e per restituire i risultati in un formato tabulare, presupponendo che sia stata creata una connessione a un server [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [OLE DB per Data Mining](../analysis-services/data-mining-programming-ole-db.md)  
 Vengono descritte le aggiunte alla specifica per il supporto di data mining e dati multidimensionali, ovvero nuovi set di righe e colonne dello schema e linguaggio DMX (Data Mining Extensions) per la creazione e la gestione di strutture di data mining.  
  
## <a name="related-reference"></a>Riferimenti correlati  
 [Sviluppo con ADOMD.NET](../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 Viene fornita un'introduzione agli oggetti di programmazione client e server ADOMD.NET.  
  
 [Lo sviluppo con Analysis Management Objects &#40; AMO &#41;](../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
 Viene fornita un'introduzione alla libreria di programmazione AMO.  
  
 [Lo sviluppo con Analysis Services Scripting Language &#40; ASSL &#41;](../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Viene fornita un'introduzione a XML for Analysis (XMLA) e alle relative estensioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione per gli sviluppatori di Analysis Services](../analysis-services/analysis-services-developer-documentation.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)  
  
  

