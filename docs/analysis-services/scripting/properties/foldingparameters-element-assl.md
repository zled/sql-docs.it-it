---
title: Elemento FoldingParameters (ASSL) | Documenti Microsoft
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
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords: FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8d6565a5898f5f41898d82a1d70d3748f8b2883c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="foldingparameters-element-assl"></a>Elemento FoldingParameters (ASSL)
  Specifica i parametri utilizzati dal server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] quando esegue la convalida incrociata di modelli di data mining.  
  
> [!NOTE]  
>  Questi parametri sono solo per uso interno. Le informazioni vengono fornite solo per riferimento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModel>  
   ...  
   <ddl100_100:FoldingParameters>...  
      <ddl100_100:FoldIndex>...</ddl100_100:FoldIndex>  
      <ddl100_100:FoldCount>...</ddl100_100:FoldCount>  
      <ddl100_100:MaxCases>...</ddl100_100:MAxCases>  
      <ddl100_100:FoldTargetAttribute>...</ddl100_100:FoldTargetAttribute  
...</ddl100_100:FoldingParameters>  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|*FoldIndex*|Valore integer che indica la posizione iniziale della partizione utilizzata per la convalida incrociata.|  
|*FoldCount*|Valore integer che indica il numero di partizioni del modello dopo la convalida incrociata.|  
|*MaxCases*|Valore integer che indica il numero di case del modello utilizzati per la convalida incrociata.<br /><br /> Il valore 0 indica che sono stati utilizzati tutti i case.|  
|*FoldTargetAttribute*|Stringa che indica l'ID della colonna del modello che contiene l'attributo stimabile.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Elementi figlio|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Osservazioni  
 Queste proprietà sono solo per uso interno e non sono supportate nelle istruzioni DDL.  
  
 Per informazioni su come utilizzare la convalida incrociata in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], vedere [misure nel Report di convalida incrociata](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
 Per informazioni su come eseguire la convalida incrociata utilizzando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] stored procedure, vedere [dati Mining Stored procedure &#40; Analysis Services - Data Mining &#41; ](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
