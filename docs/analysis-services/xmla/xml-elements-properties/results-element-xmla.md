---
title: risultati Element (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 97cebdade566f796ff09bd68e8b292868e37e0a9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="results-element-xmla"></a>Elemento results (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elementi restituiti dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo usando il [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando.  
  
 **spazio dei nomi** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[restituire](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Elementi figlio|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Se un **Batch** eseguito dal **Execute** (metodo), il **restituire** elemento contiene un singolo **risultati** elemento invece di un singolo **radice** elemento. Il contenuto del **risultati** elemento dipende dalle impostazioni utilizzate per eseguire il **Batch** comando.  
  
 Per non transazionale **Batch** comandi, il **risultati** elemento contiene una **radice** elemento per ogni comando eseguito dal **Batch**comando, se il completamento del comando esito positivo o negativo. Per transazionale **Batch** comandi, il **risultati** elemento contiene una sola classe **radice** elemento che contiene le informazioni sull'errore per il comando non riuscito all'interno di **Batch** comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
