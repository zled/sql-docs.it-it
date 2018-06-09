---
title: DELETE (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5b11bda21fe877af419442cb8b98acd4d29c21b
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841274"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Cancella un modello di data mining, una struttura di data mining o una struttura di data mining e tutti i modelli di data mining associati, a seconda delle clausole DMX (Data Mining Extensions) utilizzate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Argomenti  
 *model*  
 Identificatore del modello.  
  
 *struttura*  
 Identificatore della struttura.  
  
## <a name="remarks"></a>Remarks  
 Se non si specifica **modello di data MINING** o **struttura di data MINING**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cerca il tipo di oggetto in base al nome ed elabora l'oggetto corretto. Se il server contiene una struttura di data mining e un modello di data mining con lo stesso nome, verrà restituito un errore.  
  
 Nella tabella seguente sono descritti i risultati ottenuti utilizzando le diverse forme della sintassi.  
  
|.|Risultato|  
|---------------|------------|  
|DELETE FROM MINING STRUCTURE*\<struttura >*<br /><br /> o Gestione configurazione<br /><br /> DELETE FROM MINING STRUCTURE*\<struttura >*. CONTENUTO|Esegue ProcessClear nella struttura di data mining. Viene cancellato tutto il contenuto della struttura di data mining e dei modelli di data mining associati.|  
|DELETE FROM MINING STRUCTURE*\<struttura >*. CASI|Esegue ProcessClearStructureOnly nella struttura di data mining. Viene cancellato tutto il contenuto della struttura di data mining, lasciando invariati i modelli di data mining associati. Dopo la cancellazione della struttura di data mining non è possibile eseguire il drill-through sui modelli di data mining associati.|  
|ELIMINARE dal modello di data MINING*\<modello >*<br /><br /> o Gestione configurazione<br /><br /> ELIMINARE dal modello di data MINING*\<modello >*. CONTENUTO|Esegue ProcessClear nel modello di data mining, ma lascia invariati i valori dello stato. I valori di stato sono i possibili stati di una colonna. Per la colonna del genere, ad esempio, i valori di stato sono maschio e femmina.|  
  
 Per ulteriori informazioni sui tipi di elaborazione, vedere [elemento di tipo &#40;XMLA&#41;](../analysis-services/xmla/xml-elements-properties/type-element-xmla.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso tutto il contenuto dal modello NB_Sample.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
