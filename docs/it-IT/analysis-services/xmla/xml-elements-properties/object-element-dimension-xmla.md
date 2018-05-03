---
title: Oggetto elemento (Dimension) (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Object Element (Dimension)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: db7feb39-7cc1-4b54-8979-77ce402ef71f
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: faf8544bfac0ed161276f6d5bb7352780af40545
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="object-element-dimension-xmla"></a>Elemento Object (Dimension) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene un riferimento all'oggetto per la dimensione in cui l'elemento padre [inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [aggiornamento](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), o [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) comando viene eseguito.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Insert> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <Database>...</Database>  
      <Cube>...</Cube>  
      <Dimension>...</Dimension>  
   </Object>  
...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [aggiornamento](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Elementi figlio|[Cubo](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md), [Database](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md), [dimensione](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
