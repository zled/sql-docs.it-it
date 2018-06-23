---
title: Blocca elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Blocks Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf944cc053e7a8c32efec50d10f6cc176942cce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066170"
---
# <a name="blocks-element-assl"></a>Elemento Blocks (ASSL)
  Contiene la raccolta di blocchi di dati binari che rappresentano contenuto binario di un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
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
|Elementi padre|[I dati](../objects/data-element-assl.md) di tipo [DataBlock](../data-type/datablock-data-type-assl.md)|  
|Elementi figlio|[Blocco](../objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `Blocks` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Tipo di dati ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [File di elemento &#40;ASSL&#41;](files-element-assl.md)   
 [File di elemento &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Tipo di dati ClrAssemblyFile &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Elemento di dati &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Tipo di dati DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Elemento Blocks](blocks-element-assl.md)   
 [Bloccare l'elemento &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  