---
title: Elemento AggregationUsage (ASSL) | Documenti Microsoft
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
- AggregationUsage Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationUsage
helpviewer_keywords:
- AggregationUsage element
ms.assetid: af0c2e7f-b659-4fbf-9b1a-66128db669a2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7ecb9d7dd5bd5c8e7fdec233bb7b49f51ea65ddc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationusage-element-assl"></a>Elemento AggregationUsage (ASSL)
  I controlli come finestra di progettazione delle aggregazioni in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] progettare aggregazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeAttribute>  
   ...  
   <AggregationUsage>...</AggregationUsage>  
   ...  
</CubeAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Valore predefinito*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Full*|Ogni aggregazione del cubo deve includere l'attributo.|  
|*Nessuno*|Nessuna aggregazione del cubo deve includere l'attributo.|  
|*Senza restrizioni*|Non esistono restrizioni in Progettazione aggregazioni.|  
|*Valore predefinito*|Progettazione delle aggregazioni viene applicata una regola predefinita in base al tipo di attributo (*completo* per le chiavi, *Unrestricted* ad altri utenti).|  
  
 L'enumerazione che corrisponde ai valori consentiti per **AggregationUsage** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AggregationUsage>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CUBE &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
