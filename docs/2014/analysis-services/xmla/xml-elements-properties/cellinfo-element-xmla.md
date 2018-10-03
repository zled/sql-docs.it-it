---
title: Elemento CellInfo (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CellInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#CellInfo
- urn:schemas-microsoft-com:xml-analysis#CellInfo
helpviewer_keywords:
- CellInfo element
ms.assetid: 8b6420f1-e9a7-4975-b580-1439fa11f5ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 693495e50c78760cd130df6d12f359d96c5c0807
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216512"
---
# <a name="cellinfo-element-xmla"></a>Elemento CellInfo (XMLA)
  Rappresenta i metadati della cella contenuti dall'elemento padre [OlapInfo](olapinfo-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<OlapInfo>  
   ...  
   <CellInfo>  
      <!-- One or more cell property definitions -->  
   </CellInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[OlapInfo](olapinfo-element-xmla.md)|  
|Elementi figlio|Una o più definizioni di proprietà della cella|  
  
## <a name="remarks"></a>Note  
 L'elemento `CellInfo` contiene una raccolta di proprietà della cella per le celle incluse nel set di dati multidimensionale restituito da un elemento `root` utilizzando il tipo di dati `MDDataSet`. Ogni proprietà della cella nell'elemento `CellInfo` è definita da un elemento XML separato, ognuno con un attributo `name` e un attributo `type`. L'attributo `name` della proprietà della cella corrisponde al nome della proprietà della cella OLE DB per OLAP rappresentata dall'elemento XML, mentre l'attributo `type` rappresenta il tipo di dati XML della proprietà della cella. Il nome dell'elemento XML viene utilizzato per identificare il valore della proprietà della cella per le celle contenute nell'elemento `CellData` dell'elemento `root`.  
  
 Nella sintassi seguente è descritta una definizione di proprietà della cella:  
  
```  
<CellPropertyDefinition name="string" type"string" />  
```  
  
 Le proprietà disponibili e i relativi valori possono essere ottenuti utilizzando il tipo di richiesta DISCOVER_PROPERTIES con il `Discover` (metodo). Non è previsto un ordine obbligatorio per le proprietà elencate nell'elemento `PropertyList`.  
  
 Facoltativamente, un provider può specificare i valori predefiniti per singole proprietà del membro o della cella nella sezione `AxisInfo` o `CellInfo`. I valori predefiniti possono fornire un risultato più piccolo se la proprietà ha sempre o quasi sempre lo stesso valore. Per indicare un valore predefinito per una proprietà, il`Default` elemento può essere specificato facoltativamente come elemento figlio di uno degli elementi di definizione di proprietà della cella. L'assenza di una proprietà del membro o della cella nel risultato indica pertanto che l'impostazione predefinita specificata corrisponde al valore per la proprietà della cella.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato in che modo le proprietà della cella VALUE, FORMATTED_VALUE e FORMAT_STRING sono rappresentate nell'elemento `CellInfo`.  
  
```  
<OlapInfo>  
   ...  
      <CellInfo>  
         <Value name="VALUE"></Value>  
         <FmtValue name="FORMATTED_VALUE"></FmtValue>  
         <FormatString name="FORMAT_STRING"></FormatString>  
      </CellInfo>  
</OlapInfo>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
