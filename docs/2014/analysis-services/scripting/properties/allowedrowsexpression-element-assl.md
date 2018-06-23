---
title: Elemento AllowedRowsExpression (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 99a340f2bbeb1e5d61a20b4031beeade9fbcc5c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055575"
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
|Elementi padre|[CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Per il `CellPermission` elemento, il `Expression` elemento contiene un'espressione logica MDX che identifica celle applicabile ai diritti indicati dal [accesso](access-element-assl.md) elemento del `CellPermission` elemento. Se il valore di un elemento `Expression` per un elemento `CellPermission` è vuoto, l’elemento `CellPermission` viene ignorato.  
  
 Per l'elemento `StandardAction`, l'elemento `Expression` contiene un'espressione MDX che rappresenta il contenuto dell'azione. Se il valore di un elemento `Expression` per un elemento `StandardAction` è vuoto, l’elemento `StandardAction` viene ignorato.  
  
 Gli elementi che corrispondono agli elementi padre nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CellPermission> e <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  