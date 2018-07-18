---
title: Elemento Usage (MiningModelColumn) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Usage Element (MiningModelColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6767c4c5ac535ac603cc6182cbe645088c8ac05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265300"
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Elemento Usage (MiningModelColumn) (ASSL)
  Viene descritto come la colonna associata nell'elemento padre [MiningStructure](../objects/miningstructure-element-assl.md) viene usato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Key*|La colonna è una colonna chiave.|  
|*Input*|La colonna è una colonna di input.|  
|*Predict*|La colonna è una colonna di stima.|  
|*PredictOnly*|La colonna è solo una colonna di stima.|  
|*Nessuno*|La colonna non viene utilizzata dal modello. **Avviso:** quando il valore di Usage è "None", Analysis Services non invia alcun valore per il server per impostazione predefinita; di conseguenza, l'attributo Usage non è incluso nella richiesta/risposta.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Usage` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
