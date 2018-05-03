---
title: Elemento Persistence (ASSL) | Documenti Microsoft
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
- Persistence Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Persistence
helpviewer_keywords:
- Persistence element
ms.assetid: dafe3df2-4795-48ea-bebe-33c1a3bf18b6
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3592b60a38785c23467877762649c096edd8ef97
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="persistence-element-assl"></a>Elemento Persistence (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina quali parti dei dati di origine associati sono dinamiche e vengono verificate per gli aggiornamenti usando la frequenza specificata dal [RefreshPolicy](../../../analysis-services/scripting/properties/refreshpolicy-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Persistence>...</Persistence>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*NotPersisted*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*NotPersisted*|Metadati di origine, membri e dati sono tutti dinamici.|  
|*Metadati*|I metadati di origine sono statici, ma membri e dati sono dinamici.|  
|*Tutto*|Metadati di origine, membri e dati sono tutti statici.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **persistenza** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.PersistenceType>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
