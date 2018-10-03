---
title: In cui l'elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Where Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Where
- microsoft.xml.analysis.where
- http://schemas.microsoft.com/analysisservices/2003/engine#Where
helpviewer_keywords:
- Where element
ms.assetid: 81fb4190-3379-4ddf-8795-a0772f3b92bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9b45926ec9022e8e8092721580c2419b423dd2b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191371"
---
# <a name="where-element-xmla"></a>Elemento Where (XMLA)
  Definisce una condizione di filtro usata dal comando padre [Drop](../xml-elements-commands/drop-element-xmla.md) o [Update](../xml-elements-commands/update-element-xmla.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Drop> <!-- or Update -->  
   ...  
   <Where>  
      <Attributes>...</Attributes>  
   </Where>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Drop](../xml-elements-commands/drop-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md)|  
|Elementi figlio|[Attributi](attributes-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Per la `Drop` comandi, il `Where` elemento, combinato con il [DeleteWithDescendants](deletewithdescendants-element-xmla.md) elemento identifica l'ambito dei membri dell'attributo che si desidera eliminare.  
  
 Per i comandi `Update`, l'elemento `Where` identifica l'ambito dei membri dell'attributo da aggiornare. È possibile aggiornare più membri dell'attributo utilizzando una combinazione di attributi inclusi nella raccolta `Attributes` del comando padre `Update` e nella raccolta `Attributes` dell'elemento `Where`.  
  
 Per altre informazioni sull’eliminazione e l’aggiornamento di membri di attributo, vedere [Inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
