---
title: Elemento OrderBy (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ac17b52d36b414854da027dc3cf2c4a8f768e9f6
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="orderby-element-assl"></a>Elemento OrderBy (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive in che modo ordinare i membri contenuti nell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nome*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Nome*|Ordina per nome del membro.|  
|*Key*|Ordina per chiave del membro.|  
|*AttributeKey*|Ordina per chiave del membro dell'attributo specificato nella [OrderByAttributeID](../../../analysis-services/scripting/properties/orderbyattributeid-element-assl.md) elemento **DimensionAttribute**.|  
|*AttributeName*|Ordina per nome del membro dell'attributo specificato nell'elemento **OrderByAttributeID** di **DimensionAttribute**.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **OrderBy** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.OrderBy>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
