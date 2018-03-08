---
title: Elemento Mode (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Mode Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords: Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 656ea9623b7dea8296bc10221c916fe7afdd0568
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mode-element-xmla"></a>Elemento Mode (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Identifica la modalità da utilizzare dall'elemento padre [blocco](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) elemento durante la creazione di un blocco su un oggetto specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Lock>  
   ...  
   <Mode>...</Mode>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Blocco](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [sbloccare](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento padre **blocco** elemento utilizza il **modalità** elemento per determinare il tipo di blocco per creare un oggetto. Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*CommitShared*|Sull'oggetto specificato viene stabilito un blocco condiviso. Per lo stesso oggetto è possibile creare altri blocchi condivisi.<br /><br /> Un blocco condiviso impedisce alle transazioni contenenti operazioni di scrittura, ad esempio un [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo in esecuzione un [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comando, un oggetto specificato, eseguire il commit finché non viene rimosso il blocco condiviso. Un blocco condiviso impedisce alle transazioni contenenti operazioni di lettura, ad esempio un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) chiamata al metodo o un **Execute** chiamata al metodo in esecuzione un [istruzione](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando, eseguire il commit.|  
|*CommitExclusive*|Sull'oggetto specificato viene stabilito un blocco esclusivo. Per lo stesso oggetto non è possibile creare altri blocchi condivisi o esclusivi.<br /><br /> Un blocco esclusivo impedisce alle transazioni contenenti operazioni di lettura o scrittura su un oggetto specificato l'esecuzione del commit fino alla rimozione del blocco esclusivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [ID elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Oggetto elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
