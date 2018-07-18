---
title: Tipo di elemento (MiningStructureColumn) (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bcb7cec0d968e1320bdafc4bf53d25d6efdabc6f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040420"
---
# <a name="type-element-miningstructurecolumn-assl"></a>Elemento Type (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il tipo di [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Long*|Intero con segno a 64 bit. Questo tipo di dati esegue il mapping al **Int64** tipo di dati di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] tipo di .NET Framework e i dati di DBTYPE_I8 in OLE DB.|  
|*Boolean*|Valore booleano. Esegue il mapping di questo tipo di dati per il **booleano** tipo di dati .NET Framework e il tipo di dati DBTYPE_BOOL in OLE DB.|  
|*Text*|Flusso con terminazione Null di caratteri Unicode. Esegue il mapping di questo tipo di dati per il **stringa** tipo di dati .NET Framework e il tipo di dati DBTYPE_WSTR in OLE DB.|  
|*Double*|Numero a precisione doppia in virgola mobile compreso tra -1.79E +308 e 1.79E +308. Esegue il mapping di questo tipo di dati per il **doppie** tipo di dati .NET Framework e il tipo di dati DBTYPE_R8 in OLE DB.|  
|*Data*|Tipo di dati data, registrato come numero a virgola mobile e doppia precisione. La parte intera è il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno. Esegue il mapping di questo tipo di dati per il **DateTime** tipo di dati .NET Framework e il tipo di dati DBTYPE_DATE in OLE DB.|  
|*Tabella*|Tabella nidificata. Questo tipo di dati esegue il mapping al tipo di dati di DBTYPE_HCHAPTER in OLE DB.<br /><br /> Nota: Le colonne della tabella in .NET Framework non è un tipo di dati intrinseco equivalente, ma sono invece supportate dal **DataReader** classe.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
