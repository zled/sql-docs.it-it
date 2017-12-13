---
title: Elemento expression (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Expression Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Expression
helpviewer_keywords: Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 169567bda91aeb759fcf77e54726422992e6a032
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="expression-element-assl"></a>Elemento Expression (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contiene un'espressione MDX (Multidimensional Expressions) che definisce il contenuto dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per il **CellPermission** elemento, il **espressione** elemento contiene un'espressione logica MDX che identifica celle applicabile ai diritti indicati dal [accesso](../../../analysis-services/scripting/properties/access-element-assl.md) elemento del **CellPermission** elemento. Se il valore di un **espressione** elemento per un **CellPermission** elemento è vuoto, il **CellPermission** elemento viene ignorato.  
  
 Per il **StandardAction** elemento, il **espressione** elemento contiene un'espressione MDX che rappresenta il contenuto dell'azione. Se il valore di un **espressione** elemento per un **StandardAction** elemento è vuoto, il **StandardAction** elemento viene ignorato.  
  
 Gli elementi che corrispondono agli elementi padre nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CellPermission> e <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
