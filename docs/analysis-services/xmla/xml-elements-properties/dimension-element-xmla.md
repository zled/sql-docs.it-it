---
title: Dimensioni elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Dimension Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Dimension
- urn:schemas-microsoft-com:xml-analysis#Dimension
- microsoft.xml.analysis.dimension
helpviewer_keywords: Dimension element
ms.assetid: 85093468-e971-4b8e-9ee4-7b264ad01711
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8b142324a33a0cdab2eddcb7fe988cb50ee63663
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="dimension-element-xmla"></a>Elemento Dimension (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Identifica la dimensione del cubo rappresentata dall'elemento padre [oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Object>  
   ...  
   <Dimension>...</Dimension>  
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
 Il **dimensione** elemento è un identificatore di oggetto che contiene il nome della dimensione del cubo rappresentato dal **oggetto** elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)   
 [Elemento Dimension (XMLA)](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
