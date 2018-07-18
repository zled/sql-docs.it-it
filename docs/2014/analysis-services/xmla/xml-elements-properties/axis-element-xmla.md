---
title: Elemento Axis (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Axis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3e68903dc828f4b14ac60892d1b6fc2baed2f30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263227"
---
# <a name="axis-element-xmla"></a>Elemento Axis (XMLA)
  Contiene un set di tuple utilizzato per rappresentare un singolo asse in un dataset multidimensionale contenuto in un [assi](axes-element-xmla.md) elemento che utilizza il [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) tipo di dati restituito dal [Execute](../xml-elements-methods-execute.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Axes>  
   ...  
   <Axis> <!-- when AxisFormat XMLA property is set to ClusterFormat -->  
      <CrossProduct>...</CrossProduct>  
   </Axis>  
   <Axis> <!-- when AxisFormat XMLA property is set to TupleFormat or CustomFormat -->  
      <Tuples>...</Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Assi](axes-element-xmla.md)|  
|Elementi figlio|[CrossProduct](crossproduct-element-xmla.md) o [Tuple](tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il contenuto dell'elemento `Axis` varia a seconda del valore della proprietà XMLA `AxisFormat` utilizzata dal metodo `Execute`.  
  
## <a name="tupleformat"></a>TupleFormat  
 Quando un'applicazione client imposta la `AxisFormat` proprietà *TupleFormat*, un'asse viene rappresentata come un set di tuple. Ogni elemento `Axis` contiene un elemento `Tuples` che rappresenta il set di tuple sull'asse. Ogni tupla viene rappresentata utilizzando un elemento `Tuple` che contiene elementi `Member` di ogni gerarchia sull'asse.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Quando un'applicazione client imposta la `AxisFormat` proprietà *ClusterFormat*, i membri su ogni asse sono divisi in cluster in cui ogni cluster rappresenta un prodotto incrociato tra set ordinati di membri da ogni gerarchia. Ogni elemento `Axis` è costituito da uno o più elementi `CrossProduct`. Ogni elemento `CrossProduct` contiene un elemento `Members` per ogni gerarchia sull'asse.  
  
## <a name="customformat"></a>CustomFormat  
 Quando un'applicazione client imposta la `AxisFormat` proprietà *CustomFormat*, il valore viene considerato identico il *TupleFormat* valore da un'istanza di Analysis Services.  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene illustrata la struttura del `Axis` elementi quando un client specifica *TupleFormat* oppure *CustomFormat* per il `AxisFormat` proprietà XMLA, data la seguente membri per l'asse:  
  
|||||  
|-|-|-|-|  
|Gerarchia `Time`|1999|1999|2000|  
|Gerarchia `Category`|Valore effettivo|Budget|Budget|  
  
### <a name="code"></a>codice  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene illustrata la struttura del `Axis` elementi quando un client specifica *ClusterFormat* per il `AxisFormat` proprietà XMLA, presupponendo i membri seguenti per l'asse:  
  
||||||  
|-|-|-|-|-|  
|Gerarchia `Time`|1999|1999|2000|2001|  
|Gerarchia `Category`|Valore effettivo|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
### <a name="code"></a>codice  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size = "4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size = "1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
