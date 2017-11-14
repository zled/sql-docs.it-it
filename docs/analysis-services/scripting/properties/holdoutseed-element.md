---
title: Elemento HoldoutSeed | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HoldoutSeed
helpviewer_keywords:
- HoldoutSeed element
ms.assetid: 6b608bb3-c075-4744-9722-f5fb9fa1cc7e
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e97148f9630a125dbe6e93754c532a825de96c84
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="holdoutseed-element"></a>Elemento HoldoutSeed
  Specifica il valore di inizializzazione per una partizione di dati di controllo ripetibile che contiene il set di test di un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento. Questo valore di inizializzazione assicura che il contenuto del modello rimanga lo stesso durante la rielaborazione. Se non specificato o impostato su 0, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crea un valore di inizializzazione utilizzando un algoritmo di hash sul nome della struttura di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Long|  
|Valore predefinito|0|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi una volta e una volta soltanto.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Quando si crea per la prima volta una struttura di data mining, l'ID e il nome sono gli stessi. Tuttavia, è possibile modificare il nome della struttura di data mining. Pertanto, per garantire la ripetibilità della partizione, non ci si deve basare sul valore di inizializzazione creato dal nome, ma è necessario impostare espressamente un valore di inizializzazione.  
  
 Inoltre, quando si crea una copia di una struttura di data mining utilizzando il **ESPORTARE** istruzione [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] manterrà il nome della nuova struttura di data mining, ma genererà automaticamente un nuovo ID. Pertanto, è possibile avere due strutture di data mining che condividono lo stesso nome, ma hanno ID diversi. Due strutture di data mining qualsiasi con lo stesso nome avranno il medesimo valore di inizializzazione. Tuttavia, dal momento che il partizionamento dei dati dipende anche dai dati di origine, il contenuto effettivo delle partizioni di ciascuna struttura potrebbe essere diverso.  
  
 Le nuove proprietà **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize** sono disponibili solo in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. È pertanto necessario utilizzare per queste proprietà un prefisso con il nuovo spazio dei nomi, come illustrato nella descrizione della sintassi. In caso contrario, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene restituito un errore.  
  
 **Nota** In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istruzioni di Scripting Language (ASSL) contenenti i parametri di controllo **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize** non può essere utilizzato [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
 L'elemento che corrisponde all'elemento padre **HoldoutSeed** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Elemento HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)   
 [Elemento HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Elemento HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)  
  
  

