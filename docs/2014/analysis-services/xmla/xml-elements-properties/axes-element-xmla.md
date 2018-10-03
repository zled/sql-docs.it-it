---
title: Assi elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Axes Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords:
- Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bdb5aa48dd3a65f99b424274fdb89b3aee8c9591
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094907"
---
# <a name="axes-element-xmla"></a>Elemento Axes (XMLA)
  Contiene una raccolta di [asse](axis-element-xmla.md) gli elementi che rappresentano i dati dell'asse contenuti in un [radice](root-element-xmla.md) elemento che utilizza il [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[root](root-element-xmla.md)|  
|Elementi figlio|[Axis](axis-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 All'interno dell'elemento `Axes` gli elementi `Axis` sono elencati nell'ordine in cui sono presenti nel set di dati, a partire da zero. L'impostazione della proprietà XMLA `AxisFormat` determina la formattazione degli elementi `Axis`. Per altre informazioni sul `AxisFormat` proprietà, vedere [proprietà XMLA supportate &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
 Un asse rappresenta un set di tuple in cui tutte le tuple hanno la stessa dimensionalità. Un set può essere rappresentato in modi diversi per scopi diversi. Il set di quattro tuple seguente, ad esempio, può essere rappresentato come raccolta di tuple bidimensionali o come prodotto cartesiano di due set unidimensionali.  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Valore effettivo|Budget|Valore effettivo|Budget|  
  
 Questo set di tuple può essere rappresentato come una raccolta di tuple bidimensionali:  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 Il set può essere rappresentato anche come un prodotto cartesiano di due set unidimensionali:  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 La prima rappresentazione, come tuple bidimensionali, è più semplice per gli strumenti client da utilizzare. La seconda rappresentazione, come prodotto cartesiano di set unidimensionali, utilizza una quantità minore di spazio e mantiene la natura multidimensionale del set.  
  
 Nella tabella seguente sono incluse le operazioni che è possibile utilizzare per definire e caratterizzare la struttura e i membri di un asse.  
  
|Operazione|Description|  
|---------------|-----------------|  
|Membro|Unità minima di un asse che rappresenta il membro di una gerarchia di dimensione.|  
|Membri|Raccolta di oggetti `Member` dalla stessa gerarchia di dimensione.|  
|Tupla|Raccolta di membri da gerarchie di dimensione diverse.|  
|Tuple|Raccolta di oggetti `Tuple` con la stessa dimensionalità.|  
|Union|Unione di set.|  
|CrossJoin|Prodotto cartesiano di set.|  
  
 Queste operazioni convertono le tuple bidimensionali e il prodotto cartesiano di set unidimensionali nei modi seguenti.  
  
## <a name="two-dimensional-tuples"></a>Tuple bidimensionali  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>Prodotto cartesiano di set unidimensionali  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 Un client può utilizzare la proprietà `AxisFormat` per richiedere una rappresentazione specifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati MDDataSet &#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
