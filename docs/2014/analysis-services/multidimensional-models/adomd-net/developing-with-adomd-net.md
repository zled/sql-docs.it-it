---
title: Sviluppo con ADOMD.NET | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET
ms.assetid: abaf33aa-db55-43bf-8f30-15547559be1d
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1dfdd10ae488633812b61e2a0220f7c22e65e575
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070156"
---
# <a name="developing-with-adomdnet"></a>Sviluppo con ADOMD.NET
  ADOMD.NET è un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] provider di dati .NET Framework è progettato per comunicare con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. ADOMD.NET utilizza il protocollo XML for Analysis per comunicare con le origini dati analitici tramite connessioni TCP/IP o HTTP per trasmettere e ricevere richieste e risposte SOAP conformi con la specifica XML for Analysis. I comandi possono essere inviati nel linguaggio MDX (Multidimensional Expressions), DMX (Data Mining Extensions) o ASSL (Analysis Services Scripting Language) o anche tramite una sintassi limitata di SQL e possono anche non restituire alcun risultato. Sui dati analitici, sugli indicatori di prestazioni chiave (KPI) e sui modelli di data mining possono essere eseguite query e possono essere apportate modifiche tramite il modello a oggetti ADOMD.NET. Tramite ADOMD.NET, è possibile inoltre visualizzare e utilizzare i metadati recuperando set di righe dello schema conformi a OLE DB o tramite il modello a oggetti ADOMD.NET.  
  
 Il provider di dati ADOMD.NET viene rappresentato dal `Microsoft.AnalysisServices.AdomdClient` dello spazio dei nomi.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Programmazione di client ADOMD.NET](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|Descrive come utilizzare gli oggetti client ADOMD.NET per recuperare dati e metadati dalle origini dati analitici.|  
|[Programmazione di server ADOMD.NET](../../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|Descrive come utilizzare gli oggetti server ADOMD.NET per creare stored procedure e funzioni definite dall'utente.|  
|[Ridistribuzione di ADOMD.NET](redistributing-adomd-net.md)|Descrive il processo di ridistribuzione di ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|Illustra in dettaglio gli oggetti contenuti nello spazio dei nomi `Microsoft.AnalysisServices.AdomdClient`.|  
  
## <a name="see-also"></a>Vedere anche  
 [(Multidimensional Expressions) &#40;MDX&#41; riferimento](/sql/mdx/multidimensional-expressions-mdx-reference)   
 [Estensioni Data Mining &#40;DMX&#41; riferimento](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Set di righe dello Schema di Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [L'accesso ai dati di modello multidimensionale &#40;Analysis Services - dati multidimensionali&#41;](../mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
