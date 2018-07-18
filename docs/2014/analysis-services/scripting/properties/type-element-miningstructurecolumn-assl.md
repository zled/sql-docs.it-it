---
title: Tipo di elemento (MiningStructureColumn) (ASSL) | Microsoft Docs
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
- Type Element (MiningStructureColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30ce9327fb28e9f452e643ded604f2a8dd72a084
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304241"
---
# <a name="type-element-miningstructurecolumn-assl"></a>Elemento Type (MiningStructureColumn) (ASSL)
  Contiene il tipo dei [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Long*|Intero con segno a 64 bit. Questo tipo di dati esegue il mapping al tipo di dati `Int64` nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework e il tipo di dati di DBTYPE_I8 in OLE DB.|  
|*Boolean*|Valore booleano. Questo tipo di dati esegue il mapping al tipo di dati `Boolean` in .NET Framework e il tipo di dati di DBTYPE_BOOL in OLE DB.|  
|*Text*|Flusso con terminazione Null di caratteri Unicode. Questo tipo di dati esegue il mapping al tipo di dati `String` in .NET Framework e il tipo di dati di DBTYPE_WSTR in OLE DB.|  
|*Valore Double*|Numero a precisione doppia in virgola mobile compreso tra -1.79E +308 e 1.79E +308. Questo tipo di dati esegue il mapping al tipo di dati `Double` in .NET Framework e il tipo di dati di DBTYPE_R8 in OLE DB.|  
|*Data*|Tipo di dati data, registrato come numero a virgola mobile e doppia precisione. La parte intera è il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno. Questo tipo di dati esegue il mapping al tipo di dati `DateTime` in .NET Framework e il tipo di dati di DBTYPE_DATE in OLE DB.|  
|*Tabella*|Tabella nidificata. Questo tipo di dati esegue il mapping al tipo di dati di DBTYPE_HCHAPTER in OLE DB. **Nota:** le colonne della tabella in .NET Framework non dispongono di un tipo di dati intrinseco equivalente, ma sono supportate invece dal `DataReader` classe.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `Type` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 L'elemento che corrisponde al padre di `Type` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
