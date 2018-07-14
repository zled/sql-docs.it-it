---
title: Tipo di elemento (MeasureGroup) (ASSL) | Microsoft Docs
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
- Type Element (MeasureGroup)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 3a584baf-36bb-4e1d-9128-c4758c0b8f06
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8e8bab8b822ccb4cf8a17fe4759519eeefb974a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226371"
---
# <a name="type-element-measuregroup-assl"></a>Elemento Type (MeasureGroup) (ASSL)
  Specifica il tipo dei [MeasureGroup](../objects/group-element-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroup>  
   ...  
   <Type>...</Type>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regolare*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Gruppo di misure](../objects/group-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Regolare*|Contiene misure regolari.|  
|*ExchangeRate*|Contiene misure dei tassi di cambio esteri.|  
|*Vendite*|Contiene misure delle vendite.|  
|*Budget*|Contiene misure di budget.|  
|*FinancialReporting*|Contiene misure dei rapporti finanziari.|  
|*Marketing*|Contiene misure di marketing.|  
|*Inventario*|Contiene misure delle scorte.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Type` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MeasureGroupType>.  
  
 L'elemento che corrisponde al padre di `Type` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
