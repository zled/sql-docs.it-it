---
title: Sviluppo con ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 794692334fdee4d3cbc87fc9ccf1c2313dcc1262
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34025050"
---
# <a name="developing-with-adomdnet"></a>Sviluppo con ADOMD.NET
  ADOMD.NET è un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] provider di dati .NET Framework è progettato per comunicare con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. ADOMD.NET utilizza il protocollo XML for Analysis per comunicare con le origini dati analitici tramite connessioni TCP/IP o HTTP per trasmettere e ricevere richieste e risposte SOAP conformi con la specifica XML for Analysis. I comandi possono essere inviati nel linguaggio MDX (Multidimensional Expressions), DMX (Data Mining Extensions) o ASSL (Analysis Services Scripting Language) o anche tramite una sintassi limitata di SQL e possono anche non restituire alcun risultato. Sui dati analitici, sugli indicatori di prestazioni chiave (KPI) e sui modelli di data mining possono essere eseguite query e possono essere apportate modifiche tramite il modello a oggetti ADOMD.NET. Tramite ADOMD.NET, è possibile inoltre visualizzare e utilizzare i metadati recuperando set di righe dello schema conformi a OLE DB o tramite il modello a oggetti ADOMD.NET.  
  
 Il provider di dati ADOMD.NET è rappresentato dal **Microsoft.AnalysisServices.AdomdClient** dello spazio dei nomi.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Programmazione di client ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)|Descrive come utilizzare gli oggetti client ADOMD.NET per recuperare dati e metadati dalle origini dati analitici.|  
|[Programmazione di server ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)|Descrive come utilizzare gli oggetti server ADOMD.NET per creare stored procedure e funzioni definite dall'utente.|  
|[Ridistribuzione di ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/redistributing-adomd-net.md)|Descrive il processo di ridistribuzione di ADOMD.NET.|  
|<xref:Microsoft.AnalysisServices.AdomdClient>|Gli oggetti contenuti in dettaglio il **Microsoft.AnalysisServices.AdomdClient** dello spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni MDX & #40; MDX & #41; Riferimento](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento](../../../dmx/data-mining-extensions-dmx-reference.md)   
 [Set di righe dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [L'accesso ai dati di modello multidimensionale &#40;Analysis Services - dati multidimensionali&#41;](../../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)  
  
  
