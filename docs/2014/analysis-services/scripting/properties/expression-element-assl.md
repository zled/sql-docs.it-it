---
title: Elemento expression (ASSL) | Documenti Microsoft
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
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b56f4d09e59644b63d11c4becbb999f0536479d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055800"
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
|Elementi padre|[CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Per il `CellPermission` elemento, il `Expression` elemento contiene un'espressione logica MDX che identifica celle applicabile ai diritti indicati dal [accesso](access-element-assl.md) elemento del `CellPermission` elemento. Se il valore di un elemento `Expression` per un elemento `CellPermission` è vuoto, l’elemento `CellPermission` viene ignorato.  
  
 Per l'elemento `StandardAction`, l'elemento `Expression` contiene un'espressione MDX che rappresenta il contenuto dell'azione. Se il valore di un elemento `Expression` per un elemento `StandardAction` è vuoto, l’elemento `StandardAction` viene ignorato.  
  
 Gli elementi che corrispondono agli elementi padre nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CellPermission> e <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  