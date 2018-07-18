---
title: Valore elemento (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2ecaaf902ee1f29700b2d6333bbccd549d9c2193
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062852"
---
# <a name="value-element-xmla"></a>Elemento Value (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene il valore desiderato di un [attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) elemento da aggiungere a un [Inserisci](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) comando, o un [celle](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) elemento deve essere aggiornata da un [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [cella](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per **attributo** gli elementi, il **valore** elemento contiene il valore desiderato che deve contenere il membro dopo la **Inserisci** comando viene eseguito il commit. Per altre informazioni sull'inserimento di membri, vedere [inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Per la **cella** gli elementi, il **valore** elemento contiene il valore desiderato che la cella deve contenere dopo il **UpdateCells** comando viene eseguito il commit. Il valore effettivo archiviato nella tabella writeback per quella cella è la differenza tra il valore originale della cella e il valore desiderato della cella.  
  
 Il tipo di dati utilizzato da questo elemento deve corrispondere al tipo di dati della cella che deve essere aggiornata.  
  
 Per altre informazioni sull'aggiornamento di celle, vedere [Aggiornamento di celle &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento CellOrdinal &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [Inserire l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento UpdateCells &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
