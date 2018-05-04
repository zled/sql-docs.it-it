---
title: Assi elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Axes Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Axes
- http://schemas.microsoft.com/analysisservices/2003/engine#Axes
- microsoft.xml.analysis.axes
- urn:schemas-microsoft-com:xml-analysis#Axes
helpviewer_keywords:
- Axes element
ms.assetid: 2005d06a-f8a2-4b4f-8c0d-2f7f73eb6f5c
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3a64f078995d5984e4ff9bc6d5267febacd44cff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="axes-element-xmla"></a>Elemento Axes (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [asse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) elementi che rappresentano i dati dell'asse contenuti in un [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento che utilizza il [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo di dati.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Elementi figlio|[Asse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Sotto il **assi** elemento, il **asse** sono elencati gli elementi nell'ordine in cui sono presenti nel set di dati, a partire da zero. Il **AxisFormat** determina l'impostazione della proprietà XMLA come **asse** formattazione degli elementi. Per ulteriori informazioni sul **AxisFormat** proprietà, vedere [proprietà XMLA supportate &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
|Membri|Una raccolta di **membro** gerarchia di oggetti della stessa dimensione.|  
|Tupla|Raccolta di membri da gerarchie di dimensione diverse.|  
|Tuple|Una raccolta di **tupla** oggetti con la stessa dimensionalità.|  
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
  
 Un client può utilizzare il **AxisFormat** proprietà per richiedere una rappresentazione specifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati MDDataSet & #40; XMLA & #41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
