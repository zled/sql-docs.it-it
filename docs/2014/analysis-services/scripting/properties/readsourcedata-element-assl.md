---
title: Elemento ReadSourceData (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ReadSourceData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ReadSourceData element
ms.assetid: 7da4665a-fba3-4aae-8dee-678dc14d3b05
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dcbb6ce5b9cda3b17b69558cd60f6030f9e097b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156793"
---
# <a name="readsourcedata-element-assl"></a>Elemento ReadSourceData (ASSL)
  Determina i nomi univoci vengono generati per le gerarchie contenute all'interno di [CubePermission](../objects/cubepermission-element-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubePermission>  
   ...  
   <ReadSourceData>...</ReadSourceData>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Non è consentito alcun accesso ai dati disponibili nella sessione di calcolo 0.|  
|*È consentito*|È consentito l'accesso ai dati disponibili nella sessione di calcolo 0.|  
  
## <a name="remarks"></a>Remarks  
 L'elemento che corrisponde al padre di `ReadSourceData` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento del cubo &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Elemento della dimensione &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  