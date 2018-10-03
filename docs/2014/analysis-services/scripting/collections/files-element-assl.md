---
title: File di elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Files Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Files
helpviewer_keywords:
- Files element
ms.assetid: 8a1327cb-1f60-42a7-b8ef-213d45a63e55
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91fd214a87ea266a1c5849211bd30237b4313b20
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078621"
---
# <a name="files-element-assl"></a>Elemento Files (ASSL)
  Contiene la raccolta di [File](../objects/file-element-assl.md) gli elementi che costituiscono un [ClrAssembly](../data-type/assembly-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Assembly xsi:type="ClrAssembly">  
   ...  
   <Files>  
      <File xsi:type="ClrAssemblyFile">...</File>  
   </Files>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Assembly](../objects/assembly-element-assl.md) di tipo [ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Elementi figlio|[File](../objects/file-element-assl.md) di tipo [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ClrAssemblyFileCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Elemento database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Elemento Assemblies &#40;ASSL&#41;](assemblies-element-assl.md)   
 [Elemento di dati &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Tipo di dati DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Blocca l'elemento &#40;ASSL&#41;](blocks-element-assl.md)   
 [Bloccare l'elemento &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Tipo di dati ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
