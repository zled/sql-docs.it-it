---
title: Oggetto elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Object Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: 99470537-2c4a-4072-9613-940c41c12487
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e4fb7e25b9e813487b612bbd6269c2f080d85f5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178751"
---
# <a name="object-element-xmla"></a>Elemento Object (XMLA)
  Contiene un riferimento all'oggetto utilizzato dall'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <!-- One or more object identifiers, depending on the parent element -->  
   </Object>  
...  
</Alter>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|Predecessore o padre: [Alter](../xml-elements-commands/create-element-xmla.md) &#124; 0-1: elemento facoltativo che può ricorrere una sola volta.<br /><br /> Predecessore o padre: tutti gli altri &#124; 1-1: elemento obbligatorio che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ALTER](../xml-elements-commands/alter-element-xmla.md), [Backup](../xml-elements-commands/backup-element-xmla.md), [ClearCache](../xml-elements-commands/clearcache-element-xmla.md), [eliminare](../xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md), [blocco](../xml-elements-commands/lock-element-xmla.md), [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md), [processo](../xml-elements-commands/process-element-xmla.md), [sottoscrizione](../xml-elements-commands/subscribe-element-xmla.md), [sincronizzare](../xml-elements-commands/synchronize-element-xmla.md)|  
|Elementi figlio|Elementi ASSL (Analysis Services Scripting Language) obbligatori. Specificato elencando gli elementi ID dell'oggetto e i suoi predecessori (tranne l'oggetto `Server`.) Ad esempio, l'elemento `Object` seguente identifica una partizione:<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>Note  
 L'ordine nel quale sono visualizzati gli identificatori non è importante.  
  
 Per la `Alter` elementi, l'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene utilizzato come oggetto predefinito se la `Object` elemento non è specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
