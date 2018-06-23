---
title: Elemento FoldingParameters (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12cae8f4ad02f57f63fd168ff41503f233f53c4c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170471"
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
|Elemento padre|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Elementi figlio|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Remarks  
 Queste proprietà sono solo per uso interno e non sono supportate nelle istruzioni DDL.  
  
 Per informazioni su come usare la convalida incrociata in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], vedere [misure nel Report di convalida incrociata](../../data-mining/measures-in-the-cross-validation-report.md).  
  
 Per informazioni su come eseguire la convalida incrociata tramite [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] stored procedure, vedere [dati Mining Stored procedure &#40;Analysis Services - Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
