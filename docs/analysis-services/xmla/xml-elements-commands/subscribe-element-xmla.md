---
title: Elemento Subscribe (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f784cbe3c33eb6b2587b7b535668e793fac3b138
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973073"
---
# <a name="subscribe-element-xmla"></a>Elemento Subscribe (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Sottoscrive una traccia e restituisce un set di righe che contiene gli eventi di traccia da un'istanza di Analysis Services.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il **Sottoscrivi** comando sottoscrive e trasmette di nuovo un set di righe da una traccia specificata su un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Se un oggetto diverso da una traccia viene specificato nell'elemento **Object** , si verifica un errore.  
  
 Se il **oggetti** elemento non viene specificato, una traccia della sessione viene definita e sottoscritta sul [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. La traccia della sessione restituisce un set fisso di eventi traccia dalla sessione corrente.  
  
 Il flusso di set di righe restituito da questo comando viene concluso se l'applicazione client chiude la connessione di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza, o se la sessione sulla quale il **"Subscribe"** comando viene eseguito viene terminata.  
  
## <a name="see-also"></a>Vedere anche
 [I comandi &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
