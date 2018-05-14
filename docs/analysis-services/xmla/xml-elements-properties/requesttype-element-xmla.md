---
title: Elemento RequestType (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe6310da2b2869770e0dca99ad6c1ae6630133db
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="requesttype-element-xmla"></a>Elemento RequestType (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Determina il tipo di metadati restituiti dal [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
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
|Elementi padre|[Individuare](../../../analysis-services/xmla/xml-elements-methods-discover.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **RequestType** elemento determina il set di righe dello schema da cui il **Discover** metodo restituisce i dati. Questa enumerazione è limitata ai nomi dei set di righe dello schema supportati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per ulteriori informazioni sui set di righe dello schema, vedere [rowset dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md).  
  
> [!NOTE]  
>  Il **RequestType** elemento enumera solo i nomi di set di righe dello schema. Se viene utilizzato il GUID del set di righe dello schema, si verifica un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
