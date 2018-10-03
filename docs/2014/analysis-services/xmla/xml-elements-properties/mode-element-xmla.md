---
title: Elemento Mode (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Mode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Mode
- microsoft.xml.analysis.mode
- http://schemas.microsoft.com/analysisservices/2003/engine#Mode
helpviewer_keywords:
- Mode element
ms.assetid: 43a54181-6494-48c3-b14b-376d8939fa9f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e768d9ef176a05d4fe7622a520c9ac98f1d71d81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072411"
---
# <a name="mode-element-xmla"></a>Elemento Mode (XMLA)
  Identifica la modalità da utilizzare dall'elemento padre [blocco](../xml-elements-commands/lock-element-xmla.md) elemento durante la creazione di un blocco su un oggetto specificato.  
  
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
|Elementi padre|[Lock](../xml-elements-commands/lock-element-xmla.md), [sblocco](../xml-elements-commands/unlock-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento padre `Lock` utilizza l'elemento `Mode` per determinare il tipo di blocco da creare su un oggetto. Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*CommitShared*|Sull'oggetto specificato viene stabilito un blocco condiviso. Per lo stesso oggetto è possibile creare altri blocchi condivisi.<br /><br /> Un blocco condiviso impedisce alle transazioni contenenti operazioni di scrittura, ad esempio un [Execute](../xml-elements-methods-execute.md) chiamata al metodo che esegue un' [Alter](../xml-elements-commands/alter-element-xmla.md) comando, in un oggetto specificato, eseguire il commit finché non viene rimosso il blocco condiviso. Un blocco condiviso impedisce alle transazioni contenenti operazioni di lettura, ad esempio un [Discover](../xml-elements-methods-discover.md) chiamata al metodo o un' `Execute` chiamata al metodo che esegue una [istruzione](../xml-elements-commands/statement-element-xmla.md) comando, eseguire il commit.|  
|*CommitExclusive*|Sull'oggetto specificato viene stabilito un blocco esclusivo. Per lo stesso oggetto non è possibile creare altri blocchi condivisi o esclusivi.<br /><br /> Un blocco esclusivo impedisce alle transazioni contenenti operazioni di lettura o scrittura su un oggetto specificato l'esecuzione del commit fino alla rimozione del blocco esclusivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ID &#40;XMLA&#41;](id-element-xmla.md)   
 [Elemento dell'oggetto &#40;XMLA&#41;](object-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
