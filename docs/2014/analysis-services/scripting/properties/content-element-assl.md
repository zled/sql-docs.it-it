---
title: Contenuto elemento (ASSL) | Documenti Microsoft
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
api_name:
- Content Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Content
helpviewer_keywords:
- Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 98d2de4a0ce93e857a63ebd9fe79dd18d0f9a86e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064121"
---
# <a name="content-element-assl"></a>Elemento Content (ASSL)
  Viene descritto il contenuto della colonna nella [MiningStructure](../objects/miningstructure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Questa enumerazione descrive il tipo di contenuto rappresentato da una colonna della struttura di data mining e può essere estesa nel modo necessario dai provider dell'algoritmo di data mining. Per altre informazioni sui tipi di contenuto, vedere [Tipi di contenuto &#40;Data mining&#41;](../../data-mining/content-types-data-mining.md).  
  
 I valori inclusi nella tabella seguente sono in genere supportati da tutti i provider dell'algoritmo di data mining.  
  
|valore|Description|  
|-----------|-----------------|  
|*Discreti*|La colonna contiene valori discreti.|  
|*Continua*|I valori per la colonna definiscono un set continuo di dati numerici.|  
|*Discretizzati*|I valori nella colonna rappresentano gruppi, o bucket, di valori derivati da una colonna continua.|  
|*Ordinati*|I valori per la colonna definiscono un set ordinato.|  
|*Cyclical*|I valori per la colonna definiscono un set ordinato ciclico.|  
|*Probabilità*|I valori per la colonna specificano una probabilità per le colonne contenute nella [ClassifiedColumns](../collections/columns-element-assl.md) dell'elemento padre `ScalarMiningStructureColumn`.|  
|*Variance*|I valori per la colonna specificano una varianza per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*StdDev*|I valori per la colonna specificano una deviazione standard per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*ProbabilityVariance*|I valori per la colonna specificano una varianza della probabilità per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*ProbabilityStdDev*|I valori per la colonna specificano una deviazione standard della probabilità per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*Supporto*|I valori per la colonna specificano informazioni di supporto per la colonna contenuta nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`. **Nota:** questa colonna viene fornita come parte dello standard per provider di algoritmi di data mining di terze parti. **Nota:** forniti da Microsoft algoritmi non sono in genere utili per la colonna. <br /><br /> ,|  
|*Key*|La colonna è una colonna chiave. **Nota:** questo tipo di contenuto è applicabile solo alle colonne chiave, in cui la `IsKey` è impostato su `True`.|  
  
 Oltre a questi valori standard, inclusi con i provider dell'algoritmo di data mining [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supportano i valori elencati nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sequenza di tasti*|La colonna è una colonna chiave e i valori per la colonna rappresentano una sequenza di eventi. **Nota:** questo tipo di contenuto è applicabile solo alle colonne chiave, in cui la `IsKey` è impostato su `True`.|  
|*Chiave temporale*|La colonna è una colonna chiave e i valori per la colonna rappresentano unità di misura temporali. **Nota:** questo tipo di contenuto è applicabile solo alle colonne chiave, in cui la `IsKey` è impostato su `True`.|  
|*Sequence*|I valori per la colonna rappresentano una sequenza di eventi.|  
|*Time*|I valori per la colonna rappresentano unità di misura temporali.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Content` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ClassifiedColumns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  