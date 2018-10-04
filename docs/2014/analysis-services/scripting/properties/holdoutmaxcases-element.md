---
title: Elemento HoldoutMaxCases | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutMaxCases
helpviewer_keywords:
- HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aaf0629b51abf7e8dc4fe6efa5ac6b18a2f166b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136811"
---
# <a name="holdoutmaxcases-element"></a>Elemento HoldoutMaxCases
  Specifica il numero massimo di case nell'origine dati da utilizzare per la partizione dei dati di controllo che contiene il set di test di una [MiningStructure](../objects/miningstructure-element-assl.md) elemento. I rimanenti casi del set di dati sono utilizzati per il training. Il valore 0 indica che il numero di casi che possono essere controllati come set di test è illimitato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Numero intero maggiore di 0.|  
|Valore predefinito|0|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi una volta e una volta soltanto.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Elemento MiningStructure](../objects/miningstructure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Se si specifica un valore sia per `HoldoutMaxPercent` che per `HoldoutMaxCases`, l'algoritmo consente di limitare il set di test al più basso dei due valori.  
  
 Se `HoldoutMaxCases` è impostato sul valore predefinito 0 e non è stato impostato un valore per `HoldoutMaxPercent`, l'algoritmo utilizza l'intero set di dati per il training.  
  
 Le nuove proprietà `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, o `HoldoutActualSize` sono disponibili solo in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. È pertanto necessario utilizzare per queste proprietà un prefisso con il nuovo spazio dei nomi, come illustrato nella descrizione della sintassi. In caso contrario, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene restituito un errore.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, le istruzioni Scripting Language [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL) contenenti uno dei parametri di controllo `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` o `HoldoutActualSize` non possono essere utilizzate in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
 L'elemento che corrisponde al padre di `HoldoutMaxCases` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)   
 [Elemento HoldoutMaxPercent](holdoutmaxpercent-element.md)   
 [Elemento HoldoutSeed](holdoutseed-element.md)   
 [Elemento HoldoutActualSize](holdoutactualsize-element.md)  
  
  
