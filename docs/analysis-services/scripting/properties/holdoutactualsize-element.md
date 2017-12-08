---
title: Elemento HoldoutActualSize | Documenti Microsoft
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
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: HoldoutActualSize
helpviewer_keywords: HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fc09419e2099c4e0cb5587c4d328ef876728584e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="holdoutactualsize-element"></a>Elemento HoldoutActualSize
  Indica le dimensioni effettive, dopo l'elaborazione, della partizione di controllo che contiene il set di test di un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento. I rimanenti casi del set di dati sono utilizzati per il training. Questa proprietà è di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutActualSize>...</ddl100_100:HoldoutActualSize>  
   ...  
</MiningStructure  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Numero intero di sola lettura.|  
|Valore predefinito|Non applicabile|  
|Cardinalità|0-1: Elemento facoltativo che può verificarsi una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore per **HoldoutActualSize** a seconda dei casi i dati di origine e i valori per [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md), [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md), e [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md). Pertanto, il valore di **HoldoutActualSize** non è disponibile fino a quando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Elabora struttura di data mining.  
  
 L'elemento che corrisponde all'elemento padre **HoldoutActualSize** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istruzioni di Scripting Language (ASSL) contenenti uno dei parametri di controllo **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize**, non può essere utilizzato [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Elemento HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)   
 [Elemento HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Elemento HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md)  
  
  
