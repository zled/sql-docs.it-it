---
title: Elemento ExecuteResponse (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 30e63e8275c018eeef7603b46170709770e5cb09
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---objects---executeresponse"></a>ExecuteResponse - oggetti - elementi XML
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene le informazioni restituite da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in risposta a un [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[restituire](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **ExecuteResponse** è l'elemento in primo piano all'interno del corpo di una risposta SOAP per il **Execute** metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DiscoverResponse &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)   
 [Gli oggetti &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
