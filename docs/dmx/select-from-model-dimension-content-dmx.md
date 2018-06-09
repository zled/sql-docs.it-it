---
title: SELECT FROM &lt;modello&gt;. DIMENSION_CONTENT (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29f730f0bdff985ffceb849c429e5d1b02f70d5f
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842524"
---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM &lt;modello&gt;. DIMENSION_CONTENT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare un modello di data mining come dimensione in un cubo OLAP, dove ogni nodo nel modello è rappresentato come membro della dimensione. **SELECT FROM \<modello >. Dimension_CONTENT** istruzione restituisce il contenuto del modello pertinente al relativo utilizzo come dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Facoltativo. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente identificatori di colonne correlate derivati dal set di righe dello schema relativo al contenuto.  
  
 *model*  
 Identificatore del modello.  
  
 *Espressione della condizione*  
 Facoltativo. Condizione per limitare i valori restituiti dall'elenco di colonne.  
  
 *expression*  
 Facoltativo. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Remarks  
 I provider degli algoritmi definiscono il contenuto restituito e come organizzarlo. Il provider può ad esempio limitare il numero dei nodi descritti nel contenuto della dimensione.  
  
 Nella tabella seguente vengono elencate le colonne su cui è possibile eseguire query per ottenere il contenuto della dimensione, nonché la funzione svolta da ogni colonna come dimensione di data mining.  
  
|Colonna del set di righe relativo al contenuto|Ruolo svolto nella dimensione di data mining|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Proprietà del membro.|  
|NODE_NAME|Proprietà del membro.|  
|NODE_UNIQUE_NAME|Attributo chiave.|  
|NODE_TYPE|Proprietà del membro.|  
|NODE_CAPTION|CaptionColumn per **chiave** attributo.|  
|CHILDREN_CARDINALITY|Proprietà del membro.|  
|PARENT_UNIQUE_NAME|RelatedAttribute per **chiave** attributo (parentattribute in gerarchia padre-figlio una).|  
|NODE_DESCRIPTION|Proprietà del membro.|  
|NODE_RULE|Proprietà del membro.|  
|MARGINAL_RULE|Proprietà del membro.|  
|NODE_PROBABILITY|Proprietà del membro.|  
|MARGINAL_PROBABILITY|Proprietà del membro.|  
|NODE_SUPPORT|Proprietà del membro.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 In questo esempio vengono selezionate dal contenuto del modello `[TM Decision Tree]` tutte le colonne relative all'utilizzo del modello come dimensione.  
  
### <a name="code"></a>codice  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELEZIONARE &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Estensioni Data Mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
