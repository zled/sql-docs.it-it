---
title: Elemento AllowedRowsExpression (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a23acca8488d5fa747d29338240cf98e0f703ecc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057251"
---
# <a name="allowedrowsexpression-element-assl"></a>Elemento AllowedRowsExpression (ASSL)
  Contiene un'espressione DAX (Data Analysis Expression) di tipo booleano, che definisce il contenuto dell'elemento padre.  
  
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
  
  
