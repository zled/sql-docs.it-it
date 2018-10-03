---
title: Tipo di dati MiningModelingFlag (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningModelingFlag Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93b84a3509d3992ffac20ebeafcda2d4f15f2073
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153017"
---
# <a name="miningmodelingflag-data-type-assl"></a>Tipo di dati MiningModelingFlag (ASSL)
  Definisce un tipo di dati primitivo che rappresenta i flag di modellazione disponibili per un [ModelingFlag](../objects/modelingflag-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|String (enumerazione)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|[ModelingFlag](../objects/modelingflag-element-assl.md) ([ModelingFlags](../collections/modelingflags-element-assl.md) insieme [MiningModelColumn](miningmodelcolumn-data-type-assl.md) oppure [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Note  
 Il nome del flag può contenere spazi. Nella tabella riportata di seguito viene fornito un elenco dei valori supportati. a livello nativo  
  
|valore|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|La colonna deve essere modellata come se avesse due stati, mancante e non mancante, indipendentemente dai valori nella colonna. Questo è particolarmente utile per le colonne in una tabella nidificata, dove i valori sono sparse tra i casi.|  
|*NON È NULL*|La colonna non può accettare valori NULL.|  
|*REGRESSORE*|La colonna fornisce valori del regressore per i casi di test.|  
  
 Flag specifici del provider aggiuntivi possono essere usati se provider di data mining OLE DB o dati di terze parti sono stati aggregati sull'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 L'elemento strettamente correlato nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
