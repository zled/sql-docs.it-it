---
title: XML for Analysis (XMLA) riferimento | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e8c3645175d8d1f3251fd621825f5a542669cbb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576763"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) riferimento
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]   

Azure Analysis Services e SQL Server Analysis Services usare XML per il protocollo Analysis (XMLA) per le comunicazioni tra applicazioni client e un'istanza di Analysis Services. Al livello più elementare, altre librerie client quali ADOMD.NET e AMO costruiscono richieste e decodificano risposte in XMLA, fungendo da intermediari a un'istanza di Analysis Services, che utilizza XMLA in modo esclusivo.  
  
 Per supportare l'individuazione e la manipolazione dei dati in modalità tabulare e multidimensionale, la specifica XMLA sono definiti due metodi generalmente accessibili, [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) e [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)e un raccolta di tipi di dati ed elementi XML. Poiché XML consente un'architettura server e client a regime di controllo libero, entrambi metodi gestiscono le informazioni in ingresso e in uscita in formato XML. 

Analysis Services è conforme alla specifica XMLA 1.1 specifica, ma estende in modo da includere funzionalità di definizione e modifica dati, implementato come annotazioni sul **Discover** e **Execute** metodi. La sintassi XML estese sono Tabular Model Scripting Language (TMSL) e Analysis Services Scripting Language (ASSL). 

TMSL è riportata la sintassi di definizione del modello di comando e oggetti per i database modello tabulare a livello di compatibilità 1200 e versioni successiva. TMSL comunica con Analysis Services tramite il protocollo XMLA, in cui il `XMLA.Execute` accetta entrambi gli script basati su JSON istruzione in linguaggio TMSL, nonché gli script tradizionale basato su XML in Analysis Services Scripting Language (ASSL per XMLA). Per altre informazioni, vedere [riferimento Tabular Model Scripting Language (TMSL)](../tabular-model-scripting-language-tmsl-reference.md).

ASSL è riportata la sintassi di definizione del modello di comando e oggetti per i database modello multidimensionale e i database in modalità tabulare con livello di compatibilità 1103 o inferiore. Questa definizione compila sulla specifica XMLA senza interromperla. L'interoperabilità basata su XMLA è assicurata sia che si utilizzi solo XMLA, sia che si utilizzino XMLA e ASSL insieme. Per altre informazioni, vedere [Analysis Services Scripting Language (ASSL per XMLA)](../scripting/analysis-services-scripting-language-assl-for-xmla.md).
  
 Gli sviluppatori, è possibile utilizzare XMLA come interfaccia, se i requisiti della soluzione sono specificati protocolli standard, ad esempio XML, SOAP e HTTP. Gli sviluppatori e amministratori possono inoltre utilizzare XMLA in base ad hoc per recuperare informazioni dal server o eseguire i comandi. 
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Tipi di dati XML (XMLA)](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Descrive i tipi di dati nella specifica XMLA.|  
|[Elementi XML - comandi (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Elementi che possono essere usati all'interno dell'elemento di comando durante una chiamata al metodo Execute.|  
|[Elementi XML - comandi (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Elementi che possono essere usati all'interno dell'elemento di comando durante una chiamata al metodo Execute.|  
|[Elementi XML - intestazioni (XMLA)](../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)| Elementi di intestazione implementati da Microsoft Analysis Services.|  
|[Elementi XML - proprietà (XMLA)](../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)| Elementi per rappresentare le informazioni sulle proprietà e valori per i tipi di intestazioni, metodi, oggetti, comandi e dati XMLA.|  
|[Elementi XML - metodi - individuare (XMLA)](../../analysis-services/xmla/xml-elements-methods-discover.md)| Recupera informazioni, ad esempio l'elenco dei database disponibili o i dettagli su un oggetto specifico da un'istanza di Analysis Services.|  
|[Elementi XML - metodi - esecuzione (XMLA)](../../analysis-services/xmla/xml-elements-methods-execute.md)| Invia XML per i comandi Analysis (XMLA) a un'istanza di Analysis Services.|  
|[XML elementi - oggetti - DiscoverResponse (XMLA)](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)| Contiene le informazioni restituite da un'istanza di Analysis Services in risposta a una chiamata al metodo Discover.|  
|[XML elementi - oggetti - ExecuteResponse (XMLA)](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)| Contiene le informazioni restituite da un'istanza di Analysis Services in risposta a una chiamata al metodo Execute.|  
|[Elementi XML - oggetti (XMLA)](../../analysis-services/xmla/xml-elements-objects.md)| Oggetti implementati da Analysis Services.|  
|[XML for Analysis Compliance (XMLA)](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Descrive il livello di conformità con la specifica XMLA 1.1.|  
  
## <a name="see-also"></a>Vedere anche
 [XML per set di righe dello schema di analisi](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
 [Sviluppo con ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 [Sviluppo con Analysis Management Objects &#40;AMO&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
