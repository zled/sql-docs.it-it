---
title: Elemento MdxScript (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MdxScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MdxScript
helpviewer_keywords:
- MdxScript element
ms.assetid: 0c59a550-dc95-4d50-948a-bb99348bdd86
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3aa8d72073f5459a7e260a81ca4bf5c67ad3209b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169474"
---
# <a name="mdxscript-element-assl"></a>Elemento MdxScript (ASSL)
  Contiene informazioni su uno script MDX (Multidimensional Expressions) che è associato un [cubo](cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MdxScripts>  
   <MdxScript>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Annotations>...</Annotations>  
      <Commands>...</Commands>  
      <DefaultScript>...</DefaultScript>  
      <CalculationProperties>...</CalculationProperties>  
   </MdxScript>  
</MdxScripts>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MdxScripts](../collections/mdxscripts-element-assl.md)|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [Calculationproperty](../collections/calculationproperties-element-assl.md), [comandi](../collections/commands-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultScript](../properties/defaultscript-element-assl.md), [Descrizione](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [nome](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento `DefaultScript` di uno script è impostato su `True` per impostazione predefinita. L'impostazione di `DefaultScript` su `True` per uno script specifico comporta l'impostazione di `DefaultScript` su `False` per tutti gli altri script.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
