---
title: Elemento LastUpdate (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- LastUpdate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- LastUpdate element
ms.assetid: 639db733-a082-4f57-868d-a3bcd5e7a4f6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 940c8dfb2bbd74d431024b70673a38bbc5fc7ee6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069331"
---
# <a name="lastupdate-element-assl"></a>Elemento LastUpdate (ASSL)
  Contiene una proprietà di sola lettura timestamp che indica l'ultima volta in cui l'oggetto associato [Database](../objects/database-element-assl.md) o uno degli oggetti principali contenuti nel database è stato modificato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database> <!-- or one of the elements that are listed in the Element Relationships table -->  
   ...  
   <LastUpdate>...</LastUpdate>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|DateTime|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Database](../objects/database-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `LastUpdate` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
