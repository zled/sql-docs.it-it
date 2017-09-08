---
title: Tipo di dati MiningModelingFlag (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningModelingFlag Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bab055eef15474bfa22adefdc8ea6709659af978
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="miningmodelingflag-data-type-assl"></a>Tipo di dati MiningModelingFlag (ASSL)
  Definisce un tipo di dati primitivo che rappresenta i flag di modellazione disponibili per un [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|String (enumerazione)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|Nessuno|  
|Elementi derivati|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) ([ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md) insieme di [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md) o [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Il nome del flag può contenere spazi. Nella tabella riportata di seguito viene fornito un elenco dei valori supportati. a livello nativo  
  
|Valore|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|La colonna deve essere modellata come se avesse due stati, mancante e non mancante, indipendentemente dai valori nella colonna. Questo è particolarmente utile per le colonne in una tabella nidificata, dove i valori sono sparse tra i casi.|  
|*NON È NULL*|La colonna non può accettare valori NULL.|  
|*REGRESSOR*|La colonna fornisce valori del regressore per i casi di test.|  
  
 Flag specifici del provider aggiuntivi possono essere utilizzati se provider di data mining OLE DB o dati di terze parti sono stati aggregati sull'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 L'elemento strettamente correlato nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
