---
title: Elemento FoldingParameters (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f3c631844a71ff43d84c76ba2104a211b7aea039
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="foldingparameters-element-assl"></a>Elemento FoldingParameters (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
 Per informazioni su come eseguire la convalida incrociata tramite [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] stored procedure, vedere [dati Mining Stored procedure &#40;Analysis Services - Data Mining&#41;](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
