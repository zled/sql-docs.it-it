---
title: Elemento Tuple (XMLA) | Documenti Microsoft
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
- Tuple Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.tuple
- urn:schemas-microsoft-com:xml-analysis#Tuple
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuple
helpviewer_keywords:
- Tuple element
ms.assetid: d65aba10-55e1-49c1-81bc-0756c39c0da2
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: fe470d60aa008723034e1bdbf95f3ecf593c8a3a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077646"
---
# <a name="tuple-element-xmla"></a>Elemento Tuple (XMLA)
  Contiene una raccolta di elementi [Member](member-element-xmla.md) contenuti dall'elemento padre [Tuple](tuples-element-xmla.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
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
|Elementi padre|[Tuple](tuples-element-xmla.md)|  
|Elementi figlio|[Membro](member-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Quando un'applicazione client imposta la `AxisFormat` proprietà da *TupleFormat*, un'asse viene rappresentata come un set di tuple. Ogni elemento `Axis` contiene un elemento `Tuples` che rappresenta il set di tuple su quell’asse. Ogni tupla viene rappresentata utilizzando un elemento `Tuple` che contiene elementi `Member` di ogni gerarchia sull'asse.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del `Tuple` elemento quando un client specifica *TupleFormat* o *CustomFormat* per il `AxisFormat` proprietà XMLA, data la seguente membri per l'asse:  
  
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
  
  