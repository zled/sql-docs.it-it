---
title: Elemento Algorithm (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Algorithm Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fe1a9caffdff1de0dc62c4ddd696e1ec8b829bd
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="algorithm-element-assl"></a>Elemento Algorithm (ASSL)
  Definisce l'algoritmo utilizzato da un [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di **algoritmo** elemento è una stringa che identifica l'algoritmo. Ad esempio, la stringa può essere *Microsoft_Naive_Bayes*, *Microsoft_Decision_Trees*, o *Microsoft_Clustering.* La stringa identifica gli algoritmi forniti da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] e gli algoritmi personalizzati forniti dall'utente. I valori disponibili per il **algoritmo** elemento può essere recuperato dalla colonna SERVICE_NAME del [DMSCHEMA_MINING_SERVICES](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) set di righe dello schema.  
  
 L'elemento che corrisponde all'elemento padre **algoritmo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningModel>. Un elemento strettamente correlato nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MiningModelAlgorithms>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AlgorithmParameter &#40; ASSL &#41;](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)   
 [Elemento AlgorithmParameters &#40; ASSL &#41;](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
