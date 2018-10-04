---
title: Tipo di elemento (Binding) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: b5f5c485-dc83-4d66-a8d2-e96e96d068f9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 407c8e53a842baca13671256a8125b696d7f1e91
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225223"
---
# <a name="type-element-binding-assl"></a>Elemento Type (Binding) (ASSL)
  Contiene il tipo dell'associazione attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeBinding> <!-- or CubeAttributeBinding -->  
   ...  
   <Type>...</Type>  
   ...  
</AttributeBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AttributeBinding](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/cubeattributebinding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Tutto*|Livello totale|  
|*Key*|Chiavi di membri|  
|*Nome*|Nome membro|  
|*Valore*|Valore del membro|  
|*Traduzione*|Conversioni di membri|  
|*UnaryOperator*|Operatori unari|  
|*SkippedLevels*|Livelli ignorati|  
|*CustomRollup*|Formule personalizzate di rollup|  
|*CustomRollupProperties*|Proprietà rollup personalizzate|  
  
 Gli elementi che corrispondono ai padri di `Type` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AttributeBinding> e <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati binding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
