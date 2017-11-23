---
title: Elemento CustomRollupProperties (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
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
apiname: CustomRollupProperties Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.customrollupproperties
- urn:schemas-microsoft-com:xml-analysis#CustomRollupProperties
- http://schemas.microsoft.com/analysisservices/2003/engine#CustomRollupProperties
helpviewer_keywords: CustomRollupProperties element
ms.assetid: 4abf0129-e529-4355-b8d5-6f4e6a88e796
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 582310c692be695531e698396ab583a38130fb6c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="customrollupproperties-element-xmla"></a>Elemento CustomRollupProperties (XMLA)
  Contiene le proprietà di rollup personalizzato per un membro dell'attributo rappresentato dall'elemento padre [attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute>  
   ...  
   <CustomRollupProperties>...</CustomRollupProperties>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **CustomRollupProperties** elemento contiene un'espressione MDX (Multidimensional Expressions) che definisce le proprietà personalizzate di rollup del membro dell'attributo definito dall'elemento padre **attributo** elemento.  
  
 Per ulteriori informazioni sulle espressioni MDX, vedere [espressioni &#40; MDX &#41; ](../../../mdx/expressions-mdx.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Inserisci elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento Update &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
