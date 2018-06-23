---
title: Elemento HoldoutMaxPercent | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 089ed35d7c900e48da2ba283f8bcf9ee4a29fa7a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063438"
---
# <a name="holdoutmaxpercent-element"></a>Elemento HoldoutMaxPercent
  Specifica la percentuale massima di case nell'origine dati che verrà utilizzato per la partizione di dati di controllo che contiene il set di test di un [MiningStructure](../objects/miningstructure-element-assl.md) elemento. I rimanenti casi sono utilizzati per il training. Il valore 0 indica che il numero di casi che possono essere controllati come set di test è illimitato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Numero intero compreso tra 0 e 99.|  
|Valore predefinito|30|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi una volta e una volta soltanto.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Se si specifica un valore sia per `HoldoutMaxPercent` che per `HoldoutMaxCases`, l'algoritmo consente di limitare il set di test al più basso dei due valori.  
  
 Se `HoldoutMaxCases` è impostato sul valore predefinito 0 e non è stato impostato un valore per `HoldoutMaxPercent`, l'algoritmo utilizza l'intero set di dati per il training.  
  
 Le nuove proprietà `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oppure `HoldoutActualSize` sono disponibili solo in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. È pertanto necessario utilizzare per queste proprietà un prefisso con il nuovo spazio dei nomi, come illustrato nella descrizione della sintassi. In caso contrario, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene restituito un errore.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, le istruzioni Scripting Language [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL) contenenti uno dei parametri di controllo `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` o `HoldoutActualSize` non possono essere utilizzate in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
 L'elemento che corrisponde al padre di `HoldoutMaxPercent` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)   
 [Elemento HoldoutMaxCases](holdoutmaxcases-element.md)   
 [Elemento HoldoutSeed](holdoutseed-element.md)   
 [Elemento HoldoutActualSize](holdoutactualsize-element.md)  
  
  