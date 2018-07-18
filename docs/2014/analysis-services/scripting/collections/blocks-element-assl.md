---
title: Blocca elemento (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c2776ea261c26bd8c53d3f78ba29231823bb659d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161322"
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
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `Blocks` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
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
  
  
