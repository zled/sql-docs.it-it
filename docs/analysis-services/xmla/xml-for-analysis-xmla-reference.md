---
title: XML for Analysis (XMLA) riferimento | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c85218c4cf2bdbd20db1f45b46efe9dd677dfea4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) riferimento
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizza il protocollo XML for Analysis (XMLA) per gestire tutte le comunicazioni tra applicazioni client e un'istanza di Analysis Services. Al livello più elementare, altre librerie client quali ADOMD.NET e AMO costruiscono richieste e decodificano risposte in XMLA, fungendo da intermediari a un'istanza di Analysis Services, che utilizza XMLA in modo esclusivo.  
  
 Per supportare l'individuazione e la manipolazione dei dati in formato multidimensionale e tabulare, la specifica XMLA definisce due metodi generalmente accessibili, [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) e [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)e un raccolta di tipi di dati ed elementi XML. Poiché XML consente un'architettura server e client a regime di controllo libero, entrambi metodi gestiscono le informazioni in ingresso e in uscita in formato XML. Analysis Services è conforme alla specifica XMLA 1.1 specifica, ma estende in modo da includere funzionalità di definizione e modifica dati, implementato come annotazioni sul **Discover** e **Execute** metodi. La sintassi XML estesa viene denominata ASSL (Analysis Services Scripting Language). ASSL si compila sulla specifica XMLA senza interromperla. L'interoperabilità basata su XMLA è assicurata sia che si utilizzi solo XMLA, sia che si utilizzino XMLA e ASSL insieme.  
  
 Come programmatore, è possibile utilizzare XMLA come interfaccia di programmazione se nei requisiti della soluzione sono specificati protocolli standard, quali XML, SOAP e HTTP. Programmatori e amministratori possono utilizzare XMLA anche su base a hoc per recuperare informazioni dal server o eseguire comandi.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|Descrive gli elementi nella specifica XMLA.|  
|[Tipi di dati XML &#40; XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Descrive i tipi di dati nella specifica XMLA.|  
|[XML for Analysis conformità &#40; XMLA &#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Descrive il livello di conformità con la specifica XMLA 1.1.|  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML for Analysis i rowset dello Schema](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Sviluppo con ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Sviluppo con Analysis Management Objects &#40;AMO&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'architettura Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  

