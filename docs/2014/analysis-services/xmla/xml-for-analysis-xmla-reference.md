---
title: XML for Analysis (XMLA) riferimento | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32093211db376a156c456d4f769f78bcc1135ceb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055061"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) riferimento
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizza il protocollo XML for Analysis (XMLA) per gestire tutte le comunicazioni tra applicazioni client e un'istanza di Analysis Services. Al livello più elementare, altre librerie client quali ADOMD.NET e AMO costruiscono richieste e decodificano risposte in XMLA, fungendo da intermediari a un'istanza di Analysis Services, che utilizza XMLA in modo esclusivo.  
  
 Per supportare l'individuazione e la manipolazione dei dati in formato multidimensionale e tabulare, la specifica XMLA definisce due metodi generalmente accessibili, [Discover](xml-elements-methods-discover.md) e [Execute](xml-elements-methods-execute.md)e un raccolta di tipi di dati ed elementi XML. Poiché XML consente un'architettura server e client a regime di controllo libero, entrambi metodi gestiscono le informazioni in ingresso e in uscita in formato XML. Analysis Services è conforme alla specifica XMLA 1.1 ma la estende anche per includere la funzionalità di definizione e manipolazione dei dati, implementata sotto forma di annotazioni sui metodi `Discover` e `Execute`. La sintassi XML estesa viene denominata ASSL (Analysis Services Scripting Language). ASSL si compila sulla specifica XMLA senza interromperla. L'interoperabilità basata su XMLA è assicurata sia che si utilizzi solo XMLA, sia che si utilizzino XMLA e ASSL insieme.  
  
 Come programmatore, è possibile utilizzare XMLA come interfaccia di programmazione se nei requisiti della soluzione sono specificati protocolli standard, quali XML, SOAP e HTTP. Programmatori e amministratori possono utilizzare XMLA anche su base a hoc per recuperare informazioni dal server o eseguire comandi.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Elementi XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)|Descrive gli elementi nella specifica XMLA.|  
|[Tipi di dati XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)|Descrive i tipi di dati nella specifica XMLA.|  
|[XML for Analysis conformità &#40;XMLA&#41;](xml-for-analysis-compliance-xmla.md)|Descrive il livello di conformità con la specifica XMLA 1.1.|  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML per set di righe dello schema di analisi](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Sviluppo con ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Sviluppo con Analysis Management Objects &#40;AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'architettura Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  