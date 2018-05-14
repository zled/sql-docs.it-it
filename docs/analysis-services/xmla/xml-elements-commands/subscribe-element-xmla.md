---
title: Elemento Subscribe (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 548336f5e891cc41c485bed4047c1223d0f9344c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="subscribe-element-xmla"></a>Elemento Subscribe (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Sottoscrive una traccia e restituisce un set di righe che contiene gli eventi di traccia da un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Sottoscrivi** comando sottoscrive e trasmette di nuovo un set di righe da una traccia specificata su un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. Se un oggetto diverso da una traccia viene specificato nell'elemento **Object** , si verifica un errore.  
  
 Se il **oggetto** elemento non viene specificato, una traccia della sessione viene definita e sottoscritta sul [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza. La traccia della sessione restituisce un set fisso di eventi traccia dalla sessione corrente.  
  
 Il flusso del set di righe restituito da questo comando viene terminato qualora l'applicazione client chiude la connessione il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza, o se la sessione in cui il **Sottoscrivi** eseguito viene terminata.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
