---
title: Elemento Exception (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5b9847f1328fb0f0c7b6c1503708ca0b75b585c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="exception-element-xmla"></a>Elemento Exception (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indica che un'eccezione ha restituita un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
 **spazio dei nomi** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
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
|Elementi padre|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se si verifica un errore durante l'esecuzione di un **Discover** chiamata al metodo o un singolo comando XMLA in un **Execute** chiamata al metodo che impedisce il completamento, il metodo o un comando di **radice** elemento per tale metodo o il comando contiene un **eccezione** elemento e un **messaggi** elemento. Il **eccezione** elemento indica che si è verificato un errore che ha impedito il metodo o il comando completato correttamente l'esecuzione e **messaggi** elemento contiene l'elenco di messaggi di errore o avviso correlato all'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Messaggi di elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
