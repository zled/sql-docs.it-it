---
title: Elemento tuples (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Tuples Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuples
- microsoft.xml.analysis.tuples
- urn:schemas-microsoft-com:xml-analysis#Tuples
helpviewer_keywords:
- Tuples element
ms.assetid: 5494bbaa-c1aa-43fa-b3e0-83befb2bccdd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 36f29edb149ab6a5c7c22dfe87c4d630289f29cd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128021"
---
# <a name="tuples-element-xmla"></a>Elemento Tuples (XMLA)
  Contiene un set di [tupla](tuple-element-xmla.md) degli oggetti per un' [asse](axis-element-xmla.md) elemento che utilizza il [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) tipo di dati restituito dal [Execute](../xml-elements-methods-execute.md) (metodo).  
  
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Axis](axis-element-xmla.md)|  
|Elementi figlio|[Tupla](tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Quando un'applicazione client imposta la `AxisFormat` proprietà *TupleFormat*, un'asse viene rappresentata come un set di tuple. Ogni elemento `Axis` contiene un elemento `Tuples` che rappresenta il set di tuple su quell’asse. Ogni tupla viene rappresentata utilizzando un `Tuple` elemento contenente [membro](member-element-xmla.md) gli elementi di ogni gerarchia sull'asse.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del `Tuples` elemento quando un client specifica *TupleFormat* oppure *CustomFormat* per il `AxisFormat` XML per la proprietà Analysis (XMLA), per l'asse, presupponendo i membri seguenti:  
  
|||||  
|-|-|-|-|  
|Gerarchia `Time`|1999|1999|2000|  
|Gerarchia `Category`|Valore effettivo|Budget|Budget|  
  
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
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
