---
title: Elemento Axis (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Axis Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.axis
- http://schemas.microsoft.com/analysisservices/2003/engine#Axis
helpviewer_keywords:
- Axis element
ms.assetid: 336895e1-4a57-4b43-9a53-e31569866e6c
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 162c143ed257114ec33851e2b071c093058ca155
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="axis-element-xmla"></a>Elemento Axis (XMLA)
  Contiene un set di tuple utilizzato per rappresentare un singolo asse in un dataset multidimensionale contenuto in un [assi](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md) elemento che utilizza il [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo di dati restituito dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Assi](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md)|  
|Elementi figlio|[CrossProduct](../../../analysis-services/xmla/xml-elements-properties/crossproduct-element-xmla.md) o [Tuple](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il contenuto del **asse** elemento varia a seconda del valore del **AxisFormat** proprietà XMLA utilizzata dal **Execute** metodo.  
  
## <a name="tupleformat"></a>TupleFormat  
 Quando un'applicazione client imposta la proprietà **AxisFormat** su *TupleFormat*, un’asse viene rappresentata come un set di tuple. Ogni **asse** elemento contiene un **Tuple** elemento che rappresenta il set di tuple sull'asse. Ogni tupla viene rappresentata usando un elemento **Tuple** che contiene elementi **Member** di ogni gerarchia sull'asse.  
  
## <a name="clusterformat"></a>ClusterFormat  
 Quando un'applicazione client imposta il **AxisFormat** proprietà *ClusterFormat*, i membri su ogni asse sono divisi in cluster in cui ogni cluster rappresenta un prodotto incrociato tra set ordinati di membri di ogni gerarchia. Ogni **asse** elemento è costituito da uno o più **CrossProduct** elementi. Ogni **CrossProduct** elemento contiene un **membri** elemento per ogni gerarchia sull'asse.  
  
## <a name="customformat"></a>CustomFormat  
 Quando un'applicazione client imposta il **AxisFormat** proprietà *CustomFormat*, il valore viene considerato lo stesso come il *TupleFormat* valore da un'istanza di Analysis Services.  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene illustrata la struttura del **asse** elementi quando un client specifica *TupleFormat* o *CustomFormat* per il **AxisFormat**  Proprietà XMLA, presupponendo i membri seguenti per l'asse:  
  
|||||  
|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|  
  
### <a name="code"></a>Codice  
  
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
 Nell'esempio seguente viene illustrata la struttura del **asse** elementi quando un client specifica *ClusterFormat* per il **AxisFormat** proprietà XMLA, data la seguente membri per l'asse:  
  
||||||  
|-|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|2001|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
### <a name="code"></a>Codice  
  
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
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
