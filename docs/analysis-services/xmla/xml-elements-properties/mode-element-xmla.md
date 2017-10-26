---
title: Elemento Mode (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Mode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57c3450e8928b24dc03e2d5915983f39330d0b0c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mode-element-xmla"></a>Elemento Mode (XMLA)
  Identifica la modalità da utilizzare dall'elemento padre [blocco](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) elemento durante la creazione di un blocco su un oggetto specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Blocco](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [sbloccare](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento padre **blocco** elemento utilizza il **modalità** elemento per determinare il tipo di blocco per creare un oggetto. Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*CommitShared*|Sull'oggetto specificato viene stabilito un blocco condiviso. Per lo stesso oggetto è possibile creare altri blocchi condivisi.<br /><br /> Un blocco condiviso impedisce alle transazioni contenenti operazioni di scrittura, ad esempio un [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo in esecuzione un [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comando, un oggetto specificato, eseguire il commit finché non viene rimosso il blocco condiviso. Un blocco condiviso impedisce alle transazioni contenenti operazioni di lettura, ad esempio un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) chiamata al metodo o un **Execute** chiamata al metodo in esecuzione un [istruzione](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando, eseguire il commit.|  
|*CommitExclusive*|Sull'oggetto specificato viene stabilito un blocco esclusivo. Per lo stesso oggetto non è possibile creare altri blocchi condivisi o esclusivi.<br /><br /> Un blocco esclusivo impedisce alle transazioni contenenti operazioni di lettura o scrittura su un oggetto specificato l'esecuzione del commit fino alla rimozione del blocco esclusivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [ID elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Oggetto elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

