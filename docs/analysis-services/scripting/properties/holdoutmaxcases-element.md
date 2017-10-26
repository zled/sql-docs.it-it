---
title: Elemento HoldoutMaxCases | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HoldoutMaxCases
helpviewer_keywords:
- HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e49da22961d21088649b4eda4539e357998049e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="holdoutmaxcases-element"></a>Elemento HoldoutMaxCases
  Specifica il numero massimo di case nell'origine dati da utilizzare per la partizione di dati di controllo che contiene il set di test di un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento. I rimanenti casi del set di dati sono utilizzati per il training. Il valore 0 indica che il numero di casi che possono essere controllati come set di test è illimitato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Numero intero maggiore di 0.|  
|Valore predefinito|0|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi una volta e una volta soltanto.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se si specificano valori per entrambe **HoldoutMaxPercent** e **HoldoutMaxCases**, l'algoritmo consente di limitare il test è il più piccolo dei due valori.  
  
 Se **HoldoutMaxCases** è impostata sul valore predefinito pari a 0, e non è stato impostato un valore per **HoldoutMaxPercent**, l'algoritmo utilizza l'intero set di dati per il training.  
  
 Le nuove proprietà **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize** sono disponibili solo in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. È pertanto necessario utilizzare per queste proprietà un prefisso con il nuovo spazio dei nomi, come illustrato nella descrizione della sintassi. In caso contrario, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene restituito un errore.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istruzioni di Scripting Language (ASSL) contenenti uno dei parametri di controllo **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize**, non può essere utilizzato [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
 L'elemento che corrisponde all'elemento padre **HoldoutMaxCases** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Elemento HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Elemento HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md)   
 [Elemento HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)  
  
  

