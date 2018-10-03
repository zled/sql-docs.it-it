---
title: Elemento Language (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Language Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LANGUAGE
helpviewer_keywords:
- Language element
ms.assetid: 4d745d23-6b1f-4a85-97cf-d034cc41356f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ce2de9ae87ac0c4d22a179f25bbf7ff047e7633
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126063"
---
# <a name="language-element-assl"></a>Elemento Language (ASSL)
  Contiene l'identificatore del linguaggio dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Database, Dimension, MiningModel, MiningStructure, Translation -->  
   ...  
   <Language>...</Language>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Integer|  
|Valore predefinito|Nessuno|  
  
 **cardinalità**  
  
|Predecessore o padre|Cardinalità|  
|------------------------|-----------------|  
|[Traduzione](../objects/translation-element-assl.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
|Tutti gli altri|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [Database](../objects/database-element-assl.md), [dimensione](../objects/dimension-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [traduzione](../objects/translation-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Note  
 L'elemento `Language` contiene l'identificatore di lingua predefinito utilizzato dall'elemento padre oppure l'identificatore di lingua specifico per un elemento `Translation`. La lingua deve essere definita utilizzando codici di identificazione delle impostazioni locali (LCID). Il codice LCID 1033, ad esempio, viene utilizzato per indicare la lingua inglese (Stati Uniti).  
  
 Gli elementi che corrispondono agli elementi padre dell'elemento `Language` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure> e <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
