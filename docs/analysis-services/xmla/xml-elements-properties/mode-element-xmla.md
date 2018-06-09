---
title: Elemento Mode (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 12e792c51b2f6feb3edb4e01c12dcf4809e2d4d4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575753"
---
# <a name="mode-element-xmla"></a>Elemento Mode (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
## <a name="remarks"></a>Remarks  
 L'elemento padre **blocco** elemento utilizza il **modalità** elemento per determinare il tipo di blocco per creare un oggetto. Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*CommitShared*|Sull'oggetto specificato viene stabilito un blocco condiviso. Per lo stesso oggetto è possibile creare altri blocchi condivisi.<br /><br /> Un blocco condiviso impedisce alle transazioni contenenti operazioni di scrittura, ad esempio un [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo in esecuzione un [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comando, un oggetto specificato, eseguire il commit finché non viene rimosso il blocco condiviso. Un blocco condiviso impedisce alle transazioni contenenti operazioni di lettura, ad esempio un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) chiamata al metodo o un **Execute** chiamata al metodo in esecuzione un [istruzione](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando, eseguire il commit.|  
|*CommitExclusive*|Sull'oggetto specificato viene stabilito un blocco esclusivo. Per lo stesso oggetto non è possibile creare altri blocchi condivisi o esclusivi.<br /><br /> Un blocco esclusivo impedisce alle transazioni contenenti operazioni di lettura o scrittura su un oggetto specificato l'esecuzione del commit fino alla rimozione del blocco esclusivo.|  
  
## <a name="see-also"></a>Vedere anche
 [ID elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md)   
 [Elemento dell'oggetto &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
