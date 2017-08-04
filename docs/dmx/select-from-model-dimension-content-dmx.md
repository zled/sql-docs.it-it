---
title: SELECT FROM &lt;modello&gt;. DIMENSION_CONTENT (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- FROM
- DIMENSION_CONTENT
dev_langs:
- DMX
helpviewer_keywords:
- mining models [Analysis Services], dimension content
- SELECT FROM <model>.DIMENSION_CONTENT statement
ms.assetid: 907fb3fb-2131-4a10-8635-2a39b9a805aa
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f9caf83d8d3d151f1b324f00abf5561549e111ad
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM &lt;modello&gt;. DIMENSION_CONTENT (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  È possibile utilizzare un modello di data mining come dimensione in un cubo OLAP, dove ogni nodo nel modello è rappresentato come membro della dimensione. **SELECT FROM \<modello >. Dimension_CONTENT** istruzione restituisce il contenuto del modello pertinente al relativo utilizzo come dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Facoltativa. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente identificatori di colonne correlate derivati dal set di righe dello schema relativo al contenuto.  
  
 *model*  
 Identificatore del modello.  
  
 *espressione della condizione*  
 Facoltativa. Condizione per limitare i valori restituiti dall'elenco di colonne.  
  
 *espressione*  
 Facoltativa. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
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
  
### <a name="code"></a>Codice  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DMX SELECT &#40; &#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

