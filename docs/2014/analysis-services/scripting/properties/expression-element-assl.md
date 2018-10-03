---
title: Elemento expression (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Expression Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Expression
helpviewer_keywords:
- Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7801b94d30e0b0c4baa62dd861146ee89fb3717
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173911"
---
# <a name="expression-element-assl"></a>Elemento Expression (ASSL)
  Contiene un’espressione MDX (Multidimensional Expressions) che definisce i contenuti dell’elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per il `CellPermission` elemento, il `Expression` elemento contiene un'espressione MDX logica che identifica celle applicabile ai diritti indicati dal [Access](access-element-assl.md) elemento del `CellPermission` elemento. Se il valore di un elemento `Expression` per un elemento `CellPermission` è vuoto, l’elemento `CellPermission` viene ignorato.  
  
 Per l'elemento `StandardAction`, l'elemento `Expression` contiene un'espressione MDX che rappresenta il contenuto dell'azione. Se il valore di un elemento `Expression` per un elemento `StandardAction` è vuoto, l’elemento `StandardAction` viene ignorato.  
  
 Gli elementi che corrispondono agli elementi padre nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CellPermission> e <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
