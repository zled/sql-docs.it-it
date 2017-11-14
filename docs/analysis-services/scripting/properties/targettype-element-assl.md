---
title: Elemento TargetType (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TargetType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49c2fd13925130bfb76730708775f6bb0d5e79ca
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="targettype-element-assl"></a>Elemento TargetType (ASSL)
  Identifica il tipo di elemento dell'elemento identificato nel [destinazione](../../../analysis-services/scripting/properties/target-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Cube*|La destinazione dell'azione è un cubo.|  
|*Celle*|La destinazione dell'azione è un sottocubo.|  
|*Set*|La destinazione dell'azione è un set.|  
|*Hierarchy*|La destinazione dell'azione è una gerarchia.|  
|*Level*|La destinazione dell'azione è un livello.|  
|*DimensionMembers*|La destinazione dell'azione sono i membri di una dimensione.|  
|*HierarchyMembers*|La destinazione dell'azione sono i membri di una gerarchia.|  
|*LevelMembers*|La destinazione dell'azione sono i membri di un livello.|  
|*AttributeMembers*|La destinazione dell'azione sono i membri di un attributo.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **TargetType** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 L'elemento che corrisponde all'elemento padre **TargetType** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

