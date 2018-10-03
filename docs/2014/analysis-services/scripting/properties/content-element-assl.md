---
title: Elemento (ASSL) del contenuto | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b27152b0c181061e25727270fd89bd423728a5a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097861"
---
# <a name="content-element-assl"></a>Elemento Content (ASSL)
  Viene descritto il contenuto della colonna di [MiningStructure](../objects/miningstructure-element-assl.md) elemento.  
  
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
  
## <a name="remarks"></a>Note  
 Questa enumerazione descrive il tipo di contenuto rappresentato da una colonna della struttura di data mining e può essere estesa nel modo necessario dai provider dell'algoritmo di data mining. Per altre informazioni sui tipi di contenuto, vedere [Tipi di contenuto &#40;Data mining&#41;](../../data-mining/content-types-data-mining.md).  
  
 I valori inclusi nella tabella seguente sono in genere supportati da tutti i provider dell'algoritmo di data mining.  
  
|valore|Description|  
|-----------|-----------------|  
|*Discreta*|La colonna contiene valori discreti.|  
|*continua*|I valori per la colonna definiscono un set continuo di dati numerici.|  
|*DISCRETIZED*|I valori nella colonna rappresentano gruppi, o bucket, di valori derivati da una colonna continua.|  
|*Ordinati*|I valori per la colonna definiscono un set ordinato.|  
|*Cyclical*|I valori per la colonna definiscono un set ordinato ciclico.|  
|*Probabilità*|I valori per la colonna specificano una probabilità per le colonne contenute nella [ClassifiedColumns](../collections/columns-element-assl.md) dell'elemento padre `ScalarMiningStructureColumn`.|  
|*Variance*|I valori per la colonna specificano una varianza per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*StdDev*|I valori per la colonna specificano una deviazione standard per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*ProbabilityVariance*|I valori per la colonna specificano una varianza della probabilità per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*ProbabilityStdDev*|I valori per la colonna specificano una deviazione standard della probabilità per le colonne contenute nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`.|  
|*Supporto*|I valori per la colonna specificano informazioni di supporto per la colonna contenuta nell'elemento `ClassifiedColumns` dell'elemento padre `ScalarMiningStructureColumn`. **Nota:** questa colonna viene fornita come parte dello standard per provider di algoritmi di data mining di terze parti. **Nota:** Microsoft fornito algoritmi non sono in genere utili per questa colonna. <br /><br /> .|  
|*Key*|La colonna è una colonna chiave. **Nota:** questo tipo di contenuto è applicabile solo alle colonne chiave, in cui la `IsKey` elemento è impostato su `True`.|  
  
 Oltre a questi valori standard, inclusi con i provider di algoritmi di data mining [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supportano i valori elencati nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sequenza di tasti*|La colonna è una colonna chiave e i valori per la colonna rappresentano una sequenza di eventi. **Nota:** questo tipo di contenuto è applicabile solo alle colonne chiave, in cui la `IsKey` elemento è impostato su `True`.|  
|*Chiave temporale*|La colonna è una colonna chiave e i valori per la colonna rappresentano unità di misura temporali. **Nota:** questo tipo di contenuto è applicabile solo alle colonne chiave, in cui la `IsKey` elemento è impostato su `True`.|  
|*Sequence*|I valori per la colonna rappresentano una sequenza di eventi.|  
|*Time*|I valori per la colonna rappresentano unità di misura temporali.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Content` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ClassifiedColumns &#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
