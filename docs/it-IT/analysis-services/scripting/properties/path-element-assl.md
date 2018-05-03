---
title: Elemento Path (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Path Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Path
helpviewer_keywords:
- Path element
ms.assetid: 0edc59ac-1671-4fe1-9b7c-6c1548df5c63
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fc07267e625b5fddd08e45454efe6858c6422e98
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="path-element-assl"></a>Elemento Path (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il percorso, fornito da un'istanza di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], di un report utilizzato per il [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ReportAction>  
   ...  
   <Path>...</Path>  
   ...  
</ReportAction>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre **percorso** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ReportAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
