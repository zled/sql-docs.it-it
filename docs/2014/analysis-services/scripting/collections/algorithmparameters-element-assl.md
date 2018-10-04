---
title: Elemento AlgorithmParameters (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AlgorithmParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameters
helpviewer_keywords:
- AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c15cfd9be773af74c195860f7b0b16989b8c4355
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048891"
---
# <a name="algorithmparameters-element-assl"></a>Elemento AlgorithmParameters (ASSL)
  Contiene la raccolta di parametri per l'algoritmo utilizzato da un [MiningModel](../objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Elemento MiningModel](../objects/miningmodel-element-assl.md)|  
|Elementi figlio|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 La raccolta `AlgorithmParameters` contiene un set estensibile di parametri, rappresentato come coppie nome/valore, per un algoritmo del modello di data mining. Il set di parametri applicabili è dipendente dall'algoritmo. Per ulteriori informazioni sui parametri per un algoritmo specifico, vedere la documentazione appropriata relativa all'algoritmo.  
  
 I parametri dell'algoritmo disponibili, incluse le informazioni relative a convalida e visualizzazione, possono essere recuperati dal set di righe dello schema DMSCHEMA_MINING_SERVICE_PARAMETERS.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
