---
title: Origine elemento (ComAssembly) (ASSL) | Microsoft Docs
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
- Source Element (ComAssembly)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 5c9209e8-ace6-4688-a64d-4987a7648ab9
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81076927595714ae4e0c98847d99f2d246660cf9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152972"
---
# <a name="source-element-comassembly-assl"></a>Elemento Source (ComAssembly) (ASSL)
  Contiene il nome file o identificatore a livello di codice (ProgID) per un componente COM (Component Object Model).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ComAssembly>  
   ...  
   <Source>...</Source>  
   ...  
</ComAssembly>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ComAssembly](../data-type/assembly-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `Source` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Tipo di dati ClrAssembly &#40;ASSL&#41;](../data-type/clrassembly-data-type-assl.md)   
 [Elemento Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Elemento server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
