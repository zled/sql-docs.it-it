---
title: Elemento tuples (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Tuples Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuples
- microsoft.xml.analysis.tuples
- urn:schemas-microsoft-com:xml-analysis#Tuples
helpviewer_keywords: Tuples element
ms.assetid: 5494bbaa-c1aa-43fa-b3e0-83befb2bccdd
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 96ae916c249be7fddbf3c66e25a7b213740cbd6b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="tuples-element-xmla"></a>Elemento Tuples (XMLA)
  Contiene un set di [tupla](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) gli oggetti per un [asse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) elemento che utilizza il [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo di dati restituito dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Elementi figlio|[Tupla](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Quando un'applicazione client imposta la proprietà **AxisFormat** su *TupleFormat*, un’asse viene rappresentata come un set di tuple. Ogni elemento **Axis** contiene un elemento **Tuples** che rappresenta il set di tuple su quell’asse. Ogni tupla viene rappresentata usando un elemento **Tuple** che contiene elementi [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) di ogni gerarchia sull'asse.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del **Tuple** elemento quando un client specifica *TupleFormat* o *CustomFormat* per il **AxisFormat**  XML per la proprietà Analysis (XMLA), presupponendo i membri seguenti per l'asse:  
  
|||||  
|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
