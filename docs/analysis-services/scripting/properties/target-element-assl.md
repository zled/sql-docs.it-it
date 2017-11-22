---
title: Destinazione elemento (ASSL) | Documenti Microsoft
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
apiname: Target Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Target
helpviewer_keywords: Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d4f0334fde6506dbb5630fc1dc47efe88a5d48a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="target-element-assl"></a>Elemento Target (ASSL)
  Identifica la destinazione di [azione](../../../analysis-services/scripting/objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Target>...</Target>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore previsto di questo elemento dipende dal valore del [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) elemento per l'elemento padre **azione**. Nella tabella seguente vengono descritti i valori previsti di **destinazione** in base al valore di **TargetType**.  
  
|Valore di TargetType|Valore previsto|  
|----------------------|--------------------|  
|*Cube*|Nome di un cubo.|  
|*Celle*|Espressione di sottocubo.|  
|*Set*|Espressione set o nome di un set denominato.<br /><br /> Nota: Impossibile utilizzare un'istruzione sub-SELECT.|  
|*Gerarchia, HierarchyMembers*|Nome di una gerarchia.|  
|*Dimensione, DimensionMembers*|Nome di una dimensione.|  
|*Livello, LevelMembers*|Nome di un livello.|  
|*Attributo AttributeMembers*|Nome di un attributo.|  
  
 L'elemento che corrisponde all'elemento padre **destinazione** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
