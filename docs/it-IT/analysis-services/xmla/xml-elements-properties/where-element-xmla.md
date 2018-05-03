---
title: In cui l'elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Where Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Where
- microsoft.xml.analysis.where
- http://schemas.microsoft.com/analysisservices/2003/engine#Where
helpviewer_keywords:
- Where element
ms.assetid: 81fb4190-3379-4ddf-8795-a0772f3b92bb
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3d4f957adb67241a2f3b3dbf416f6bc4a412972b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="where-element-xmla"></a>Elemento Where (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce una condizione di filtro usata dal comando padre [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) o [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md).  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Elementi figlio|[Attributi](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Per i comandi **Drop**, l'elemento **Where**, combinato con l'elemento [DeleteWithDescendants](../../../analysis-services/xmla/xml-elements-properties/deletewithdescendants-element-xmla.md), identifica l'ambito dei membri dell'attributo da eliminare.  
  
 Per i comandi **Update** , l'elemento **Where** identifica l'ambito dei membri dell'attributo da aggiornare. È possibile aggiornare più membri dell'attributo utilizzando una combinazione di attributi inclusi nella raccolta **Attributes** del comando padre **Update** e nella raccolta **Attributes** dell'elemento **Where** .  
  
 Per altre informazioni sull’eliminazione e l’aggiornamento di membri di attributo, vedere [Inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
