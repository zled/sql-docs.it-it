---
title: File di elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- File
helpviewer_keywords:
- File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 645882666ba82f965fddff9e1c886e97ff092a90
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064320"
---
# <a name="file-element-assl"></a>Elemento File (ASSL)
  Definisce uno dei file che compongono un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../data-type/assembly-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[File](../collections/files-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `Files` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento server &#40;ASSL&#41;](server-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](database-element-assl.md)   
 [Elemento Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Elemento assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Tipo di dati ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Elemento di dati &#40;ASSL&#41;](data-element-assl.md)   
 [Tipo di dati DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Blocca l'elemento &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Bloccare l'elemento &#40;ASSL&#41;](block-element-assl.md)   
 [Tipo di dati ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  