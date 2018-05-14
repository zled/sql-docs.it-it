---
title: Elemento (XMLA) del database | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f874d72700646456fa046b820f0fdf29e4738d58
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="database-element-xmla"></a>Elemento Database (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifica il database che contiene la dimensione rappresentata dall'elemento padre [oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Object>  
   ...  
   <Database>...</Database>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Database** elemento è un identificatore di oggetto che contiene il nome del database di Analysis Services che contiene la dimensione rappresentata dal **oggetto** elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CUBE & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md)   
 [Elemento Dimension & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
