---
title: Oggetto elemento (Dimension) (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9d66d84632079ce1cb0d27d505086896ad36f571
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="object-element-dimension-xmla"></a>Elemento Object (Dimension) (XMLA)
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
|Elementi padre|[Eliminare](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [aggiornamento](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Elementi figlio|[Cubo](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md), [Database](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md), [dimensione](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

