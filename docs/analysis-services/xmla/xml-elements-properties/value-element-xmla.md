---
title: Valore elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Value Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61a5fa276918a176eb60340fce44e5dfdae0d4da
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="value-element-xmla"></a>Elemento Value (XMLA)
  Contiene il valore desiderato di un [attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) elemento devono essere aggiunti da un [inserire](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) comando, o un [cella](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) elemento da aggiornare tramite un [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [cella](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per **attributo** elementi, il **valore** elemento contiene il valore desiderato che deve contenere il membro dopo il **inserire** comando viene eseguito il commit. Per ulteriori informazioni sull'inserimento di membri, vedere [inserimento, aggiornamento e rimozione di membri &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Per **cella** elementi, il **valore** elemento contiene il valore desiderato della cella deve contenere dopo il **UpdateCells** comando viene eseguito il commit. Il valore effettivo archiviato nella tabella writeback per quella cella è la differenza tra il valore originale della cella e il valore desiderato della cella.  
  
 Il tipo di dati utilizzato da questo elemento deve corrispondere al tipo di dati della cella che deve essere aggiornata.  
  
 Per altre informazioni sull'aggiornamento di celle, vedere [Aggiornamento di celle &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CellOrdinal &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [Inserisci elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento UpdateCells &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
