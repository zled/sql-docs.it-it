---
title: Elemento FoldingParameters (ASSL) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac348aa326c53b1266edfff3396feadda6c80ea6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161142"
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
|Elemento padre|[Elemento MiningModel](../objects/miningmodel-element-assl.md)|  
|Elementi figlio|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>Note  
 Queste proprietà sono solo per uso interno e non sono supportate nelle istruzioni DDL.  
  
 Per informazioni su come usare la convalida incrociata in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], vedere [misure nel Report di convalida incrociata](../../data-mining/measures-in-the-cross-validation-report.md).  
  
 Per informazioni su come eseguire la convalida incrociata usando [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] stored procedure, vedere [Data Mining Stored procedure &#40;Analysis Services - Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
